---
title: Tax calculation in projects in Brazil tax reform
description: The article describes tax calculation in projects in Brazil tax reform solution
author: yanansong
ms.author: yanansong
ms.topic: how-to
<<<<<<< HEAD:articles/finance/localizations/brazil/br-reform-calculation-project.md
ms.date: 09/30/2025
=======
ms.date: 09/29/2025
>>>>>>> 431829cd3f4ae856ae08491e3f5e83baf06aec4e:articles/finance/localizations/brazil/brazil-reform-calculation-project.md
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2025-10-01
ms.custom: 
  - bap-template
---

# Tax calculation in projects in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes how to calculate taxes in projects using the Brazil tax reform solution.

## Procedure: create a project with Brazilian taxes

You can create a project by specifying fiscal information, such as the operation type and the Código Fiscal de Operações e Prestações (CFOP) code. When you create a sales order line, you can select a CFOP code in the **CFOP** field. The CFOP codes that are available in this field depend on the fiscal establishment of the site that you selected in the **Site** field. The tax groups in the **Sales tax group** and **Item sales tax group** fields are also updated based on the tax matrix and applicability rules in Globalization studio. 

This procedure uses the BRMF demo company.

To create a project that uses Brazilian taxes, follow these steps.

1. In Dynamics 365 Finance, go to **Project management and accounting > Projects > All projects**.
1. Select **New**.
1. In the **Project type** field, select an option.
1. In the **Project name** field, enter values.
1. In the **Project group** field, select a value.
1. Select **Create project**.
1. Select the **Project** section.
1. Select the **Journals** group.
1. Create and post journals.
1. Select the **Manage** section.
1. Select a task under the **New** group and generate it if necessary.
1. Select **Project invoice proposals** under the **Bill** group.
1. Select the record and then select the **Invoice proposal** field.
1. Post the invoice.
1. Select **OK**.
1. Close the page.

## Check the tax calculation results

1. Select **Project invoice proposals** in the **Manage** tab.
   - Select the **Sales tax** button.
   - The targeted tax codes are displayed. 
   - During the transition period, **No posting** is marked for **CBS** and **IBS** to ensure compliance with the current policy from the Brazilian government.

1. Select **Project invoice proposals** in **Manage** tab
   - Select the record, and then select the **Invoice proposal** field.
   - Expand **Invoice proposal transactions**.
   - Scroll to the right to view **Use override for tax reform**, **Item tax group for tax reform**, and **Tax group for tax reform**.
   - Based on the applicability rule settings, the default values for the new tax types (**CBS**, **IBS**) appear in the **Tax group** and **Item tax group** under the **Tax reform** group.
   - Change these defaults by setting the **Use override** checkbox to **YES**, and then specify the desired values in the **Tax group** and **Item tax group**.
    
1. Select **Project invoice proposals** in **Manage** tab
   - Select the record, and then select the **Invoice proposal** field.
   - Select the **Sales tax** button
   - The targeted tax codes are displayed. 
   - During the transition period,**No posting** is marked for **CBS** and **IBS** to ensure compliance with the current policy from Brazilian government.
 
1. Select **Invoice journals** in the **Manage** tab.
   - Select the **Sales tax** button.
   - View the targeted tax codes.
   
1. Select **Invoice** journal in the **Invoice** tab after generation.
   - Select the **Posted sales tax** button.
   - View the targeted tax codes.
   - During the transition period, **Prevent posting of ledger accounting entities for sales tax transactions** is marked for **CBS** and **IBS** to ensure compliance with the current policy from the Brazilian government.
   - During the transition period, **Prevent posting of ledger accounting entities for sales tax transactions** is marked for **CBS** and **IBS** to ensure compliance with the current policy from the Brazilian government.
   
