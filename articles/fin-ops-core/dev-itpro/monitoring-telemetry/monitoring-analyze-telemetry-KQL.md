---
title: Analyze and monitor telemetry with KQL
description: Learn how to query Microsoft Dynamics 365 Finance and Microsoft Dynamics 365 Supply Chain Management telemetry with KQL.  
author: kennysaelen
ms.topic: how-to
ms.custom: bap-template
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 08/11/2024
ms.author: kesaelen
ms.reviewer: johnmichalak

---

# Analyze and monitor telemetry with KQL

[!include [banner](../includes/banner.md)]

Telemetry from Microsoft Dynamics 365 Finance and Microsoft Dynamics 365 Supply Chain Management is stored in Application Insights. To query that telemetry, the _Kusto Query Language (KQL)_ is used. This article has information and links to resources to get started learning about the KQL language.

## Run your first KQL query

To run your first KQL query, follow these steps.
  
1. On the Azure portal, open your Application Insights resource.
1. On the **Monitoring** menu, select **Logs**.
1. To get the last 100 traces, on the **New Query** tab, enter the following:

    ```kql
    pageViews
    | where timestamp > ago(7d)                              // look back 7 days
    | take 100                                               // only take 100 rows
    | project timestamp, name, duration, customDimensions    // only choose these columns 
    | sort by timestamp desc                                 // show the most recent data first
    ```

## Where can I use Kusto Queries?

You can use Kusto queries as the data source in many places. For example:

* The **logs** part of Application Insights in the Azure portal
* Power BI reports
* Alerts
* Azure Dashboards
* Jupyter Notebooks (with the Kqlmagic extension)

## Where can I learn more about KQL?

The Kusto Query Language is very well documented. For more information, see [Kusto Query Language (KQL)](/kusto/query/?view=microsoft-fabric).

## Which tools can I use (KQL editors and clients)?

To get an overview of the different tools, see [Azure Data Explorer tools and integrations overview](/azure/data-explorer/integrate-overview?tabs=connectors).

## How can I query telemetry from Log Analytics?

With workspace-based resources, Azure Application Insights sends telemetry to a common Azure Log Analytics workspace, providing full access to all the features of Azure Log Analytics while keeping your application, infrastructure, and platform logs in a single consolidated location. This integration allows for common Azure role-based access control across your resources and eliminates the need for cross-app/workspace queries.

This table shows table names for Finance and Supply Chain Management telemetry when queried from Azure Application Insights and from Azure Log Analytics:

| Table name | Table name in Azure Log Analytics | 
| --------- | ------------| 
| traces    | AppTraces |
| pageViews | AppPageViews |
| exceptions | AppExceptions |
| customEvents | AppEvents |
| customMetrics | AppMetrics |

## KQL example - Listing the top 20 most used forms

In Finance and Supply Chain Management form loading, times are logged as pageViews in the **pageViews** table. Using this information, you can query form loads to understand the most used forms, the slowest form loads, etc.

Use this KQL code to query the top 20 form loads based on the number of times the forms were opened:

```kql
pageViews                                                                       // Dynamics 365 F&SCM form loads are captured as pageViews
| where timestamp between (ago(7d) .. now())                                    // Filter on the last 7 days
| where name !in ("SysOperationSandboxForm", "SysBoxForm", "Dialog")            // exclude these form names
| extend ['Activity Id'] = customDimensions.activityId                          // grab the dynamics 365 activity id field from the custom payload
| summarize ["Form Opens"] = count() by name                                    // count the number of pageViews by name
| top 20 by ["Form Opens"] desc                                                 // limit to 20 rows
```

## KQL example - Adding statistics on the duration of forms

Taking this one step further, you can write the following KQL query to fetch the slowest forms:

```kql
pageViews                            
| where timestamp between (ago(7d) .. now())                                                           // Filter on the last 7 days
| where duration > 0                                                                                   // Ensure there is a captured duration
| extend ['Activity Id'] = customDimensions.activityId                                                 // grab the dynamics 365 activity id
| project ['Form name'] = name, duration                                                               // select the name and duration fields
| summarize     ['Number of executions']            = count()                                          // Add summarization fields for count, avg, min, max, percentile
            ,   ['Avg duration (s)']                = round(avg(duration)/1000,2)
            ,   ['Min duration (s)']                = round(min(duration)/1000,2)
            ,   ['Max duration (s)']                = round(max(duration)/1000,2)
            ,   ['Percentile 95 (s)']               = round(percentile(duration,95)/1000,2)
            ,   ['Accumulated total duration (s)']  = round(sum(duration)/1000,2) by ['Form name'] 
| order by ['Avg duration (s)'] desc                                                                   // List the slowest first
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
