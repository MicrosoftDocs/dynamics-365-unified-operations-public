---
title: Migrate a POS extension to the independent packaging model
description: This article explains how to migrate Point of Sale (POS) extensions to the independent packaging model.
author: josaw1
ms.date: 04/13/2021
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-04-13
ms.dyn365.ops.version: AX 10.0.18
---

# Migrate a POS extension to the independent packaging model

[!include [banner](../../../includes/banner.md)]

This article applies to version 10.0.18 and later of the Retail software development kit (SDK).

The independent packaging model in the Retail SDK provides an updated and improved developer experience for the development of Microsoft Dynamics 365 Commerce extensions. The independent packaging model creates more separation between the Retail SDK and the extension that is being developed. The Retail SDK consists of a set of NuGet packages. These packages contain artifacts that enable Commerce development. Because of the scope of changes in the independent packaging model, a few changes are required. Conversion of customizations so that they use the independent packaging model requires a code migration that takes slightly more work than a standard version update.

This article explains the benefits and changes of the independent packaging model. It also provides a high-level set of steps for converting existing Point of Sale (POS) extensions to the independent packaging model.

## Benefits of the independent packaging model in the Retail SDK

### No code merge is required when you update to the latest version

In earlier versions of the Retail SDK, the design and distribution method required a code merge to update to the latest version of the Commerce components. The code merge was a time-consuming upgrade process, you had to maintain the full Retail SDK in the repository (repo), and you had to compile the core **POS.App** project. By using the independent packaging model, you must maintain only your extension. The process of updating to the latest version of the Retail SDK is as easy as updating the version of the NuGet package that your project consumes.

### Simplified consumption of custom headless Commerce APIs

In earlier versions of the Retail SDK, generation of the TypeScript proxy had to consume headless Commerce APIs in POS. In the independent packaging model, the TypeScript code for data service requests and entities is now automatically generated. Therefore, the process is simpler. Because the TypeScript proxy for POS is automatically generated when you build your POS extension project, you don't have to manually run CommerceProxyGenerator and copy the files.

### Automated packaging and configuration of Commerce runtime and Hardware station extensions for Modern POS

In the independent packaging model, much of the configuration and packaging has been automated, and is automatically generated when your solution is built. For example, extension configuration files are automatically generated for offline and dedicated Hardware station. Additionally, the assemblies for offline and dedicated Hardware station are automatically included in your Modern POS package during the build. Therefore, you don't have to manually update the **Customization.settings** file.

### Improved build times

In the independent packaging model, generation of a deployable package requires only that you build your Commerce extension solution. This design greatly reduces the build time during extension development and packaging.

### Modern POS framework and system requirement changes

To enable Modern POS to support the independent packaging model, the POS framework has been enhanced so that it uses the Windows optional package extension model. Modern POS and optional packages are supported only in the following Windows versions:

+ Windows 10 version 1809 or later
+ Windows Server 2019 or later

## POS API and SDK changes

### Removal of the Pos.UI.Sdk library

During the migration to the independent packaging model, Microsoft removed the **Pos.UI.Sdk** library, which was dependent on **Knockout.js**. In its place is a library-agnostic design that lets you use POS controls in extensions. When you develop extensions, you can choose which user interface (UI) library you want to use. At the same time, you can maintain a consistent look and feel throughout the application. For more information, see [Use POS controls in extensions](controls-pos-extension.md).

### Knockout.js changes

One of the biggest changes to the POS APIs in the sealed extensibility model was the removal of all references to **Knockout.js** in the POS contracts.

+ The POS UI SDK library has been replaced with **Consume** APIs for POS controls. You can find these APIs under **PosApi/Consume/Controls**. For more information about how to develop extensions that use POS controls, see [Use POS controls in extensions](controls-pos-extension.md).
+ The **knockout.d.ts** file has been removed from the SDK. Therefore, the global **ko** variable isn't available to extensions. For information about how to use **Knockout.js** in your POS extensions, see [Use Knockout.js in POS extensions](knockout-pos-extension.md).

### <a id="custom-view"></a>Changes when you create a custom view

To make the process of creating extension views more maintainable and intuitive, Microsoft has replaced the **ExtensionViewControllerBase** class with a new base class for custom views, **CustomViewControllerBase**. The new class provides the same functionality but in a more maintainable way. In the independent packaging model, extension views that are derived from **ExtensionViewControllerBase** aren't supported and won't be loaded. The main difference between the new **CustomViewControllerBase** class and the **ExtensionViewControllerBase** class is that, when the independent packaging model is used, the header and navigation bars are automatically shown. Therefore, the extension development experience is simplified. For more information, see [Create a custom view in POS](custom-pos-view.md).

### Extension loading changes

If you used extension packages that are independently distributed and serviced, POS relied on a single **extensions.json** file to list all the extension packages that had to be loaded. However, that approach was incompatible with the independent packaging model. In the independent packaging model, POS calls the headless Commerce engine to get the list of extension packages that should be loaded. For more information, see [Configuring extension packages](pos-extension-basics.md#configuring-extension-packages).

## Code migration steps

To migrate existing POS extensions from the **Pos.Extensions** project in the Retail SDK to the independent packaging model, follow these steps.

1. Follow the steps in [Create a POS extension package project](create-pos-extension-package.md).
2. Copy the content of your extension package directory from the **Pos.Extensions** project in the Retail SDK to the root directory of the project that you created in the previous step.

    + Copy only the source files for your extension package. Exclude any build artifacts that might be present in the source directory.
    + When you've finished, you should have a **manifest.json** file in the project root directory.

3. In the **manifest.json** file, change the reference to the POS Extension Manifest Schema by updating the `$schema` line as shown here.

    ```json
    "$schema": "./devDependencies/schemas/manifestSchema.json"
    ```

4. **Required only if you're using Pos.UI.Sdk:** Convert all references to the **Pos.UI.Sdk** library. The independent packaging model doesn't support the **Pos.UI.Sdk** library but has a different way to use POS controls in extensions.

    1. In Visual Studio, do a global search for **PosUISdk** in the solution.
    2. For each reference to **PosUISdk**, replace the use of the POS UI SDK control with the approach that uses POS controls from **PosApi/Consume/Controls**. For information about how to complete this step, see [Use POS controls in extensions](controls-pos-extension.md).
    3. Do another global search for **PosUISdk** to confirm that all uses of POS UI SDK controls have been replaced.

5. **Required only if you're using Knockout.js:** Update all references to **Knockout.js** so that they use a copy of the library that is included in your extension package instead of the global instance that is used in POS. For more information, see [Use Knockout.js in POS extensions](knockout-pos-extension.md).
6. Convert all references to **ExtensionViewControllerBase** to **CustomViewControllerBase**. For more information, see the [Changes when you create a custom view](#custom-view) section earlier in this article.
7. Build your POS extension project, and verify that it's successfully built.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
