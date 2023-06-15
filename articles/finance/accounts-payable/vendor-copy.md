---
# required metadata

title: Copy vendors by using shared number sequences
description: This article explains how to use shared number sequences to copy a vendor to another legal entity but keep the same vendor ID.
author: sunfzam
ms.date: 06/13/2023
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  VendTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Copy vendors by using shared number sequences

[!include [banner](../includes/banner.md)]

You can use shared number sequences to assign vendor IDs. Shared number sequences also let you copy vendors from one legal entity to another legal entity but use the same vendor IDs in both legal entities.

## Setup

The feature is activated when you use a shared number sequence to assign vendor IDs. You must use the same number sequence in every legal entity that you want to copy a vendor to. You change the vendor number sequence on the **Accounts payable parameters** page for each legal entity. Select **Accounts payable** \> **Setup** \> **Accounts payable parameters**, and then select the **Number sequences** tab.

You can also set up vendor number sequences for each vendor group. These number sequences must also be shared. The number sequence for a vendor group is used first. If no number sequence is specified for a vendor group, the number sequence that is specified on the **Accounts payable parameters** page is used.

You can also copy vendors between legal entities if you use manual vendor IDs. However, if you try to copy a vendor to a legal entity where the vendor ID already exists, the copy process won't be started.

## Copy a vendor

To copy a vendor, select **New** on the **All vendors** list page to open the **All vendors, new record** page. The new vendor ID isn't assigned immediately. This behavior differs from the behavior in previous versions. Because you haven't yet selected the vendor group, the correct number sequence to use can't be determined. Additionally, it can't determine whether you're trying to create a new vendor or copy a vendor. Therefore, the vendor ID isn't assigned until you select **Save** at the bottom of the page.

If you're creating a new vendor, you can continue to fill in all the fields as you usually do. When you've finished, and you select **Save**, the vendor ID is assigned automatically. Alternatively, for manual number sequences, you will see that your manual vendor ID was used.

To copy a vendor, in the **Name** field, enter one or more characters that represent the vendor that you're looking for. A search dialog box shows a list of parties that might represent the vendor that you're looking for. When you select one of the parties, additional information appears on the right side of the dialog box:

- The **General** tab displays the party's phone number and address.
- The **Roles** tab displays the roles that the selected party can have and the legal entity where it has each role.
- **Tax registration ID** tab displays the tax registration IDs that are assigned to the party.

You can copy a party only if it has a vendor role, and if it has that role in a legal entity that isn't the current legal entity. When you find a party that meets these criteria, follow these steps.

1. A **Copy vendor** option appears. By default, this option is set to **No**. To copy the vendor to the current legal entity, set the option to **Yes**. 
2. A **Legal entity** field appears. Select the legal entity to copy the vendor from. If the vendor exists in only one legal entity, the field is set to that legal entity by default.
3. Select **Select**. The new vendor is created.

## Validation

When you copy a vendor, the new vendor information will tried to be saved. Validations are run to verify that the data that was copied is good. You receive an error message for every validation that fails. The error messages explain what information must be updated. The copy of the vendor can't be saved until you fix all the validation errors.

## Copy a vendor by using the Tax exempt number search feature

You can also copy vendors by using the **Tax exempt number** search feature in the **Registration** group on the **Vendor** tab on the Action Pane of the **All vendors** page. The **Tax exempt number search** dialog box that appears shows tax exempt numbers, the vendor ID, the vendor name, and the legal entity where the tax exempt ID is used. You can copy a vendor only if it's in a legal entity that isn't the current legal entity. After you select a vendor that meets this criterion, follow these steps.

1. A **Copy vendor** option appears. By default, this option is set to **No**. To copy the vendor to the current legal entity, set the option to **Yes**.
2. Select **Select**. The new vendor is created.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
