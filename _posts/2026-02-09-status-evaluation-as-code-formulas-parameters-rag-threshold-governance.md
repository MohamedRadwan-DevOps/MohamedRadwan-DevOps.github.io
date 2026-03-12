---
layout: post
title: "Status Evaluation as Code: Formulas, Parameters, and RAG Threshold Governance"
date: 2026-02-09 08:00:00 +0000
pin: true
---

# Status Evaluation as Code With RAG Threshold
## Formulas, Parameters, and RAG Threshold Governance

In the previous post, we focused on retrieving the correct data using REST for structure and Analytics OData for historical snapshots. Data retrieval alone, however, does not produce a KPI. The transformation from raw counts into actionable insight happens in the evaluation layer.

This is where many KPI implementations become inconsistent. Teams often retrieve correct data but apply threshold logic manually, inconsistently, or differently across teams. When that happens, the metric loses governance value.

In a KPI-as-code framework, status evaluation must be deterministic, parameterized, and version-controlled.

# From Ratio to Decision

Consider Commitment Ratio.

The raw formula is straightforward:

```bash
Ratio = Completed / Planned
```

However, stakeholders do not consume ratios alone. They consume status. Typically, that status is expressed through RAG logic:

- Red if performance is below a defined lower bound  
- Amber if performance is between defined thresholds  
- Green if performance meets or exceeds the target  

If these thresholds are applied manually, two risks appear:

1. Different teams interpret boundaries differently.  
2. Threshold changes are not traceable over time.  

This is why status evaluation must be implemented in code.

# Designing Threshold Logic

Threshold logic should never be hardcoded without abstraction. Instead, it must be driven by configuration.

For example, a configuration file might define:

```bash
{
  "RedThreshold": 50,
  "AmberThreshold": 70
}
```

The evaluation logic then becomes:

```bash
If Ratio < RedThreshold      -> Red
If Ratio < AmberThreshold    -> Amber
Else                         -> Green
```

This ensures:

- Consistency across environments.  
- Ability to adjust governance rules.  
- Version-controlled change history.  
- Reproducibility of historical KPI evaluations.  

The formula remains stable. The governance rules become configurable.

# Threshold Governance and Change Control

Thresholds are not technical constants. They are governance decisions.

For example:

- Leadership may raise the acceptable Commitment Ratio from 70 percent to 75 percent.  
- Quality teams may tighten defect leakage tolerances.  
- Deployment stability requirements may change after a major incident.  

When thresholds are embedded in source-controlled configuration:

- Changes require pull requests.  
- Reviews can be enforced.  
- Historical context is preserved.  
- Auditability is automatic.  

This is where KPI-as-code aligns with enterprise governance.

# Example: RAG Evaluation in Practice

Below is a simplified representation aligned with the approach used in the automation scripts.

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

This evaluation block ensures that the same logic is applied every time the pipeline runs.

If RedMax and AmberMax are configuration-driven values, then the evaluation remains stable while thresholds remain flexible.

# Multi-KPI Evaluation Pattern

A KPI framework should support multiple evaluation types.

For example:

- Ratio-based KPIs (Commitment Ratio)  
- Percentage-based KPIs (Defect Detection Rate)  
- Count-based KPIs (Escaped Defects)  
- Time-based KPIs (Average Lead Time)  

The evaluation engine should be generic.

Instead of writing unique evaluation logic for each KPI, the framework should:

1. Compute the numeric value.  
2. Load threshold configuration.  
3. Apply evaluation rules.  
4. Produce structured status output.  

This pattern ensures scalability across KPI categories.

# Handling Edge Cases

Robust evaluation logic must also handle edge cases.

For example:

- Planned stories equals zero.  
- No deployments occurred in a date range.  
- Missing data from Analytics.  
- Partial iteration data.  

A well-designed KPI framework should:

- Prevent divide-by-zero errors.  
- Return deterministic fallback values.  
- Log anomalies.  
- Preserve auditability.  

Without this, automation becomes fragile.

# Publishing Status as Structured Output

Once evaluation is complete, the KPI framework must generate structured output that includes:

- Numeric value  
- Status label  
- Threshold reference  
- Evaluation timestamp  
- Iteration or time window context  

For example, a Markdown table may include:

| Sprint | Planned | Completed | Ratio | Status |
|--------|---------|-----------|-------|--------|
| S12    | 20      | 14        | 70%   | Green  |

Because evaluation logic is deterministic, dashboard outputs remain consistent across runs.

# Why Evaluation Must Be Engineered

The evaluation layer is where KPI credibility is either strengthened or weakened.

If RAG status is subjective, stakeholders question it.  
If thresholds drift informally, comparisons lose meaning.  
If evaluation is not traceable, governance breaks down.  

By engineering status evaluation as code, you ensure:

- Consistent interpretation.  
- Configurable governance.  
- Version-controlled changes.  
- Reproducible results.  

This transforms a ratio into a decision mechanism.

# What Comes Next

In the next post, we will focus on publishing results natively inside Azure DevOps dashboards and explain how Markdown widgets and REST automation complete the KPI lifecycle.
