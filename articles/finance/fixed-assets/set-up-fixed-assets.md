---
title: Set up fixed assets
description: Learn about the setup of the Fixed assets module, including outlines on depreciation profiles, books, and fixed asset posting profiles and groups.
author: moaamer
ms.author: saraschi
ms.topic: article
ms.date: 05/27/2026
ms.update-cycle: 1095-days
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: AssetTable
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 8be64197-fea1-4a34-8af2-d939919c28b1
ms.custom: evergreen
---

# Set up fixed assets

[!include [banner](../includes/banner.md)]
[!INCLUDE [lcs-freeze-banner](../../includes/lcs-freeze-banner.md)]

This article provides an overview of the setup of the **Fixed assets** module. 

Parameters control the general behavior in Fixed assets. Fixed asset groups let you group your assets and specify default attributes for every asset that you assign to a group. You assign books to fixed asset groups. Books track the financial value of a fixed asset over time by using the depreciation configuration that you define in the depreciation profile.

You assign fixed assets to a group when you create them. By default, the books that you assign to the fixed asset group are then assigned to the fixed asset. You associate books that are configured to post to the general ledger with a posting profile. You define ledger accounts for each book in the posting profile, and these accounts are used when fixed asset transactions are posted.

:::image type="content" source="./media/FAComponents_Updated.png" alt-text="Screenshot of fixed asset components.":::

## Depreciation profiles

First, set up depreciation profiles. In the depreciation profile, configure how the value of an asset is depreciated over time. Define the method of depreciation, the depreciation year (calendar year or fiscal year), and the frequency of depreciation. For more information, see [Set up and create depreciation profiles](tasks/set-up-depreciation-profiles.md).

## Books

After you set up depreciation profiles, create the required books for your assets. Each book tracks an independent financial lifecycle of an asset. You can configure books to post associated transactions to the general ledger. This configuration is the default setting, because it's typically used for corporate financial reporting. Books that don't post to the general ledger post only to the Fixed asset subledger and are typically used for tax reporting purposes.

You assign a primary depreciation profile to every book. Books can also have an alternative or switchover depreciation profile, if this type of profile is applicable. To automatically include the fixed asset book in depreciation runs, you must enable the **Calculate depreciation** option. If you don't enable this option for an asset, the depreciation proposal skips the asset.

You can also set up derived books. The specified derived transactions are posted against the derived books as an exact copy of the primary transaction. Therefore, derived transactions are typically set up for acquisitions and disposals, not for depreciation transactions. For more information, see [Set up value models](tasks/set-up-value-models.md).

An option on the **Fixed assets parameters** page lets you turn the locking functionality on or off. This feature is enabled in the **Feature management workspace**.

## Fixed asset posting profiles

After you set up books, you can create the posting profile. The posting profile must be defined by book, but it can also be defined at a more detailed level. For example, you can define the posting profile for the combination of a book and a fixed asset group, or even for an individual fixed asset book. By default, the ledger accounts that are defined are used for your fixed asset transactions.

You must define the ledger accounts that are used during the disposal processes, both disposal sales and disposal scraps. At the time of disposal, the fixed asset transactions that were previously posted are reversed out of the original accounts. The net amounts are then moved to the appropriate account for gain and loss for asset disposal. To help guarantee that transactions are correctly reversed, you must set up accounts for each type of transaction that you use in your business. The main account should be the original account that you set on the posting profile for the transaction type, and the offset account should be your gain and loss for disposal account. The exception is the net book value. In this case, both the main account and the offset account should be set to the gain and loss for disposal account. For more information, see [Set up fixed asset posting profiles](tasks/set-up-fixed-asset-posting-profiles.md).

## Fixed asset groups

The **Fixed asset group** field is the only required field when you create a fixed asset. The value of this field determines the default value of several informational fields for the asset. Books are set up so that a default book is assigned to each asset in a group. In this way, attributes that you set for the books can be specific to a group of assets. These attributes include the service life and the depreciation convention.

