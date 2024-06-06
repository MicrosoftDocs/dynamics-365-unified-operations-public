---
title: Delete master records in financial journals
description: Learn how to delete master records that are used in a financial journal, including examples for deleting a MainAccount master record.
author: rcarlson
ms.author: rcarlson
ms.topic: article
ms.date: 03/01/2024
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2024-03-01
ms.search.form: 
ms.dyn365.ops.version: 10.0.38
---

# Delete master records in financial journals

[!include[banner](../includes/banner.md)]

This article describes how to delete the following master records in financial journals:

- MainAccount
- Customer
- Vendor
- Project
- BankAccount
- FixedAsset

When you delete a master record, the system does a check to determine where that master record is used and what cleanup actions are required to remove it.

Master records that are used in a posted document can't be deleted. Only the financial journal and setup pages that reference one of these master records can be cleaned up and allow the master record to be deleted.

## Example

For example, if you want to delete a MainAccount master record, follow these steps.

1. Go to **General ledger** \> **Chart of accounts** \> **Accounts** \> **Main accounts**.
2. Select the main account to delete.
3. Select **Delete**.

    You receive the following message: "The main account may be in use as a default account. This scan may take a while. Would you like to proceed?"

4. Select **OK**.

   You receive the following message: "A delete check is scheduled and will make the dimension value inactive if there are no references found. Would you like to see the current status of the check?"

5. Select **OK**.

    A new page appears and shows the scan of the main account that you requested to delete. This page informs you that a check is being done to determine where the account is used. You receive the following message: "The MainAccount '\<*account ID*\>' is currently being checked for references before it can be deleted. It can't be deleted until the process is complete."

6. When the message is closed, you can view the accounts that have a pending or completed scan request. The **Status** field indicates that the system is waiting for a scan to be completed. To update the status, refresh the page.

    The page lists all the references that were found and provides links to the related pages. For example, if the selected main account is used on the **Accounts for automatic transactions** page, a link to that page is provided.

7. Select the related page link to clear the usage of the main account that you're deleting.
8. Select the back arrow to return to the **Dimension value delete check result** page. Delete the references that have been corrected or cleared of the main account that you're deleting.
9. Go to the **Main accounts** page, and select **Delete**.

    The scan verifies that no other references are found. After the scan is completed, the status is **Delete allowed. Record was prepared for delete. You may attempt to delete it again.**

10. Return to the **Main accounts** page, and select **Delete**.

    The record is removed.

> [!NOTE]
> The scanning and deletion capabilities are enabled only for master records, such as MainAccount, Customer, Vendor, Project, BankAccount, and FixedAsset.
