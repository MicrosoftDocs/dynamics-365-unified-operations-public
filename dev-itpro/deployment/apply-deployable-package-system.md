---
# required metadata

title: Apply a deployable package on a Dynamics 365 for Operations system
description: This tutorial walks you through the steps for applying a deployable package on a Microsoft Dynamics 365 for Operations system. This package can be either a binary hotfix for Application Object Server (AOS) or a deployable package that was created in your development environment.
author: annbe
manager: AnnBe
ms.date: 2016-08-10 23 - 27 - 58
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: Operations, Platform, AX Platform
# ms.tgt_pltfrm: 
ms.custom: 107013
ms.assetid: 1742d199-4e1a-4206-96af-5e3032cc8dc4
ms.search.region: Global
# ms.search.industry: 
ms.author: annbe
ms.dyn365.intro: May-16
ms.dyn365.version: Platform update 1

---

# Apply a deployable package on a Dynamics 365 for Operations system

This tutorial walks you through the steps for applying a deployable package on a Microsoft Dynamics 365 for Operations system. This package can be either a binary hotfix for Application Object Server (AOS) or a deployable package that was created in your development environment.

Supported environments
----------------------

-   **Demo** - Customers/partners can apply a deployable package in their demo environments using LCS without having to establish a remote connection to each computer.
-   **Dev/Test/Build**  – Customers/partners can apply a deployable package in their dev/test environments by establishing a remote connection to the computers and running the package manually. For more information about this environment, see [Install a deployable package in Microsoft Dynamics 365 for Operations](install-deployable-package.md).
-   **Sandbox** – Customers/partners can apply a deployable package in their sandbox environments using LCS without having to establish a remote connection to each computer.
-   **Production** – Customers can submit requests to the Microsoft Service Engineering team through Microsoft Dynamics Lifecycle Services (LCS) to apply a deployable package in their production environments. They will then be able to see the progress of their request in the **Environment details** view in LCS.
-   **Downloadable VHD** – Customers/partners can manually apply a deployable package by establishing a remote connection to the computers. For more information about this environment, see [Install a deployable package in Microsoft Dynamics 365 for Operations](install-deployable-package.md).

## Key concepts
-   **Deployable package** – A deployable package is a unit of deployment that can be applied in any Dynamics 365 for Operations environment. A deployable package can be a binary hotfix to the Application Object Server (AOS) runtime components, an updated Dynamics 365 for Operations customization package, or a new Dynamics 365 for Operations customization/application module package. [![Example of a deployable package](./media/applypackage_deployablepackage.jpg)](./media/applypackage_deployablepackage.jpg)
-   **Runbook** – The deployment runbook is a series of steps that are generated for applying the deployable package to the target environment. Some of the steps are automated, and some are manual. AXUpdateInstaller lets you run these steps one at a time and in the correct order. [![Example of a deployment runbook](./media/applypackage_runbook-1024x528.jpg)](./media/applypackage_runbook.jpg)
-   **AXUpdateInstaller** – When you create a customization package from Microsoft Visual Studio or a Microsoft binary hotfix, the installer executable is bundled together with the deployable package. The installer generates the runbook for the specified topology. The installer can also run steps in order, according to the runbook for a specific topology.

## Types of packages
-   **AOT deployable package** – A deployable package that is generated after the application source code is applied, any conflicts are resolved, and the code is compiled.
-   **Binary package** – A deployable package that contains binary dynamic-link libraries (DLLs) that the platform and application depend on.
-   **Retail deployable package (combined)** – A combined deployable package that is generated from the source code.

## Prerequisite steps
When the status of the package application changes, LCS sends notifications to all the project users. Any additional stakeholders who must be notified must be specified in the notification list.

1.  To add additional stakeholders, in LCS, in the **Environment details** view, click **Notification list**.
2.  Add the email address of each user who must be notified, and then click **Save**.

## A customer applies a package in a demo/sandbox environment
**Note:** Package application causes system downtime. All the relevant services will be stopped, and you won't be able to use your environments while the package is being applied.

