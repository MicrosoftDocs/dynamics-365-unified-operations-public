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

You can run a simulation analysis to find the obsolete released products or product variants and then update their product lifecycle status. This article shows how to find obsolete released products or product variants and how to associate a product lifecycle state to the obsolete products. It also shows how to view the simulation results and assess how many products and product variants will be associated with a new product lifecycle state when running the update without simulation.  

By running the analysis in a simulation mode, the products and product variants identified as obsolete are displayed in a specific form, where they can easily be reviewed. The analysis searches for transactions and specific master data to identify products that have no demand within a variable period and no master data that can result in demand. New released products within a variable period can be excluded from the analysis. When the analysis simulation returns the expected result, the user can run the analysis and set a new product lifecycle state to all products identified as obsolete by the analysis.  

> [!NOTE]
> All analysis and updates must be done within the same legal entity.  

## Run a simulation

1. Go to **Product information management** \> **Periodic tasks*** \> **Change lifecycle state for obsolete products**.
1. In the **New product lifecycle state** field, enter or select a value.
1. Select *Yes* in the **Run simulation without updating product data** field.
1. In the **Exclude products created within this number of days** field, enter a number.
1. In the **Exclude products used in transactions (in number of days)** field, enter a number.
1. Expand the **Records to include** section.
1. Select **Filter**.
1. In the list, mark the selected row.
1. In the **Criteria** field, type a value.
1. Select **OK**.
1. Select **OK**.

> [!NOTE]
> It is recommended to run the simulation in batch if you expect to search a large number of products. Also, make sure that the simulation is not run during the most active working time of the company.  

## Review the simulation results

To review the simulation results, go to **Product information management** \> **Inquiries and reports** \> **Product lifecycle state maintenance history**.

> [!NOTE]
> On this page, you can review the simulation results and make an assessment of how many products and product variants will be associated with a new product lifecycle state when running the update without simulation.  

## Run the update of the Product lifecycle state for obsolete products

1. Close the page.
1. Go to **Product information management** \> **Periodic tasks** \> **Change lifecycle state for obsolete products**.
1. Expand the **Records to include** section.

> [!NOTE]
> Note that the last selection has been saved.  

1. Select *No* in the **Run simulation without updating product data** field.
1. Expand the **Run in the background** section.

    > [!NOTE]
    > Depending on how many products and product variants are affected, consider running this job in batch. Make sure that you are not running a large update job during the most active working hours in the company.  

1. Select **OK**.
1. Go to **Product information management** \> **Inquiries and reports** \> **Product lifecycle state maintenance history**.

    > [!NOTE]
    > Review the changed released products and product variants.  

1. In the list, find and select the desired record.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
