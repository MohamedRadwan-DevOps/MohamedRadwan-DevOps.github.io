---
layout: post
title: "Scaling the Framework: Adding Defects Leakage, Rejection Rate, and Detection Rate"
date: 2026-03-16 08:00:00 +0000
pin: true
---

# Scaling the KPI As Code Framework  
## Adding Defects Leakage, Rejection Rate, and Detection Rate

At this stage, the KPI framework is not only functional and hardened, it is extensible. The next architectural question is no longer how to calculate a KPI correctly, but how to scale the system safely as new KPIs are introduced.

Commitment Ratio demonstrated the execution lifecycle. However, enterprise delivery environments rarely operate with a single metric. Once stakeholders see deterministic and traceable results, they request additional indicators.

This post explores how the framework expands to support additional KPIs without redesigning the execution engine.

# The Expansion Problem

When new KPIs are introduced, teams often fall into one of two traps:

1. Copy the existing script and modify it slightly.
2. Build an entirely separate automation pipeline for each KPI.

Both approaches create long-term maintenance risk. Duplication increases drift. Separate pipelines increase operational overhead. Governance becomes fragmented.

The objective of a scalable KPI framework is to allow expansion without structural change.

# From Single KPI to KPI Portfolio

Consider three additional KPIs:

Defects Leakage  
Defect Rejection Rate  
Defect Detection Rate  

Each of these appears different from Commitment Ratio. However, when broken down architecturally, they follow the same pattern:

- Define domain.
- Define time window.
- Retrieve snapshot or operational data.
- Apply formula.
- Evaluate thresholds.
- Publish results.

The framework does not change. Only the configuration and formula logic change.

# Example: Defects Leakage

Defects Leakage typically measures how many defects escape from one phase into another. For example:

Leakage = Defects found in UAT that originated in SIT / Total defects identified in SIT

To compute this correctly:

- Domain is primarily Boards (if phases are modeled through iteration paths or custom fields).
- Time behavior may be sprint-based or release-based.
- Snapshot evaluation ensures historical accuracy.
- Threshold logic assigns acceptable leakage levels.

The same snapshot query pattern used for Commitment Ratio can be extended by filtering on:

- Custom field values
- StateCategory
- Iteration paths representing phases

The difference lies in filter logic, not execution lifecycle.

# Example: Defect Rejection Rate

Rejection Rate measures the percentage of logged defects that are later rejected as invalid.

RejectionRate = RejectedDefects / TotalLoggedDefects

This requires:

- Filtering work items by type “Bug”
- Filtering by resolution or state classification
- Evaluating over a defined time window
- Applying threshold logic

Again, the data retrieval pattern remains consistent:

- Structural time boundaries via REST (if sprint-based)
- Snapshot counts via Analytics
- Deterministic formula evaluation
- Configurable threshold assignment

The framework remains unchanged.

# Example: Defect Detection Rate

Detection Rate measures the effectiveness of test execution.

DetectionRate = DefectsDetected / TestsExecuted

This may combine Boards and Test data depending on modeling approach.

Architecturally, this introduces multi-domain retrieval:

- Boards for defect counts
- Test Plans for execution counts

The framework supports this because:

- Data retrieval functions are modular.
- Domain selection is explicit.
- Evaluation logic is independent of data source.

The expansion does not require redesign. It requires configuration and additional filter logic.

# Avoiding Code Duplication

To scale safely, formula logic should be modular.

For example:

- A generic ratio function
- A generic threshold evaluator
- A generic snapshot retrieval function
- A configuration-driven filter builder

New KPIs should reuse these components rather than reimplement them.

Instead of creating separate scripts, the framework can:

- Add new JSON configuration files.
- Extend filter logic parameters.
- Reuse execution pipeline definitions.

This keeps governance centralized.

# Threshold Diversity Across KPIs

Not all KPIs use identical thresholds.

For example:

- Commitment Ratio may define Red below 50 percent.
- Leakage may define Red above 15 percent.
- Detection Rate may define Red below 80 percent.

The evaluation engine must therefore support both:

- “Lower is worse” logic.
- “Higher is worse” logic.

This is achieved by parameterizing:

- Comparison direction
- Threshold boundaries
- Target orientation

Configuration drives behavior. Code remains stable.

# Governance at Scale

As KPI count increases, governance complexity grows.

Scaling the framework requires:

- Centralized configuration repository
- Consistent naming conventions
- Defined ownership per KPI
- Pull request review for threshold changes
- Clear documentation of definitions

Without governance discipline, a growing KPI portfolio becomes chaotic.

With the engineered framework, expansion remains controlled.

# Maintaining Determinism Across KPIs

Every KPI added to the framework must respect three invariants:

1. Data retrieval must be deterministic.
2. Formula logic must be version-controlled.
3. Status evaluation must be governed.

If a new KPI violates any of these principles, it should not be added without architectural adjustment.

This guardrail preserves long-term system integrity.

# From Framework to Platform

When multiple KPIs share:

- A common execution engine
- A common evaluation pattern
- A common publication layer
- A common governance model

The framework evolves into a KPI platform.

The organization moves from reporting metrics to operating a metric system.

That shift is architectural, not cosmetic.

# What Comes Next

In the next post, we will examine governance and ownership patterns for managing a KPI catalog at scale, including documentation standards, review cycles, and long-term roadmap alignment.