1.  Download a hotfix from LCS. For information about how to download a hotfix from LCS, see [Download hotfixes from Lifecycle Services](download-hotfix-lcs.md).
    -   For a binary hotfix, upload the hotfix directly to the Asset library.
    -   For an application/X++ hotfix, apply the package in a dev environment. After you resolve any conflicts, generate a deployable package from Visual Studio, and upload the package to the Asset library. For information about how to upload to the Asset library and create a deployable package, see [Create and apply a deployable package](create-apply-deployable-package.md).

2.  Open the **Environment details** view for the sandbox environment where you want to apply the package.
3.  Click **Maintain** &gt; **Apply updates** to apply an update.
4.  Click the type of package to apply.
5.  Select the package to apply, and then click **Apply**. Notice that the status in the upper right of the **Environment details** view changes to **Queued**, and that an **Environment updates** section now shows the progress of the package. [![Environment details view showing Queued status and an Environment updates section](./media/applypackage_sandbox_6-1024x302.png)](./media/applypackage_sandbox_6.png)
6.  Refresh the page to see the progress of the package application. Notice that the servicing status is **In Progress**, and the environment status is **Servicing**. [![Environment details view showing a servicing status of In Progress and an environment status of Servicing](./media/applypackage_sandbox_7-1024x397.png)](./media/applypackage_sandbox_7.png)
7.  Continue to refresh the page to see the status updates for the package application request. When the package has been applied, the environment status changes to **Deployed**, and the servicing status changes to **Completed**. [![Environment details view showing an environment status of Deployed and a servicing status of Completed](./media/applypackage_sandbox_8-1024x396.png)](./media/applypackage_sandbox_8.png)
8.  To sign off on the package application, click **Sign off** if there are no issues. If issues occurred when you applied the package, click **Sign off with issues**.

### Troubleshooting

#### General troubleshooting/diagnostics

If package application isn't successful, you can download either the logs or the runbook to see the detailed logs. You can also use Remote Desktop Protocol (RDP) to establish a remote connection to an environment to fix issues. If you must report the issue to Microsoft, be sure to include the activity ID that is reported in the **Environment updates** section. [![Environment details view showing the activity ID and the buttons for downloading the logs and the runbook](./media/applypackage_sandbox_10-1024x397.png)](./media/applypackage_sandbox_10.png)

#### Using the logs

1.  Download the logs.
2.  Unzip the log files.
3.  Select the role that had the step failure, such as AOS or BI.
4.  Select the virtual machine (VM) where the step failed. This information appears in the **Machine name** column in the **Environment updates** section.
5.  In the logs for the VM, select the folder that corresponds to the step where the issue occurred. The folder name identifies the step that each folder corresponds to. For example, if the issue occurred in the executing a step, select the **ExecuteRunbook\*** folder.

For example, if the folder name is ExecuteRunbook-b0c5c413-dae3-4a7a-a0c4-d558614f7e98-1\_I0\_R0, the step number is highlighted and is the number after the GUID.

#### Failure of a specific step

If a specific step fails, you have two options:

-   Click **Rerun step** or, if you've manually fixed the issue that caused the step to fail, mark the step as **Complete**.
-   Click **Abort** to stop package application. **Note:** If you click **Abort**, you don't roll back the changes that have already been made to your environment. To proceed, you must fix the issue. [![Message box that appears when you abort package application](./media/applypackage_sandbox_13-1024x274.png)](./media/applypackage_sandbox_13.png)

