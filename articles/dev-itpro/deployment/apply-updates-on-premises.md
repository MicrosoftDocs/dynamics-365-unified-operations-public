---
# required metadata

title: Apply updates to on-premises deployments
description: This topic explains how to apply updates to an on-premises deployment of Microsoft Dynamics 365 for Finance and Operations.
author: manalidongre
manager: AnnBe
ms.date: 03/01/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sarvanis
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Platform update 12

---
# Apply updates to on-premises deployments

[!include [banner](../includes/banner.md)]

This topic explains how to apply supported updates to an on-premises deployment of Microsoft Dynamics 365 for Finance and Operations. All updates to on-premises environments are done through Microsoft Dynamics Lifecycle Services (LCS).

## Search for and download updates
For more information about how to find the updates that you can apply to your on-premises environment, see [Issue search](../lifecycle-services/issue-search-lcs.md). For information about how to download updates from the tiles in the **Updates** section of the **Environment details** page in LCS, see [Download updates](../migration-upgrade/download-hotfix-lcs.md).
   
> [!NOTE]
> When you are updating an on-premises environment, always select updates from the update tiles on the **Environment** details page. If you select updates from another location, the updates might not work. 

## Update an on-premises deployment
You can apply updates to an on-premises environment either during deployment or after the deployment is completed.

While an on-premises environment is being deployed, you can select to deploy a custom package in the **Advanced** settings. For more information about how to apply customizations or application X++ updates, see [Develop and Deploy custom models to on-premises environments](develop-deploy-custom-models-on-premises.md).

To apply updates to an on-premises environment after it has been deployed, in LCS, on the **Environment details** page for the environment, under **Maintain**, select **Apply updates**.

> [!NOTE]
> You can apply updates after deployment only on environments that have Platform update 12 or later. The environment must also have the latest version of the local agent available in LCS. For more information, see [Update the local agent](../lifecycle-services/update-local-agent.md). 
> If you're on a platform version that is older than Platform update 12, you can reconfigure an environment that is already deployed to update the customizations or update to the latest platform release. For more information about how to redeploy an environment, see [Redeploy an on-premises environment](redeploy-on-prem.md).

## Apply application or binary updates through LCS
The following steps can be used to apply X++, All Binary, or Platform Binary updates. For information about how to move from one platform release to another, see the "Apply the latest platform update" section later in this topic.

> [!IMPORTANT]
> The application of updates requires downtime for your environment. Therefore, no business transactions can be performed in the environment during the update. When you complete the following steps, verify that the system isn't being used, and that an official downtime notice has been communicated to all system users.

### Prerequisites
- Before you begin, complete a full backup of the Management Reporter (MR), Microsoft Dynamics AX, and Microsoft SQL Server Reporting Services (SSRS databases). Although the code is restored through LCS, the database must be manually restored to help guarantee that there is no data loss.
- Update your environment to the latest build of Platform update 12.
- Update the local agent to the latest version. For more information, see [Update the local agent](../lifecycle-services/update-local-agent.md).
- Depending on the type of update, complete the following steps to generate a deployable package:

    - **Application binary updates** – Download or save the update directly to the Asset library in LCS by following the steps in [Download updates wiki](../migration-upgrade/download-hotfix-lcs.md).
    - **Application X++ updates** – Download the required hotfix to your development environment, and then follow the steps in [Create a deployable package of your models in order to apply it to a runtime environment](create-apply-deployable-package.md).
    - **Customizations** – Follow the steps in [Develop and deploy custom models](develop-deploy-custom-models-on-premises.md).

### Update a sandbox environment
1. In the LCS Asset library, upload the deployable package that was generated in the "Prerequisites" section of this topic to the **Software deployable packages** tab.
2. In LCS, open the on-premises implementation project, and then open the **Environment details** page of the environment to update.
3. Under **Maintain**, select **Apply updates**. A dialog box shows the updates that were uploaded to the Asset library. Note that only packages that are marked as **Valid** in the Asset library appear.
4. Select the update, and then select **Apply**.
5. In the confirmation message, select **Yes**. The servicing operation has started on this environment.

    The environment state is changed from **Deployed** to **Preparation**. During the **Preparation** stage, the actual deployment hasn't yet started. Therefore, even if preparation fails, the on-premises environment isn't touched and can be used.

    >[!NOTE]
    > Even though the **Preparation** stage doesn't directly touch the on-premises environment, we recommend that you not use the environment to perform transactions during this time.

    When the preparation is completed, the environment state is changed from **Preparation** to **Deploying**.

    After the update is completed, the environment state is changed back to **Deployed**. If application of the update fails, the environment state is changed to **Failed**. For information about what to do if package application fails, see the "Resolve a failed update application" section later in this topic.

