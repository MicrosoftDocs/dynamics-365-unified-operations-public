---
title: Tax Reform Overview
description: The article describes tax calculation in sales order in Brazil tax reform solution
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

# Tax calculation in sales order in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes tax calculation in sales order in Brazil tax reform solution.

## Procedure: Create a sales order with Brazilian taxes

Create a quotation by specifying fiscal information, such as the operation type and the Código Fiscal de Operações e Prestações (CFOP) code. When you create a sales order line, select a CFOP code in the **CFOP** field. The CFOP codes that are available in this field depend on the fiscal establishment of the site that you selected in the **Site** field. The tax groups in the **Sales tax group** and **Item sales tax group** fields are also updated based on the tax matrix and applicability rules in Globalization studio. 

This procedure uses the BRMF demo company.

To create a sales quotation that uses Brazilian taxes, follow these steps:

1. In Dynamics 365 Finance, go to **Sales and marketing -> Sales orders -> All sales orders**.
1. Select **New**.
1. In the **Account type** field, select an option.
1. In the **Customer account** field, enter or select a value.
1. Select **OK**.
1. Select **Yes**.
1. Expand the **Lines** section.
1. In the **Item** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. In the **Site** field, enter or select a value.
1. In the **Warehouse** field, enter or select a value.
1. In the **CFOP** field, enter or select a value.
1. Expand the **Line details** section.
1. Select the **Setup** tab.
1. In the **Sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, enter or select a value.
1. Select the **Fiscal information** tab.
1. Select **Save**.
1. On the Action Pane, select **Sell**.
1. Select **Sales order confirmation**.
1. Select **OK**.
1. Close the page.

## Check the tax calculation results

1. Select **sales tax** in **Sell** tab
   - The targeted tax codes are displayed. 
   - During the transition period, **No posting** is marked for **CBS** and **IBS** to ensure compliance with the current policy from the Brazilian government.
1. Select **Financials** button in **Sales order lines** section
   - Select **Sales tax** option
   - The targeted tax codes are displayed. During the transition period,
   - **No posting** is marked for **CBS** and **IBS** to ensure compliance with the current policy from the Brazilian government.
   
1. Expand **Line details** section, then select **Setup** tab
   - Based on the applicability rule settings, the default values for the new tax types (**CBS**,**IBS**) appear in the **Tax group** and **Item tax group** under the **Tax reform** group.
   - You can change these defaults by setting the **Use override** checkbox to be **YES**, then specifying the desired values in the **Tax group** and **Item tax group** .
   - During the transition period, you might see targeted groups for both legacy tax types and reformed tax types coexisting under the **Sales tax** group and the **Tax reform** group.
   
1. Select **Sales order confirmation** journal in **Sell** tab
   - Select **Sales tax** button
   - You can view the targeted tax codes.  
   
1. Select **Invoice** journal in **Invoice** tab after generation.
   - Select **Posted sales tax** button
   - You can view the targeted tax codes.     
   - During the transition period, **Prevent posting of ledger accounting entities for sales tax transactions** is marked for **CBS** and **IBS** to ensure compliance with the current policy from the Brazilian government.

