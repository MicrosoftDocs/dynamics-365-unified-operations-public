---
title: Use tax calculation in project quotation in Brazil tax reform
description: Learn how to calculate taxes in project quotations using the Brazil tax reform solution
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 09/30/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2025-10-01
ms.custom: 
  - bap-template
---

# Use tax calculation in project quotation in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes how to calculate taxes in project quotations using the Brazil tax reform solution.

## Create a project quotation with Brazilian taxes

Create a quotation by specifying fiscal information like the operation type and the Código Fiscal de Operações e Prestações (CFOP) code. When you create a quotation line, select a CFOP code in the **CFOP** field. The CFOP codes available in this field depend on the fiscal establishment of the site selected in the **Site** field. The tax groups in the **Sales tax group** and **Item sales tax group** fields are also updated based on the tax matrix and applicability rules maintained in Global studio. 

To create a project quotation that uses Brazilian taxes, follow these steps.

1. In Dynamics 365 Finance, go to **Project management and accountings** \> **Quotations** \> **Project quotations**.
1. Select **New**.
1. In the **Account type** field, select an option.
1. In the **Customer account** field, enter or select a value.
1. Select **OK**.
2. Expand the **Lines** section.
1. In the **Transaction type** field, enter or select a value.
1. In the **Project category** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. In the **Unit price** field, enter a number.
2. In the **Line property** field, enter or select a value.
1. Expand the **Line details** section.
1. Select the **Setup** tab.
1. In the **Sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, enter or select a value.
2. In the **Use override** field, select a value if required.
3. In the **Tax group** field under **Tax reform** group, enter or select a value.
1. In the **Item tax group** field  under **Tax reform** group, enter or select a value.
1. Select **Save**.
1. On the Action Pane, select **Quote**.
1. Select **Send quotation** under **Process**.
1. In the **Print quotation** field, select **Yes**.
1. Select **OK**.
1. Close the page.
1. On the Action Pane, select **Follow up**.
1. Select **Confirm**.
1. Select **Yes**.
1. In the **Reason** field, enter or select a value.
1. Select the **Print confirmation** checkbox.
1. Select **OK**.

## Check the results for tax calculation in Brazil.

1. Select **sales tax** in the **Quote** tab.
   - The targeted tax codes are displayed during the transition period.
   - **No posting** is marked for **CBS** and **IBS** to ensure compliance with the current policy from Brazilian government.
1. Expand the **Line details** section, then select the **Setup** tab.
   - Based on the applicability rule settings, the default values for the new tax types (**CBS**, **IBS**) appear in the **Tax group** and **Item tax group** under the **Tax reform** group.
   - You can change these defaults by setting the **Use override** checkbox to be **YES**, then specifying the desired values in the **Tax group** and **Item tax group**.
   - During the transition period, you might see targeted groups for both legacy tax types and reformed tax types coexisting under the **Sales tax** group and the **Tax reform** group.
1. Select **Totals** in the **project quotation** tab.
   - You can view the summary by tax type for Brazilian tax.
   - 
> [!IMPORTANT] 
> The **tax group** and **item tax group** are not populated when the line is saved in Brazil tax reform 2026. They will be populated once tax calculation is triggered — for example, by clicking the **Sales tax** or **Totals** button, or during document confirmation or posting.
> 
[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
