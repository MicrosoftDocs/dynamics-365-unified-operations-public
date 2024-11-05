---
title: Apply updates to on-premises deployments
description: Learn how to apply supported updates to Dynamics 365 Finance + Operations (on-premises), including prerequisites.
author: PeterRFriis
ms.author: peterfriis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/19/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Platform update 12
ms.service: dynamics-365-op
---
# Apply updates to on-premises deployments

[!include [banner](../includes/banner.md)]

This article explains how to apply supported updates to Dynamics 365 Finance + Operations (on-premises). All updates to on-premises environments are done through Microsoft Dynamics Lifecycle Services (LCS).

## Search for and download updates
For more information about how to find the updates that you can apply to your on-premises environment, see [Issue search in Lifecycle Services (LCS)](../lifecycle-services/issue-search-lcs.md). For information about how to download updates from the tiles in the **Updates** section of the **Environment details** page in LCS, see [Download updates from Lifecycle Services (LCS)](../migration-upgrade/download-hotfix-lcs.md).
   

## Update an on-premises deployment
You can apply updates to an on-premises environment either during deployment or after the deployment is completed.

While an on-premises environment is being deployed, you can select to deploy a custom package in the **Advanced** settings. For more information about how to apply customizations or application X++ updates, see [Develop and deploy custom models to on-premises environments](develop-deploy-custom-models-on-premises.md).

To apply updates to an on-premises environment after it has been deployed, in LCS, on the **Environment details** page for the environment, under **Maintain**, select **Apply updates**.

> [!NOTE]
> The environment must also have the latest version of the local agent available in LCS. For more information, see [Update the local agent](../lifecycle-services/update-local-agent.md). 

## Apply platform update package updates through LCS
The following steps can be used to apply platform update packages. 

> [!IMPORTANT]
> The application of updates requires downtime for your environment. Therefore, no business transactions can be performed in the environment during the update. When you complete the following steps, verify that the system isn't being used, and that an official downtime notice has been communicated to all system users.

### Prerequisites
- Before you begin, complete a full backup of the Management Reporter (MR), Microsoft Dynamics AX, and Microsoft SQL Server Reporting Services (SSRS databases). Although the code is restored through LCS, the database must be manually restored to help guarantee that there is no data loss.
- Update the local agent to the latest version. For more information, see [Update the local agent](../lifecycle-services/update-local-agent.md).
- Depending on the type of update, complete the following steps to generate a deployable package:

    - **Platform update packages** – Download or save the update directly to the Asset library in LCS by following the steps in [Download updates from Lifecycle Services (LCS)](../migration-upgrade/download-hotfix-lcs.md).
    - **Customizations** – Follow the steps in [Develop and deploy custom models to on-premises environments](develop-deploy-custom-models-on-premises.md).

### Update a sandbox environment
1. In LCS, open the on-premises implementation project, and select the project menu and **Asset library**.  Ensure the platform update package, or custom deployable package are in the **Software deployable packages** tab.
2. In LCS, open the on-premises implementation project, and then open the **Environment details** page of the environment to update.
3. Under **Maintain**, select **Apply updates**. A slider shows the updates that were uploaded to the Asset library. Note that only packages that are marked as **Valid** in the Asset library appear.
4. Select the update, and then click **Prepare**. Clicking on **Prepare** will prepare your on-premises environment for servicing. 

    >[!NOTE]
    > During preparation, the environment state will be **Deployed** but the Deployment status field will show the progress of Preparation. Steps such formatting the package and downloading the package are executed during preparation. The environment is not directly touched during preparation and hence there is no downtime during the preparation phase. Users can continue to use the system during preparation. 

5. After the preparation is complete, you will see **Abort** and **Update Environment** buttons. To start applying the update, click **Update Environment**. If preparation fails, see the "Resolve a failed update application" section later in this article.
6. In the confirmation message, select **Yes**. The servicing operation has started on this environment. This is the start of the downtime on your environment. 
7. The environment state is changed from **Deployed** to **Deploying**. 
8. After the update is completed, the environment state is changed back to **Deployed**. If application of the update fails, the environment state is changed to **Failed**. For information about what to do if package application fails, see the "Resolve a failed update application" section later in this article.

    >[!NOTE]
    > During the update the database will be synchronized to update any changes to table definitions, this action can take some time particularly for larger databases. Additionally, all reports are deployed again to the SQL Reporting Services nodes. 

9. Open the **History** and **Environment details** pages to view the operations that were performed on the environment. You can also view a record of major actions that were performed on the environment, such as deployments, servicing, and rollbacks.

### Update a production environment
Before you update a production environment, you must successfully complete the package application update on a sandbox environment.

1. In the project for the sandbox environment that you applied the package to, open the Asset library, and then, on the **Software deployable packages** tab, select the package, and mark it as a **Release candidate**.
2. On the **Environment details** page, under **Maintain**, select **Apply updates**. In the dialog box, only packages that are marked as a **Release candidate** are shown.
3. Select the Release candidate package to be applied to the Production environment. 
4. The rest of the Update flow is the same as that of a sandbox environment. 

## Resolve a failed update application
When preparation fails, the environment state is **Deployed**. When the application of an update fails, the environment state is **Failed**. The first step is to determine why there is a failure. The location of the logs varies, depending on the stage where the failure occurred:

- **Preparation stage:** If the operation fails during the **Preparation** stage, the logs are uploaded to LCS. In the log files, select **Download logs** to download the log files. If the package has any merge issues, the error is included in the log file.
- **Deploying stage:** If the operation fails during the **Deploying** stage, the logs are located in the on-premises environment. You must sign in to the environment, and then access the logs and event viewer.

For more information about how to use the troubleshooting logs, see [Troubleshoot on-premises deployments](troubleshoot-on-prem.md).

After you review the logs and determine the cause of the failure, complete one of the following operations to restore the environment to a healthy state. No actions can be performed on an environment that is in a **Failed** state. The environment must first be restored to a healthy state.

- **Retry failed operation** – If update application fails, select **Retry** to recover from the failed operation.
- **Abort failed operation** – Because there is no change made to the on-premises environment, if the preparation fails, you have the option to cancel the operation. Select **Abort** to cancel the preparation.
- **Roll back the update** – To roll back the update that failed, select **Rollback**. Before you start the rollback, you must restore the database to the last known good state. When you select **Rollback**, the environment is restored to the last known good state. The environment state is then changed to **Preparation**, then to **Deploying**, and then to either **Deployed** or **Failed**.

    >[!NOTE]
    > The **Rollback** button doesn't roll back the database. You're responsible for restoring the database to the last known backup that was made before update application. This step is critical to help guarantee that there is no data loss.

- **Refresh the state** – If update application fails during the **Preparation** stage, the failure is on the LCS side, and update application hasn't yet started. Therefore, the on-premises environment is in a good state. To restore the LCS environment state to **Deployed**, on the project dashboard page, select **Refresh**.
- **Delete and redeploy an environment** – If the retry and rollback options don't work, you must delete and redeploy the environment. To delete the environment, on the project dashboard page, select **Delete**. You then see the option to configure the environment.

    > [!IMPORTANT]
    > This option should **not** be used on a production environment. However, it can be used on a sandbox deployment to restore the environment to a healthy state. 
    
    > Because this option requires that you do a fresh deployment of the environment, you lose any updates that were previously applied. Any customizations and binary updates must be reapplied to the environment.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

