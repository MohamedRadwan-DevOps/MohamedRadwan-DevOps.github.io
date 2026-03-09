---
date: "2026-01-26 08:00:00 +0000"
layout: post
pin: true
title: "Designing KPI as Code: Versioned Logic, Reusable Patterns,
  Traceability"
---

# Designing KPI as Code

## Versioned Logic, Reusable Patterns, Traceability

In the previous posts, we established three foundations. First, KPIs
must be engineered natively inside Azure DevOps rather than relying on
external extensions. Second, enterprise constraints such as least
privilege shape architecture decisions. Third, selecting the correct
data access pattern requires following the Domain to Time to Interface
model.

This post moves from principles to implementation structure. It explains
how KPI logic should be designed when treated as version-controlled
engineering artifacts instead of manual reports.

The shift from "reporting automation" to "KPI as code" is not cosmetic.
It fundamentally changes how metrics are defined, governed, and evolved.

# From Calculation to Definition

Most teams automate KPIs by scripting a calculation. That is only the
first step.

Designing KPI as code means formally defining what a KPI is before
implementing how it runs.

Every KPI should have:

-   A clearly defined data domain
-   A deterministic formula
-   Explicit parameters
-   Governed threshold logic
-   Defined output format

For example, Commitment Ratio can be defined precisely as:

``` bash
Planned = Count(UserStories at iteration start date)
Completed = Count(UserStories with StateCategory = Completed at iteration end date)

Ratio = Completed / Planned
```

That definition is not documentation. It becomes executable logic stored
in source control.

Once defined this way, the KPI is no longer dependent on a spreadsheet
owner. It becomes part of the system.

# Repository Structure for KPI as Code

A mature KPI framework should have a structured repository layout. For
example:

``` bash
/kpi-framework
  /config
    commitment-ratio.json
    defect-leakage.json
  /scripts
    get-iterations.ps1
    get-workitems-snapshot.ps1
    evaluate-thresholds.ps1
    publish-dashboard.ps1
  /pipelines
    kpi-execution.yml
```

This separation allows:

-   Configuration files to define KPI behavior.
-   Scripts to implement reusable logic.
-   Pipeline definitions to orchestrate execution.

When a new KPI is introduced, you add a configuration file and, if
needed, extend formula logic. You do not redesign the framework.

This is what makes the solution scalable.

# Separating Definition from Execution

One of the most important architectural decisions is separating KPI
definition from execution orchestration.

The definition layer contains:

-   Formula logic
-   Threshold configuration
-   Domain-specific filters
-   Iteration windows

The execution layer contains:

-   Pipeline triggers
-   Scheduling configuration
-   Service account identity
-   Dashboard publishing logic

For example, if stakeholders decide that Amber should start at 75
percent instead of 70 percent, that change belongs in the configuration
layer. The execution pipeline should not need modification.

This separation ensures that KPI evolution does not break automation.

# Configuration-Driven Design

Hardcoding logic is the fastest way to limit scalability.

Instead, KPIs should be configuration-driven. For example:

``` bash
{
  "KPIName": "CommitmentRatio",
  "Domain": "Boards",
  "WorkItemType": "User Story",
  "RedThreshold": 50,
  "AmberThreshold": 70,
  "SprintWindow": 4
}
```

This configuration allows the same execution engine to process different
KPIs by reading structured parameters.

For example:

-   Changing SprintWindow from 4 to 6 adjusts historical scope.
-   Changing WorkItemType supports Product Backlog Item instead of User
    Story.
-   Changing thresholds modifies RAG evaluation without altering formula
    code.

Configuration becomes governance.

# Reusable Execution Pattern

Every KPI should follow the same execution lifecycle.

1.  Load KPI configuration.
2.  Retrieve metadata via REST.
3.  Retrieve historical or operational data.
4.  Apply formula.
5.  Evaluate thresholds.
6.  Generate structured output.
7.  Publish to dashboard.
8.  Log execution metadata.

This pattern must remain constant across all KPIs.

For example:

Commitment Ratio uses iteration boundaries and WorkItemSnapshot.
Defects Leakage uses work item filters across phases.
Deployment Frequency uses PipelineRuns grouped by date range.

The formula changes. The execution pattern does not.

That consistency reduces operational complexity.

# Traceability as a First-Class Requirement

Traceability is often treated as a reporting afterthought. In KPI as
code, it is built in.

Because logic is version-controlled:

-   Every formula change is a commit.
-   Every threshold adjustment has a timestamp.
-   Every KPI addition can require pull request approval.
-   Every execution is logged by Azure Pipelines.

This creates full traceability across the lifecycle:

-   Which commit defined the formula?
-   Which configuration version was used?
-   Which pipeline run generated the dashboard?
-   Which service account executed it?

When stakeholders question numbers, the response is not recalculation.
It is traceability.

This increases trust in KPIs.

# Deterministic Recalculation

One of the hidden advantages of KPI as code is deterministic
recalculation.

Because the system stores:

-   Formula logic
-   Configuration parameters
-   Execution logs
-   Snapshot-based data access

You can reproduce historical KPI results consistently.

For example, if Sprint 10 Commitment Ratio was 62 percent six months
ago, you can re-run the logic against the same sprint boundaries and
verify the same result.

Manual reporting rarely offers that guarantee.

# Designing for Multiple KPI Categories

A KPI framework must anticipate growth.

Initially, you may implement:

-   Commitment Ratio
-   Defects Leakage
-   Rejection Rate

Later, stakeholders may request:

-   Escaped Defect Ratio
-   Average Lead Time
-   Deployment Stability Index
-   Test Automation Coverage Ratio

If each KPI requires architectural redesign, the framework has failed.

By designing around reusable scripts, configuration-driven parameters,
and stable execution flow, the framework supports expansion without
structural change.

# Engineering Discipline Applied to Metrics

Software engineering principles apply directly to KPI design:

-   Version control for logic.
-   Code review for formula changes.
-   Separation of concerns.
-   Parameterization.
-   Deterministic execution.
-   Logging and observability.

Metrics should not be treated as presentation artifacts. They should be
treated as governed system components.

When you apply engineering discipline to KPIs, the organization gains
something more valuable than automation. It gains confidence in its
data.

# What Comes Next

In the next post, we will move deeper into the data retrieval layer and
show how REST iteration metadata and Analytics snapshot queries work
together to enable correct time-based KPI calculations.

This is where the theoretical model meets implementation detail.