6. Open the **History** and **Environment details** pages to view the operations that were performed on the environment. You can also view a record of major actions that were performed on the environment, such as deployments, servicing, and rollbacks.

### Update a production environment
Before you update a production environment, you must successfully complete the package application update on a sandbox environment.

1. In the project for the sandbox environment that you applied the package to, open the Asset library, and then, on the **Software deployable packages** tab, select the package, and mark it as a **Release candidate**.
2. On the **Environment details** page, under **Maintain**, select **Apply updates**. In the dialog box, only packages that are marked as a **Release candidate** are shown.
3. In the confirmation message, select **Yes**.

    As when you updated the sandbox environment, the environment state is changed from **Deployed** to **Preparation**. During the **Preparation** stage, the actual deployment hasn't yet started. Therefore, even if preparation fails, the on-premises environment isn't touched and can be used.

    >[!NOTE]
    > Even though the **Preparation** stage doesn't directly touch the on-premises environment, we recommend that you not use the environment to perform transactions during this time.

    When the preparation is completed, the environment state is changed from **Preparation** to **Deploying**.

    After the update is completed, the environment state is changed back to **Deployed**. If application of the update fails, the environment state is changed to **Failed**. For information about what to do if package application fails, see the "Resolve a failed update application" section later in this topic.

4. Open the **History** and **Environment details** pages to view the operations that were performed on the environment. You can also view a record of major actions that were performed on the environment, such as deployments, servicing, and rollbacks.

## Resolve a failed update application
When application of an update fails, the environment state is **Failed**. The first step is to determine why the update application failed. The location of the logs varies, depending on the stage where the failure occurred:

- **Preparation stage:** If the operation fails during the **Preparation** stage, the logs are uploaded to LCS. In the log files, select **Download logs** to download the log files. If the package has any merge issues, the error is included in the log file.
- **Deploying stage:** If the operation fails during the **Deploying** stage, the logs are located in the on-premises environment. You must sign in to the environment, and then access the logs and event viewer.

For more information about how to use the troubleshooting logs, see [Troubleshoot Dynamics 365 for Finance and Operations on-premises](troubleshoot-on-prem.md).

After you review the logs and determine the cause of the failure, complete one of the following operations to restore the environment to a healthy state. No actions can be performed on an environment that is in a **Failed** state. The environment must first be restored to a healthy state.

- **Retry failed operation** – If update application fails, select **Retry** to recover from the failed operation.
- **Roll back the update** – To roll back the update that failed, select **Rollback**. Before you start the rollback, you must restore the database to the last known good state. When you select **Rollback**, the environment is restored to the last known good state. The environment state is then changed to **Preparation**, then to **Deploying**, and then to either **Deployed** or **Failed**.

    >[!NOTE]
    > The **Rollback** button doesn't roll back the database. You're responsible for restoring the database to the last known backup that was made before update application. This step is critical to help guarantee that there is no data loss.

- **Refresh the state** – If update application fails during the **Preparation** stage, the failure is on the LCS side, and update application hasn't yet started. Therefore, the on-premises environment is in a good state. To restore the LCS environment state to **Deployed**, on the project dashboard page, select **Refresh**.
- **Delete and redeploy an environment** – If the retry and rollback options don't work, you must delete and redeploy the environment. To delete the environment, on the project dashboard page, select **Delete**. You then see the option to configure the environment.

    > [!IMPORTANT]
    > This option should **not** be used on a production environment. However, it can be used on a sandbox deployment to restore the environment to a healthy state. 
    
    > Because this option requires that you do a fresh deployment of the environment, you lose any updates that were previously applied. Any customizations and binary updates must be reapplied to the environment.

## Apply the latest platform update 
There are two ways to apply the latest platform update:

- Deploy a new environment, and select the latest platform update topology during deployment. Then follow the usual steps for deploying an environment.
- Update an existing environment with the latest update by redeploying the environment. For more information about how to redeploy an environment, see [Redeploy an on-premises environment](redeploy-on-prem.md).
