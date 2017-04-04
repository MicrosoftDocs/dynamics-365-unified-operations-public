---
# required metadata

title: Production order defaults in manufacturing execution
description: 
author: YuyuScheller
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: JmgProdParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 70073
ms.assetid: 620944ae-3e20-444a-807e-65495f160904
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Production order defaults in manufacturing execution



You should carefully consider all the settings on the **Production order defaults** page before workers start to make registrations on production jobs. If your company uses the multisite functionality, you might want to set up different defaults for production orders for each site. The order defaults for integration with Production control are set up on the following tabs on the **Production order defaults** page:

-   **General** – General order defaults for production jobs in Manufacturing execution.
-   **Start** – Order defaults that are used when production jobs or operations are started.
-   **Operations** – Order defaults that are applied to production jobs or operations and feedback on operations during the production process.
-   **Report as finished** – Order defaults that are applied when items are reported as finished on the last operation of a production order.
-   **Quantity validation** – Order defaults for validating start and feedback quantities on production orders.

## Types of production jobs
On the **Operations** tab, you select the types of production jobs that require registration on the **Job registration** page. Typically, workers make registrations on setup jobs and process jobs. However, if job scheduling is applied, you can select other job types, such as transport jobs, that workers must also make registrations on when a production order is processed. **Important:** Make sure that all relevant job types are selected. Otherwise, jobs might not be available for registration on the **Job registration** page. Align your selections with the selections that are made in the **Job management** column on the **Route groups** page. If **Job management** is selected on the route group, the job type will be reported as finished on the production order. This reporting occurs when the job is reported as finished in Manufacturing execution. When all job types that **Job management** is selected for have been reported as finished on an operation, Manufacturing execution will also report the operation as finished. **Note:** Some job types can be reported manually through production journals. In this case, select **Job management** for the job type, but don't select the job type for registration on the **Operations** tab on the **Production order defaults** page.

## BOM consumption and picking list journals
Materials can be set up so that they are consumed either automatically or manually during production. Automatic consumption is controlled by the flushing principle that is set up on the bill of materials (BOM) lines, and by the setting of the **Automatic BOM consumption** field in the production order defaults. Automatic consumption can be set up so that it occurs when a production order is started or reported as finished. Alternatively, it can occur on the job level when a job is started or completed.

### Controlling material consumption when a production order is started

Material consumption during the start of a production order is controlled by the **Automatic BOM consumption** field on the **Start** tab. The following values are available:

-   **Flushing principle** – When a production order is started, quantities of materials will be consumed according to the flushing principle that is set on the production BOM lines. Only material lines where the flushing principle is set to **Start** will be consumed during the production start.
-   **Always** – Quantities of materials that are proportional to the started quantity will always be consumed.
-   **Never** – Quantities of materials will never be consumed.

### Controlling material consumption when a production job is started or completed

Material consumption during the start or completion of a production job is controlled by the **Automatic BOM consumption** field on the **Operations** tab. The following values are available:

-   **Flushing principle** – When a quantity on a production job is started or completed, quantities of materials will be consumed according to the flushing principle that is set on the production BOM lines. Only material lines where the flushing principle is set to **Start** or **Finish** will be consumed.
-   **Always** – Quantities of materials that are proportional to the started quantity on the job will always be consumed.
-   **Never** – Quantities of materials will never be consumed.

### Controlling material consumption when a production order is reported as finished

Material consumption during the Report as finished process for a production order is controlled by the **Automatic BOM consumption** field on the **Report as finished** tab. The following values are available:

-   **Flushing principle** – When a production order is reported as finished, quantities of materials will be consumed according to the flushing principle that is set on the production BOM lines. Only material lines where the flushing principle is set to **Finish** will be consumed.
-   **Always** – Quantities of materials that are proportional to the quantity that is reported as finished will always be consumed.
-   **Never** – Quantities of materials will never be consumed.


