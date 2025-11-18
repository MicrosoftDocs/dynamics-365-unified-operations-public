
---
title: Use tax calculation in request for quotation (RFQ) in Brazil tax reform
description: Learn about tax calculation in request for quotation (RFQ) in the Brazil tax reform solution
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

# Use tax calculation in request for quotation in Brazil tax reform

[!include [banner](../../includes/banner.md)]

This article describes tax calculation in Request for quotation (RFQ) in the Brazil tax reform solution.

## Create a purchase requisition with Brazilian taxes

You can create a purchase requisition by specifying fiscal information, such as the operation type and the Código Fiscal de Operações e Prestações (CFOP) code. When you create a purchase requisition line, you can select a CFOP code in the **CFOP** field. The CFOP codes that are available in this field depend on the fiscal establishment of the site that you selected in the **Site** field. The tax groups in the **Sales tax group** and **Item sales tax group** fields are also updated based on the tax matrix and applicability rules in Globalization studio. 

To create a purchase requisition that uses Brazilian taxes, follow these steps.

1. In Dynamics 365 Finance, go to **Procurement and sourcing** \> **Requests for quotations** \> **All requests for quotations**.
1. Select **New**.
1. In the **Purchase type** field, enter or select a value.
2. Select values for all related fields.
1. Select **OK**.
1. Expand the **Request for quotation lines** section.
2. In the **Item** field, enter or select a value.
1. In the **Quantity** field, enter a number.
2. In the **Vendor account** field, enter or select a value.
1. Select **Header** page.
3. Expand the **Vendor** section.
1. In the **Account** field, enter or select a value.
2. In the **Operation type** field, enter or select a value.
3. Select values for all related fields.
1. Select **Send** button under **Process** group.

To check a purchase quotation that uses Brazliaian taxes, follow these steps.
1. In Dynamics 365 Finance, go to **Procurement and sourcing** \> **Requests for quotations** \> **Request for quotations follow-up**\>**Request for quotation**.
1. Select the request for quotation number.
1. Select **USe Override** option if required.
3. Under **Tax Reform** group, in the **Item sales tax group** field, enter or select a value.
4. Under **Tax Reform** group, in the **Sales tax group** field, enter or select a value.
1. Select the **Fiscal information** tab.
1. Select **Save**.
 
 In the **CFOP** field, enter or select a value.

## Check the tax calculation results
No tax calculation for RFQ.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
