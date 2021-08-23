---
# required metadata

title: Use Azure Data Explorer to query raw information logs
description: This topic explains how to use Azure Data Explorer to query raw information logs.
author: andreashofmann1
ms.date: 08/23/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: andreash
ms.search.validFrom: 2021-08-20
---

# Use Azure Data Explorer to query raw information logs

[!include[banner](../includes/banner.md)]

There are occasions when a customer, partner, consultant, or support engineer needs to look at the low-level telemetry data for a Finance and Operations app. These use cases include troubleshooting of errors, performance-related investigations, or just trying to gain some additional understanding of how the Finance and Operations app works. Telemetry data can be accessed by authorized users via the Environment monitoring features of Lifecycle Services (LCS) and can be filtered in a few different ways and displayed inside the LCS's [raw information logs](monitoring-diagnostics.md#raw-information-logs). A data grid can be used to inspect the log entries. LCS does not allow for more sophisticated pivoting, so users can use Excel for that purpose. The telemetry data can also be downloaded and formatted in CSV format. 

However, Excel is not the optimal tool for advanced querying of this data. The perfect tool, designed for this purpose is the Azure Data Explorer. It provides an innovative query language Kusto that is optimized for high-performance data analytics. Answering questions like *how often has a certain process taken place*, *how long has it taken in 90% of the times*, *how often per hour has a certain action taken place over the course of a day* becomes a lot easier and can be backed up with powerful graphics as well. 

Here are examples of how the graphics could look like:

![Bar graph example 1](https://user-images.githubusercontent.com/45279749/130295988-59e63346-348b-4531-a3f3-e3ab55a02719.png)

![Bar graph example 2](https://user-images.githubusercontent.com/45279749/130296001-e1a757e7-f2f7-4469-a5df-ae29319b2ea9.png)

A less known feature of the Azure Data Explorer is that it supports ingestion of CSV files. We can use it to get our CSV data files uploaded and staged so it can be queried with the Kusto language. If you have not setup Azure Data Explorer Cluster, see [Quickstart: Create an Azure Data Explorer cluster and database](/azure/data-explorer/create-cluster-database-portal).

## Steps to upload to Azure Data Explorer
1.	Run your query on LCS raw logs page.
2.	**Important:** Adjust the time interval or filter to get to the right data (row limit is 5000 for export in next step).
3.	Export the grid to Excel.

    ![Environment monitoring page in LCS](https://user-images.githubusercontent.com/45279749/130296479-6904b125-cd7b-4fee-9a1e-7e1bfb619e1e.png)

4.	Open the file in Excel and save it without making any changes (this seems to fix a formatting issue).
5.	In Azure Data Explorer, right-click on the cluster in the tree view and select **Ingest new data**. On the next page select **Ingest data from a local file**.

    ![Select Ingest new data.](https://user-images.githubusercontent.com/45279749/130296578-7e957c4f-807f-47eb-bf8e-40b69b64a29b.png)

6.	Pick your cluster, name a new table for the data to be imported into, select up to 10 CSV files to import, and select CSV format. Hit next a few times till your data is getting imported.

    ![Data is imported.](https://user-images.githubusercontent.com/45279749/130296627-8969fa68-1232-4c73-84e1-271d7af97a70.png)

7. Use the Query tile to write a Kusto query against your data. 

    ![Use Query tile.](https://user-images.githubusercontent.com/45279749/130296674-15db289d-b994-44cf-b783-ce3b54e33d0f.png)

To learn more about the Kusto query language, see [Tutorial: Use Kusto queries in Azure Data Explorer and Azure Monitor](/azure/data-explorer/kusto/query/tutorial?pivots=azuredataexplorer).

## Sample queries
### Analysis of SQL queries occurring in the Commerce Runtime (custom or built-in)

```kusto
new2
| where EventId == 1809 // designates SQL finnished trace
| project executionTimeMilliseconds, sqlQuery
| summarize NumAllCalls=count(), TotalDuration=sum(executionTimeMilliseconds), AvgDuration = avg(executionTimeMilliseconds), 
    percentiles(executionTimeMilliseconds, 90) by tostring(substring(sqlQuery, 0, 70))
| where percentile_executionTimeMilliseconds_90 > 1
| order by TotalDuration desc
```

### Performance of any RetailServer calls > 100ms

```kusto
// run this for the data
new2
| where EventId == 5009 // designates a RetailServer finished trace
| project executionTimeMilliseconds, apiAction
| summarize NumAllCalls=count(), TotalDuration=sum(executionTimeMilliseconds), AvgDuration = avg(executionTimeMilliseconds), percentiles(executionTimeMilliseconds, 90) by tostring(apiAction)
| where percentile_executionTimeMilliseconds_90 > 100
| order by percentile_executionTimeMilliseconds_90 desc

// include this for the chart
| project apiAction, percentile_executionTimeMilliseconds_90
| render columnchart
```
