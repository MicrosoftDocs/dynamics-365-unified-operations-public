---
# required metadata

title: Edit financial dimensions for retail transactions
description: This topic describes how to edit financial dimensions for retail transactions in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 11/04/2020
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2018-11-15
ms.dyn365.ops.version: 

---
# Edit financial dimensions for retail transactions

[!include [banner](../includes/banner.md)]

This topic describes how to edit financial dimensions for retail transactions in Microsoft Dynamics 365 Commerce.

## Edit financial dimensions

To edit financial dimensions for retail transactions in Commerce headquarters, follow these steps.

1. Open the **Financial dimensions configuration for integrating applications** page.
1. Select the active **Default dimensions integration** record.
1. On the **Financial dimensions** FastTab, make sure that all the dimensions that you want to edit in the Excel worksheet are present in the **Selected** list. For more information, see [Data entities](../fin-ops-core/dev-itpro/financial/financial-dimension-configuration-integration.md#data-entities).
1. Download and open the Excel file from the **Statements** page, the **Retail transactions** page, or the **Transaction validation failures** tile in the **Store financials** workspace.
1. To change the transaction financial dimension, select **Design**, and then select the pencil symbol next to the **Transaction (auditable)** row.
1. Find and select the **FinancialDimensionDisplayValue** field, select a cell in the header part of the Excel worksheet, and then select **Add label**.
1. Select a cell below the cell that you selected in the previous step, select **Add Value**, and then select **Refresh**. The financial dimensions are added to the Excel worksheet, and they can then be edited and published.
1. To change the dimensions on the transaction lines, select the **Sales transactions (auditable)** row, select the pencil symbol, and then repeat steps 6 and 7.
1. To change the dimensions on the payment lines, select the **Payment transactions (auditable)** row, select the pencil symbol, and then repeat steps 6 and 7.

## Additional resources

[Edit and audit cash and carry and cash management transactions](edit-cash-trans.md)

[Edit and audit online order and asynchronous customer order transactions](edit-order-trans.md)

[Create an Excel workbook to edit retail transactions](create-excel-edit.md)

[Add fields to an Excel workbook to edit retail transactions](add-fields-excel.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]