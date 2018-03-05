---
# required metadata

title: Apply updates to an on-premises deployment
description: This topic explains how to apply updates to an on-premises deployment of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
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
# Apply updates to an on-premises deployment

[!include[banner](../includes/banner.md)]

This topic explains how to apply supported updates to an on-premises deployment of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. All updates to on-premises environments are done through Microsoft Dynamics Lifecycle Services (LCS).

## Search for and download updates
To learn more about how to find the updates that you can apply to your on-premises environment, see the topic, Issue search. To download the updates from the tiles in the **Updates** section of the **Environment details** page, see the topic, [Download updates](../migration-upgrade/download-hotfix-lcs.md). 

## Update an on-premises deployment
You can apply updates to an on-premises environment during the deployment or after the deployment is complete.  

When an on-premises environment is being deployed, you can select to deploy a custom package in the **Advanced** settings.For more information about how to apply customizations or application X++ updates, complete the steps in the topic, [Develop and Deploy custom models to on-premises environments](develop-deploy-custom-models-on-premises.md).  

If you are on a platform version that is older than Update 12, you will have the option to reconfigure an already deployed environment to update the customizations or to update to the latest platform release. For more information about redeploying, see [Redeploy an on-premises environment](redeploy-on-prem.md). 

To apply updates a deployed on-premises environment, in LCS, navigate to the **Environment details** page for that environment and under Maintain, select **Apply Updates**.  

   > [!NOTE]
   > You can only apply updates after deployment on environments with Platform Update 12 or higher. The environment must also have the latest version of the local agent available in LCS. For more information, see the topic [Update the local agent](../lifecycle-services/update-local-agent.md).


## Apply application or binary updates through LCS 
The following steps can be used to apply X++, All Binary, or Platform Binary updates. To move from one platform release to another, refer to the **Apply the latest platform update** section later in this topic.  
    > [!IMPORTANT]
    > Applying updates will require downtime to your environment. This means that no business transactions can be performed on the environment during the update. When you complete the following steps, verify that the system is not being used and that an official downtime notice has been communicated to all system users. 


