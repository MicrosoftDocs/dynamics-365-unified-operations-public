---
title: POS extension basics
description: This article describes the basic concepts of point of Sale (POS) extension in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 05/28/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: anupamar
ms.search.validFrom: 2020-04-13
ms.custom: 
  - bap-template
---

# POS extension basics

[!include [banner](../../../includes/banner.md)]

This article describes the basic concepts of point of Sale (POS) extension in Microsoft Dynamics 365 Commerce. It applies to version 10.0.18 and later of the Retail software development kit (SDK).

Extension developers can create customizations by using the POS API library. The POS APIs let you customize both business logic and user interface (UI) layers of POS.

## Terminology

The following terms are used in this article.

| Term | Definition | Examples |
|---|---|---|
| Extension point | A specific location where POS can be extended, or a technique that can be used to add new functionality to POS. | <p>**PreOperationTrigger** invocation point</p><p>Addition of a new view</p> |
| Extension | An individual component that helps you use a specific extension point to customize POS. | <p>New operation</p><p>New view</p><p>**PreOperationTrigger** implementation</p> |
| Extension package | A set of extensions that, when they are combined, enable a custom end-to-end POS scenario. | A package that contains an operation that opens a new view |

## Types of extensions

POS extensions can be classified into two types:

+ *Extend* extensions modify POS functionality by modifying existing pages or workflows.
+ *Create* extensions supplement POS, and create new functionality by introducing new pages or workflows that don't exist out of the box.

The distinction between *extend* and *create* extensions is incorporated throughout the POS extensibility framework. When you're developing an extension, it can be helpful to ask yourself, "Am I extending an existing POS component or creating entirely new functionality?"

## POS API library

The POS API library contains a set of modules that are organized based on the way that the extension will use them.

+ **Extend**

    + These modules help extensions extend POS components and workflows.
    + Subdirectories are organized first by the type of component that will be extended and then by the feature area that will be extended.
    + Examples include **PosApi/Extend/Views/CustomerDetailsView** and **PosApi/Extend/Triggers/ProductTriggers**.

+ **Create**

    + These modules help extensions create new components and functionality.
    + Subdirectories are organized by the type of component that will be created.
    + An example is **PosApi/Create/Views**.

+ **Consume**

    + These modules enable extensions to run POS functionality.

For a complete list of APIs and the type declarations for the modules in the POS API library, see the **Pos.Api.d.ts** file that is distributed together with the **Microsoft.Dynamics.Commerce.Sdk.Pos** NuGet package.

## Manifest.json file

Each extension package must have a **manifest.json** file in the extension package's root directory. The manifest file contains important information about the extension package and defines the list of extensions in the package. The manifest file must follow the manifest schema that is provided in the **Microsoft.Dynamics.Commerce.Sdk.Pos** NuGet package. Otherwise, POS can't load the extensions.

### Fields

The manifest file contains the following fields:

+ **name** – The name of the extension package.
+ **description** – A description of the extension package's functionality.
+ **publisher** – The name of the extension package's publisher or organization.
+ **version** – The version of the extension package. The version must follow a semantic versioning pattern.
+ **minimumPosVersion** – The minimum POS version that is required to run the extension package. The version number depends on the POS NuGet package that you're consuming and the POS app that is installed. For example, the extension project should not use POS APIs or extension artifacts from a version that is later than the version of the POS app that is installed. At runtime, the POS app checks the version of the extension package. If it's later than the version of the installed POS app, the extension package won't be loaded.
+ **supportedCountryRegions** – The optional list of country/region codes to load the extension package in. If no value is specified for this field, the extension package will be loaded regardless of the current POS country or region.
+ **components** – The list of extensions in the extension package.

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

Each POS extension contains one or more TypeScript modules. Extension classes must inherit from the applicable base class that is exposed from the POS API. The components and types in the POS API can be imported into the extension module by using a non-relative import of a POS API module, as shown in the following example.

```JavaScript
import { ApplicationStartTrigger } from "PosApi/Extend/Triggers/ApplicationTriggers";
```

Each extension module should contain a single, default export of the extension class, as shown in the following example.

```JavaScript
import { ApplicationStartTrigger } from "PosApi/Extend/Triggers/ApplicationTriggers";
export default class MyCustomApplicationStartTrigger extends ApplicationStartTrigger {
    public execute(options): Promise<void> {
        return Promise.resolve();
    }
}
```

### Configuring extension packages

POS loads the list of configured extension package definitions from the headless Commerce engine by calling the **GetExtensionPackageDefinitions** API. The **GetExtensionPackageDefinitions** API runs the **GetExtensionPackageDefinitions** Commerce runtime (CRT) request. To configure POS to load your extension package, add a CRT trigger for **GetExtensionPackageDefinitionsRequest**, and add your extension package definition to the list of definitions in **GetExtensionPackageDefinitionsResponse**, as shown in the following example.

The fields in **ExtensionPackageDefinition** must match the values that were used when the POS extension package was created.

+ **Name** – The name is used to find and load the POS extension package. Therefore, it must exactly match the **PackageName** value for the extension package project. 
+ **Publisher** – The publisher must match the publisher that is specified in the extension package's **manifest.json** file.

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
