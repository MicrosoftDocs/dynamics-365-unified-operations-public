---
# required metadata

title: Master record delete enhancements
description: This article provides information about how to delete master records that may have been used in a financial journal.
author: rcarlson
ms.date: 03/01/2024
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2024-03-01
ms.dyn365.ops.version: 10.0.38

---

# Master record delete enhancements

[!include[banner](../includes/banner.md)]

When you would like to clean up and remove a master record such as MainAccount, Customer, Vendor, Project, BankAccount, or FixedAsset - the system will now check for any places it has been used and inform you of the missing cleanup action that is required in order to remove the master record. 
Any record that has been used on a posted document will not be allowed for delete.  Only the financial journal forms and setup forms that still hold a reference to one of these master records can be cleaned up and allow the master reocrd to be deleted. 

## Example process
For an example lets follow the delete process for MainAccount following these steps:
   1. Select a main account to delete from the main account list page under General Ledger - Chart of Accounts - Accounts - Main accounts.
   2. Find the main account you wish to delete and press the delete button.
   3. 

