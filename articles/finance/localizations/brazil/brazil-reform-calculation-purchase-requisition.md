---
title: Use tax calculation in purchase requisitions in Brazil tax reform
description: Learn about tax calculation in purchase requisitions in the Brazil tax reform solution
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

# Use tax calculation in purchase requisitions in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes tax calculation in purchase requisitions in the Brazil tax reform solution.

## Create a purchase requisition with Brazilian taxes

You can create a purchase requisition by specifying fiscal information, such as the operation type and the Código Fiscal de Operações e Prestações (CFOP) code. When you create a purchase requisition line, you can select a CFOP code in the **CFOP** field. The CFOP codes that are available in this field depend on the fiscal establishment of the site that you selected in the **Site** field. The tax groups in the **Sales tax group** and **Item sales tax group** fields are also updated based on the tax matrix and applicability rules in Globalization studio. 

To create a purchase requisition that uses Brazilian taxes, follow these steps.

1. In Dynamics 365 Finance, go to **Procurement and sourcing** \> **purchase requisitions** \> **All purchase requisitions**.
1. Select **New**.
1. In the **Name** field, enter or select a value.
1. Select **Select default project** if required.
2. Then select **Buying legal entity** and **Project**.
3. Select **OK**.
1. Expand the **Lines** section.
2. In the **Operation type** field, enter or select a value.
3. In the **Buying legal entity** field, enter or select a value of the legal entity in Brazil.
1. In the **Item** field, enter or select a value.
1. In the **Quantity** field, enter a number.
2. In the **Vendor account** field, enter or select a value.
1. In the **Site** field, enter or select a value.
1. In the **Warehouse** field, enter or select a value.
1. In the **CFOP** field, enter or select a value.
1. Expand the **Line details** section.
1. Select the **Details** tab.
1. Select **USe Override** option if required.
3. Under **Tax Reform** group, in the **Item sales tax group** field, enter or select a value.
4. Under **Tax Reform** group, in the **Sales tax group** field, enter or select a value.
1. Select the **Fiscal information** tab.
1. Select **Save**.
  

## Check the tax calculation results

To check the tax calculation results, follow these steps.

1. In the **Purchase order lines** section, select **Financials**.
1. Select **Sales tax**.
   - The targeted tax codes appear. 
   - During the transition period, the system marks **No posting** for **CBS** and **IBS** to ensure compliance with the current policy from the Brazilian government.
1. Expand the **Line details** section, and then select the **Details** tab.
   - Based on the applicability rule settings, the default values for the new tax types (**CBS**, **IBS**) appear in the **Tax group** and **Item tax group** under the **Tax reform** group.
   - You can change these defaults by setting the **Use override** checkbox to **YES**, then specifying the desired values in **Tax group** and **Item tax group**.
   - During the transition period, targeted groups for both legacy tax types and reformed tax types might coexist under **Sales tax** and **Tax reform**.   
   
[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
