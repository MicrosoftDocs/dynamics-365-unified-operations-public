---
title: Use tax calculation in purchase orders in Brazil tax reform
description: Learn about tax calculation in purchase orders in the Brazil tax reform solution
author: yanansong
ms.author: yanansong
ms.topic: how-to
ms.date: 10/06/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2025-10-01
ms.custom: 
  - bap-template
---

# Use tax calculation in purchase orders in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes tax calculation in purchase orders in the Brazil tax reform solution.

## Create a purchase order with Brazilian taxes

You can create a quotation by specifying fiscal information, such as the operation type and the Código Fiscal de Operações e Prestações (CFOP) code. When you create a purchase order line, you can select a CFOP code in the **CFOP** field. The CFOP codes that are available in this field depend on the fiscal establishment of the site that you selected in the **Site** field. The tax groups in the **Sales tax group** and **Item sales tax group** fields are also updated based on the tax matrix and applicability rules in Globalization studio. 

To create a sales quotation that uses Brazilian taxes, follow these steps.

1. In Dynamics 365 Finance, go to **Procurement and sourcing** \> **Purchase orders** \> **All purchase orders**.
1. Select **New**.
1. In the **Vendor account** field, enter or select a value.
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
1. Select **purchase order confirmation**.
1. Select **OK**.
1. Close the page.

## Check the tax calculation results

To check the tax calculation results, follow these steps.

1. In the **Purchase** tab, select **sales tax**.
   - The targeted tax codes appear. 
   - During the transition period, the system marks **No posting** for **CBS** and **IBS** to comply with the current policy from the Brazilian government.
1. In the **Purchase order lines** section, select **Financials**.
1. Select **Sales tax**.
   - The targeted tax codes appear. 
   - During the transition period, the system marks **No posting** for **CBS** and **IBS** to ensure compliance with the current policy from the Brazilian government.
1. Expand the **Line details** section, and then select the **Setup** tab.
   - Based on the applicability rule settings, the default values for the new tax types (**CBS**, **IBS**) appear in the **Tax group** and **Item tax group** under the **Tax reform** group.
   - You can change these defaults by setting the **Use override** checkbox to **YES**, then specifying the desired values in **Tax group** and **Item tax group**.
   - During the transition period, targeted groups for both legacy tax types and reformed tax types might coexist under **Sales tax** and **Tax reform**.   
1. In the **Purchase** tab, select the **Purchase order confirmations** journal.
1. Select **Sales tax**.
   - View the targeted tax codes.  
1. After generation, in the **Invoice** tab, select the **Invoice** journal.
1. Select **Posted sales tax**.
   - View the targeted tax codes.
   - During the transition period, the system marks **Prevent posting of ledger accounting entities for sales tax transactions** for **CBS** and **IBS** to comply with the current policy from the Brazilian government.

> [!IMPORTANT] 
> The **tax group** and **item tax group** are not populated when the line is saved in Brazil tax reform 2026. They will be populated once tax calculation is triggered — for example, by clicking the **Sales tax** or **Totals** button, or during document confirmation or posting.

> [!TIP]
> For using tax calculation in purchase orders, refer to the Brazil tax reform: Calculation in purchase orders video.

> [!VIDEO <dd430006-9300-485a-8c9c-766e06d48a06>] 

[Brazil tax reform: Calculation in purchase orders](https://learn-video.azurefd.net/vod/player?id=dd430006-9300-485a-8c9c-766e06d48a06)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
