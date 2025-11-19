---
title: Use tax calculation in vendor invoice journal in Brazil tax reform
description: Learn about tax calculation in vendor invoice journal in Brazil tax reform solution
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

# Use tax calculation in vendor invoice journal in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes tax calculation in vendor invoice journal in Brazil tax reform solution.

## Create a vendor invoice journal with Brazilian taxes

You can create a vendor invoice journal by specifying fiscal information, such as the operation type and the Código Fiscal de Operações e Prestações (CFOP) code. When you create a vendor invoice journal line, you can select a CFOP code in the **CFOP** field. The CFOP codes that are available in this field depend on the fiscal establishment of the site that you selected in the **Site** field. The tax groups in the **Sales tax group** and **Item sales tax group** fields are also updated based on the tax matrix and applicability rules in Globalization studio. 

To create a vendor invoice journal that uses Brazilian taxes, follow these steps.

1. In Dynamics 365 Finance, go to **Account Payable** \> **Invoices** \> **Invoice journal**.
1. Select **New**.
1. In the **Name** field, enter or select a value.
1. Select **Lines**.
1. In the **Account type** field, select **Vendor**.
1. In the **Account** field, enter or select a vendor account.
1. In the **Sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, enter or select a value.
1. Select **Use override for tax reform** if necessary.
1. In the **Tax group for tax reform** field, enter or select a value.
1. In the **Item tax group for tax reform** field, enter or select a value.
1. Select the **Fiscal information** tab.
1. Select **Save**.
   
## Check the tax calculation results

To check the tax calculation results, follow these steps.

1. Select **sales tax** on top in the **List** page.
   - The targeted tax codes are displayed. 
   - During the transition period, **No posting** is marked for **CBS** and **IBS** to ensure compliance with the current policy from the Brazilian government.
1. Select **OK**.
   - Based on the applicability rule settings, the default values for the new tax types (**CBS**,**IBS**) appear in the **Tax group for tax reform** and **Item tax group for tax reform**.
   - You can change these defaults by setting the **Use override** checkbox to be **YES**, then specifying the desired values in the **Tax group** and **Item tax group**.
1. Select **General** page
   - Based on the applicability rule settings, the default values for the new tax types (**CBS**,**IBS**) appear in the **Tax group** and **Item tax group** under **Tax reform** group 
   - You can change these defaults by setting the **Use override** checkbox to be **YES**, then specifying the desired values in the **Tax group** and **Item tax group**.
   - During the transition period, you might see targeted groups for both legacy tax types and reformed tax types coexisting under the **Sales tax** group and the **Tax reform** group.
   - 
[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
