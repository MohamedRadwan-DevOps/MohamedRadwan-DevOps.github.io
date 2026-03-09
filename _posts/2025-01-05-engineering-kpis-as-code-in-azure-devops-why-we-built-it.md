---
date: "2025-01-05 08:00:00 +0000"
layout: post
pin: true
title: "Engineering KPIs as Code in Azure DevOps: Why We Built It"
---

## Engineering KPIs as Code in Azure DevOps: Why We Built It

Azure DevOps provides built-in dashboards and reporting views across
Boards, Pipelines, and Test Plans. However, enterprise delivery
organizations often require KPIs that combine multiple dimensions of
data, apply custom formulas, and enforce governance rules that go beyond
what the platform exposes natively.

In our case, the KPI portfolio included a wide range of delivery and
quality indicators. Examples included:

-   Commitment Ratio
-   Defects Leakage across phases
-   Defect Rejection Rate
-   Defect Detection Rate

These are representative examples of the type of KPIs the program
required, not the full list. The broader initiative covered multiple
metrics across delivery predictability, testing effectiveness, and
quality governance.

None of these composite KPIs are available as first-class, configurable
metrics in Azure DevOps. Even in environments where Marketplace
extensions are permitted, there is no built-in extension that provides
these KPIs with customizable formulas, snapshot-based evaluation, and
enterprise-level RAG governance. In our environment, the situation was
more restrictive: strict least-privilege governance prevented installing
extensions or integrating external reporting tools. Even if such an
extension existed, it would not have been allowed in production.

This forced a fundamental architectural question:

How can we build a scalable, automated KPI framework entirely inside
Azure DevOps using only native capabilities?

------------------------------------------------------------------------

## The Real Operational Problem

At first glance, calculating a KPI such as Commitment Ratio appears
simple:

> Commitment Ratio = Completed Stories / Planned Stories

But once we examined the definition more closely, the complexity became
clear.

What exactly counts as "Planned Stories"?\
Is it the number of stories assigned to the sprint at the end?\
Or the number of stories present at the start of the sprint?

What qualifies as "Completed"?\
Is it state = Done?\
Or StateCategory = Completed?\
What about stories moved between sprints mid-iteration?

What happens if Planned Stories equals zero?\
How do we evaluate RAG thresholds?\
Are thresholds static or configurable?

When these questions are answered informally in spreadsheets, logic
becomes inconsistent. Different teams interpret definitions differently.
Historical recalculations become unreliable because the calculation
context is lost.

Before automation, the process followed a manual workflow:

1.  Retrieve iteration data.
2.  Query work items.
3.  Count planned and completed stories.
4.  Calculate percentage.
5.  Apply RAG thresholds.
6.  Update slide deck.
7.  Present in review meeting.

Every sprint repeated the same steps. Each step introduced potential
inconsistency. Most importantly, there was no traceable system governing
how formulas evolved over time.

The KPI existed as a number. It did not exist as engineered logic.

------------------------------------------------------------------------

## Architectural Constraints That Shaped the Solution

The solution had to operate under strict constraints:

-   No Marketplace extensions.
-   No external reporting systems.
-   No custom databases.
-   Least-privilege access model.
-   Full traceability and auditability required.
-   Scalability to support an expanding KPI portfolio.

Additionally, Azure DevOps separates operational APIs from reporting
APIs. Operational REST endpoints are designed for current-state data and
object manipulation. Historical and snapshot-based reporting is exposed
through Analytics OData. Many teams mistakenly attempt to build trend
KPIs using operational endpoints, which leads to inconsistent historical
evaluation.

Any sustainable solution had to respect this architectural separation.

------------------------------------------------------------------------

## Reframing the Problem: KPI as a Deterministic Function

The turning point was redefining the KPI not as a report, but as a
deterministic function.

A KPI can be modeled as:

``` bash
KPI = f(DataSource, Formula, Parameters, Thresholds)
```

For Commitment Ratio, this becomes:

``` bash
Planned = Count(UserStories at iteration start date)
Completed = Count(UserStories with StateCategory = Completed at iteration end date)

Ratio = Completed / Planned

If Ratio < 50%  -> Red
If Ratio < 70%  -> Amber
Else            -> Green
```

