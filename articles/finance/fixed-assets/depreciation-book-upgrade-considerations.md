---
# required metadata

title: Depreciation book upgrade overview
description: This article describes the current book functionality in Fixed assets. 
author: moaamer
ms.date: 06/20/2017
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: ["221624"]
ms.collection: get-started
ms.assetid: cf434099-36f9-4b0f-a7c8-bed091e34f39
ms.search.region: global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Depreciation book upgrade overview

[!include [banner](../includes/banner.md)]

This article describes the current book functionality in Fixed assets. This functionality is based on the value model functionality that was available in earlier versions, but it also includes all the functionality that was previously provided only in depreciation books. The value model functionality and depreciation book functionality have been merged into a single concept that is known as a book. Book functionality lets you use a single set of pages, inquiries, and reports for all your organization's fixed asset processes. This article provides some things that you should consider before you upgrade. 

The upgrade process will move your existing setup and all existing transactions to the new book structure. Value models will remain as they currently are, as a book that posts to the general ledger. Depreciation books will be moved to a book that has the Post to general ledger option set to No. Depreciation book journal names will be moved to a general ledger journal name with the posting layer set to None. Depreciation book transactions will be moved to Fixed asset transactions.

Before running the data upgrade, you should understand the two options available for upgrading depreciation book journal lines to transaction vouchers, and the number sequence that will be used for the voucher series.

Option 1:  **System-defined number sequence** - This is the default option to optimize upgrade performance. The upgrade will not use the number sequences framework, but instead will allocate vouchers with a set-based approach. After the upgrade, the new number sequence will be created with the **Next number set** appropriately based on the upgraded transactions. By default, the number sequence used will be in the FADBUpgr\#\#\#\#\#\#\#\#\# format. There are a few parameters available to you to adjust the format when using this approach:

-   **Number sequence code** – The code to identify the number sequence. This number sequence code cannot exist since it will be created by the upgrade.
    -   Constant name: **NumberSequenceDefaultCode**
    -   Default value: "FADBUpgr"
-   **Prefix** – The constant string value that will be used as a prefix for the voucher numbers.
    -   Constant name: **NumberSequenceDefaultParameterPrefix**
    -   Default value: "FADBUpgr"
-   **Alphanumeric length** – The length of the alphanumeric segment of the number sequence.
    -   Constant name: **NumberSequenceDefaultParameterAlpanumericLength**
    -   Default value: 9
-   **Start number** - The first number to be used in the number sequence.
    -   Constant name: **NumberSequenceDefaultParameterStartNumber**
    -   Default value: 1

Option 2: **Existing user-defined number sequence** - This option will allow you to define the number sequence to be used for the upgrade. Consider using this option if you need advanced number sequence configuration. To use a number sequence, you must modify the upgrade class ReleaseUpdateDB70\_FixedAssetJournalDepBookRemovalDepBookJournalTrans with the following information:

-   **Number sequence code** – The code of the number sequence.
    -   Constant name: **NumberSequenceExistingCode**
    -   Default value: No default, this must be updated to the number sequence code.
-   **Shared number sequence** – A Boolean value to identify the scope of the number sequence. Use "true" for shared number sequences across all companies, and "false" for a company-specific scope. When using "false", the number sequence with the specified name must exist in every company that contains depreciation book transactions. Shared number sequences exist in every partition that contains depreciation book transactions.
    -   Constant name: **NumberSequenceExistingIsShared**
    -   Default value: true

The parameters are located at the beginning of the ReleaseUpdateDB70\_FixedAssetJournalDepBookRemovalDepBookJournalTrans class. 

*// Specify a preferable approach of vouchers allocation* 
*// true, if you want to use an existing number sequence code* 
*// false, if you intend to use the system-defined number sequence (default)* const boolean NumberSequenceUseExistingCode = false;  

*// If using the system-defined number sequence approach, specify the parameters for the number sequence.*
*// A new number sequence will be created with these parameters.* 
const str NumberSequenceDefaultCode = 'FADBUpgr'; 
const str NumberSequenceDefaultParameterPrefix = 'FADBUpgr'; 
const int NumberSequenceDefaultParameterAlpanumericLength = 9; 
const int NumberSequenceDefaultParameterStartNumber = 1;   

*// If using the existing number sequence approach, specify the existing number sequence code.* 
*// Voucher allocation will go row-by-row for existing number sequences.* 
const str NumberSequenceExistingCode = ''; 
*// Specify the scope of the existing number sequence code* 
*// true, if the specified number sequence is shared* 
*// false, if the specified number sequence is per-company* 
*// The default system-defined number sequence will be used if a number sequence code with the specified scope is not found.* 
const boolean NumberSequenceExistingIsShared = true; 

Rebuild the project that contains the class after the constants have been modified. 

When using the system-generated number sequence approach (option 1), the upgrade will use set-based processing to allocate the voucher numbers as specified in the upgrade script parameters. It will also create a new number sequence with specified parameters after the allocation. 

When using the user-defined existing number sequence approach (option 2), the data upgrade checks whether the number sequence with the specified scope exists in the database for each partition and company with depreciation book transactions. If it does exist, the upgrade will use row-by-row processing to allocate the voucher numbers as specified by the number sequence using the number sequence framework. If the number sequence does not exist with the specified scope, the upgrade will use the default system-defined number sequence approach to allocate the voucher numbers, and will create a new number sequence with specified default parameters after the allocation.

With either approach, the data upgrade script will also use the number sequence for the **Voucher series** field on the new general ledger journal names created for the former depreciation book journal names.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
