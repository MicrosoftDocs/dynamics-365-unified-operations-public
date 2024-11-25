---
title: Forecast position reports for the public sector
description: You can use the Forecast position summary and Forecast position detail reports to generate information about forecast positions during a specified budget plan.
author: velofog
ms.author: twheeloc
ms.topic: article
ms.date: 10/29/2019
ms.custom: 
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2019-8-04
ms.search.form:
ms.dyn365.ops.version: 10.0.5
---

# Forecast position reports for the public sector

[!include [banner](../includes/banner.md)]

You can use the **Forecast position summary** and **Forecast position detail** reports to generate information about forecast positions during a budget plan and scenario that you specify.  

The **Forecast position summary** report shows forecast position costs by account distributions. The forecast position costs are shown, grouped by their assigned account distributions. The cost amounts are factored by the percentage assigned to the account distribution. 

The **Forecast position details** report contains most of the information displayed on the forecast position form. The account distributions assigned to the forecast position via financial dimensions and financial dimension templates are shown, along with the costs associated with each distribution combination for the forecast position. 

To view more information about a **Forecast position**, select the **Position number** to open the **Forecast position** page.

## Filter the data on this report

When you generate the report, the following default parameters are shown.  You can use these parameters to filter the data that appears on the report.  

| Field | Description |
| --------- | ------- |
| Budget plan scenario | Select the budget plan scenario that should be listed on the report. <p> Budget plan scenarios define categories of data for the budget plans. You define budget plan scenarios to support monetary and other unit of measure classes, such as quantity. Examples of monetary budget plan scenarios include Department previous year and Department requests. Examples of budget plan scenarios that use quantities include Previous year support calls and Full-time equivalent (FTE) count. </p>  |
| Budget planning process | Select the budget planning process that should be listed on the report.<p> Budget planning processes determine how budget plans can be updated, routed, reviewed, and approved in the budgeting organization hierarchy. A budget planning process is linked to a budget cycle and an organization via a legal entity. </p> |
| Default account structure | Select the default account structure to display the accounting dimensions on the forecast positions in the order you desire.|
| Department | Select a department that should be listed on the report. Leave the field blank to run the report for all accounts. |
| Unfilled only | Set this option to Yes to exclude positions that are currently filled. |
| Suppress total | Set this option to Yes to exclude totals from appearing on the report. |



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
