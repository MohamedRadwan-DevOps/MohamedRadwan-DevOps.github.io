---
layout: post
title: "Charts in Markdown Widgets: Generating PNGs in Pipelines and Hosting in Repos"
date: 2026-03-02 08:00:00 +0000
pin: true
---

# Charts in Markdown Widgets  
## Generating PNGs in Pipelines and Hosting in Repos

In the previous post, the KPI lifecycle was completed by publishing structured Markdown tables directly into Azure DevOps dashboards. While this approach provides deterministic and native reporting, it has a limitation: Markdown widgets cannot render dynamic charts from raw data.

For enterprise stakeholders, visual trend representation is often as important as numeric values. A table communicates detail. A chart communicates direction.

This post explains how the KPI framework was extended to generate chart images inside Azure Pipelines and publish them natively in Markdown widgets, without using extensions or external services.

Before explaining the image-generation approach, it is important to understand that this was not the original design intention.

# Why Mermaid Was the First Design Choice

Mermaid is an open-source JavaScript-based diagramming and charting framework that allows diagrams and charts to be defined using text-based syntax. Its official site is:

[https://mermaid.js.org](https://mermaid.js.org)

Mermaid supports multiple diagram types, including flowcharts, sequence diagrams, class diagrams, Gantt charts, pie charts, and more recently, X/Y charts. The architectural value of Mermaid lies in its philosophy: diagrams become text, text becomes version-controlled, and visualization becomes part of the codebase.

For a KPI-as-code framework, this is ideal. Visualization logic remains in source control. It becomes reviewable, traceable, and reproducible through pull requests and commits.

# Mermaid X/Y Charts and GitHub Support

Mermaid introduced X/Y charts under the `xychart-beta` syntax. Documentation is available at:

[https://mermaid.js.org/syntax/xyChart.html](https://mermaid.js.org/syntax/xyChart.html)

GitHub supports Mermaid rendering directly within Markdown files, including X/Y charts in beta. The following example renders correctly on GitHub:

## Commitment Ratio

**Definition:**  
`Commitment ratio = Completed Stories / Planned Stories`

### Data

| Metric | Sep-25 | Oct-25 | Nov-25 | Dec-25 |
|---|---:|---:|---:|---:|
| Planned Stories | 5 | 4 | 5 | 6 |
| Completed Stories | 3 | 2 | 5 | 5 |
| Commitment ratio | 60% | 50% | 100% | 83% |

### Chart (Mermaid)

```markdown
xychart-beta
  title "Commitment ratio"
  x-axis ["Sep-25","Oct-25","Nov-25","Dec-25"]
  y-axis "Percentage" 0 --> 120
  line "Commitment ratio" [60,50,100,83]
```

On GitHub, this chart renders directly from text. No image generation is required. The chart definition is version-controlled, auditable, and fully native to Markdown.

From an architectural perspective, this represents the cleanest possible solution for KPI visualization.

# The Limitation: Azure DevOps Does Not Yet Support Mermaid X/Y Charts

At the time of implementation, Azure DevOps Markdown widgets do not support Mermaid rendering for X/Y charts. Even though GitHub renders these diagrams natively, Azure DevOps does not interpret Mermaid syntax in its Markdown widgets.

Because of this limitation, charts defined using Mermaid syntax do not render inside Azure DevOps dashboards.

The expectation is that Mermaid support, including X/Y charts, will eventually become available in Azure DevOps. When that happens, image generation will no longer be required. Visualization can return to being pure text under version control, aligning perfectly with the KPI-as-code philosophy.

Until that capability becomes available, an alternative rendering mechanism was required.

That alternative was deterministic image generation inside the pipeline.


# Why Markdown Alone Is Not Enough in Azure DevOps

Azure DevOps Markdown widgets allow formatted text, structured tables, and embedded images. They do not currently support dynamic chart rendering from raw data or Mermaid X/Y syntax.

For enterprise reporting, numerical tables are important, but trend visualization plays a different role. A table communicates precision and detail. A chart communicates direction, stability, and trajectory over time. Leadership often consumes trend information faster visually than numerically.

Because Mermaid X/Y charts are not yet supported inside Azure DevOps dashboards, visualization logic could not remain purely text-based. The system required a rendering mechanism that would:

- Remain fully automated  
- Stay native to Azure DevOps  
- Avoid external BI platforms  
- Preserve governance boundaries  

The solution was to shift visualization into the pipeline execution layer.

# The Visualization Architecture

Once chart rendering could not occur natively inside Markdown, the visualization lifecycle was redesigned as follows:

- KPI values are calculated.  
- Chart-ready data arrays are prepared.  
- A PNG image is generated inside the pipeline.  
- The generated image is committed to a repository.  
- The Markdown widget embeds the raw image URL.  

This architecture preserves all core design principles of the KPI framework:

- Deterministic execution  
- Version control  
- Governance alignment  
- No external runtime dependencies  

The dashboard does not generate the chart. The pipeline does.

# Generating Charts Inside the Pipeline

The KPI pipeline includes a rendering step using Python and matplotlib. The pipeline installs matplotlib at runtime:

```yaml
- bash: |
    python3 -m pip install --upgrade pip
    python3 -m pip install --user matplotlib
  displayName: 'Install matplotlib (for chart generation)'
```

The PowerShell automation then dynamically constructs and executes a Python script to generate the PNG:

```powershell
$py = @"
import matplotlib.pyplot as plt
months = [$monthsPy]
ratios = [$ratiosPy]

plt.figure(figsize=($WidthIn, $HeightIn))
plt.plot(months, ratios, marker="o")
plt.ylim(0, $yMax)
plt.xlabel("Sprint / Month")
plt.ylabel("Percentage")
plt.title("Commitment Ratio")
plt.grid(True, linewidth=0.5)

for x, y in zip(months, ratios):
    plt.text(x, y + 2, f"{y}%", ha="center", va="bottom")

plt.tight_layout()
plt.savefig(r"$OutFile", dpi=$Dpi)
plt.close()
"@
```

This ensures:

- Charts are generated deterministically.  
- No external visualization service is required.  
- Styling is controlled in code.  
- Historical charts are reproducible.  

The pipeline becomes both the calculation engine and the rendering engine.


# Deterministic Rendering as a Governance Requirement

Rendering inside the pipeline is not just a workaround. It preserves governance properties.

Because the image is generated during pipeline execution:

- The exact data used for rendering is known.  
- The rendering logic is version-controlled.  
- The visual output corresponds to a specific pipeline run.  
- The execution identity is governed.  

The chart is not an external artifact. It is a traceable product of pipeline execution.

# Why Store Generated Images in a Repository

Once a chart image is generated inside the pipeline, it must be accessible to the Markdown widget. Azure DevOps Markdown widgets require a URL reference to embed an image.

Rather than relying on external storage such as blob services or third-party hosting, the generated PNG is committed into a Git repository. This keeps visualization artifacts under the same governance model as KPI logic.

From the automation layer:

```powershell
Commit-FileToRepo -OrgUrl $cfg.ImageOrgUrl `
  -Project $cfg.ImageProject `
  -RepoName $cfg.ImageRepo `
  -BranchName $cfg.ImageBranch `
  -Pat $ImagePat `
  -FilePath $localPng `
  -RepoRelPath $imageRelPath
```

This achieves several architectural objectives:

- Images are version-controlled.  
- Historical visual artifacts are preserved.  
- Access control is enforced through repository permissions.  
- No external hosting dependency is introduced.  

The Markdown widget embeds the raw repository URL, making the dashboard a direct consumer of versioned artifacts.

# Raw Image Embedding in Markdown

Once committed, the image is referenced through a raw file endpoint and embedded into the Markdown content:

```markdown
![](https://dev.azure.com/{organization}/{project}/_apis/git/repositories/{repo}/items?path=/charts/commitment-ratio-20260302.png&download=true)
```

Because the image resides in a repository branch, it inherits all governance properties of that repository, including access control, branch policies, and history retention.

The dashboard does not store the image. It renders the referenced artifact.

# Two-Organization Design Pattern

The implementation supports separation between the operational environment and the image storage environment.

One organization may host:

- KPI execution pipelines  
- Dashboards  
- Data retrieval  

Another organization may host:

- Visualization artifacts  
- Dedicated image repositories  

This separation allows enterprises to enforce different permission boundaries and operational controls while maintaining automation continuity.

The script also supports fallback behavior, enabling a single-organization configuration when required. This flexibility allows the architecture to adapt to different enterprise structures without redesign.

# Image Versioning and Idempotency

Each generated chart image includes a timestamp or unique identifier before being committed. This ensures that:

- Concurrent runs do not overwrite each other unintentionally.  
- Historical visualizations remain available.  
- Dashboards can reference a specific committed artifact.  

Idempotency is preserved at two levels:

First, dashboard widgets are updated deterministically, replacing content without duplicating layout elements.  
Second, image generation produces unique artifacts while maintaining controlled references.

This prevents automation from degrading the dashboard experience over time.

# Security and Governance Alignment

Image repository access must align with least privilege principles.

The identity responsible for committing images must:

- Have write access only to the designated image repository.  
- Operate under defined credential rotation policies.  
- Be auditable through pipeline logs.  
- Avoid elevated administrative privileges.  

Separation of identities between KPI execution and image storage can further reinforce least-privilege enforcement.

Because images are stored inside Azure DevOps repositories, the entire lifecycle remains within the governed DevOps platform.

# Architectural Reflection

The original architectural preference was to use Mermaid X/Y charts directly in Markdown. GitHub already supports this rendering model, including the `xychart-beta` syntax. Azure DevOps does not yet render Mermaid charts in Markdown widgets.

The image-generation approach therefore serves as a deterministic and governed workaround.

When Azure DevOps introduces Mermaid support for X/Y charts, the visualization layer can be simplified significantly:

- Chart definitions will remain pure text.  
- No image generation will be required.  
- No repository storage of images will be needed.  
- Visualization will become fully declarative and version-controlled.  

Until that support becomes available, pipeline-based image rendering provides a stable, enterprise-ready solution.

# End-to-End Visualization Lifecycle

The complete visualization lifecycle now becomes:

1. Retrieve data via REST and Analytics.  
2. Compute KPI values.  
3. Apply threshold evaluation.  
4. Generate chart image inside the pipeline.  
5. Commit image to repository.  
6. Embed raw image URL into Markdown.  
7. Update dashboard widget.  

The KPI framework now spans computation, evaluation, rendering, and publication, entirely within Azure DevOps.

# Why This Approach Is Architecturally Strong

The visualization layer introduced in this post is not simply a workaround for a missing feature. It reinforces the same architectural principles that govern the rest of the KPI framework.

The solution uses:

- Azure Pipelines for deterministic rendering.
- Azure Repos for governed artifact storage.
- REST APIs for dashboard publication.
- Markdown widgets for native presentation.

No external BI platform is required. No third-party hosting is introduced. No unmanaged rendering logic is embedded inside dashboards.

Each component remains:

- Version-controlled.
- Auditable.
- Governed by Azure DevOps permissions.
- Executed through traceable pipeline runs.

Even the generated chart image becomes a governed artifact under source control.

The system remains cohesive and native.

When Mermaid X/Y chart support becomes available in Azure DevOps, the architecture simplifies further. The image-generation layer can be removed cleanly because visualization logic will already exist in declarative text form.

That future transition will not require redesign. It will only require removing a rendering step.

This is a sign of strong architectural design: adaptability without structural disruption.

# What Comes Next

In the next post, the focus shifts toward enterprise hardening patterns. Topics will include configuration resolution, secret management, idempotent execution strategies, and defensive error handling inside automation scripts.

The goal is to move from a functional KPI framework to a production-grade, enterprise-ready platform pattern.