---
title: Calculate sales totals
description: Learn how to use and configure the Calculate sales totals batch job, including performance guidance, recommended usage, and configuration instructions.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 02/26/2026
ms.custom: 
  - bap-template
---

# Calculate sales totals

[!include [banner](../../includes/banner.md)]

The *Calculate sales totals* batch job recalculates and updates aggregated metrics for sales orders and sales quotations. This critical maintenance task ensures that all summary totals, delivery metrics, and key performance indicators (KPIs) shown on inquiry pages, workspaces, and analytics dashboards remain accurate and up-to-date. The recalculation updates:

- Order‑level totals  
- Quotation‑level totals  
- Aggregated values used by workspaces, analytics, and reporting  
- KPI caches across sales, retail, and commerce experiences  

Use the *Calculate sales totals* job to maintain data integrity and reporting accuracy, especially after bulk data imports, mass updates to sales documents, or as part of regular system maintenance. By running this job on a scheduled basis—such as nightly or as part of month-end closing processes—you ensure that your sales teams, managers, and executives always see current, reliable totals when reviewing orders, quotations, and performance metrics.

This feature provides benefits to many parts of your organization:

- *Sales teams and order managers* get accurate order summaries and delivery information without manual calculation or delays.
- *Finance and management* rely on current KPI data for accurate reporting, forecasting, and business analysis.
- *System administrators* can control the scope and timing of recalculations to balance data accuracy with system performance.
- *E-commerce and retail operations* benefit from fresh aggregated metrics used in commerce workspaces and analytics.

This article walks you through the configurable parameters that let you control which documents to recalculate and how far back to look, explains how to schedule the job to run automatically, and provides performance best practices to ensure the job runs efficiently in your environment.

Learn more about batch jobs in [Batch processing overview](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md).

## When to recalculate sales totals

Run the *Calculate sales totals* batch job in the following scenarios:

- After *bulk data imports* (data management and integrations).  
- After *mass updates* to sales orders or quotations.  
- As part of *month‑end closing*.  
- On a *nightly schedule* to maintain accurate workspace KPI totals.

## Performance considerations

To keep your system running smoothly, follow these performance best practices:

- Avoid full recalculation during peak business hours.
- Run targeted recalculations by adjusting the **Ignore documents updated before (days)** parameter.  
- If totals appear incorrect, check whether you have any customizations that bypass update triggers.

## Set up, run, and schedule sales total calculations

To set up, run, and schedule the *Calculate sales totals* batch job, follow these steps:

1. Go to **Sales and marketing** \> **Periodic tasks** \> **Calculate sales totals**.

1. In the **Calculate sales totals** dialog, make the following settings on the **Parameters** FastTab:

   - **Ignore documents updated before (days)** – Enter the number of days to look back for recalculation. Only documents that were last updated *after* this date are recalculated. The system uses the following formula to calculate the cutoff date:

        *Cutoff date = Today - Entered number of days*

        To balance data freshness with performance for routine recalculations, we recommend that you look back 7 to 30 days. Avoid running full historical recalculations in high-volume environments unless necessary.

   - **Calculate totals for sales orders** – Set to *Yes* to recalculate aggregated totals for sales orders, including:

        - Order-level summary totals  
        - Line-level aggregated contributions  
        - Delivery totals  
        - Remaining quantities and values  
        - KPI totals used in workspaces and analytics  

        Set this option to *No* only in niche scenarios where sales orders aren't part of your workflow.

   - **Calculate totals for sales quotations** – Set to *Yes* to recalculate aggregated totals for sales quotations, including:

        - Quotation value summaries  
        - Aggregated line-level metrics  
        - Totals used in quotation inquiry and reporting  

        Set this option to *No* if your organization doesn't use the sales quotation process.

   - **Number of threads** – Enter the maximum number of parallel threads to use for the job (or set to zero to let the system decide automatically). If your sales totals calculations take too long, consider increasing this value. To allow more resources for other processes while calculating sales totals, reduce this value. The actual maximum number of used threads never exceeds the maximum batch threads configured for your system. The system distributes orders and quotations selected for the calculation evenly between the threads.

1. On the **Run in the background** FastTab, choose whether to run the job in batch mode and set up a recurrent schedule. Select **Recurrence** to set up the run schedule (or choose to run just once). Tips for when and how often to run this job are provided earlier in this article. Select **Alerts** to configure notifications for job completion or failures. The settings here work just as they do for other types of [batch jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
