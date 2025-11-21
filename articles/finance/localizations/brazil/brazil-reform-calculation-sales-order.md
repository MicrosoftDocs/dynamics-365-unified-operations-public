---
title: Use tax calculation in sales order in Brazil tax reform
description: Learn how to calculate taxes in sales orders under Brazil's tax reform. Follow step-by-step instructions to ensure compliance with updated policies.
#customer intent: As a sales manager in Brazil, I want to understand how to create a sales order with Brazilian taxes so that I can ensure compliance with the Brazil tax reform.
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 11/19/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2025-10-01
ms.custom: 
  - bap-template
---

# Use tax calculation in sales order in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes tax calculation in sales order in Brazil tax reform solution.

## Create a sales order with Brazilian taxes

You can create a quotation by specifying fiscal information, such as the operation type and the Código Fiscal de Operações e Prestações (CFOP) code. When you create a sales order line, you can select a CFOP code in the **CFOP** field. The CFOP codes that are available in this field depend on the fiscal establishment of the site that you selected in the **Site** field. The tax groups in the **Sales tax group** and **Item sales tax group** fields are also updated based on the tax matrix and applicability rules in Globalization studio. 

To create a sales order that uses Brazilian taxes, follow these steps.

1. In Dynamics 365 Finance, go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
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

To check the tax calculation results, follow these steps.

1. Select **sales tax** in the **Sell** tab.
   - The targeted tax codes are displayed. 
   - During the transition period, **No posting** is marked for **CBS** and **IBS** to ensure compliance with the current policy from the Brazilian government.
1. Select **Financials** in the **Sales order lines** section.
1. Select **Sales tax** option.
   - The targeted tax codes are displayed. During the transition period,
   - **No posting** is marked for **CBS** and **IBS** to ensure compliance with the current policy from the Brazilian government.
1. Expand **Line details** section, then select **Setup** tab.
   - Based on the applicability rule settings, the default values for the new tax types (**CBS**,**IBS**) appear in the **Tax group** and **Item tax group** under the **Tax reform** group.
   - You can change these defaults by setting the **Use override** checkbox to be **YES**, then specifying the desired values in the **Tax group** and **Item tax group**.
   - During the transition period, you might see targeted groups for both legacy tax types and reformed tax types coexisting under the **Sales tax** group and the **Tax reform** group.
1. Select **Sales order confirmation** journal in **Sell** tab.
1. Select **Sales tax** button.
   - You can view the targeted tax codes.  
1. Select **Invoice** journal in **Invoice** tab after generation.
1. Select **Posted sales tax**.
   - You can view the targeted tax codes.
   - During the transition period, **Prevent posting of ledger accounting entities for sales tax transactions** is marked for **CBS** and **IBS** to ensure compliance with the current policy from the Brazilian government.

> [!IMPORTANT]
> The **tax group** and **item tax group** aren't populated when you save the line in Brazil tax reform 2026. They populate once tax calculation is triggered—for example, by clicking the **Sales tax** or **Totals** button, or during document confirmation or posting.

> [!TIP]
> For using tax calculation in sales orders, refer to the Brazil tax reform: Calculation in sales orders video.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=c5c1b7bb-1ba0-4281-addc-2d1835ff3632]

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