You can also define special depreciation allowances, or bonus depreciation, for a specific combination of a fixed asset group and a book. You must assign a priority to the special depreciation allowance to specify the order that allowances are calculated in when multiple allowances are assigned to a book. For more information, see [Set up fixed asset groups](tasks/set-up-fixed-asset-groups.md).

## Journal names

On the **Journal names** page, you must create the journal names that should be used with the Fixed assets journal. You must set the **Journal type** field to **Post fixed assets**. Set the **Voucher series** field so that the journal names are used for the Fixed assets journal. Fixed assets journals shouldn't use the **One voucher number only** setting, because a unique voucher number is required for several automated processes, such as transfers and splits.

## Fixed asset parameters

The last step is to update the fixed asset parameters.

The **Capitalization threshold** field determines the assets that are depreciated. If you select a purchase line as a fixed asset but it doesn't meet the specified capitalization threshold, the system still creates or updates a fixed asset, but it sets the **Calculate depreciation** option to **No**. Therefore, the asset isn't automatically depreciated as part of the depreciation proposals.

One important option is named **Automatically create depreciation adjustment amounts with disposal**. When you set this option to **Yes**, the asset depreciation is automatically adjusted, based on the depreciation settings at the time of asset disposal. Another option lets you deduct cash discounts from the acquisition amount when you acquire fixed assets by using a vendor invoice.

The **Lock asset books in a depreciation journal** parameter lets you lock asset books in a depreciation journal. When depreciation transactions are being posted, the system verifies that the same asset book hasn't been added to more than one depreciation journal. If it has, that asset book is locked and posting will stop. If an asset book ID is in a locked journal, it is unlocked automatically when posting is complete for the original journal. You can also unlock the journal manually. 

**Post disposal transactions in detail** determines which disposal scrap or sale to consider which detailed disposal posting of acquisition to **Acquisition this year** and **Acquisition prior years**. 

- If you set this option to **Yes**, the disposal sale or scrap posting process validates the posting profile to ensure that it has all posting types. 
- If you set this option to **No**, the disposal scrap or sale posting process validates the posting profile to ensure that the **Acquisition value** field is defined in it.

In Microsoft Dynamics 365 Finance version 10.0.41, the **Allow depreciation when placed in service and disposal are in the same fiscal year** parameter is available on the **Fixed assets parameters** page. When you enable this parameter, depreciation is calculated when an asset is both put into service and disposed of within the same fiscal year. This setting becomes the default behavior for any new asset books that you create afterwards. However, you can modify the setting at the level of the individual asset book as required. Changes that you make at the asset book level apply only to new asset books that you create after the modification. They don't retroactively affect asset books that already exist in the system. 

> [!NOTE]
> You can't define both the options of posting types **Acquisition value** and **Acquisition this year** or **Acquisition prior year** in the disposal sale/scrap at the same time to ensure accurate disposal posting.

On the **Purchase orders** FastTab, you can configure how assets are created as part of the purchasing process. The first option is named **Allow asset acquisition from Purchasing**. If you set this option to **Yes**, asset acquisition occurs when you post the invoice. If you set this option to **No**, you can still put a fixed asset on a purchase order (PO) and invoice, but the acquisition isn't posted. You must post as a separate step, from the Fixed assets journal. Use the **Create asset during product receipt or invoice posting** option to create a new asset during posting. Therefore, you don't have to set up the asset as a fixed asset before the transaction. The last option, **Check for fixed assets creation during line entry**, applies only to purchase requisitions.

You can configure reason codes so that they're required for changes to a fixed asset or for specific fixed asset transactions.

Finally, on the **Number sequences** tab, you define number sequences for fixed assets. The **Fixed asset** number sequence can be overridden by the **Fixed asset group** number sequence if it has been specified.

For more information, see [Create a fixed asset](tasks/create-fixed-asset.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
