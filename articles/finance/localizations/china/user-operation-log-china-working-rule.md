---
title: CN-00016 User operation log by China working rule
description: This procedure demonstrates how to generate a user operation log.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: China (PRC)
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: SysDatabaseLogSetup, SysDatabaseLogWizard, BankAccountTable, ComplianceUserOperationLogConfig_CN
---
# CN-00016 User operation log by China working rule

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to generate a user operation log. The database log must be set up before you can generate the user operation log.  

Based on the criteria that you specify,  user operations are tracked and recorded in a log, including the type of operation, user name, and time and date. This procedure walks you through setting up criteria for tracking bank account creation, creating a bank account for demonstration purposes, and then generating the user log.

This procedure uses the CNMF demo data. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Set up the database log
1. Go to System administration > Setup > Database log setup.
2. Click New.
3. Click Next.
4. In the tree, expand 'Bank'.
5. In the tree, check 'Bank\Bank accounts'.
    * For this demonstration, we want to keep track of who creates bank accounts, but you may want to track other user actions.  
6. Click Next.
7. Select the Track new transactions check box.
8. Select the Update check box.
9. Select the Delete check box.
10. Click Next.
11. Click Finish.

## Create a new bank account for demonstration purposes
1. Go to Cash and bank management > Bank statement reconciliation > Bank accounts.
2. Click New.
3. In the Bank account field, type a value.
4. In the Bank account number field, type a value.
5. In the Main account field, specify the desired values.
6. Click Save.

## Print the user operation log report
1. Go to System administration > Inquiries > User operation log inquiry.
2. In the tree, expand 'Bank'.
3. In the tree, check 'Bank\Bank accounts'.
4. Expand the By user section.
5. In the User field, enter or select a value.
    * For this example, select your user name if you created the bank account in the previous subtask. Otherwise, select another user who created a bank account recently.  
6. Expand the By date section.
7. In the From date field, enter a date.
8. In the To date field, enter a date.
9. Click OK.
10. Click OK.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
