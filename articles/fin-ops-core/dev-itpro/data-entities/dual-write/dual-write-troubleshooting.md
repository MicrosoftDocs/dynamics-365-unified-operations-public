---
# required metadata

title: Troubleshooting guide for data integration
description: This topic provides troubleshooting information for data integration between Finance and Operations apps and Common Data Service.
author: RamaKrishnamoorthy 
manager: AnnBe
ms.date: 07/25/2019
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
ms.search.validFrom: 2019-07-15

---

# Troubleshooting guide for data integration

[!include [banner](../../includes/banner.md)]

[!include [preview-banner](../../includes/preview-banner.md)]

## Enable plug-in trace logs in Common Data Service and inspect the dual-write plug-in error details

If you experience an issue or error during dual-write synchronization, follow these steps to inspect the errors in the trace log.

1. Before you can inspect the errors, you must enable plug-in trace logs. For instructions, see the "View trace logs" section of [Tutorial: Write and register a plug-in](https://docs.microsoft.com/powerapps/developer/common-data-service/tutorial-write-plug-in#view-trace-logs).

    You can now inspect the errors.

2. Sign in to Microsoft Dynamics 365 Sales.
3. Select the **Settings** button (the gear symbol), and then select **Advanced Settings**.
4. On the **Settings** menu, select **Customization \> Plug-In Trace Log**.
5. Select **Microsoft.Dynamics.Integrator.CrmPlugins.Plugin** as the type name to show the error details.

## Inspect dual-write synchronization errors

Follow these steps to inspect errors during testing.

1. Sign in to Microsoft Dynamics Lifecycle Services (LCS).
2. Open the LCS project to do dual-write testing for.
3. Select **Cloud-hosted environments**.
4. Make a Remote desktop connection to the application virtual machine (VM) by using local account that is shown in LCS.
5. Open Event Viewer. 
6. Go to **Applications and Services Logs \> Microsoft \> Dynamics \> AX-DualWriteSync \> Operational**. The errors and details are shown.

## Unlink one Common Data Service environment from the application and link another environment

Follow these steps to update links.

1. Go to the application environment.
2. Open Data Management.
3. Select **Link to CDS for apps**.
4. Select all the mappings that are running, and then select **Stop**.
5. Select all the mappings, and then select **Delete**.

    > [!NOTE]
    > The **Delete** option isn't available if the **CustomerV3-Account** template is selected. Clear the selection of this template as required. **CustomerV3-Account** is an older provisioned template and works with the Prospect to Cash solution. Because it's globally released, it appears under all templates.

6. Select **Unlink environment**.
7. Select **Yes** to confirm the operation.
8. To link the new environment, follow the steps in the [installation guide](https://aka.ms/dualwrite-docs).
