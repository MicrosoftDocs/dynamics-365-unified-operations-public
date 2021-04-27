---
# required metadata

title: Create an Excel workbook to edit retail transactions
description: This topic describes how to create an Excel workbook so that you can edit retail transactions in Microsoft Dynamics 365 Commerce.
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
# Create an Excel workbook to edit retail transactions

[!include [banner](../includes/banner.md)]

This topic describes how to create an Excel workbook so that you can edit retail transactions in Microsoft Dynamics 365 Commerce.

## Overview

There is a predefined Excel template that customers can access from different parts of the system and use to edit and audit retail transactions. However, customers can also create a custom Excel workbook for this purpose.

## Create and configure an Excel workbook

To create and configure an Excel workbook so that you can edit retail transactions, follow these steps.

1. Open Excel, and create a blank workbook.
1. On the **Insert** tab, select **My add-ins**.
1. In the right pane, select the **Add server information** link.
1. Enter the server URL, and then select **OK**.
1. If you receive a "No applet registrations found" error message, follow these steps to resolve the issue:

    1. In Commerce, go to **System administration \> Setup \> Office app parameters**.
    1. On the **App parameters** FastTab, select **Initialize app parameters**.
    1. In the confirmation message box, select **OK**.
    1. On the **Registered applets** FastTab, select **Initialize applet registration**.
    1. Repeat the previous three steps as required.

1. Select **Design**, and then select **Add table**.
1. Based on the data that has to be modified, select the entities that must be added to the Excel workbook for editing. Use the following table as a reference.

    | Transaction type | Data entities to use |
    |------------------|----------------------|
    | Cash and carry transactions, Online orders, Async customer orders, Async customer quotes | Transaction (auditable), Sales transaction (auditable), Payment transactions (auditable), Tax transactions (auditable), Discount transactions (auditable), Charge transactions (auditable) |
    | Bank drop | Transaction (auditable), Banked tender transactions (auditable) |
    | Safe drop | Transaction (auditable), Safe tender transactions (auditable) |
    | Tender declaration | Transaction (auditable), Tender declaration transactions (auditable) |
    | Income, Expense | Transaction (auditable), Income/Expense transactions (auditable), Payment transactions (auditable) |
    | Declare starting amount, Tender removal, Float entry, Change tender, Invoice payment, Customer deposit | Transaction (auditable), Payment transactions (auditable) |

    > [!NOTE]
    > It's important that you add only one data entity to each Excel workbook. Additionally, all fields that are marked by a key symbol must be added to the relevant workbook.

1. After the workbook is configured, apply the required filters. Be sure to apply the same filters to all the worksheets in the file. Avoid loading very large amounts of data into the Excel file. Otherwise, performance might be affected, and Excel and your system might slow down. We recommend that you always use "Company" and either "Statement Number" or "Transaction Number" as filters for your file.
1. After the filters are configured, select **Refresh** to load the data.
1. Edit the required data, and then publish it. If the **Publish** button is unavailable, some key fields probably weren't added to the Excel workbook.

## Additional resources

[Edit and audit cash and carry and cash management transactions](edit-cash-trans.md)

[Edit and audit online order and asynchronous customer order transactions](edit-order-trans.md)

[Edit financial dimensions for retail transactions](edit-financial-dim.md)

[Add fields to an Excel workbook to edit retail transactions](add-fields-excel.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]