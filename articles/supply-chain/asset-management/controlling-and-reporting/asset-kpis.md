---
# required metadata

title: Asset KPIs
description: This topic explains asset KPIs in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 07/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Asset KPIs

In Asset Management, you can calculate various Key Performance Indicators (KPIs) for assets and asset types. You use KPIs to get an overview of performance on assets in relation to, for example, uptime, downtime, repair time, and Mean Time Between Failure (MTBF).

1. Click **Asset management** > **Inquiries** > **Assets** > **Asset KPIs**.

2. In the **Calculate asset KPIs** dialog, you select the **Time scale** to be used in the calcualtion, and a period in the **From date** and **To date** fields. 

3. On the **Records to include** FastTab, you can select specific assets and asset types to be included in the calculation, if required.

4. Click **OK** to start the calculation.

5. On the **Overview** FastTab, the results of the calculation are displayed in grid view. Each asset is displayed on a separate line.

6. On the **KPIs for selected line** FastTab, you see calculations for the asset selected on the **Overview** FastTab. The KPI values are categorized regarding **Time**, **Availability**, **Work orders**, **Maintenance**, **Faults**, and **Maintenance downtime**. You're also able to see cost registrations and, if available, the replacement value registered on the asset.

In the table below, you'll find a description of the asset KPIs.

| Field                   | Description                                                                                                                                                                                                                                                                                           |
|-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Asset                   | Asset ID.                                                                                                                                                                                                                                                                            |
| Total time              | Total time set up in the calendar used in the calculation. If the object is related to a resource, the related resource calendar is used. If the object is not related to a resource, the calendar selected in the **Standard calendar** field in **Enterprise asset management parameters** is used. |
| Uptime                  | Total time minus downtime.                                                                                                                                                                                                                                                                            |
| Downtime                | Production stop registrations made on the object in the selected period.                                                                                                                                                                                                                              |
| Repair time             | Total number of work hours consumed on repair work orders.                                                                                                                                                                                                                                            |
| Availability %          | Uptime divided by total time and multiplied by 100.                                                                                                                                                                                                                                                   |
| Number of faults        | Number of fault causes registered on fault symptoms on the object in the selected period.                                                                                                                                                                                                             |
| MTBF                    | Mean Time Between Failure, which is total time divided by number of faults registered on the object in the selected period. If number of faults is zero, MTBF is set to total time.                                                                                                                   |
| Fail rate               | 1 divided by MTBF.                                                                                                                                                                                                                                                                                    |
| MRT                     | Mean Repair Time, which is repair time divided by number of faults registered on the object in the selected period. If number of faults is zero, MRT is set to repair time.                                                                                                                           |
| Number of stops         | Number of production stops registered on the object.                                                                                                                                                                                                                                                  |
| MTBS                    | Mean Time Between Stops, which is total time divided by number of production stop registrations. If number of production stop registrations is zero in the selected period, the MTBS value is set to total time.                                                                                      |
| MTPS                    | Mean Time Production Stops, which is production stop time divided by number of production stop registrations. If number of production stop registrations is zero in the selected period, the MTPS value is set to zero.                                                                               |
| Preventive cost         | Costs posted on the object related to cost type "Preventive" in the selected period. Cost types are set up on work order types.                                                                                                                                                                       |
| Corrective cost         | Costs posted on the object related to cost type "Corrective" in the selected period. Cost types are set up on work order types.                                                                                                                                                                       |
| Replacement value       | Value defined on the object as the replacement cost.                                                                                                                                                                                                                                                  |
| Object type             | Identification of the object type selected on the object.                                                                                                                                                                                                                                             |
| Product                 | Identification of the product selected on the object.                                                                                                                                                                                                                                                 |
| Model                   | Identification of the product model selected on the object.                                                                                                                                                                                                                                           |
| From date               | Start date of the KPI calculation. If the object was created after the start date selected for the calculation, the start date of the object is shown in this field.                                                                                                                                  |
| To date                 | End date of the KPI calculation. If the object was registered as inactive before the end date selected for the calculation, the date from which the object was no longer active is shown in this field.                                                                                               |
| Time scale              | During calculation of the KPIs, you select a time scale to be used: Hours, Days, or Weeks.                                                                                                                                                                                                            |
| Availability            | Uptime divided by total time.                                                                                                                                                                                                                                                                         |
| Work orders             | Total number of work orders included in the KPI calculation.                                                                                                                                                                                                                                          |
| Work order time         | Total number of work hours consumed on the work orders.                                                                                                                                                                                                                                               |
| Primary work orders     | Number of primary work orders included in the KPI calculation.                                                                                                                                                                                                                                        |
| Secondary work orders   | Number of secondary work orders included in the KPI calculation.                                                                                                                                                                                                                                      |
| Maintenance work orders | Number of maintenance work orders included in the KPI calculation. A maintenance work order is a work order with no related fault causes.                                                                                                                                                             |
| Maintenance time        | Total number of work hours consumed on maintenance work orders.                                                                                                                                                                                                                                       |
| Repair work orders      | Number of repair work orders included in the KPI calculation. A repair work order is a work order with a related fault causes.                                                                                                                                                                        |
| Reliability %           | Calculation based on the expected exponential development in fault registrations on an object meaning that, over time, the object becomes less reliable due to wear and tear. The calculation of this KPI is based on MTBF and total time.                                                            |
| Total cost              | Total costs posted on the object in the selected period.                                                                                                                                                                                                                                              |
| Investment cost         | Costs posted on the object related to cost type "Investment" in the selected period. Cost types are set up on work order types.                                                                                                                                                                       |

The figure below shows a screenshot of a KPI calculation for four assets.

![Figure 1](media/11-controlling-and-reporting.png)

- You can multi-select several assets in **All assets** and click the **Asset KPIs** button on the **General** tab. Then, click **OK** in the **Calculate asset KPIs** dialog to calculate KPIs for the selected assets.  
- Results from a KPI calculation may or may not include [maintenance downtime registrations](../work-orders/maintenance-downtime.md), depending on the setup and use of maintenance downtime reason codes. 

