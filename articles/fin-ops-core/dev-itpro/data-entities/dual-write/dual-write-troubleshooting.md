---
title: General troubleshooting
description: This topic provides general troubleshooting information for dual-write integration between Finance and Operations apps and Dataverse.
author: RamaKrishnamoorthy 
ms.date: 03/16/2020
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: tfehr
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2020-03-16
---

# General troubleshooting

[!include [banner](../../includes/banner.md)]



This topic provides general troubleshooting information for dual-write integration between Finance and Operations apps and Dataverse.

> [!IMPORTANT]
> Some of the issues that this topic addresses might require either the system admin role or Microsoft Azure Active Directory (Azure AD) tenant admin credentials. The section for each issue explains whether a specific role or credentials are required.

## <a id="enable-view-trace"></a>Enable and view the plug-in trace log in Dataverse to view error details

**Required role to turn on the trace log and view errors:** System admin

To turn on the trace log, follow these steps.

1. Sign in to the customer engagement app, open the **Settings** page, and then, under **System**, select **Administration**.
2. On the **Administration** page, select **System Settings**.
3. On the **Customization** tab, in the **Plug-in and custom workflow activity tracing** column, select **All** to enable the plug-in trace log. If you want to log trace logs only when exceptions occur, you can select **Exception** instead.


To view the trace log, follow these steps.

1. Sign in to the customer engagement app, open the **Settings** page, and then, under **Customization**, select **Plug-in Trace Log**.
2. Find the trace logs where the **Type Name** column is set to **Microsoft.Dynamics.Integrator.DualWriteRuntime.Plugins.PreCommmitPlugin**.
3. Double-click an item to view the full log, and then, on the **Execution** FastTab, review the **Message Block** text.

## Enable debug mode to troubleshoot live synchronization issues in Finance and Operations apps

**Required role to view the errors:** System admin

Dual-write errors that originate in Dataverse can appear in the Finance and Operations app. To enable verbose logging for the errors, following these steps:

1. For all project configurations in Finance and Operations app there is a flag **IsDebugMode** on the **DualWriteProjectConfiguration** table.
2. Open the **DualWriteProjectConfiguration** using the Excel addin. To use the addin, enable design mode in the Finance and Operations Excel addin and add the **DualWriteProjectConfiguration** to the sheet. For more information, see [View and update entity data with Excel](../../office-integration/use-excel-add-in.md).
3. Set **IsDebugMode** to **Yes** on the project.
4. Run the scenario that is generating errors.
5. The verbose logs are stored in the **DualWriteErrorLog** table.
6. To lookup data on table browser use the following link: `https://999aos.cloudax.dynamics.com/?mi=SysTableBrowser&tableName=DualWriteErrorLog`, replacing `999` as needed.
7. Update again after [KB 4595434](https://fix.lcs.dynamics.com/Issue/Details?kb=4595434&bugId=527820&dbType=3&qc=98e5dc124ac125c57ad633d885ac612aea3ddb8f4abf9d71ab3aa354f2e06cbe), which is available for platform updates 37 and later. If you have this fix installed then the debug mode will capture more logs.  

## Check synchronization errors on the virtual machine for the Finance and Operations app

**Required role to view the errors:** System administrator

1. Sign in to Microsoft Dynamics Lifecycle Services (LCS).
2. Open the LCS project that you chose to do the dual-write testing for.
3. Select the **Cloud-hosted environments** tile.
4. Use Remote Desktop to sign in to the virtual machine (VM) for the Finance and Operations app. Use the local account that is shown in LCS.
5. Open Event viewer.
6. Select **Applications and Services Logs \> Microsoft \> Dynamics \> AX-DualWriteSync \> Operational**.
7. Review the list of recent errors.

## Unlink and link another Dataverse environment from a Finance and Operations app

**Required role to unlink the environment:** System administrator for either Finance and Operations app or Dataverse.

1. Sign in to the Finance and Operations app.
2. Go to **Workspaces \> Data management**, and select the **Dual Write** tile.
3. Select all running mappings, and then select **Stop**.
4. Select **Unlink environment**.
5. Select **Yes** to confirm the operation.

You can now link a new environment.

## Unable to view the sales order line Information form 

When you create a sales order in Dynamics 365 Sales, clicking on **+ Add products** might redirect you to the Dynamics 365 Project Operations order line form. There is no way from that form to view the sales order line **Information** form. The option for **Information** does not appear in the dropdown below **New Order Line**. This happens because Project Operations has been installed in your environment.

To re-enable the **Information** form option, follow these steps:

1. Navigate to the **Order Line** table.
2. Find the **Information** form under the forms node.
3. Select the **Information** form and click **Enable security roles**.
4. Change the security setting to **Display to everyone**.

## How to enable and save network trace so that traces can be attached to support tickets

The support team might need to review network traces to troubleshoot some issues. To create a network track, follow these steps:

### Chrome

1. In the opened tab, press **F12** or choose **Developer tools** to open the developer tools.
2. Open the **Network** tab and type **integ** in the filter text box.
3. Run your scenario and observe the requests being logged.
4. Right-click on the entries and select **Save all as a HAR with content**.

### Microsoft Edge

1. In the opened tab, press **F12** or choose **Developer tools** to open the developer tools.
2. Open the **Network** tab.
3. Run your scenario.
4. Select **save** to export the results as HAR.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
