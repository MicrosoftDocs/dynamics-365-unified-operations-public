---
title: Use tax calculation in free text invoices in Brazil tax reform
description: Learn how to calculate taxes in free text invoices under Brazil's tax reform. Follow step-by-step instructions to ensure compliance with updated regulations.
#customer intent: As a finance professional in Brazil, I want to create a free text invoice with Brazilian taxes so that I can comply with local tax regulations.
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

# Use tax calculation in free text invoices in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes tax calculation in free text invoices in Brazil tax reform solution.

## Create a free text invoice with Brazilian taxes

You can create a free text invoice by specifying fiscal information, such as the operation type and the Código Fiscal de Operações e Prestações (CFOP) code. When you create a free text invoice line, you can select a CFOP code in the **CFOP** field. The CFOP codes that are available in this field depend on the fiscal establishment of the site that you selected in the **Site** field. The tax groups in the **Sales tax group** and **Item sales tax group** fields are also updated based on the tax matrix and applicability rules in Globalization studio. 

To create a free text invoice that uses Brazilian taxes, follow these steps:

1. In Dynamics 365 Finance, go to **Account Receivable** \> **Invoices** \> **All free text invoices**.
1. Select **New**.
1. In the **Fiscal establishment ID** field, select an option.
1. In the **Customer account** field, enter or select a value.
1. In the **Invoice account** field, enter or select a value.
1. In the **Operation type** field, enter or select a value.
1. Select **Save**.
1. Expand the **Lines** section.
1. In the **Main account** field, enter or select a value.
1. In the **Quantity** field, enter or select a value.
1. In the **Unit price** field, enter or select a value.
1. In the **CFOP** field, enter or select a value.
1. In the **Sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, enter or select a value.
1. Select **Use override for tax reform** if necessary.
1. In the **Tax group for tax reform** field, enter or select a value.
1. In the **Item tax group for tax reform** field, enter or select a value.
1. Select the **Fiscal information** tab.
1. Select **Save**.
   
## Check the tax calculation results

To check the tax calculation results, follow these steps:

1. Select **sales tax** at the top.
   - The targeted tax codes are displayed. 
   - During the transition period, **No posting** is marked for **CBS** and **IBS** to ensure compliance with the current policy from the Brazilian government.
1. Select line
   - Based on the applicability rule settings, the default values for the new tax types (**CBS**,**IBS**) appear in the **Tax group for tax reform** and **Item tax group for tax reform**.
   - You can change these defaults by setting the **Use override** checkbox to **YES**, then specifying the desired values in the **Tax group** and **Item tax group**.
   - During the transition period, you might see targeted groups for both legacy tax types and reformed tax types coexisting under the **Sales tax** group and the **Tax reform** group.
   
[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
