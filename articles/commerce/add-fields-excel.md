---
# required metadata

title: Add fields to an Excel spreadsheet to edit retail transactions
description: This topic describes how to add fields to a Microsoft Excel spreadsheet to edit retail transactions in Microsoft Dynamics 365 Commerce.
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
# Add fields to an Excel spreadsheet to edit retail transactions

[!include [banner](../includes/banner.md)]

This topic describes how to add fields to a Microsoft Excel spreadsheet to edit retail transactions in Microsoft Dynamics 365 Commerce.

## Overview

When an Excel file is generated to edit retail transactions, the Excel file is populated with some default fields. If a field that needs to be updated is not visible by default in the generated Excel file, the desired field can be added.

## Add fields to an Excel spreadsheet sheet

To add fields to an Excel spreadsheet to edit transactions, follow these steps.

1. Download and open the Excel file from the **Statements** page, **Retail transactions** page, or the **Transaction validation failures** tile on the **Store financials** workspace.
1. Select **Design**.
1. Select the pencil symbol on the desired table and find the field that you want to add in the list of available fields.
1. Select **Add**, and then select **Update**. You can reorder fields fields as you prefer.   
1. Once the update is finished, select **Refresh** to fetch the data for the new column.

The new field and data for the field should now be available in Excel for editing.

## Additional resources

[Edit and audit cash and carry and cash management transactions](edit-cash-trans.md)

[Edit and audit online order and asynchronous customer order transactions](edit-order-trans.md)

[Edit financial dimensions for retail transactions](edit-financial-dim.md)

[Create an Excel spreadsheet to edit retail transactions](create-excel-edit.md)
