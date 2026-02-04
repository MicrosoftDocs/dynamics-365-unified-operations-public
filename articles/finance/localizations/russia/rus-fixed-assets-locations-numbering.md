---
title: Set up fixed asset locations and numbering (Russia)
description: Learn how to set up locations and numbering for Russian fixed assets in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/22/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
---

# Set up fixed asset locations and numbering (Russia)

[!include [banner](../../includes/banner.md)]

This article explains how to set up locations and numbering for Russian fixed assets in Microsoft Dynamics 365 Finance.

## Set up a fixed asset location 

Locations are defined for fixed assets and are used to calculate depreciation accrual. Depending on the fixed asset location, the calculated depreciation amount is allocated either to the production cost of the product or to a ledger account.

You must define the location of a fixed asset before you acquire the fixed asset. If you're transferring a fixed asset from one location to another, you can create a transfer transaction to register the transfer of the asset.

You can use the **FA location** page to set up a fixed asset location and specify the company division that the asset belongs to.

To set up a fixed asset location , follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets (Russia)** \> **Setup** \> **Location** to open the **FA location** page.
1. Select **New** to create a fixed asset location.
1. In the **Location** field, enter a location code. In the **Name** field, enter a description for the location.
1. If the fixed asset location is somewhere other than the company's head office, in the **Separate division ID** field, select a separate division. If you don't specify a separate division, the location of the fixed asset is the head office. If the selected division is independent, the **Independent** option is automatically set to **Yes**. 
1. On the **Fixed asset posting profiles** FastTab, select **New** to create a line.
1. In the **Groupings** field, select the grouping for the fixed asset posting profile:

    - **Table** – The posting profile is grouped by the selected fixed asset.
    - **Group** – The posting profile is grouped by the depreciation group.
    - **All** – The posting profile is grouped by all fixed assets.
    - **Accounting** – The posting profile is grouped by the value model.

1. In the **Account relation** field, select the depreciation group, fixed asset, or value model that the posting profile is used for.
1. In the **Main account** field, select the ledger account to use to post the fixed asset transactions.
1. In the **Account for depr.bonus** field, select the ledger account to use to post the depreciation bonus for the fixed asset, if a depreciation bonus applies.

## Set up fixed asset numbering

You have two options for assigning numbers to fixed assets:

- **Manual selection** – This option is appropriate for a company that has few fixed assets. No setup is required for manual selection.
- **Automatic numbering of fixed assets that is based on the fixed asset group** – This option is appropriate for a company that has many fixed assets. On the **FA groups** page, you can create many account/group numbers for fixed assets and attach a number sequence to each group (**Fixed assets (Russia)** \> **Setup** \> **FA groups**). You must specify a default number sequence when you set up fixed assets.

### Set up automatic numbering of all fixed assets from one default number sequence

To set up automatic numbering of all fixed assets from one default number sequence, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** \> **Number sequences** \> **Number sequences**, and create a default number sequence that is used to number fixed assets.
1. Select **Fixed assets (Russia)** \> **Setup** \> **Parameters** to open the **Fixed asset parameters** page.
1. On the **Number sequences** tab, select a number sequence code, which is used for automatic creation of fixed asset number.
1. On the **Fixed assets** tab, set the **Autonumeration FA** option to **Yes**. 

If the **Autonumeration FA** option is set to **Yes**, then when you create a fixed asset on the **Fixed assets** page (**Fixed assets (Russia)** \> **Common** \> **Fixed assets**), the next number in the sequence is automatically entered in the **FA inventory number** field.

### Set up automatic numbering of fixed assets that is based on the fixed asset group

To set up automatic numbering of fixed assets that is based on the fixed asset group, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets (Russia)** \> **Setup** \> **FA groups**.
1. Select the **Autonumeration FA** checkbox for the selected fixed asset group, and then select the appropriate number sequence in the **FA autonumbering sequence** field.

This number sequence is used for all fixed assets that are assigned to the fixed asset group.

> [!NOTE]
> To create a fixed asset group, select **New**, and then enter the required details.

## Create bar codes from fixed asset numbers

To create bar codes from fixed asset numbers, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets (Russia)** \> **Periodic** \> **Create barcodes from FA inventory number**.
1. On the **Records to include** FastTab, select **Filter**, and then, in the **Assets** dialog, enter the criteria that are used to select fixed assets. Then select **OK** to return to the **Create barcodes from FA inventory number** dialog.
1. Select **OK**. If you haven't specified a bar code for the fixed asset, the value that you specified in the **FA inventory number** field appears in the **Bar code** field on the **Fixed assets** page (**Fixed assets (Russia)** \> **Common** \> **Fixed assets**).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
