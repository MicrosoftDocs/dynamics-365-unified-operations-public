---
# required metadata

title: General troubleshooting
description: This topic provides general troubleshooting information for dual-write integration between Finance and Operations apps and Common Data Service.
author: RamaKrishnamoorthy 
manager: AnnBe
ms.date: 03/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-03-16

---

# General troubleshooting

[!include [banner](../../includes/banner.md)]



This topic provides general troubleshooting information for dual-write integration between Finance and Operations apps and Common Data Service.

> [!IMPORTANT]
> Some of the issues that this topic addresses might require either the system admin role or Microsoft Azure Active Directory (Azure AD) tenant admin credentials. The section for each issue explains whether a specific role or credentials are required.

## When you try to install the dual-write package by using the package deployer tool, no available solutions are shown

Some versions of the package deployer tool are incompatible with the dual-write solution package. To successfully install the package, be sure to use [version 9.1.0.20](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment.Wpf/9.1.0.20) or later of the package deployer tool.

After you install the package deployer tool, install the solution package by following these steps.

1. Download the latest solution package file from Yammer.com. After the package zip file is downloaded, right-click it, and select **Properties**. Select the **Unblock** check box, and then select **Apply**. If you don't see the **Unblock** check box, the zip file is already unblocked, and you can skip this step.

    ![Properties dialog box](media/unblock_option.png)

2. Extract the package zip file, and copy all the files in the **Dynamics365FinanceAndOperationsCommon.PackageDeployer.2.0.438** folder.

    ![Contents of the Dynamics365FinanceAndOperationsCommon.PackageDeployer.2.0.438 folder](media/extract_package.png)

3. Paste all the copied files into the **Tools** folder of the package deployer tool. 
4. Run **PackageDeployer.exe** to select the Common Data Service environment and install the solutions.

    ![Content of the Tools folder](media/paste_copied_files.png)

## Enable and view the plug-in trace log in Common Data Service to view error details

**Required role to turn on the trace log and view errors:** System admin

To turn on the trace log, follow these steps.

1. Sign in to the Finance and Operations app, open the **Settings** page, and then, under **System**, select **Administration**.
2. On the **Administration** page, select **System Settings**.
3. On the **Customization** tab, in the **Plug-in and custom workflow activity tracing** field, select **All** to enable the plug-in trace log. If you want to log trace logs only when exceptions occur, you can select **Exception** instead.


To view the trace log, follow these steps.

1. Sign in to the Finance and Operations app, open the **Settings** page, and then, under **Customization**, select **Plug-in Trace Log**.
2. Find the trace logs where the **Type Name** field is set to **Microsoft.Dynamics.Integrator.DualWriteRuntime.Plugins.PreCommmitPlugin**.
3. Double-click an item to view the full log, and then, on the **Execution** FastTab, review the **Message Block** text.

## Enable debug mode to troubleshoot live synchronization issues in Finance and Operations apps

**Required role to view the errors:** System admin
Dual-write errors that originate in Common Data Service can appear in the Finance and Operations app. In some cases, the full text of the error message isn't available because the message is too long or contains personally identifying information (PII). You can turn on verbose logging for errors by following these steps.

1. All project configurations in Finance and Operations apps have an **IsDebugMode** property in the **DualWriteProjectConfiguration** entity. Open the **DualWriteProjectConfiguration** entity by using the Excel add-in.

    > [!TIP]
    > An easy way to open the entity is to turn on **Design** mode in the Excel add-in and then add **DualWriteProjectConfigurationEntity** to the worksheet. For more information, see [Open entity data in Excel and update it by using the Excel add-in](../../office-integration/use-excel-add-in.md).

2. Set the **IsDebugMode** property to **Yes** for the project.
3. Run the scenario that is generating errors.
4. The verbose logs are available in the DualWriteErrorLog table. To look up data in the table browser, use the following URL (replace **XXX** as appropriate):

    `https://XXXaos.cloudax.dynamics.com/?mi=SysTableBrowser&tableName=>DualWriteErrorLog`

## Check synchronization errors on the virtual machine for the Finance and Operations app

**Required role to view the errors:** System administrator

1. Sign in to Microsoft Dynamics Lifecycle Services (LCS).
2. Open the LCS project that you chose to do the dual-write testing for.
3. Select the **Cloud-hosted environments** tile.
4. Use Remote Desktop to sign in to the virtual machine (VM) for the Finance and Operations app. Use the local account that is shown in LCS.
5. Open Event viewer.
6. Select **Applications and Services Logs \> Microsoft \> Dynamics \> AX-DualWriteSync \> Operational**.
7. Review the list of recent errors.

## Unlink and link another Common Data Service environment from a Finance and Operations app

**Required role to unlink the environment:** System administrator for either Finance and Operations app or Common Data Service.

1. Sign in to the Finance and Operations app.
2. Go to **Workspaces \> Data management**, and select the **Dual Write** tile.
3. Select all running mappings, and then select **Stop**.
4. Select **Unlink environment**.
5. Select **Yes** to confirm the operation.

You can now link a new environment.

## Unable to view the sales order line Information form 

When you create a sales order in Dynamics 365 Sales, clicking on **+ Add products** might redirect you to the Dynamics 365 Project Operations order line form. There is no way from that form to view the sales order line **Information** form. The option for **Information** does not appear in the dropdown below **New Order Line**. This happens because Project Operations has been installed in your environment.

To re-enable the **Information** form option, follow these steps:
1. Navigate to the **Order Line** entity.
2. Find the **Information** form under the forms node. 
3. Select the **Information** form and click **Enable security roles**. 
4. Change the security setting to **Display to everyone**.
