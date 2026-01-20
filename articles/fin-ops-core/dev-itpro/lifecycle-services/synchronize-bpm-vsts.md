---
title: Synchronize BPM libraries with Azure DevOps
description: Learn about how to synchronize a BPM library in Lifecycle Services with Azure DevOps, including outlines for Lifecycle Services project settings.
author: amarshall
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom:
ms.search.form: 
ms.dyn365.ops.version: 2012
---

# Synchronize BPM libraries with Azure DevOps

[!include [banner](../includes/banner.md)]

You start the implementation stage of a project by synchronizing a Business process modeler (BPM) library with your project in Microsoft Azure DevOps. By using this approach, you can review processes and associate requirements with business processes. When you synchronize a BPM library with an Azure DevOps project, you can track the progress of your implementation project in Azure DevOps. You can also associate various work items with requirements and business processes. These work items include bugs, tasks, backlog items, tests, and documents.

Currently, BPM-Azure DevOps synchronization doesn't support custom work item types or synchronizing business processes with custom work item types. If you try either of these actions, you receive a warning. If you choose to ignore the warning and attempt an Azure DevOps sync by using a custom template, you can avoid synchronization problems by verifying the following conditions for the template:

- It doesn't delete any work item type.
- It doesn't delete any state of a work item type.
- It doesn't add any required fields to a work item type.

