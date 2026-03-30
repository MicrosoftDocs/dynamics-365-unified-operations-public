---
title: Subscribe to events in Dataverse
description: Learn about how to subscribe to and manage finance and operations apps business events and data events in Microsoft Dataverse.
author: jaredha
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/15/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-11-03
ms.dyn365.ops.version: 10.0.22
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Subscribe to events in Dataverse

[!include[banner](../../includes/banner.md)]

> [!IMPORTANT]
> Before you subscribe to finance and operations apps business events and data events in Microsoft Dataverse, you must enable the Microsoft Power Platform integration. For information about how to enable the Microsoft Power Platform integration for a finance and operations apps environment, see [Enabling the Power Platform integration](../../power-platform/enable-power-platform-integration.md).

You can subscribe to finance and operations apps business events and data events in Dataverse by registering plug-ins and software development kit (SDK) steps on the events in Dataverse. This article describes how to use the Power Platform Tools extension for Visual Studio to register a plug-in for a finance and operations apps event. The subscriptions appear together with other subscriptions in the business event catalog in finance and operations apps. The endpoint then works like other endpoints in the finance and operations apps business event catalog.

## Set up your development environment

### Install the Power Platform Tools extension

Power Platform Tools for Visual Studio is an extension that provides code templates for Dataverse plug-ins. It includes a Dataverse explorer that shows tables, business events, and virtual entity data events. The explorer lets you register plug-ins directly from Visual Studio. You can deploy the C# code for the plug-in directly to Dataverse from the solution.

For information about how to install the Power Platform Tools extension, see [Install Power Platform Tools](/powerapps/developer/data-platform/tools/devtools-install).

### Create a project

After you install the Power Platform Tools extension, create a new project.

1. Open Visual Studio 2019 or later.
1. In the **Get started** dialog box, select **Create a new project**.
1. In the **Create a new project** dialog box, search for **Power Platform Solution Template**, select it, and then select **Next**.

    :::image type="content" source="../media/businessevents_SelectSolutionTemplate.png" alt-text="Screenshot of Selecting Power Platform Solution Template in the Create a new project dialog box.":::

1. In the **Configure your new project** dialog box, enter a project name, select the location where you want to save the solution file, and then select **Create**.
1. In the **Configure Microsoft Power Platform Solution** dialog box, under **1. Solution Type to Configure**, select **Start from Dataverse**.
1. In the **Power Platform Tools** dialog box, under **2. Connect to Dataverse**, follow these steps:

    1. In the **Deployment Type** field group, select the **Office 365** option.
    1. Select the **Display list of available organizations** checkbox.
    1. Select **Login**, and enter the credentials to sign in to the Dataverse environment that is linked to your finance and operations apps environment.
    1. In the list of organizations, select the Microsoft Power Platform environment that you want to work with. Then select **Login**.
    1. Select **Next**.

    :::image type="content" source="../media/businessevents_PowerPlatformToolsConnectToDataverse.png" alt-text="Screenshot of Connecting to Dataverse in the Power Platform Tools dialog box.":::

1. Under **3. Select Solution**, select the Microsoft Power Platform solution where you want to create the event subscription. If you didn't create a solution, create one in the Power Apps maker portal by following the steps in [Create a solution](/powerapps/maker/data-platform/create-solution).

    :::image type="content" source="../media/businessevents_PowerPlatformToolsSelectSolution.png" alt-text="Screenshot of Selecting a solution in the Power Platform Tools dialog box.":::

1. Select **Done**.
1. In the **Visual Studio Template Selection Microsoft Power Platform** dialog box, under **1. Select Items for Template**, select **Add New Templates**.

    :::image type="content" source="../media/businessevents_PowerPlatformToolsSelectItemsForTemplate.png" alt-text="Screenshot of Select to add new templates in the Visual Studio Template Selection Microsoft Power Platform dialog box.":::

1. In the **Create New Items** dialog box, under **2. Selected Template Projects**, select the **Add Plugin Project** checkbox, and then select **Next**.
1. Under **3. Assign project Names**, in the **Plugins** field, enter a name for the plug-in project. The name is the name of the Visual Studio project. By default, it's also the name of the assembly.

    :::image type="content" source="../media/businessevents_PowerPlatformToolsCreateNewItems.png" alt-text="Screenshot of Adding a plug-in project in the Create New Items dialog box.":::

1. Select **Done**.

For more information about how to use the Power Platform Tools extension to create a project, see [Quickstart: Create a Power Platform Tools project](/powerapps/developer/data-platform/tools/devtools-create-project).

