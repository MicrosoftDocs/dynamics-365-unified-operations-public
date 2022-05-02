---
# required metadata

title: Set up fixed asset locations and numbering (Russia)
description: This topic explains how to set up locations and numbering for Russian fixed asset.
author: anasyash
ms.date: 05/02/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Set up fixed asset locations and numbering (Russia)

[!include [banner](../includes/banner.md)]

## Set up a fixed asset location 

Locations are defined for fixed assets and are used to calculate depreciation accrual. Depending on the fixed asset location, the calculated depreciation amount is allocated either to the production cost of the product or to a ledger account.

You must define the location of a fixed asset before you acquire the fixed asset. If you're transferring a fixed asset from one location to another, you can create a transfer transaction to register the transfer of the asset.

You can use the **FA location** page to set up a fixed asset location and specify the company division that the asset belongs to.

1. Select **Fixed assets (Russia)** \> **Setup** \> **Location** to open the **FA location** page.
2. Select **New** to create a fixed asset location.
3. In the **Location** field, enter a location code. In the **Name** field, enter a description for the location.
4. If the fixed asset location is somewhere other than the company's head office, in the **Separate division ID** field, select a separate division. If you don't specify a separate division, the location of the fixed asset is the head office. If the selected division is independent, the **Independent** option is automatically set to **Yes** (**[Division setup](/dynamicsax-2012/appuser-itpro/rus-set-up-a-division-for-a-company-and-associate-it-with-a-vendor)**). 
5. On the **Fixed asset posting profiles** FastTab, select **New** to create a line.
7. In the **Groupings** field, select the grouping for the fixed asset posting profile:

    - **Table** – The posting profile is grouped by the selected fixed asset.
    - **Group** – The posting profile is grouped by the depreciation group.
    - **All** – The posting profile is grouped by all fixed assets.
    - **Accounting** – The posting profile is grouped by the value model.

8. In the **Account relation** field, select the depreciation group, fixed asset, or value model that the posting profile is used for.
9. In the **Main account** field, select the ledger account to use to post the fixed asset transactions.
10. In the **Account for depr.bonus** field, select the ledger account to use to post the depreciation bonus for the fixed asset, if a depreciation bonus applies.

## Set up fixed asset numbering

You have two options for assigning numbers to fixed assets:

- **Manual selection** – This option is appropriate for a company that has few fixed assets. No setup is required for manual selection.
- **Automatic numbering of fixed assets that is based on the fixed asset group** – This option is appropriate for a company that has many fixed assets. On the **FA groups** page, you can create many account/group numbers for fixed assets and attach a number sequence to each group (**Fixed assets (Russia)** \> **Setup** \> **FA groups**). You must specify a default number sequence when you set up fixed assets.

### Set up automatic numbering of all fixed assets from one default number sequence

1. Select **Organization administration** \> **Number sequences** \> **Number sequences**, and create a default number sequence that is used to number fixed assets.
2. Select **Fixed assets (Russia)** \> **Setup** \> **Parameters** to open the **Fixed asset parameters** page.
3. On the **Number sequences** tab, select a number sequence code, which is used for automatic creation of fixed asset number
4. On the **Fixed assets** tab, set the **Autonumeration FA** option to **Yes**. 

If **Autonumeration FA** option is set to **Yes**. then when you create a fixed asset on the **Fixed assets** page (**Fixed assets (Russia)** \> **Common** \> **Fixed assets**), the next number in the sequence is automatically entered in the **FA inventory number** field.

### Set up automatic numbering of fixed assets that is based on the fixed asset group

1. Select **Fixed assets (Russia)** \> **Setup** \> **FA groups**.
2. Select the **Autonumeration FA** check box for the selected fixed asset group, and then select the appropriate number sequence in the **FA autonumbering sequence** field.

This number sequence is used for all fixed assets that are assigned to the fixed asset group.

> [!NOTE]
> To create a fixed asset group, select **New**, and then enter the required details.

## Create bar codes from fixed asset numbers

1. Select **Fixed assets (Russia)** \> **Periodic** \> **Create barcodes from FA inventory number**.
2. On the **Records to include** FastTab, select **Filter**, and then, in the **Assets** dialog box, enter the criteria that are used to select fixed assets. Then select **OK** to return to the **Create barcodes from FA inventory number** dialog box.
4. Select **OK**. If you haven't specified a bar code for the fixed asset, the value that you specified in the **FA inventory number** field appears in the **Bar code** field on the **Fixed assets** page (**Fixed assets (Russia)** \> **Common** \> **Fixed assets**).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
