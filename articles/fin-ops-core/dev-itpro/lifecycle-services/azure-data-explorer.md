---
# required metadata

title: Title
description: Description of topic.
author: andreashofmann1
ms.date: 08/20/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: andreash
ms.search.validFrom: 2021-08-20
---

# Use Azure Data Explorer to query Raw information logs

[!include[banner](../includes/banner.md)]

There are occasions when a customer, partner, consultant, or support engineer needs to look at the low-level Dynamics 365 Finance & Operations telemetry data. These use cases include troubleshooting of errors, performance-related investigations or just to gain some additional understanding of how the platform work. Telemetry data can be accessed by authorized users via the Environment monitoring part of the LCS portal, can be filtered in a few different ways and displayed inside the LCS portal’s raw logs section. A data grid can be used to inspect the log entries. LCS does not allow for more sophisticated pivoting and users can use Excel for that purpose. For that purpose, the telemetry data can also be downloaded formatted in CSV format. 

However, Excel is not the optimal tool for advanced querying of this data. The perfect tool, designed for this purpose is the Azure Data Explorer. It provides an innovative query language Kusto that is optimized for high-performance data analytics. Answering questions like “how often has a certain process taken place, how long has it taken in 90% of the times, how often per hour has a certain action taken place over the course of a day” becomes a lot easier and can be backed up with powerful graphics as well. 

Here are examples how the graphics could look like:
![image](https://user-images.githubusercontent.com/45279749/130295988-59e63346-348b-4531-a3f3-e3ab55a02719.png)
![image](https://user-images.githubusercontent.com/45279749/130296001-e1a757e7-f2f7-4469-a5df-ae29319b2ea9.png)

A less known feature of the Azure Data Explorer is that it supports ingestion of CSV files. We can use it to get our CSV data files uploaded and staged so it can be queried with the Kusto language. If you have not setup Azure Data Explorer Cluster, follow these [steps](https://docs.microsoft.com/en-us/azure/data-explorer/create-cluster-database-portal).

## Steps to upload to Azure Data Explorer
*	Run your query on LCS raw logs page
*	Important: adjust the time interval or filter to get to the right data (row limit is 5000 for export in next step) 
*	export the grid to Excel

![image](https://user-images.githubusercontent.com/45279749/130296479-6904b125-cd7b-4fee-9a1e-7e1bfb619e1e.png)

*	Open the file in Excel and save it without making any changes (this seems to fix a formatting issue)
*	In your Azure Data Explorer, right click on the cluster in the tree view and select “ingest new data” and then on the next page “ingest data from a local file”

![image](https://user-images.githubusercontent.com/45279749/130296578-7e957c4f-807f-47eb-bf8e-40b69b64a29b.png)

*	Pick your cluster, name a new table for the data to be imported into, select up to 10 CSV files to import, select CSV format. Hit next a few times till your data is getting imported.

![image](https://user-images.githubusercontent.com/45279749/130296627-8969fa68-1232-4c73-84e1-271d7af97a70.png)

* Use the Query tile to write a Kusto query against your data. 

![image](https://user-images.githubusercontent.com/45279749/130296674-15db289d-b994-44cf-b783-ce3b54e33d0f.png)

To learn more about the Kusto query language, go [here](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/tutorial?pivots=azuredataexplorer).

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

![image](https://user-images.githubusercontent.com/45279749/130297232-d9ff5121-78f9-4c3c-abfc-c1bc9dabbf5c.png)

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

![image](https://user-images.githubusercontent.com/45279749/130297275-db70c053-e2fb-4b1f-854f-05d551ff7af5.png)

![image](https://user-images.githubusercontent.com/45279749/130297287-c82a8239-f0c6-4acc-b6ec-4cd87516344b.png)
