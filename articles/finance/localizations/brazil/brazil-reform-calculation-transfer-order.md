---
title: Use tax calculation in transfer orders in Brazil tax reform
description: Learn how to calculate taxes in transfer orders under Brazil's tax reform. Follow step-by-step instructions to ensure compliance with updated fiscal policies.
#customer intent: As a finance professional in Brazil, I want to understand how to calculate taxes in transfer orders so that I can ensure compliance with the Brazil tax reform.
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

# Use tax calculation in transfer orders in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes tax calculation in transfer orders in Brazil tax reform solution.

## Create a transfer order with Brazilian taxes

You can create a quotation by specifying fiscal information, such as the operation type and the Código Fiscal de Operações e Prestações (CFOP) code. When you create a transfer order line, you can select a CFOP code in the **CFOP** field. The CFOP codes that are available in this field depend on the fiscal establishment of the site that you selected in the **Site** field. The tax groups in the **Sales tax group** and **Item sales tax group** fields are also updated based on the tax matrix and applicability rules in Globalization studio. 

To create a transfer order that uses Brazilian taxes, follow these steps:

1. In Dynamics 365 Finance, go to **Inventory management** \> **Inbound order** \> **Transfer orders** or **Inventory management** \> **Outbound orders** \> **Transfer order**
1. Select **New**.
1. Expand the **Lines** section.
1. In the **From warehouse** field, enter or select a value.
1. In the **To warehouse** field, enter or select a value.
1. Select **Save**.
1. Expand the **Transfer order Lines** section.
1. In the **Item** field, enter or select a value.
1. In the **Transfer Quantity** field, enter a number.
1. In the **CFOP** field, enter or select a value.
1. Expand the **Line details** section.
1. Select the **Fiscal information** tab.
1. In the **Sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, enter or select a value.
1. Set the **Use override** checkbox to be **YES** if necessary.
1. In the **Tax group** field under the **Tax reform** group, enter or select a value.
1. In the **Item tax group** field under the **Tax reform** group, enter or select a value.
1. Select **Save**.
1. On the Action Pane, select **Sales tax** under **View** group in the **Transfer order** page.
1. Select **transfer order confirmation**.
1. Select **OK**.
1. Close the page.

## Check the tax calculation results

To check the tax calculation results, follow these steps:

1. On the Action Pane, select **Sales tax** under **View** group in the **Transfer order** page.
   - The targeted tax codes are displayed. 
   - During the transition period, **No posting** is marked for **CBS** and **IBS** to ensure compliance with the current policy from the Brazilian government.
1. Expand **Line details** section, then select **Fiscal information** tab.
   - Based on the applicability rule settings, the default values for the new tax types (**CBS**,**IBS**) appear in the **Tax group** and **Item tax group** under the **Tax reform** group.
   - You can change these defaults by setting the **Use override** checkbox to be **YES**, then specifying the desired values in the **Tax group** and **Item tax group**.
   - During the transition period, you might see targeted groups for both legacy tax types and reformed tax types coexisting under the **Sales tax** group and the **Tax reform** group.
  
> [!IMPORTANT] 
> The **tax group** and **item tax group** aren't populated when the line is saved in Brazil tax reform 2026. They are populated once tax calculation is triggered—for example, by clicking the **Sales tax** or **Totals** button, or during document confirmation or posting.

> [!TIP]
> For using tax calculation in transfer orders, refer to the Brazil tax reform: Calculation in sales orders video.

> [!video https://learn-video.azurefd.net/vod/player?id=271d2617-666b-48eb-8058-46ce067f832f]

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
