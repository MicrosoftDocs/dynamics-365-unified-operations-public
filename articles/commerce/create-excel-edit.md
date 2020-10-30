---
# required metadata

title: Create an Excel spreadsheet to edit retail transactions
description: This topic describes how to create an Excel spreadsheet to edit retail transactions in Microsoft Dynamics 365 Commerce.
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
# Create an Excel spreadsheet to edit retail transactions

[!include [banner](../includes/banner.md)]

This topic describes how to create an Excel spreadsheet to edit retail transactions in Microsoft Dynamics 365 Commerce.

## Overview

While there is a predefined Excel template that customers can access from different parts of the system to edit and audit retail transactions, customers also have a choice to create a custom Excel sheet for this purpose.

## Create and configure the spreadsheet

To create and configure the Excel spreadsheet to edit retail transactions, follow these steps.

1. Open Excel and create a blank spreadsheet.
1. Select the **Insert** tab, and then select **My add-ins**.
1. Select the **Add server information** link on the right pane. 
1. Enter the **Server URL**, and then select **OK**.
1. If you get the **No applet registrations found** error message, follow these steps to resolve the issue.
    1. Go to **System administration > Setup > Office app parameters**.
    1. In the **App parameters** FastTab, select **Initialize app parameters**.
    1. In the confirmation dialog box, select **OK**.
    1. In the **Registered applets** FastTab, select **Initialize applet registration**.
    1. Repeat steps ii-iv as needed.   
1. Select **Design**, and then select **Add table**.
1. Based on the data that needs to be modified, select the entities that need to be added to the Excel sheet for editing using the following table as a reference.
    
    | Transaction type | Data entities to use|
    |------------------|---------------------|
    | Cash and carry transactions / Online orders / Async customer orders / Async customer quotes | Transaction (auditable), Sales transaction (auditable), Payment transactions (auditable), Tax transactions (auditable), Discount transactions (auditable), Charge transactions (auditable) |
    | Bank drop | Transaction (auditable), Banked tender transactions (auditable) |
    | Safe drop |	Transaction (auditable), Safe tender transactions (auditable) |
    | Tender declaration | Transaction (auditable), Tender declaration transactions (auditable) |
    | Income / Expense | Transaction (auditable), Income/Expense transactions (auditable), Payment transactions (auditable) |
    | Declare starting amount / Tender removal / Float entry / Change tender / Invoice payment / Customer deposit | Transaction (auditable), Payment transactions (auditable) |

    > [!NOTE]
    > It is important to add only one data entity to each Excel spreadsheet. Also, all fields that are indicated with key symbol must be added to the relevant spreadsheet.

1. Once the spreadsheet is configured, apply the required filters. Make sure to apply the same filters to all the worksheets in the file. Avoid loading huge amounts of data to the Excel file since this can impact performance, slowing down Excel and your system. It is recommended to always use "Company" and "Statement Number" or "Transaction Number" as filters on your file.
1. After the filters are configured, select **Refresh** to load the data.
1. Edit the required data and then publish it. If the **Publish** button is disabled, it is probably because not all key fields were added to the Excel spreadsheet.

## Additional resources

[Edit and audit cash and carry and cash management transactions](edit-cash-trans.md)

[Edit and audit online order and asynchronous customer order transactions](edit-order-trans.md)

[Edit financial dimensions for retail transactions](edit-financial-dim.md)

[Add fields to an Excel spreadsheet to edit retail transactions](add-fields-excel.md)
