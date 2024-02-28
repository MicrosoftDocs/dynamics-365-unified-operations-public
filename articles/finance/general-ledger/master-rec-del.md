---
# required metadata

title: Master record delete enhancements
description: This article provides information about how to delete master records that are used in a financial journal.
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
ms.reviewer: twheeloc
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

When you would like to clean up and remove a master record such as MainAccount, Customer, Vendor, Project, BankAccount, or FixedAsset, the system checks where the master record has been used and inform of missing cleanup actions required to remove the master record. 

Any record that has been used on a posted document will not be allowed for delete.  Only the financial journal forms and setup forms that still hold a reference to one of these master records can be cleaned up and allow the master reocrd to be deleted. 

## Example 
For example, if you want to delete the MainAccount, follow these steps:
   1. Go to **General ledger** > **Chart of accounts** > **Accounts** > **Main accounts**.
   2. Select a main account to delete.
   3. Click **Delete**.
   4. A message displays: **The main account may be in use as a default account. This scan may take a while. Would you like to proceed?**.
   5. Click **OK**.
   6. Another message appears **A delete check is scheduled and will make the dimension value inactive if there are no references found. Would you like to see the current status of the check?**.
   7. Click **OK** will display a new page that shows the scan of the main account requested to be deleted. It lets you know the account is currently being checked where it has been used. The message appears **The MainAccount '11000Test' is currently being checked for references before it can be deleted. It cannot be deleted until the process is complete.**.
   8. Closing the message lets you view the accounts that have a scan request pending or completed. Initially, the **Status** field indicates it's waiting for a scan to complete. Refreshing the page provides the results and updated status. All of the references found are listed. For this example, it may be used on the **Accounts for automatic transactions** and provides a link to that page.
   9. Click on the link to open the related form (if available) to clear the useage of the account you are trying to delete.
   10. Press the back arrow to return to the "**Dimension value delete check result**" page. Delete the references found that have been corrected or cleared of the main account to be deleted.
   11. Go to the **Main accounts** page. Attempt the delete again, the scan verifies no other references are found.
   12. After the scan is complete and the status is **Delete allowed. Record was prepared for delete. You may attempt to delete it again.**.
   13. Return to the **Main accounts** page again and click **Delete**. The record will be removed.

> [!NOTE]
> Only the master records such as MainAccount, Customer, Vendor, Project, BankAccount, or FixedAsset have this added scanning and ability to delete are enabled.  
