---
title: Upgrade from AX 2012 - Pre-upgrade checklist for data upgrade
description: This article describes each task in the Microsoft Dynamics AX 2012 checklist that is associated with data upgrade to finance and operations apps.
author: gianugo
ms.date: 06/01/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: sericks
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2017-05-31
ms.dyn365.ops.version: Platform update 8
ms.custom: 106163
ms.assetid: 
---

# Upgrade from AX 2012 - Pre-upgrade checklist for data upgrade

[!include [banner](../includes/banner.md)]

[!include [upgrade banner](../includes/upgrade-banner.md)]

This article describes each task in the Microsoft Dynamics AX 2012 checklist that is associated with data upgrade to finance and operations apps.

## Installation

The pre-upgrade checklist for the Dynamics 365 upgrade is included in AX 2012 R3 cumulative update 13 (CU13). If you're on an older version, you must install one of the following updates: 

- If you're upgrading from AX 2012 R3, install [KB 4035163](https://go.microsoft.com/fwlink/?linkid=852255).
- If you're upgrading from AX 2012 R2, install [KB 4048614](https://go.microsoft.com/fwlink/?linkid=869025).

> [!NOTE] 
> If you're upgrading from AX 2012 R3, CU13 must be installed in your environment. If you're on an older version and have issues or concerns updating to CU13, contact Microsoft Support.

## Run the pre-upgrade checklist

To run the pre-upgrade checklist, follow these steps.

- Go to **System Administration \> Setup \> Checklists \> Dynamics 365 for Unified Operations data upgrade checklist**.	

If the checklist isn't shown, follow these steps.

1. Open the **Developer workspace**, and in the **AOT** go to **Menu Items \> Display \> SysCheckList\_UpgradeToNextV**.
2. Select and hold (or right-click) **SysCheckList\_UpgradeToNextV**, and then select **Open**.

You must run each of the following checklist tasks. 

## Validate baseline version

Run this task to validate that the current version can be upgraded.

- In the finance and operations data upgrade checklist, select **Validate baseline version**.

If the baseline version is one of the supported baseline versions, the task is marked as completed.

## Prepare model metadata

During data upgrade, one goal is to maintain element IDs between the existing AX 2012 environment and the upgraded finance and operations environment. To accomplish this goal, you must bring a copy of the element IDs from the AX 2012 environment into the finance and operations environment. AX 2012 stores element IDs in a table that is named ModelElement. This table is in the model database, which is a separate database from the AX 2012 business data database. During an upgrade to finance and operations, you must copy the AX 2012 database to Microsoft Azure. This process can be time consuming. 

To avoid copying the whole model database to Azure SQL Database, use the following procedure to replicate the ModelElement table in the business data database. Later, during data upgrade runs, the database synchronization process will retrieve the required information from this replicated table and make sure that element IDs are maintained in the upgraded finance and operations environment.

1. In the finance and operations data upgrade checklist, select **Prepare model metadata**.
2. When you're prompted, select **Yes**.
3. Wait for the copy process to be completed.

If the process is successful, the task is marked as completed.

## Prepare security role metadata

Another goal during data upgrade is to preserve security role assignments. This task resembles the previous "Prepare model metadata" task. Security role information that is stored in the AX 2012 model database must be copied to the AX 2012 business data database, so that the information is preserved in the finance and operations environment after upgrade. During data upgrade runs, the same security role will be restored in the upgraded finance and operations environment.

1. In the finance and operations data upgrade checklist, select **Prepare security role metadata**.
1. When you're prompted, select **Yes**.
1. Wait for the copy process to be completed.

If the process is successful, the task is marked as completed.

## Set up user mapping

In AX 2012, users are authenticated against an on-premises Active Directory server. However, in finance and operations apps, users are authenticated against Azure Active Directory (Azure AD). This task provides a form where you can map existing AX 2012 users to equivalent Azure AD users. The AX 2012 users will then be able to access finance and operations apps.

1. In the finance and operations data upgrade checklist, select **Set up user mapping**.
2. The **User info email mapping** form appears. Follow one of these steps to fill in the grid:

    - Import users from AX 2012, and then manually fill in the Azure AD email address:

        1. Select **Import from AX**. The grid is filled with existing users.
        1. For each user, enter the corresponding Azure AD email address, as shown in the following illustration.

            ![Azure AD email addresses for AX 2012 users.](media/userInfoEmailMapping.png)

    - Import users from a file. This option is faster. We recommend that you use this option when many users must be updated.

        1. In a comma-separated values (CSV) file, create the mapping between AX 2012 users and Azure AD email addresses. Your IT department can export a similar mapping from your on-premises Active Directory Domain Services (AD DS). The file should have two columns: **UserId** and **EmailAddress**.

            > [!NOTE]
            > The first row in the file is treated as a header row and will be ignored during the import.

        2. After the file is ready, select **Import from file**, browse to the file, and import it.

            The grid should be filled with the mappings that you specified in the file.

If the imported file contains an entry that isn't valid, an error file is generated.


## Archive retail salt data

This task is used to migrate the registry key that RetailSaltUtility uses. This tool is used for some deployments where the customer wants to inject a specific random value into the hash that is used to authenticate channel users.

- In the finance and operations data upgrade checklist, select **Archive retail salt data**.

If the process is successful, the task is marked as completed.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
