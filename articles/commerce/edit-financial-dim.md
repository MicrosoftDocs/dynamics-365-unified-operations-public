---
# required metadata

title: Edit financial dimensions for retail transactions
description: This topic describes how to edit financial dimensions for retail transactions in Microsoft Dynamics 365 Commerce.
author: josaw1
manager: AnnBe
ms.date: 10/30/2020
ms.topic: index-page
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Core, Operations, Retail
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

This topic describes how to edit financial dimensions for retail transactions in Microsoft Dynamics 365 Commerce.

[!include [banner](../includes/banner.md)]

## Edit financial dimensions

To edit financial dimensions for retail transactions in Commerce headquarters, follow these steps.

1. Go to **Financial dimensions configuration for integrating applications**.
1. Select the active **Default Dimensions integration** record.
1. Under the **Financial dimensions** FastTab, ensure that all the dimensions that you want to edit in the Excel worksheet are present in the **Selected** column. For more information, see https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/financial/financial-dimension-configuration-integration#data-entities.
1. Download and open the Excel file from the **Statements** page, **Retail transactions** page, or the **Transaction validation failures** tile on the **Store financials** workspace.   
1. To change the transaction header financial dimension, select **Design**, and then select the pencil symbol next to the **Transaction (auditable)** row.
1. Find the field **FinancialDimensionDisplayValue**, select a cell in the header part of the Excel worksheet, and then select **Add label**.
1. Select a cell below the cell chosen in the step above, select **Add Value**, and then select **Refresh**. The financial dimensions will be added to the Excel sheet and these can now be edited and published.
1. To change the dimensions on the transaction lines, select the **Sales transactions (auditable)** row, and then select the pencil button and repeat steps 6 and 7 above.
1. To change the dimensions on the payment lines, select the **Payment transactions (auditable)** row, and then select the pencil button and repeat steps 6 and 7 above.

## Additional resources

[Edit and audit cash and carry and cash management transactions](edit-cash-trans.md)

[Edit and audit online order and asynchronous customer order transactions](edit-order-trans.md)

[Create an Excel spreadsheet to edit retail transactions](create-excel-edit.md)

[Add fields to an Excel spreadsheet to edit retail transactions](add-fields-excel.md)
