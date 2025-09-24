---
title: Analyze and monitor telemetry with KQL
description: Learn how to query Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management telemetry by using Kusto Query Language (KQL).
author: kennysaelen
ms.topic: how-to
ms.custom: bap-template
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 01/20/2025
ms.author: kesaelen
ms.reviewer: johnmichalak

---

# Analyze and monitor telemetry with KQL

[!include [banner](../includes/banner.md)]

Telemetry from Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management is stored in Application Insights. To query that telemetry, the Kusto Query Language (KQL) is used. This article provides information and links to resources to help you learn about KQL.

## Run your first KQL query

To run your first KQL (Kusto) query, follow these steps.

1. In the [Azure portal](https://portal.azure.com), open your Application Insights resource.
1. On the **Monitoring** menu, select **Logs**.
1. To get the last 100 traces, on the **New Query** tab, enter the following query.

    ```kql
    pageViews
    | where timestamp > ago(7d)                              // look back 7 days
    | take 100                                               // only take 100 rows
    | project timestamp, name, duration, customDimensions    // only choose these columns 
    | sort by timestamp desc                                 // show the most recent data first
    ```

## Where can I use Kusto queries?

You can use Kusto queries as the data source in many places. Here are some examples:

* The **logs** part of Application Insights in the Azure portal
* Power BI reports
* Alerts
* Azure dashboards
* Jupyter notebooks (with the Kqlmagic extension)

## Where can I learn more about KQL?

KQL is very well documented. You can learn more about it in [Kusto Query Language (KQL) overview](/kusto/query/?view=microsoft-fabric).

## Which tools can I use (KQL editors and clients)?

You can get an overview of the different tools in [Integrations overview](/azure/data-explorer/integrate-overview?tabs=connectors).

## How can I query telemetry from Log Analytics?

With workspace-based resources, Azure Application Insights sends telemetry to a common Azure Log Analytics workspace. Therefore, you get full access to all the features of Azure Log Analytics, and your application, infrastructure, and platform logs, in a single consolidated location. This integration allows for common Azure role-based access control across your resources and eliminates the need for cross-app/workspace queries.

The following table shows the table names for Finance and Supply Chain Management telemetry when it's queried from Azure Application Insights and Azure Log Analytics.

| Table name | Table name in Azure Log Analytics | 
| ---------- | --------------------------------- | 
| traces | AppTraces |
| pageViews | AppPageViews |
| exceptions | AppExceptions |
| customEvents | AppEvents |
| customMetrics | AppMetrics |

## KQL example - Listing the top 20 most used forms

Times for Finance and Supply Chain Management form loads are logged as `pageView` entries in the `pageViews` table. You can use the information to query form loads. In this way, you can learn about the most used forms, the slowest form loads, and other details.

Use the following KQL code to query the top 20 form loads, based on the number of times that the forms were opened.

```kql
pageViews                                                                       // Dynamics 365 F&SCM form loads are captured as pageViews
| where timestamp between (ago(7d) .. now())                                    // Filter on the last 7 days
| where name !in ("SysOperationSandboxForm", "SysBoxForm", "Dialog")            // exclude these form names
| extend ['Activity Id'] = customDimensions.activityId                          // grab the dynamics 365 activity id field from the custom payload
| summarize ["Form Opens"] = count() by name                                    // count the number of pageViews by name
| top 20 by ["Form Opens"] desc                                                 // limit to 20 rows
```

## KQL example - Adding statistics about the duration of forms

You can take the previous example one step further and use the following KQL query to fetch the slowest forms.

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
