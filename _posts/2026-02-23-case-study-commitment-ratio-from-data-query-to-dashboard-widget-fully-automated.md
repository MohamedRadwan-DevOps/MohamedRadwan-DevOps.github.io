---
layout: post
title: "Case Study: Commitment Ratio — From Data Query to Dashboard Widget (Fully Automated)"
date: 2026-02-23 08:00:00 +0000
pin: true
---

# Case Study: Commitment Ratio  
## From Data Query to Dashboard Widget (Fully Automated)

In the previous posts, we discussed architecture, data retrieval patterns, status evaluation logic, and dashboard publication. This post brings everything together through a concrete, end-to-end example: the Commitment Ratio KPI.

Rather than describing components independently, this case study walks through the full lifecycle of the KPI as it executes inside Azure DevOps. It explains what happens at each stage, how time is handled, how determinism is preserved, and how governance is enforced.

Commitment Ratio is a useful example because it appears simple on the surface. In practice, it exposes every architectural decision required to build KPIs correctly.

# The Timeline of a Single KPI Run

Before diving into code and endpoints, it is important to understand the execution timeline. A KPI run is not just a calculation. It is a sequence of controlled operations executed by a pipeline under a governed identity.

A typical execution unfolds as follows:

1. A scheduled or manual pipeline trigger starts the KPI execution.
2. The pipeline loads KPI configuration from the repository.
3. The pipeline retrieves iteration metadata using REST.
4. For each iteration, snapshot counts are retrieved using Analytics OData.
5. The ratio is calculated deterministically.
6. Threshold evaluation logic assigns a RAG status.
7. Markdown output is constructed.
8. The dashboard widget is updated via REST.
9. The pipeline logs the entire execution for traceability.

Each step depends on the correctness of the previous one. The value seen on the dashboard is the final artifact of this controlled sequence.

# Step 1: Formalizing the KPI Definition

The Commitment Ratio KPI is defined as:

```bash
Planned = Count(UserStories at iteration start date)
Completed = Count(UserStories with StateCategory = Completed at iteration end date)

CommitmentRatio = Completed / Planned
```

This definition forces two architectural requirements.

First, we must retrieve iteration boundaries accurately. Second, we must evaluate work item state at those exact historical boundaries. Any deviation from those requirements introduces inconsistency.

This is why the KPI cannot rely on current-state queries alone.

# Step 2: Retrieving Iteration Boundaries

The first data operation retrieves completed iterations for the team:

```bash
GET https://dev.azure.com/{organization}/{project}/{team}/_apis/work/teamsettings/iterations?timeframe=past&includeIterationDates=true
```

From this response, the script extracts:

- Iteration path
- Start date
- Finish date

These values define the temporal anchors of the KPI.

At this stage, no work item counts are calculated. The system is establishing the time frame within which the KPI will be evaluated. This separation between structural time and data state is intentional and essential.

# Step 3: Snapshot Evaluation at Sprint Boundaries

Once iteration boundaries are known, the KPI framework evaluates work items at two points in time.

From your implementation:

```powershell
$filter = "DateValue eq $d and WorkItemType eq '$witEsc' and Iteration/IterationPath eq '$iterEsc'"
if ($CompletedOnly) { $filter += " and StateCategory eq 'Completed'" }

$apply = "filter($filter)/aggregate(`$count as Count)"
```

This logic produces deterministic counts because:

- DateValue fixes evaluation to a specific day.
- IterationPath scopes the query to a sprint.
- StateCategory ensures completion logic is explicit.
- Aggregation happens server-side.

At sprint start, the system calculates Planned.  
At sprint end, the system calculates Completed.

This guarantees that even if a work item is moved after the sprint concludes, the historical evaluation remains stable.

# Step 4: Deterministic Ratio Calculation

Once counts are retrieved, the ratio calculation is straightforward. However, robustness must be enforced.

For example:

- If Planned equals zero, division must not fail.
- If snapshot data is temporarily unavailable, fallback behavior must be predictable.
- Percentages must be normalized consistently.

This stage transforms historical state into a numeric value that represents delivery predictability for that sprint.

The key principle is that this calculation must always produce the same result when given the same inputs.

# Step 5: Applying RAG Evaluation

Numeric values alone are insufficient for executive reporting. The system therefore applies governed threshold logic.

From your implementation:

```powershell
if ($pct -lt $RedMax) {
    $status = "Red"
}
elseif ($pct -lt $AmberMax) {
    $status = "Amber"
}
else {
    $status = "Green"
}
```

Threshold values are loaded from configuration. This means governance decisions are version-controlled and traceable.

If leadership adjusts acceptable performance levels, that change is committed and reviewed like any other code modification.

The evaluation layer converts a ratio into a decision signal.

# Step 6: Constructing Dashboard Output

The KPI framework then constructs Markdown output dynamically. The content includes raw values, calculated percentages, and evaluated RAG indicators.

A rendered result might appear as:

```markdown
## Commitment Ratio

| Metric | Sprint 14 | Sprint 15 | Sprint 16 |
|--------|-----------|-----------|-----------|
| Planned Stories | 22 | 18 | 25 |
| Completed Stories | 17 | 16 | 21 |
| Commitment Ratio | 🟠 77% | 🟢 89% | 🟢 84% |
```

This output is not manually curated. It is generated programmatically and passed directly into the dashboard widget API.

The dashboard becomes the presentation layer of the codebase.

# Step 7: Publishing via REST

The final operational step updates the Markdown widget using the Dashboard REST API through your New-MarkdownWidget function.

This step ensures:

- The correct dashboard is targeted.
- The widget position is preserved.
- The layout remains stable.
- Content is replaced deterministically.

If the pipeline runs again, the widget updates consistently. No duplication occurs. No layout corruption appears.

The KPI becomes a continuously refreshed artifact of pipeline execution.

# Governance and Auditability Across the Timeline

The real strength of this architecture appears when someone challenges a KPI value.

If a stakeholder questions Sprint 15’s Commitment Ratio, the framework provides:

- The exact sprint start and finish dates retrieved via REST.
- The OData snapshot filters used for counts.
- The formula version from source control.
- The threshold configuration applied.
- The pipeline run ID.
- The service account that executed the run.

This is not manual justification. It is architectural traceability.

Because every stage is engineered, the KPI becomes defensible.

# Scaling the Pattern Beyond Commitment Ratio

Although this case study focuses on Commitment Ratio, the pattern applies across other KPIs.

For example:

- Defects Leakage evaluates defect state transitions across environments using snapshot queries.
- Rejection Rate calculates ratio of rejected defects relative to logged defects.
- Deployment Frequency aggregates pipeline runs across defined time windows.

In each case, the timeline remains consistent:

Structural metadata → Snapshot evaluation → Formula application → Status evaluation → Dashboard publication.

The KPI changes. The lifecycle does not.

# Why This Case Study Is Foundational

Commitment Ratio demonstrates that KPI engineering is not about charts. It is about discipline.

It requires:

- Respecting time boundaries.
- Separating operational and historical data.
- Applying deterministic formulas.
- Enforcing governed threshold logic.
- Publishing results natively.
- Maintaining auditability.

When all of these elements operate together, the KPI ceases to be a manual reporting exercise. It becomes a governed system component inside Azure DevOps.

# What Comes Next

In the next post, we will extend the visualization layer further by introducing dynamic chart generation within pipelines and image hosting inside Azure Repos, enabling richer dashboard experiences while remaining fully native and governed.
