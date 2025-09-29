---
title: Tax calculation in projects in Brazil tax reform
description: The article describes tax calculation in projects in Brazil tax reform solution
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 09/29/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2025-10-01
ms.custom: 
  - bap-template
---

# Tax calculation in projects in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes tax calculation in projects in Brazil tax reform solution

## Procedure: Create a project with Brazilian taxes

You can create a project by specifying fiscal information, such as the operation type and the Código Fiscal de Operações e Prestações (CFOP) code. When you create a sales order line, you can select a CFOP code in the **CFOP** field. The CFOP codes that are available in this field depend on the fiscal establishment of the site that you selected in the **Site** field. The tax groups in the **Sales tax group** and **Item sales tax group** fields are also updated based on the tax matrix and applicability rules in Golobalization studio. 

The procedure uses the BRMF demo company.

To create a project that uses Brazilian taxes, follow these steps.

1. In Dynamics 365 Finance, go to **Project management and accounting -> Projects -> All projects**.
1. Select **New**.
1. In the **Project type** field, select an option.
1. In the **Project name** field, enter values.
2. In the **Project group** field, select a value.
1. Select **Create project**.
1. Select **Project** section
1. Select the **Journals** group
2. Create and post journals.
3. Select the **Manage** section
4. Select a task under **New** group and generate if required
5. Select **Project invoice proposals** under the **Bill** group
6. Select the record and click **Invoice proposal** field
8. Post the invoice.
1. Select **OK**.
1. Close the page.

## Check the tax calculation results

1. Select **Project invoice proposals** in **Manage** tab
   - Select the **Sales tax** button
   - The targetd tax codes are displayed. 
   - During the transition period,**No posting** is marked for **CBS** and **IBS** to eunsure compliance with the current policy from Brazilian government.
  

2. Select **Project invoice proposals** in **Manage** tab
   - Select the record and click **Invoice proposal** field
   - Expand **Invoice proposal transactions**
   - Scroll to the right where displays **Use override for tax reform**, **Item tax group for tax reform** and **Tax group for tax reform**
   - Based on the applicability rule settings, the default values for the new tax types (**CBS**,**IBS**) appear in the **Tax group** and **Item tax group** under the **Tax reform** group.
   - You can change these defaults by setting the **Use override** checkbox to be **YES**, then specifying the desired values in the **Tax group** and **Item tax group** .
    
2. Select **Project invoice proposals** in **Manage** tab
   - Select the record and click **Invoice proposal** field 
   - Select the **Sales tax** button
   - The targetd tax codes are displayed. 
   - During the transition period,**No posting** is marked for **CBS** and **IBS** to eunsure compliance with the current policy from Brazilian government.
 
3. Select **Invoice journals** in **Manage** tab
   - Select **Sales tax** button
   - You can view the targeted tax codes.  
   
3. Select **Invoice ** journal in **Invoice** tab after generation.
   - Select the **Posted sales tax** button
   - You can view the targeted tax codes.     
   - During the transition period,**Prevent posting of ledger accounting entities for sales tax transactions** is marked for **CBS** and **IBS** to eunsure compliance with the current policy from Brazilian government.
   