### Sign the assemblies

You must sign Dataverse assemblies. You can set up a self-signed key in the solution or provide another key if you have one available. To create a self-signed key, follow these steps:

1. In Visual Studio, in Solution Explorer, select and hold (or right-click) the project name, and then select **Properties**.
1. On the **Signing** tab, select the **Sign the assembly** checkbox.
1. In the **Choose a strong name key file** field, select **New**.
1. Enter a name and password for the key, and then select **OK**.

## Subscribe to a finance and operations apps event

After you finish setting up the development environment, you can begin to write code. Create a C# class library that runs business logic in Dataverse when a finance and operations apps business event or data event that the plug-in subscribes to occurs.

### Register a new step

1. In Visual Studio, on the **View** menu, select **Power Platform Explorer**.

    Power Platform Explorer shows a list of components from the Dataverse environment that you selected during the setup of the development environment. These components include tables, choices, and event catalogs.

1. Under the **Event Catalog** node, expand **finance and operations**.

    Under the **finance and operations** node, you see a list of catalogs that are available in the **Dynamics 365 ERP Virtual Entities** solution in the selected Microsoft Power Platform environment. Under each catalog, you see a list of the virtual entities that are generated for that category in the environment, and the data events that are available for each of those virtual entities (**Created**, **Updated**, and **Deleted**). 

    (If you don't see any catalogs under the **finance and operations** node, you might have to generate and enable the virtual entities that are required for your solution. For more information about how to generate virtual entities in a Dataverse environment, see [Enable Microsoft Dataverse virtual entities](../../power-platform/enable-virtual-entities.md). After you enable the required virtual entities, select **Refresh** in Power Platform Explorer to update the list so that it shows the entities.)

    Under each catalog, under the **Global** node, you see all the finance and operations apps business events that are activated for the category.

1. Select and hold (or right-click) the data event under the virtual entity that triggers your business logic, and then select **Add Plugin**.

    :::image type="content" source="../media/businessevents_RegisterWorkerPlugin.png" alt-text="Screenshot of Adding a plug-in for the OnExternalCreated event of the Worker entity in Power Platform Explorer.":::

1. In the **Register New Step** dialog box, follow these steps:

    1. In the **Class Name** field, change the value to the name of the class that you want to create.
    1. Under **Event Pipeline Stage of Execution**, select **PostOperation** in the drop-down list.
    1. Under **Execution Mode**, select the **Asynchronous** option.
    1. Select **Register New Step**.

    > [!NOTE]
    > The **PreValidation** and **PreOperation** execution stages and the **Synchronous** execution mode aren't currently supported for virtual entities.

    :::image type="content" source="../media/businessevents_PowerPlatformToolsRegisterNewStep.png" alt-text="Screenshot of Registering a new step for your plug-in in the Register New Step dialog box.":::

When you register the new step, a new class is generated that has the base code for the plug-in. In the **ExecuteCdsPlugin** method of the new class, you write the custom business logic in the place that is indicated by the **TODO**. You can then build your solution and deploy the plug-in to your environment.

## Deploy the plug-in

Deploy your plug-in to the Microsoft Power Platform solution.

- In Visual Studio, in Solution Explorer, select and hold (or right-click) the project, and then select **Deploy**.

To verify that deployment is successful, view the plug-in assembly in the Power Apps maker portal. Go to the Microsoft Power Platform solution that you deployed the plug-in to. In the navigation on the left, select **Plug-in assemblies**. To view the registered plug-in step, select **Plug-in steps** in the navigation.

:::image type="content" source="../media/businessevents_PowerPlatformToolsPluginAssemblies.png" alt-text="Screenshot of Plug-in assemblies in the Power Apps maker portal.":::

You can also verify that the new endpoint appears correctly on the **Endpoints** tab of the **Business events** page in the finance and operations app, and that the new event appears on the **Active events** tab.

:::image type="content" source="../../media/businessevents_PowerPlatformToolsFinOpsEvents.png" alt-text="Screenshot of Dataverse events on the Active events tab of the Business events page.":::

## Troubleshooting

If deployment fails, troubleshoot the issue by turning on verbose logging.

1. In Visual Studio, on the **Tools** menu, select **Options**.
1. In the **Options** dialog box, under the **Power Platform Tools** node, select **General**.
1. Select **Display Detailed Log Data** and **(Diagnostics) Capture Detailed Dataverse Communications Log**.
1. Select **OK**.