For more information about Azure DevOps, see [www.visualstudio.com/team-services](https://www.visualstudio.com/team-services).

## Lifecycle Services project settings: Set up Azure DevOps

If you already set up Azure DevOps from Microsoft Dynamics Lifecycle Services, you can skip the procedures in this section.

### Create a personal access token

To connect to an Azure DevOps project, Lifecycle Services authenticates by using a personal access token. Follow these steps to create a personal access token in Azure DevOps.

1. Go to <https://www.visualstudio.com>, sign in, and find your Azure DevOps project.
1. In the upper-right corner, hold the pointer over your name, and then, on the menu that appears, select **Security**.
1. Select **Add** to create a new personal access token.
1. Enter a name for the token, and then specify how long the token should last.
1. Select **Create Token**.
1. Copy the token to your clipboard.

    > [!NOTE]
    > You can't find the token details again after you complete this step and move away from the page. Make sure that you copy the token before you move away from the page.

### Configure your Lifecycle Services project to connect to Azure DevOps

1. In your Lifecycle Services project, select the **Project settings** tile.
1. Select **Azure DevOps**, and then select **Setup Azure DevOps**. Many Lifecycle Services tools require this configuration. If you already configured Lifecycle Services to connect to your Azure DevOps project, you can either skip this procedure or select **Change** to change the existing configuration.
1. Enter the root URL for your Azure DevOps account, and the personal access token that you created earlier, and then select **Continue**.
1. Select your Azure DevOps project.

    > [!NOTE]
    > Lifecycle Services requires entering the Azure DevOps root URL in the legacy format. The legacy format is `https://ACCOUNT.visualstudio.com` and `https://contoso.visualstudio.com`.

1. Specify the mapping between Lifecycle Services/BPM items and the associated Azure DevOps work item types.

    :::image type="content" source="./media/newbpm_BlogPost24.png" alt-text="Screenshot of work item type mappings.":::

1. Select **Continue**, review your changes, and then select **Save**.

## Synchronize a BPM library with an Azure DevOps project

After you set up the connection between the Lifecycle Services project and an Azure DevOps project, you can synchronize a BPM library with the Azure DevOps project. When you synchronize a BPM library with an Azure DevOps project, you create an Azure DevOps work item for each business process line in the BPM library. In addition, the hierarchy of business processes in BPM is reflected in the hierarchy of work items in Azure DevOps. The type of work items that you create in Azure DevOps depends on the settings of your Lifecycle Services project.

This synchronization is one-way. Changes in Lifecycle Services are reflected in Azure DevOps, but changes in Azure DevOps aren't reflected in Lifecycle Services.

The following information is synchronized:

- Business process names
- Business process descriptions
- Keywords (as tags)
- Countries or regions (as tags)
- Industries (as tags)

To synchronize a BPM library with an Azure DevOps project, on the **Business process libraries** page, on the tile for the library that you want to synchronize, select the ellipsis button (…), and then select **Azure DevOps sync**.

:::image type="content" source="./media/newbpm_BlogPost25.png" alt-text="Screenshot of starting Azure DevOps synchronization from the tile for a library.":::

You can also start Azure DevOps synchronization from the toolbar in a BPM library. Select the ellipsis button (…), and then select **Azure DevOps sync**.

:::image type="content" source="./media/newbpm_BlogPost26.png" alt-text="Screenshot of starting Azure DevOps synchronization from the toolbar in a library.":::

> [!NOTE]
> BPM localization isn't supported. If you edit in the new BPM client in any language other than EN-US, your changes only display when you view the BPM in the language in which the changes were made. To view any changes made in EN-US, you must synchronize with Visual Studio Team Server before the changes display.

## Turn off synchronization of BPM with Azure DevOps

To turn off synchronization, on the **Business process libraries** page, select the library that you want to stop synchronizing, select the ellipsis button (…), and then clear **Azure DevOps sync**.

## Review processes and add requirements

During the project phase where you're gathering requirements, use the BPM library to review business processes and tasks, and to identify requirements. In BPM, you can mark business processes as reviewed to track the review process.

To mark a process or one of its child processes as reviewed, select the process in BPM. In the right pane, on the **Overview** tab, select **Mark as reviewed**.

When you mark a business process as reviewed, the **Reviewed** column updates. This column shows the following information:

- A fraction indicates how many direct child processes are reviewed.
- A symbol indicates how completely the process and its child processes are reviewed:

  - **Green check mark** – The process and all its child processes are fully reviewed.
  - **Yellow circle** – The process and its child processes are partially reviewed.
  - **Red dash** – The process and its child processes aren't reviewed.

    :::image type="content" source="./media/newbpm_BlogPost28.png" alt-text="Screenshot of example of a Review column.":::

While you're reviewing a business process that you connected to Azure DevOps, add a requirement directly to your Azure DevOps project.

1. Select a business process.
1. In the right pane, on the **Requirements** tab, select **Add requirement**.
1. Enter a name, description, and type, and then select **Create**.

    In Azure DevOps, a requirement work item is created that is associated with the current business process.

To go to the Azure DevOps work items that are associated with the current business process, on the **Requirements** tab, select the appropriate links.

## Common syncing errors

If the BPM to Azure DevOps synchronization fails, you see the failed process name, work item type, and an error message.

:::image type="content" source="./media/BPMsyncError.jpg" alt-text="Screenshot of BPM sync error.":::

Here are some common causes and suggested actions to resolve the error.

| **Possible cause** | **Error message** | **Suggested solution** |
|---------|--------|--------|
| Required field added | Failed to create work item. You added a required field to this work item type, which isn't supported. Remove this requirement or provide a default value in the process template to unblock the operation. | Remove the required field or provide a default value. |
| Work item type disabled | Failed to create work item. You disabled the work item type in the process template. Enable the work item type to unblock the operation. | Enable the work item type in the process template |  
| Couldn't find work item to update | Failed to update work item. The work item doesn't exist, or you don't have permissions to read it. Check the PAT configuration in the project settings or restore the work item if you deleted it directly from the DevOps project. | Restore the work item from the recycle bin if you deleted it, or create a new Personal Access Token (PAT) and make sure that it has full permissions. |  
| Personal Access Token is expired | Failed to sync with Visual Studio Team Services. The request response is: Unauthorized. Check that the PAT is set up correctly and still valid, try again and contact support if the error persists. | Create a new Personal Access Token (PAT) from Azure DevOps and update the PAT value in your Lifecycle Services Project settings. |
| Generic error | Failed to sync with Visual Studio Team Services. The request response is: {0}. Check that the PAT is set up correctly and still valid, try again and contact support if the error persists. | Contact customer support with the request response that caused the syncing error. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
