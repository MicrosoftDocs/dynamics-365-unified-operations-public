---
title: CN-00016 User operation log by China working rule
description: This article describes how to generate a user operation log for China in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/05/2025
ms.reviewer: johnmichalak
ms.search.region: China (PRC)
ms.search.validFrom: 2016-06-30
ms.search.form: SysDatabaseLogSetup, SysDatabaseLogWizard, BankAccountTable, ComplianceUserOperationLogConfig_CN
ms.custom: 
  - bap-template
---

# CN-00016 User operation log by China working rule

[!include [banner](../../includes/banner.md)]

This article describes how to generate a user operation log for China in Microsoft Dynamics 365 Finance.

Based on the criteria that you specify, the system tracks and records user operations in a log, including the type of operation, username, and time and date.

The following procedures demonstrate how to set up criteria for tracking bank account creation, create a bank account for demonstration purposes, and generate the user log. You must set up the database log before you can generate the user operation log. This procedure uses the demo data company CNMF.

## Set up the database log

To set up the database log, follow these steps.

1. In Dynamics 365 Finance, go to **System administration \> Setup \> Database log setup**.
1. Select **New**.
1. Select **Next**.
1. In the tree, expand **Bank**.
1. In the tree, select the **Bank\Bank accounts** checkbox. For this demonstration, you want to keep track of who creates bank accounts, but you might want to track other user actions.  
1. Select **Next**.
1. Select the **Track new transactions** checkbox.
1. Select the **Update** checkbox.
1. Select the **Delete** checkbox.
1. Select **Next**.
1. Select **Finish**.

## Create a new bank account for demonstration purposes

To create a new bank account for demonstration purposes, follow these steps.

1. In Dynamics 365 Finance, go to **Cash and bank management \> Bank statement reconciliation \> Bank accounts**.
1. Select **New**.
1. In the **Bank account** field, enter a value.
1. In the **Bank account number** field, enter a value.
1. In the **Main account** field, enter the desired values.
1. Select **Save**.

## Print the user operation log report

To print the user operation log report, follow these steps.

1. In Dynamics 365 Finance, go to **System administration \> Inquiries \> User operation log inquiry**.
1. In the tree, expand **Bank**.
1. In the tree, check **Bank\Bank accounts**.
1. Expand the **By user** section.
1. In the **User** field, enter or select a value. For this example, select your username if you created the bank account in the previous procedure. Otherwise, select another user who recently created a bank account.  
1. Expand the **By date** section.
1. In the **From date** field, enter a date.
1. In the **To date** field, enter a date.
1. Select **OK**.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