## A customer submits a request to apply a package in a production environment
**Note:** See [Enable additional notifications on package application through LCS](https://ax.help.dynamics.com/en/wp-admin/post.php?post=1139123&action=edit#_Pre-requisite_Step).

1.  Download a hotfix from LCS. For information about how to download a hotfix from LCS, see [Download hotfixes from Lifecycle Services](download-hotfix-lcs.md).
    -   For a binary hotfix, upload the hotfix directly to the Asset library.
    -   For an application/X++ hotfix, apply the package in a dev environment. After you resolve any conflicts, generate a deployable package from Visual Studio, and upload the package to the Asset library. For information about how to upload to the Asset library and create a deployable package, see [Create and apply a deployable package](create-apply-deployable-package.md).

2.  On the LCS **Asset library** page, on the tab that corresponds to the asset type (**Software deployable package**), select a package, and then click **Release candidate**.
3.  Open the **Environment details** view for the production environment where you want to apply the package.
4.  Click **Maintain** &gt; **Apply updates** to apply the package.
5.  Select the type of package to apply.
6.  Select the package to apply in your production environment, and then click **Schedule** to submit a request to the Service Engineering team to apply it. The list of packages includes only packages that have been successfully signed off in the sandbox environment, and that have been marked as release candidates.
7.  Specify the date and time when you want to schedule package application, click **Submit**, and then click **OK** to confirm. Note that your environments will be down and unavailable to perform business while the package is being applied.
8.  Refresh the page. Two fields on the page indicate the status of the request.
    -   **Request status** – This field indicates the status of the request that you submitted to Microsoft.
    -   **Actionable by** – This field indicates who needs to take action.

    [![Request status and Actionable by fields](./media/applypackage_prod_7-1024x269.png)](./media/applypackage_prod_7.png)
9.  The Service Engineering team can either accept or deny the request.
    -   If the request is accepted, the Service Engineering team begins to update the environment. [![Accepted request: Request status = Request accepted, Actionable by = Microsoft](./media/applypackage_prod_9-1024x384.png)](./media/applypackage_prod_9.png)
    -   If the request is denied, Microsoft informs the customer about the reason for the denial and the action that the customer must take. The customer can then reschedule the request, change the package, or cancel the request. [![Denied request: Request status = Request denied, Actionable by = Customer/Partner](./media/applypackage_prod_8-1024x322.png)](./media/applypackage_prod_8.png)

    At any time, the customer can use the **Comments** field to post comments to the request. [![Example of comments that are posted to a request](./media/applypackage_prod_10-1024x336.png)](./media/applypackage_prod_10.png)
10. After the environment is serviced, you can monitor the status. The **Servicing status** field indicates the status of the package application. [![Servicing status and Request status fields](./media/applypackage_prod_11-1024x399.png)](./media/applypackage_prod_11.png) You can also see the number of steps that have been run, out of the total number of steps that are available. [![Progress indicator](./media/applypackage_prod_12-1024x414.png)](./media/applypackage_prod_12.png)

### Successful package application

-   After the deployment is successfully completed, the **Servicing** **status** field is set to **Completed**, but the **Request status** is still set to **In progress**, because the request hasn't yet been closed. [![Successful deployment: Servicing status = Completed, Request status = In progress](./media/applypackage_prod_13-1024x392.png)](./media/applypackage_prod_13.png)
-   After the Service Engineering team has finished applying the request, you must close the request by clicking **Close servicing request**.
-   When you're closing a successful request, in the **Edit work item details** dialog box, set the **Service request status** field to **Succeeded**, and then click **Submit**.

### Unsuccessful package application

-   If package application fails, Microsoft will investigate the issue. The **Servicing status** will indicate that package application has failed. [![Unsuccessful package deployment: Servicing status = Failed](./media/applypackage_prod_17-1024x289.png)](./media/applypackage_prod_17.png)
-   When the deployment fails, Microsoft can abort the package, revert the environment to a good state, and send the request back to the customer, so that the customer can validate the environment and close the request. If there is an issue in the package, the customer must submit a new request with the new package. [![Comment from Microsoft that changes were reverted, and that the customer must validate the environment](./media/applypackage_prod_18-1024x346.png)](./media/applypackage_prod_18.png)
-   When you're closing a failed request, in the **Edit work item details** dialog box, set the **Service request status** field to **Aborted**.


See also
--------

[Install a deployable package in Microsoft Dynamics AX](install-deployable-package.md)

