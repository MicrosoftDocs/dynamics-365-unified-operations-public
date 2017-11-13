---
# required metadata

title: Import and maintain credit card transactions

description: This topic explains how to import and maintain expense-related credit card transactions. These transactions can be set up so that they are automatically imported on a recurring schedule, or they can be manually imported as they are required.
author: KimANelson 
manager: AnnBe
ms.date: 08/29/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 274023
ms.assetid: 3605eda1-a7ed-4675-8031-5279c5a8f5e4
ms.search.region: Global
# ms.search.industry: 
ms.author: knelson
ms.dyn365.ops.intro: Version 1611
ms.search.validFrom: 2016-11-30

---

# Import and maintain credit card transactions

[!include[banner](../includes/banner.md)]

Expense-related credit card transactions can be set up so that they are automatically imported on a recurring schedule. Alternatively, the transactions can be manually imported as they are required. The credit card transactions are imported through the Credit card transactions data entity.

For more information about data entities, see [Data entities](../../dev-itpro/data-entities/data-entities.md).

## Import credit card transactions

1. On the **Credit card transactions** page, select **Import transactions**. If you’re opening data management for the first time, the system must update the list of data entities before you can continue.
2. In the **Name** field, enter a unique description of the import job.
3. In the **Source data format** field, select the format of the file that contains the credit card transactions to import.
4. Select **Upload**, and then find and select the file to import.
5. After the file has been uploaded, validate the mapping of the credit card transaction file and the columns of the Credit card transactions data entity by selecting the **View map** link on the tile. If there are mapping errors, or if you must change the mapping, make the mapping changes from either the **Mapping visualization** tab or the **Mapping details** tab.
6. To automate the credit card transactions, select **Create recurring data job**. You can then set the recurrence that defines how often credit card transactions should be imported. When you’ve finished, select **OK**.
7. To import the selected file now, select **Import**.
8. If errors occur during the import, you can view the execution log or staging data to see the errors that you must fix to help guarantee a successful import.

> [!NOTE]
> If you must import more than one file format, you must create separate import jobs for each format type.

## Reassign the credit card transactions for terminated employees

After an employee record is terminated, the employee’s Active Directory Domain Services (AD DS) account is disabled. However, there might be active credit card transactions that must still be expensed and reimbursed. From the **Credit card transactions** page, you can reassign the employee for any credit card transaction where the associated employee has been terminated.

Select one or more credit card transactions, and then select **Reassign transactions**. You can then select another employee to assign the credit card transactions to. After the credit card transactions have been reassigned, they can be selected for an expense report and paid through the usual process for expense report reimbursement.
