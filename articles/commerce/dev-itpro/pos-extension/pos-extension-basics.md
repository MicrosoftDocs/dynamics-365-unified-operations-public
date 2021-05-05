---
title: POS extension basics
description: This topic describes the basic POS extension concepts.
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

# POS extension basics

[!include [banner](../../../includes/banner.md)]

This topic describes the basic POS extension concepts. It to the Retail SDK version 10.0.18 and later.

POS lets extension developers create customizations by using the POS API library.  The POS APIs let you customize both business logic and UI layers of POS.

## Terminology

These terms are used in this topic.

Term | Definition | Examples
---|---|---
Extension point | A specific location at which POS can be extended, or a technique through which new functionality can be added to POS. | **PreOperationTrigger** invocation point.<br>Adding a new view.
Extension | An individual component that helps to customize POS by utilizing a specific extension point. | New operation<br>New view<br>**PreOperationTrigger** implementation
Extension package | A set of extensions that when combined enable a custom end-to-end POS scenario. | A package that contains an operation that navigates to a new view.

## Types of Extensions

POS extensions can be classified into two types.

+ *Extend* extensions modify POS functionality by modifying existing pages or workflows.
+ *Create* extensions supplement POS and create new functionality by introducing new pages or workflows that do not exist out of the box.

The distinction between *extend* and *create* extensions is incorporated throughout the POS extensibility framework. When you are developing an extension, it can be helpful to think: “Am I extending an existing POS component or creating entirely new functionality?”

## POS API

The POS API library contains a set of modules that are organized based on how the module will be used by the extension.

+ **Extend**
    + Modules that help extensions extend POS components and workflows.
    + Subdirectories are organized based on the type of component to be extended and then the feature area to be extended.
    + Examples: **PosApi/Extend/Views/CustomerDetailsView**, **PosApi/Extend/Triggers/ProductTriggers**

+ **Create**
    + Modules that help extensions create new components and functionality.
    + Subdirectories under this node are organized based on the type of component to be created.
    + Example: **PosApi/Create/Views**

+ **Consume**
    + Modules that allow extensions to execute POS functionality.

The complete list of APIs and the type declarations for the modules in the POS API library can be found in **Pos.Api.d.ts**, which is distributed with the **Microsoft.Dynamics.Commerce.Sdk.Pos** NuGet package.

## Manifest.json

Each extension package must have a **manifest.json** file in the extension package's root directory. This manifest file contains important information about the extension package and defines the list of extensions contained in the package. The manifest file must follow the manifest schema that is provided in the **Microsoft.Dynamics.Commerce.Sdk.Pos** NuGet package for POS to load the extensions.

### Fields

These fields are contained in the manifest file.

+ **name** - The name of the extension package.
+ **description** - A description of the extension package's functionality.
+ **publisher** - The name of the extension package's publisher or organization.
+ **version** - The extension package version. The version must follow semantic versioning pattern.
+ **minimumPosVersion** - The minimum POS version that is required to run the extension package. The version number depends on the POS NuGet package that you're consuming and the POS app that is installed. For example, the extension project should not use POS APIs or extension artifacts from a version that is later than the version of the POS app that is installed. At runtime, the POS app checks the version of the extension package. If it's later than the version of the installed POS app, the extension package won't be loaded.
+ **supportedCountryRegions** - The optional list of country region codes in which to load the extension package. If this value is not specified, then the extension package will be loaded regardless of the current POS country region.
+ **components** - The list of extensions contained in the extension package.

Here is an example of a manifest file.

```json
{
    "$schema": "./devDependencies/schemas/manifestSchema.json",
    "name": "Contoso.Pos.Developer.Samples",
    "publisher": "Contoso",
    "version": "1.0.0",
    "minimumPosVersion": "9.28.0.0",
    "description": "An extension package containing POS developer samples to showcase various types of POS extensions.",
}
```

### Extension structure

Each POS extension is contains of one or more TypeScript modules. Extension classes must inherit from the applicable base class exposed from the POS API. The components and types in the POS API can be imported into the extension module using a non-relative import of a POS API module, as shown in the following code example.

```JavaScript
import { ApplicationStartTrigger } from “PosApi/Extend/Triggers/ApplicationTriggers”;
```

Each extension module should contain a single, default export of the extension class as shown in the following code example.

```JavaScript
import { ApplicationStartTrigger } from “PosApi/Extend/Triggers/ApplicationTriggers”;
export default class MyCustomApplicationStartTrigger extends ApplicationStartTrigger {
    public execute(options): Promise<void> {
        return Promise.resolve();
    }
}
```

### Configuring Extension Packages

POS loads the list of configured extension package definitions from the headless Commerce engine by calling the **GetExtensionPackageDefinitions** API. The **GetExtensionPackageDefinitions** API runs the **GetExtensionPackageDefinitions** Commerce Runtime request. To configure POS to load your extension package, add a Commerce Runtime trigger for the **GetExtensionPackageDefinitionsRequest** and add your extension package definition to the list of definitions in the **GetExtensionPackageDefinitionsResponse** as shown in the following code example.
The fields in **ExtensionPackageDefinition** must match the values used when creating the POS extension package.

+ **Name** - The name must match the **PackageName** for the extension package project. The name is used to locate and load the POS extension package so the values must match exactly.
+ **Publisher** - The publisher must match the publisher specified in the extension package’s manifest.json.

```CSharp
/// <summary>
/// Class that implements a post trigger for the GetExtensionPackageDefinitionsRequest request type.
/// </summary>
public class DefinePosExtensionPackageTrigger : IRequestTrigger
{
    /// <summary>
    /// Gets the supported requests for this trigger.
    /// </summary>
    public IEnumerable<Type> SupportedRequestTypes
    {
        get
        {
            return new[] { typeof(GetExtensionPackageDefinitionsRequest) };
        }
    }

    /// <summary>
    /// Post trigger to retrieve extension package.
    /// </summary>
    /// <param name="request">The request.</param>
    /// <param name="response">The response.</param>
    public void OnExecuted(Request request, Response response)
    {
        var getExtensionsResponse = (GetExtensionPackageDefinitionsResponse)response;
        var extensionPackageDefinition = new ExtensionPackageDefinition();

        // Should match the PackageName used when packaging the customization package.
        extensionPackageDefinition.Name = "Contoso.Commerce";
        extensionPackageDefinition.Publisher = "Contoso";
        extensionPackageDefinition.IsEnabled = true;

        getExtensionsResponse.ExtensionPackageDefinitions.Add(extensionPackageDefinition);
    }

    public void OnExecuting(Request request)
    {
    }
}
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
