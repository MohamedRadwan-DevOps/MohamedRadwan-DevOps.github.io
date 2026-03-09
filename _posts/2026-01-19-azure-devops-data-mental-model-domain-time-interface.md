---
date: "2026-01-19 08:00:00 +0000"
layout: post
pin: true
title: "Azure DevOps Data Mental Model: Domain to Time to Interface
  (REST vs Analytics OData)"
---

# Azure DevOps Data Mental Model

## Domain to Time to Interface (REST vs Analytics OData)

Azure DevOps exposes data across multiple services such as Boards,
Pipelines, Test Plans, Repos, and Artifacts. Each of these services
provides operational REST APIs, and some of them are also available
through the Analytics OData endpoint for reporting scenarios.

When teams begin building KPIs, the most common mistake is starting with
an endpoint instead of starting with the question. They search for an
API that "looks close enough" and then attempt to shape the KPI around
the data they can easily retrieve. This often works for simple,
current-state queries, but it fails for reproducible, historical KPIs.

To avoid that trap, we use a structured decision flow:

Domain → Time → Interface

This mental model ensures that KPI logic is built on the correct data
foundation.

# Step 1: Choose the Domain

The first decision is not technical. It is conceptual.

You must decide which Azure DevOps service domain contains the data you
need.

## Azure Boards Domain

Azure Boards is the work tracking domain. It contains structured
entities such as user stories, product backlog items, bugs, tasks,
features, and epics. These entities have fields such as state, iteration
path, assigned user, and area path. They also contain state transition
history and metadata that influence delivery KPIs.

For example, if you need to calculate Commitment Ratio for Sprint 12,
you are operating in the Boards domain. You must retrieve work items
assigned to that iteration, evaluate their state at specific sprint
boundaries, and compute ratios.

Similarly, if you need to measure defect leakage between SIT and UAT
phases, and those phases are modeled through custom fields or iteration
paths, you are again operating inside the Boards domain.

## Azure Pipelines Domain

Azure Pipelines is the execution and deployment domain. It contains
pipeline definitions, runs, jobs, stages, results, and timestamps.

For example, if you need to calculate the number of successful
production deployments in March and April, you are in the Pipelines
domain. You must query pipeline run history and filter by environment or
stage, then aggregate by date range.

That is not Boards data. It is pipeline execution metadata.

## Azure Test Domain

Azure Test Plans contains structured test execution information,
including test runs, test results, pass and fail outcomes, and
configuration data.

If your KPI measures test pass rate trend across the last five sprints,
or defect detection efficiency during UAT, then your primary domain is
Test.

Choosing the correct domain first prevents mixing unrelated data models
and simplifies the next decisions.

# Step 2: Choose the Time Behavior

After selecting the domain, you must decide whether you need
current-state data or historical data.

This distinction is critical for KPI design.

## Current-State Data

Current-state data answers questions about the system as it exists right
now.

For example:

"How many active bugs are currently in the 'Active' state in the
Production area path?"

That question does not require historical reconstruction. It requires
the latest saved values in Azure Boards. REST APIs are sufficient.

Another example:

"What is the result of the latest run of pipeline 'Prod-Deployment'?"

Again, that is current state. Operational APIs are designed for this.

## Historical or Snapshot Data

Historical data answers questions about how things changed over time or
what the state was at a specific moment.

For example:

"How many user stories were committed at the start of Sprint 12, and how
many were completed by the sprint end date?"

That requires evaluating work items at two distinct timestamps. Current
state is not enough, because work items may have moved or changed state
after the sprint ended.

Another example:

"How many successful production deployments occurred between March 1 and
April 30?"

This requires filtering pipeline runs by completion date and
environment, and grouping results across a defined time window.

Historical KPIs require snapshot-capable data sources.

# Step 3: Choose the Interface

Once domain and time behavior are clear, the interface selection becomes
straightforward.

Azure DevOps supports two primary access patterns.

# Operational Access Using REST APIs

REST APIs are designed for operational control and current-state
retrieval.

They are appropriate when you need to:

-   Create, update, or delete objects.
-   Retrieve the latest stored values of work items.
-   Trigger pipeline runs.
-   Manage dashboards and widgets.
-   Retrieve iteration metadata.

For example, retrieving the list of iterations for a team typically uses
an endpoint like:

https://dev.azure.com/{organization}/{project}/{team}/\_apis/work/teamsettings/iterations

Similarly, updating a dashboard widget uses the Dashboard REST API.

REST APIs return the latest state of the entity. They do not provide
historical snapshots of past states.

For KPI frameworks, REST is often used to orchestrate execution and
manage presentation layers.

# Reporting Access Using Analytics OData

Analytics OData is designed for reporting and trend analysis.

It provides structured entities such as:

-   WorkItemSnapshot
-   PipelineRuns
-   TestResultsDaily

These entities are optimized for time-based grouping, filtering, and
aggregation.

For example, to calculate Commitment Ratio correctly, you must count
work items at sprint start and sprint end. The WorkItemSnapshot entity
allows you to filter by DateValue and IterationPath to retrieve counts
at those exact dates.

A simplified OData query might look like:

https://analytics.dev.azure.com/{organization}/{project}/\_odata/v2.0/WorkItemSnapshot

Similarly, to calculate deployment frequency across March and April, you
would query PipelineRuns and filter by CompletedDate and
EnvironmentName, then aggregate results across the defined date range.

Analytics OData is read-only and structured for reporting. It is not
used for operational control.

# Where WIQL Fits

WIQL, or Work Item Query Language, belongs inside the Boards REST
surface. It is useful for filtering work items based on field criteria.

For example, you can use WIQL to retrieve IDs of all active user stories
in the current iteration. However, WIQL returns current-state results.
It does not provide historical snapshots.

Therefore, WIQL is appropriate for operational queries but not for
historical KPI trend calculations.

Understanding this prevents one of the most common mistakes in Azure
DevOps reporting.

# Applying the Model to Real KPI Scenarios

Let us apply Domain → Time → Interface to real use cases.

Use Case 1: Commitment Ratio for Sprint 12\
Domain: Boards\
Time: Snapshot at sprint start and sprint end\
Interface: REST for iteration metadata, Analytics OData for snapshot
counts

Use Case 2: Production Deployment Frequency for March and April\
Domain: Pipelines\
Time: Historical trend across a date range\
Interface: Analytics OData

Use Case 3: Current Active Defects in Production Area\
Domain: Boards\
Time: Current state\
Interface: REST with WIQL

The decision flow is consistent across domains.

# Why This Model Is Critical for KPI as Code

The KPI-as-code framework depends on reproducibility. If a KPI cannot be
recalculated consistently for past periods, it cannot be governed.

By enforcing Domain → Time → Interface:

-   Operational actions use REST.
-   Historical reporting uses Analytics.
-   Filtering logic stays within its appropriate boundary.
-   Snapshot-based KPIs remain stable over time.

This model is not just conceptual clarity. It is an architectural
safeguard that ensures KPIs remain accurate as the system evolves.

# What Comes Next

In the next post, we will build on this mental model and show how KPI
logic is structured as versioned, reusable code inside Azure Repos. We
will move from choosing the correct interface to designing the KPI
execution pattern itself.