### Pre-requisites
- Before you begin, complete a full backup of the MR, AX and SSRS databases. While the restoring the code is completed through LCS, restoring the database must be done manually to ensure that there is no data loss.  
- Update you environment to the latest build of Platform Update 12. 
- Update the local agent to the latest version. For more information, see [Update the local agent](../lifecycle-services/update-local-agent.md).Visit the agent version topic for more details.  
- Depending on the update type, complete the following steps to generate a deployable package: 

   - Application binary updates - Download or save the update directly to the Asset library by following the steps in the topic, [Download updates wiki](../migration-upgrad/download-hotfix-lcs.md).  
   - Application X++ updates - Download the required hotfix to your development environment, and then follow the steps in the topic, [Create a deployable package of your models in order to apply it to a runtime environment(create-apply-deployable-package.md).
   - Customizations - Follow the steps in the topic, [Develop and Deploy custom models](develop-deploy-custom-models-on-premises.md). 

### Update a sandbox environment
1. In the LCS Asset library, upload the deployable package from the pre-requisite section to the **Software deployable packages** tab.
2. In LCS, open the on-premises Implementation project and navigate to the **Environment details** page of the environment you want to update.  
3. Under **Maintain**, select **Apply updates**. A slider will open that shows the updates that were uploaded to the Asset library. Note that only packages marked as **Valid** in the Asset Library will show up.  
4. Select the update and click **Apply**.  
5. On the confirmation dialog, click **Yes**. The servicing operation has started on this environment.  
The environment state will change from **Deployed** to **Preparation**. During the **Preparation** phase, the actual deployment has not yet started. This means that even if the preparation fails, the on-premises environment is not touched and can be used.  
    >[!NOTE]
    > Even though the **Preparation** phase does not touch the on-premises environment directly, we recommend you do not use the environment to perform transactions during this time.  
When the preparation is complete, the environment state changes from **Preparation** to **Deploying**.  

After the update is complete, the environment will return to the **Deployed** state. If the update application fails, the environment state will update to **Failed**. For details on what to do when package application fails, refer to the **What to do** section later in this topic.
6. Navigate to **History** and **Environment details** to view the operations performed on the environment. You can also view a record of major actions performed on the environment such as deployment, servicing, and rollback.   

### Update a production environment 
Before you update a production environment, you must first successfully complete the package application update on a sandbox environment. 

1. In the project of the sandbox environment to which you applied the package, open the Asset Library, select the package on the **Software deployable packages** tab, and mark it is as a **Release candidate**.  
2. Open the **Environment details** page.
3. Under **Maintain**, select **Apply Updates**. In the slider that opens, only packages marked as **Release candidates** will be included.  
4. On the confirmation dialog, click **Yes**. 
As with updating the sandbox environment, the environment state will change from **Deployed** to **Preparation**. During the **Preparation** phase, the actual deployment has not yet started. This means that even if the preparation fails, the on-premises environment is not touched and can be used.  
    >[!NOTE]
    > Even though the **Preparation** phase does not touch the on-premises environment directly, we recommend you do not use the environment to perform transactions during this time.  
When the preparation is complete, the environment state changes from **Preparation** to **Deploying**.  
After the update is complete, the environment will return to the **Deployed** state. If the update application fails, the environment state will update to **Failed**. For details on what to do when package application fails, refer to the **What to do** section later in this topic.
5. Navigate to **History** and **Environment details** to view the operations performed on the environment. You can also view a record of major actions performed on the environment such as deployment, servicing, and rollback.  

## Resolve a failed application
When update application fails, the environment is in a **Failed** state. The first step is to figure out why the update application failed. Based on where the failure is, the logs will be located in two difference locations.  

- **Preparation** stage: When the operation fails in the **Preparation** stage, the logs are uploaded to LCS. In the log files, click **Download Logs** to download the log files. If there are any merge issues with the package, the error will be included in the log file.  
- **Deploying** stage: When the operation fails in the **Deploying** stage, the logs are located in the on-premises environment. You will need to login to the environment and then access the logs and event viewer.  

For more information about to use the troubleshooting logs, see [Troubleshoot Dynamics 365 for Finance and Operations, Enterprise edition on-premises](troubleshoot-on-prem-md). 


After you have reviewed the logs and determined the cause of the failure, complete one of the following options to restore the environment to a healthy state. During the time that the environment is in a failed state, actions that can be performed on the environment will not be enabled until it been restored to a healthy state.

- **Retry failed operation:** If update application fails, click **Retry** to recover from the failed operation.  
- **Rollback the update:** To roll back the update that failed, click **Rollback**. Restoring the database to the last known good state must be completed prior to starting the rollback. When you click **Rollback**, the environment will be restored to the last known good state. The environment will then go into the **Preparation** state followed by the **Deploying** and then **Deployed** or **Failed** state.  
   >[!NOTE]
   > Clicking **Rollback** does not rollback the database. You are responsible to restoring the database to the last know backup taken before applying the update. This is critical to ensure that there is no data loss.  
- **Refresh the state:** - If the update application fails in the **Preparation** state, the failure was on the LCS side and the update application had not yet started. This means that the on-premises environment is in a good state. To restore the LCS environment state back to **Deployed**, on the Project dashboard page, click **Refresh**.  
- **Delete and redeploy an environment:** - **Important** - This option should NOT be exercised on a production environment. This can be used on a sandbox deployment to restore the environment to a healthy state. 
If the retry and rollback options do not work, you will need to delete and redeploy the environment. To delete the environment, on the Project dashboard page, click **Delete** . You will now see the option to **Configure** the environment.  
   > [!NOTE]
   > Because this option requires you to do a fresh deployment of the environment, you will lose any previously applied updates. Any customizations and binary updates will have to be re-applied to this environment.

## Apply the latest platform update 
There are two ways to apply the latest platform update: 
- Deploy a new environment and select the latest platform update topology during deployment. Then, follow the usual steps for deploying an environment. 
- Update an existing environment with the latest update by redeploying the environment. For more information about redeploying, see [Redeploy an on-premises environment](redeploy-on-prem.md). 