Once defined in this way, the KPI is no longer a slide artifact. It
becomes executable logic.

And executable logic belongs in source control.

------------------------------------------------------------------------

## KPI as Code: The Foundational Principle

We established a simple rule:

Every KPI must be implemented as version-controlled code, executed
through Azure Pipelines, and published back into Azure DevOps dashboards
automatically.

This approach introduced several structural improvements.

First, formulas became explicit. Instead of being embedded in
spreadsheets, they were written in script files stored in Azure Repos.
If the formula changed, the change was committed and traceable.

Second, thresholds became configurable parameters rather than hard-coded
assumptions. This allowed governance bodies to adjust RAG evaluation
without rewriting the entire logic.

Third, execution became automated. Azure Pipelines could run KPI
calculations on schedule or on demand, ensuring consistency across
iterations.

Fourth, publication became native. Instead of exporting results
externally, we used Azure DevOps REST APIs to update Markdown widgets
directly on team dashboards.

The KPI was no longer computed by a person. It was computed by the
system.

------------------------------------------------------------------------

## Native Architecture Inside Azure DevOps

The architecture deliberately avoided external dependencies.

**Azure Repos**\
Stores KPI logic, configuration, reusable scripts, and version history.

**Azure Pipelines**\
Executes KPI scripts, retrieves data, evaluates formulas, and handles
scheduling.

**REST APIs**\
Used for operational tasks such as retrieving iteration metadata and
managing dashboards or widgets.

**Analytics OData**\
Used for historical and snapshot-based calculations such as counting
work items at a specific date.

For example, to compute Commitment Ratio correctly:

-   The Work REST API retrieves the list of past iterations with start
    and end dates.
-   Analytics OData queries the WorkItemSnapshot entity for counts at
    iteration boundaries.
-   The pipeline applies formula logic and RAG evaluation.
-   A Markdown widget is updated via REST to display results.

This combination ensures we use the right interface for the right
purpose.

Operational APIs handle object management and current-state retrieval.\
Analytics handles historical evaluation.

This separation prevents common reporting errors.

------------------------------------------------------------------------

## A Concrete Example: Commitment Ratio Automation Flow

To make this more tangible, here is the automated flow for a single KPI
run:

1.  Pipeline triggers (scheduled or manual).
2.  Script retrieves last four completed iterations via REST.
3.  For each iteration:
    -   Query WorkItemSnapshot at iteration start date.
    -   Query WorkItemSnapshot at iteration end date with StateCategory
        = Completed.
4.  Compute ratio.
5.  Evaluate RAG thresholds.
6.  Generate Markdown table.
7.  Optionally generate chart image via pipeline.
8.  Update dashboard widget using REST.

No manual recalculation.\
No spreadsheet.\
No presentation rework.

If someone asks how the number was derived, the answer is not "check the
slide." The answer is "check the repository and pipeline run."

------------------------------------------------------------------------

## Why This Approach Scales

The first KPI establishes the pattern. After that, adding new KPIs
becomes systematic:

-   Define formula.
-   Identify data source.
-   Define parameters.
-   Implement script.
-   Reuse pipeline execution model.
-   Publish result.

The same architecture supports Commitment Ratio and many other KPIs
across delivery, quality, and governance domains.

This is why we refer to the solution as a framework rather than a
script. The objective was not simply to automate one KPI. The objective
was to build a reusable KPI execution engine inside Azure DevOps.

------------------------------------------------------------------------

## The Strategic Outcome

By implementing KPIs as code:

-   Logic became traceable.
-   Threshold changes became reviewable.
-   Historical evaluation became consistent.
-   Execution became automated.
-   Governance aligned naturally with DevOps controls.

Most importantly, the KPI stopped being a presentation artifact and
became a governed capability embedded within the delivery platform.

In the next post, we will examine how least-privilege governance and the
absence of extensions directly shaped the architecture and forced a
native solution rather than an external one.

This is where engineering discipline meets reporting maturity.
