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
   3. After pressing delete, a new message will appear, "**The main account may be in use as a default account. This scan may take a while. Would you like to proceed?**
   4. Pressing OK lets the next message appear, "**A Delete check is scheduled and will make the dimension value inactive if there are no references found. Would you like to see the current status of the check?**"
   5. Pressing OK on this message will bring you to a new form that shows the scan of the main account requested to be deleted. It will let you know the account is currently being checked for any places it has been used in the system. The message will appear of, "**The MainAccount '11000Test' is currently being checked for references before it can be deleted. It cannot be deleted until the process is complete.**"
   6. Closing the message will let you view the accounts that have a scan request pending or completed. Initially the Status field will indicate it is waiting for a scan to complete. A refresh of the form after a few minutes will provide the results and updated status. All of the references found will be listed.  For this example, it may be used on the Accounts for automatic transactions and provides a link to that form on the right hand side of the grid.
   7. Click on the link to open the related form (if available) to clear the useage of the account you are trying to delete.
   8. Press the back arrow to return to the "**Dimension value delete check result**" page. Delete the references found that have been corrected or cleared of the main account to be deleted.
   9. Return to the main account page. Attempt the delete again, and the scan will start over to verify no other references are found.
   10. Once the scan is complete and the status shows "**Delete allowed. Record was prepared for delete. You may attempt to delete it again.**"
   11. Return to the main account page one last time and press the delete button. It will be removed successfully!

> [!NOTE]
> Only the master records such as MainAccount, Customer, Vendor, Project, BankAccount, or FixedAsset will have this added scanning and ability to delete are enabled.  
