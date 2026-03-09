---
layout: post
title: "Data Retrieval Patterns: Team Iterations (REST) and WorkItemSnapshot (Analytics OData)"
date: 2026-02-02 08:00:00 +0000
pin: true
---

# Data Retrieval Patterns  
## Team Iterations (REST) and WorkItemSnapshot (Analytics OData)

In the previous post, we defined what it means to design KPI logic as version-controlled, reusable code. That structure depends entirely on retrieving the correct data in the correct way. If the data retrieval layer is wrong, everything above it becomes unreliable.

This post focuses on one of the most important architectural patterns in KPI design: combining operational REST APIs with Analytics OData to produce deterministic, reproducible time-based metrics.

This pattern is not optional for sprint-based or historical KPIs. It is foundational.

# Why Iteration Boundaries Must Come from REST

Consider the Commitment Ratio KPI. The formula appears simple:

```bash
Ratio = Completed / Planned
```

However, the complexity lies in defining what “Planned” and “Completed” mean within the context of a sprint.

Planned must represent the count of work items present in the iteration at the sprint start date. Completed must represent the count of those items that were in a completed state at the sprint end date.

To determine sprint start and end dates programmatically, we use the Work REST API:

```http
GET https://dev.azure.com/{organization}/{project}/{team}/_apis/work/teamsettings/iterations?timeframe=past&includeIterationDates=true
```

This endpoint provides iteration name, iteration path, start date, and finish date.

REST gives us the structural time boundaries required for KPI evaluation.

However, REST alone cannot reconstruct historical state.

# Why Snapshot Data Is Required

Azure DevOps operational APIs return the latest stored values. They do not return how a work item looked on a specific past date.

This is where Analytics OData becomes essential.

The WorkItemSnapshot entity stores daily snapshots of work items. Each row represents how a work item appeared on a given DateValue.

This allows us to evaluate how many stories were in the sprint on the start date, how many were completed on the finish date, and what state distribution looked like at any specific point in time.

Without snapshot data, historical KPIs drift. A story moved after sprint completion would distort retrospective calculations.

# Concrete OData Filter Example

Below is a simplified example of querying WorkItemSnapshot to count planned stories at sprint start:

```http
GET https://analytics.dev.azure.com/{organization}/{project}/_odata/v2.0/WorkItemSnapshot?
$apply=filter(
    DateValue eq 2026-01-01T00:00:00Z and
    Iteration/IterationPath eq 'Project\Sprint 12' and
    WorkItemType eq 'User Story'
)/aggregate($count as Count)
```

To count completed stories at sprint end:

```http
GET https://analytics.dev.azure.com/{organization}/{project}/_odata/v2.0/WorkItemSnapshot?
$apply=filter(
    DateValue eq 2026-01-14T00:00:00Z and
    Iteration/IterationPath eq 'Project\Sprint 12' and
    StateCategory eq 'Completed'
)/aggregate($count as Count)
```

Notice what makes this deterministic: DateValue locks the evaluation to a specific day, IterationPath scopes to the sprint, StateCategory ensures correct completion classification, and aggregation returns structured counts.

# Short PowerShell Example Combining REST and Analytics (from your script)

```powershell
function Get-SnapshotCountLocal {
  param(
    [string]$OrgName,[string]$Project,[string]$ODataVersion,
    [datetime]$DateValue,[string]$IterationPath,[string]$WorkItemType,
    [bool]$CompletedOnly,[hashtable]$Headers
  )

  $d = $DateValue.ToString("yyyy-MM-dd") + "Z"
  $iterEsc = $IterationPath.Replace("'", "''")
  $witEsc  = $WorkItemType.Replace("'", "''")

  $filter = "DateValue eq $d and WorkItemType eq '$witEsc' and Iteration/IterationPath eq '$iterEsc'"
  if ($CompletedOnly) { $filter += " and StateCategory eq 'Completed'" }

  $apply = "filter($filter)/aggregate(`$count as Count)"
  $applyEnc = [uri]::EscapeDataString($apply)

  $url = "https://analytics.dev.azure.com/$OrgName/$Project/_odata/$ODataVersion/WorkItemSnapshot?`$apply=$applyEnc"
  $resp = Invoke-JsonGetLocal -Uri $url -Headers $Headers

  if ($resp.value -and $resp.value.Count -gt 0 -and $resp.value[0].Count -ne $null) {
    return [int]$resp.value[0].Count
  }
  return 0
}

$teamEnc = [uri]::EscapeDataString($Team)
$iterUrl = "$OrgUrl/$Project/$teamEnc/_apis/work/teamsettings/iterations?timeframe=past&includeIterationDates=true&api-version=7.1"

$iters = (Invoke-JsonGetLocal -Uri $iterUrl -Headers $Headers).value
```

This snippet shows the orchestration pattern: REST returns iteration boundaries and metadata, and Analytics OData returns point-in-time snapshot counts through a server-side aggregation query.

# Combining REST and Analytics in Practice

Let us walk through a practical scenario.

Objective: Calculate Commitment Ratio for the last four completed sprints.

Step 1: Retrieve past iterations using REST.  
Step 2: Sort by finish date and select the last four.  
Step 3: For each iteration, query WorkItemSnapshot at the start date and end date, compute planned and completed counts, then compute the ratio and evaluate thresholds.

This pattern guarantees reproducibility because the counts are tied to exact dates.

Without snapshot evaluation, historical KPIs drift over time.

# Example: Deployment Frequency Across March and April 2026

Now consider a Pipelines KPI.

Objective: Count successful production deployments between March 1 and April 30, 2026.

Domain: Pipelines  
Time: Historical date range  
Interface: Analytics OData  

An OData query might filter the PipelineRuns entity:

```http
GET https://analytics.dev.azure.com/{organization}/{project}/_odata/v3.0-preview/PipelineRuns?
$apply=filter(
    CompletedDate ge 2026-03-01T00:00:00Z and
    CompletedDate le 2026-04-30T23:59:59Z and
    Result eq 'Succeeded' and
    StageName eq 'Production'
)/aggregate($count as DeploymentCount)
```

This query returns the total number of successful production deployments during the specified period.

The logic is identical to sprint-based KPIs: define time window, filter appropriately, aggregate deterministically.

# Performance and Data Considerations

Analytics OData is optimized for reporting, but it is not infinite.

When building enterprise KPI frameworks, consider limiting query windows to required date ranges, using aggregation instead of retrieving full entity sets, avoiding client-side filtering where server-side filters are available, and understanding that Analytics may have slight data refresh latency compared to operational APIs.

These considerations ensure the KPI framework remains scalable.

# Architectural Pattern Summary

For time-based KPIs:

1. Retrieve structural metadata via REST.
2. Retrieve historical state via Analytics OData.
3. Apply formula logic in code.
4. Evaluate thresholds.
5. Publish deterministic output.

This pattern remains stable across multiple KPIs, including Commitment Ratio, Defects Leakage, Throughput per sprint, Deployment Frequency, and Test pass rate trends.

The formula changes. The retrieval pattern does not.

# Governance and Reproducibility

A KPI that cannot be reproduced is not governable.

By tying sprint boundaries to REST metadata, historical state to snapshot entities, and formula logic to version-controlled scripts, you ensure that past KPI values remain stable even if work items change after sprint completion.

This is what transforms reporting into engineered metrics.

# What Comes Next

In the next post, we will move into status evaluation logic and show how RAG thresholds, parameter-driven rules, and configurable evaluation patterns are implemented consistently across the KPI portfolio.
