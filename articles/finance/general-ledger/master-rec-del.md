---
# required metadata

title: Delete master records in financial journals
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

# Delete master records 

[!include[banner](../includes/banner.md)]

This article describes how to delete the following master records in financial journals:
- MainAccount
- Customer
- Vendor
- Project
- BankAccount
- FixedAsset

When removing a master record, the system checks where the master record is used and required missing cleanup actions to remove the master record. 

Any record used on a posted document can't be deleted. Only the financial journal and setup pages that reference one of these master records can be cleaned up and allow the master record to be deleted. 

## Example 
For example, if you want to delete the MainAccount, follow these steps:
   1. Go to **General ledger** > **Chart of accounts** > **Accounts** > **Main accounts**.
   2. Select a main account to delete.
   3. Click **Delete**.
   4. A message displays: **The main account may be in use as a default account. This scan may take a while. Would you like to proceed?**.
   5. Click **OK**.
   6. Another message appears **A delete check is scheduled and will make the dimension value inactive if there are no references found. Would you like to see the current status of the check?**.
   7. Click **OK** will display a new page that shows the scan of the main account requested to be deleted. It lets you know the account is currently being checked where it has been used. The message appears **The MainAccount '11000Test' is currently being checked for references before it can be deleted. It can't be deleted until the process is complete.**.
   8. When the message is closed, you can view the accounts that have a scan request pending or completed. The **Status** field indicates it's waiting for a scan to complete. Refreshing the page updates the status. All of the references found are listed. For this example, it may be used on the **Accounts for automatic transactions** and provides a link to that page.
   9. Click the related page link to clear the usage of the account you're deleting.
   10. Press the back arrow to return to the "**Dimension value delete check result**" page. Delete the references that have been corrected or cleared of the main account to be deleted.
   11. Go to the **Main accounts** page. Click **Delete** and the scan verifies no other references are found.
   12. After the scan is complete, the status is **Delete allowed. Record was prepared for delete. You may attempt to delete it again.**
   13. Return to the **Main accounts** page and click **Delete**. The record is removed.

> [!NOTE]
> Only the master records such as MainAccount, Customer, Vendor, Project, BankAccount, or FixedAsset have this added scanning and ability to delete are enabled.  
