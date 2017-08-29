---
# required metadata

title: Import and maintain credit card transactions

description: Expense related credit card transactions can be set up to be automatically imported on a recurring schedule, or can be 
manually imported as required. 
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
ms.search.scope: Operations, UnifiedOperations
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


Expense related credit card transactions can be set up to be automatically imported on a recurring schedule, or can be manually imported
as required. The credit card transactions are imported through the Credit card transactions data entity. 

For more information on data entities, see [Data entities](/dev-itpro/data-entities/data-entities.md).

### Import credit card transactions

1.  On the **Credit card transactions** page, click **Import transactions**. If this is the first time data management has
    been opened, the system will need to refresh the list of data entities before you can continue.

2.  In the **Name** field, enter a unique description of the import job.

3.  Select the **Source data format** of the file that contains the credit card transactions to be imported.

4.  Click **Upload** and find and select the file to be imported.

5.  Once the file has been uploaded, validate the mapping of the credit card transaction file and the credit card transaction data entity
    columns by clicking the View map link in the tile. If there are mapping errors or mapping changes you need to do, make the mapping 
    changes from either the **Mapping visualization** or the **Mapping details** tab.

6.  If you want the credit card transactions to be automated, click the **Create recurring data job** button where you can set the 
    recurrence that defines how frequently credit card transactions should be imported. Click OK.

7.  To import the selected file now, click **Import**.

8.  If you have errors during the import, you can view the execution log or staging data to see the errors that need to be fixed for a 
    successful import.

> [!NOTE]
> If you have more than one file format to import, you will need to create separate import jobs for each format type.

### Reassign terminated employee’s credit card transactions

Once an employee record is terminated, his or her Active Directory Domain Services (AD DS) account is disabled and there may be active 
credit card transactions that must still be expensed and reimbursed. You can reassign the employee for any credit card transaction where 
the associated employee is terminated from within the **Credit card transactions** page. 

Select one or more credit card transactions and
click the **Reassign transactions** button where you can select another employee to assign the credit card transactions to. After the 
credit card transactions have been reassigned, they can be selected for an expense report and paid through the regular process for 
expense report reimbursement.
