--- 
title: Find obsolete product variants 
description: Learn how to find obsolete released products or product variants and how to associate a product lifecycle state to the obsolete products. 
author: sgmsft
ms.author: shwgarg
ms.topic: how-to
ms.date: 12/10/2025
ms.custom:
ms.reviewer: kamaybac    
ms.search.form: 
---

# Find obsolete product variants

[!include [banner](../../includes/banner.md)]

This article shows how to find obsolete released products or product variants and how to associate a product lifecycle state to the obsolete products. It also shows how to view the simulation results and assess how many products and product variants will be associated with a new product lifecycle state when running the update without simulation.  

When you run the analysis in simulation mode, it displays the products and product variants identified as obsolete. You can easily review these products. The analysis searches for transactions and specific master data to identify products that have no demand within a variable period and no master data that can result in demand. You can exclude new released products within a variable period from the analysis. When the analysis simulation returns the expected result, you can run the analysis and set a new product lifecycle state to all products identified as obsolete by the analysis.  

> [!NOTE]
> Perform all analyses and updates within the same legal entity.  

To find obsolete product variants and associate a product lifecycle state to them, follow these steps:

1. Go to **Product information management** \> **Periodic tasks*** \> **Change lifecycle state for obsolete products**.
1. In the **New product lifecycle state** field, enter or select a value.
1. Set **Run simulation without updating product data** to *Yes*.
1. In the **Exclude products created within this number of days** field, enter a number.
1. In the **Exclude products used in transactions (in number of days)** field, enter a number.
1. If you want to limit the scope of the simulation, expand the **Records to include** FastTab and select **Filter** to open the standard query dialog, where you can define selection criteria. The fields work just as they do for other types of queries in Supply Chain Management.
1. On the **Run in the background** FastTab, specify how, when, and how often the job runs. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.

    > [!TIP]
    > Run the simulation in batch if you expect to search a large number of products. Also, don't run the simulation during the most active working time of the company.  

1. Select **OK** to apply your settings and close the dialog.

1. Go to **Product information management** \> **Inquiries and reports** \> **Product lifecycle state maintenance history**.
1. The **Product lifecycle state maintenance history** page shows the results of the simulation. Review the results and decide whether you'd like to actually apply the suggested changes. You might decide to adjust the filter criteria and run the simulation again.
1. When you're satisfied with the simulation results, go to **Product information management** \> **Periodic tasks** \> **Change lifecycle state for obsolete products**.
1. Set **Run simulation without updating product data** to *No*.
1. Expand the **Records to include** FastTab and confirm that it still shows the filter criteria that you used for the simulation that you want to apply.
1. Depending on how many products and product variants are affected, consider running this job in batch by using the settings on the **Run in the background** FastTab. Make sure that you're not running a large update job during the most active working hours in the company.  

1. Select **OK**.
1. Go to **Product information management** \> **Inquiries and reports** \> **Product lifecycle state maintenance history** and confirm that the changes you expected were applied.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
