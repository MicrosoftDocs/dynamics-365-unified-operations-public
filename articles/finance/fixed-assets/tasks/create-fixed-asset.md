---
title: Create a fixed asset
description: Learn how to manually create a new fixed asset record from the Fixed asset list page and import fixed assets, including a step-by-step process.
author: moaamer
ms.author: moaamer
ms.topic: how-to
ms.date: 10/06/2023
ms.custom: 
ms.reviewer: twheeloc
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: AssetTable, AssetBook
ms.dyn365.ops.version: Version 7.0.0 
---

# Create a fixed asset

[!include [banner](../../includes/banner.md)]

This article explains how to create a new fixed asset record from the **Fixed asset** list page.

The system assigns the asset number, based on the number sequence that is assigned to the fixed asset group. If you use the fixed asset template to import assets via the Microsoft Excel add-in, or if you use another import job, fixed asset records are automatically created and increments the asset number.

To manually create an asset record, follow these steps.

1. Go to **Fixed assets \> Fixed assets \> Fixed assets**.
2. On the **Action pane**, select **New**.
3. In the **Fixed asset group** field, enter or select a value. The **Number** field will default if you have enabled **Autonumber fixed assets functionality** in the **Fixed assets parameters** and the **Fixed asset group**. If not, you must enter a unique number to identify the fixed asset.
4. In the **Name** field, enter a value. Enter the additional information that your business needs for this asset.
5. On the **Action pane**, select **Books**.
6. In the **Acquisition date** field, enter a date.
7. In the **Acquisition price** field, enter a number.

    - Enter the additional information that your business needs for this book.
    - Enter the additional information that your business needs for the remaining books.

8. Close the page.

You can also import fixed assets by using the Excel add-in or by running an import job from the **Data management** workspace. Before you run the import, enter the values for required fields in the template.

If you didn't define the fixed asset number in the template of the Excel add-in, or in Data management, a fixed asset number is created for each imported asset and automatically increments the number sequence for each. However, if you import assets and define asset numbers in the template, the system does **not** automatically increment the number sequence. In this case, an admin might have to manually update the number sequence. If you defined the fixed asset number in the template of the Excel add-in, the system uses the defined fixed asset number and increments the number sequence.

> [!NOTE]                                                                                                         
> After posting depreciation, the **Placed in service** and **Depreciation run date** fields are locked on the **Book** page. Both fields will be updated from the data entity.

> [!WARNING]
> A fixed asset record can't be deleted if:
> - transactions have already been posted to an associated fixed asset book.
> - the newly created fixed asset is entered on a journal line that's not posted.
> - A newly created fixed asset can't be deleted if there's an active financial dimension that is based on fixed assets. To delete this asset:
> 1. Rename the fixed asset record to mark it as deleted. Go to **Options > Record info > Rename** and set the fixed asset number accordingly.
> 2. Remove all associated fixed asset books or set **Calculate depreciation** to **No** in the asset books to avoid including the fixed asset in depreciation proposals.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
