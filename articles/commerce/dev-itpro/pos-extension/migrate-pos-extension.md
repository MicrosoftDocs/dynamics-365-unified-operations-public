---
title: Migrate a POS extension to the independent-packaging model
description: This topic explains how to migrate POS extensions to the independent-packaging model.
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 04-13-2020
ms.dyn365.ops.version: AX 10.0.18
---

# Migrate a POS extension to the independent-packaging model

[!include [banner](../../../includes/banner.md)]

This topic applies to the Retail SDK version 10.0.18 and later.

The independent-packaging model in the Retail SDK provides a significantly updated and improved developer experience for Dynamics 365 Commerce extension development. The independent-packaging model in the Retail SDK creates greater separation between the Retail SDK and the extension being developed. The SDK is composed of a set of NuGet packages that contain artifacts to enable Commerce development. Due to the scope of changes in the independent-packaging model, there are a few changes that required. Converting customizations to use the independent-packaging model requires a code migration that is slightly more work than a standard version update. This topic explains the benefits and changes of the independent-packaging model. It also provides a high-level set of steps to convert existing Point of Sale (POS) extensions to the independent-packaging model.

## Benefits of the independent-packaging model in the Retail SDK

### No code merge required when updating to the latest version

With the legacy Retail SDK, the design and distribution method required a code merge to update to the latest version of the Commerce components. The code merge was a time-consuming upgrade process, you had to maintain the full Retail SDK in the repo, and you had to compile the core POS.App project. Using the independent-packaging model, you have to maintain only your extension. Updating to the latest Retail SDK is as simple as updating the NuGet package version your project is consuming.

### Simplified consumption of custom headless Commerce APIs

Another one of the pain points with the legacy Retail SDK was the generation of the TypeScript proxy needed to consume headless Commerce APIs in Point of Sale. With the independent-packaging model, we have simplified this process to automatically generate the TypeScript code for the data service requests and entities. The TypeScript proxy for POS will be automatically generated when building your POS extension project, removing the need to manually run the CommerceProxyGenerator and copy the files.

### Automated packaging and configuration of Commerce Runtime and Hardware Station extensions for MPOS

Another improvement in the independent-packaging model is that much of the configuration and packaging has been automated and is generated automatically when your solution is built. Two examples are the automatic generation of extension configuration files for offline and dedicated hardware station. The offline and dedicated hardware station assemblies are also automatically included in your MPOS package during the build, removing the need to manually update the **Customization.settings** file.

### Improved build times

When using the the independent-packaging model, generating a deployable package only requires building your Commerce extension solution. This design greatly reduces the build time during extension development and packaging.

### Modern POS framework and system requirement changes

To enable Modern POS to support the independent packaging model, the POS framework is enhanced to utilize the Microsoft Windows optional package extension model. Modern POS and optional packages are only supported in the Windows Versions listed.

+ Windows 10 version 1809 or later
+ Windows Server 2019 or later

## POS API and SDK changes

### Removal of Pos.UI.Sdk library

With the migration to the independent-packaging model we have removed the **Pos.UI.Sdk** library which was dependent on **Knockout.js**. In it's place is a library-agnostic design to use POS controls within extensions. This lets you choose which UI library you want to use when developing extensions, while maintaining a consistent look and feel throughout the application. For more information, see [POS controls in extensions](controls-pos-extension.md).

### Knockout.js changes

One of the biggest changes to the POS APIs in the sealed extensibility model was the removal of all references to **Knockout.js** in the POS contracts.

+ You will notice that the POS UI SDK library has been replaced with **Consume** APIs for POS controls under **PosApi/Consume/Controls**. For more information on how to develop extensions that utilize POS controls, see [POS controls in extensions](controls-pos-extension.md).
+ The **knockout.d.ts** file has been removed from the SDK, so the global **ko** variable is not available to extensions. To use **Knockout.js** in your POS extensions, see [Use knockout.js in POS extensions](knockout-pos-extension.md).

### <a id="custom-view"></a>Changes when creating a custom view

To provide a more maintainable and intuitive way to create extension views, we have replaced the **ExtensionViewControllerBase** class with a new base class for custom views called **CustomViewControllerBase**. The new class provides the same functionality in a more maintainable way. Extension views that derive from **ExtensionViewControllerBase** are not supported using the independent-packaging model and will not be loaded. The key difference between **ExtensionViewControllerBase** and the new **CustomViewControllerBase** is that with the independent-packaging model the header and navigation bars will be automatically displayed to simplify the extension development experience. For more information, see [Create a custom view in POS](custom-pos-view.md).

### Extension loading changes

To use extension packages that are independently distributed and serviced changed how packages are discovered for loading. POS no longer relies on a single **extensions.json** file to list all the extension packages to be loaded. That approach was incompatible with independent-packaging model. In the independent-packaging model, POS calls the headless Commerce Engine to get the list of extension packages that should be loaded. For more information, see [Configuring extension packages](pos-extension-basics.md#configuring-extension-packages)

## Code migration steps

To migrate existing POS extensions from the **Pos.Extensions** project in the Retail SDK to the independent-packaging model, follow these steps.

1. Complete the steps in [Create a POS extension package project](create-pos-extension-package.md).

2. Copy the content of your extension package directory from the **Pos.Extensions** project in the Retail SDK to the root directory of the project created in the previous steps.
    + Copy only the source files for your extension package and exclude any build artifacts that might be present in the source directory.
    + When you are done, you should have a **manifest.json** file in the project root directory.

3. Change the reference to the POS Extension Manifest Schema. To do this, update the `$schema` line in **manifest.json** to:

    ```json
    "$schema": "./devDependencies/schemas/manifestSchema.json"
    ```

4. Required only if using Pos.UI.Sdk: Convert all references to the Pos.UI.Sdk library. The Pos.UI.Sdk library is not supported in independent-packaging, which has a different way of using POS controls in extensions.

    1. In Visual Studio, do a global search for **PosUISdk**.
    2. For each reference to **PosUISdk**, replace the usage of the POS UI SDK control with the new approach to use POS controls from **PosApi/Consume/Controls**. For instructions how to make these updates, see [POS controls in extensions](controls-pos-extension.md).
    3. Search the solution again for **PosUISdk** to confirm that all uses have been updated.

5. Required only if using **Knockout.js**: Update all references to **Knockout.js** to use a copy of the library included in your extension package instead of relying on the global instance used in POS. For more information, see [Use knockout.js in POS extensions](knockout-pos-extension.md).

6. Convert all references to **ExtensionViewControllerBase** to **CustomViewControllerBase**. For more information, see the section [Changes when creating a custom view](#custom-view)
    + Please see “Custom ViewController class change” section for more details

7. Build your POS extension project and verify that it builds successfully.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
