---
# required metadata

title: Copy a vendor to another legal entity and keep the same vendor ID using shared number sequences
description: You can copy a vendor to another legal entity and keep the same vendor ID when a shared number sequence is used
author: mikefalkner
manager: aolson
ms.date: 08/24/2018
ms.topic: index-page
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  VendTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mikefalkner
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Copy a vendor using global number sequences

[!include [banner](../includes/banner.md)]

Starting with 8.1, you will be able use a shared number sequence for assigning vendor IDs. In addition, you will be able to copy
a vendor from one legal entity to another legal entity and use the same vendor ID for both legal entities.  

## Setup

The feature is activated when you use a shared number sequence for assigning vendor IDs. You must use the same number sequence in each legal where you want to copy the vendor.  Change the vendor number sequence to the new number sequence on the parameters page for each legal entity using Accounts receivable > Parameters > Number sequences.

You can also set up vendor number sequences for each vendor group and these number sequences must also be shared (CHECK THIS). The number sequences for a vendor group will be used first. If there is no number sequence specified for a vendor group, then the number sequence found in the parameters form will be used 

You can still use manual vendor IDs and copy vendors between legal entities. However, if you try to copy a vendor to a legal entity where the vendor ID already exists, the copy process will not be started.

## Copy a vendor

To copy a vendor, click on New to display the new vendor page. Notice that, unlike previous versions of Dynamics 365 for Finance and Operations, the new vendor ID will not be assigned immediately. The vendor group has not yet been selected so it is not possible to identify the correct number sequence or use yet. In addition, you may be creating a new vendor or you may be copying a vendor. Until we know what action will be taken, the vendor ID will not be assigned until you click on the Save button at the bottom of the form. 

If you are creating a new vendor, you can continue filling in all of the fields as you normally would. When you are done, click on Save and you will see that the vendor ID was assigned automatically or, for manual number sequences, your vendor ID was used.

To copy a vendor, select the Name field and enter one or more characters that represent the vendor that you are looking for. The search form will display a list of parties that may represent the vendor that you are looking for. When you click on one of the parties, you can see additional information on the right side of the page
1) The General tab shows the party's phone number and address
2) The Role tab shows the roles that the selected party can have and the legal entity in which it has the role
3) Tax registration ID shows the tax registration IDs assigned to the party

You can only copy a party that has a vendor role and has that role in a legal entity that is not in the current legal entity. When you find a party that fits this criteria, follow these steps:
1) A Copy vendor field is displayed and defaulted to No. 
2) If you want to copy that vendor into the current legal entity, change the Copy vendor field to Yes. 
3) Another field, Legal entity, is displayed. Select the legal entity from which you want to copy the vendor. If the vendor only exists in one legal entity, the field will default to that value.
4) Click on Select and the new vendor is created

## Validation

When you copy a vendor, an attempt is made to save the new vendor information. All validations are executed to ensure that the data that was copied is good. If any validations fail, an error message will be display for each validation that did fail, explaining what information needs to be updated. The new vendor will not be saved until you have fixed the validation errors. Once they are fixed, you can save the copy of the vendor.

**Copying a vendor using the tax exempt search**

You can also copy vendors using the tax exempt number search found under the Vendor > Registration menu. A form will be displayed showing tax exempt numbers, the vendor ID, vendor name, and legal entity in which the tax exempt ID is used. You can only copy a vendor that is in a legal entity that is not in the current legal entity. When you click on a vendor that fits this criteria, follow these steps:
1) A Copy vendor field is displayed and defaulted to No. 
2) If you want to copy that vendor into the current legal entity, change the Copy vendor field to Yes. 
3) Click on Select and the new vendor is created

## Frequently asked questions
Can you use the vendor group sequences without being global?
