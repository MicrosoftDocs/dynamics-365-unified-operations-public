---
# required metadata

title: POS Extensibility basics
description: This topic walkthrough some of the basic POS concepts.
author: mugunthanm
ms.date: 04/13/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom: 28021
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 04-13-2020
ms.dyn365.ops.version: AX 10.0.18

---

# POS Extensibility basics

[!include [banner](../../../includes/banner.md)]

This topic walkthrough some of the basic POS concepts, this topic applies to Retail software development kit (SDK) version 10.0.18 and later.

POS enables extension developers to perform a wide variety of customizations through the POS API library.  The POS API provides ways for extensions to customize both business logic and UI layers of POS. 

### Terminology
+ **Extension Point:** A specific location at which POS can extended, or a technique through which new functionality can be added to POS
    + Ex. The PreOperationTrigger invocation point, adding a new view

+ **Extension:** An individual component that helps to customize POS by utilizing a specific extension point
    + Ex. A new operation, new view, a PreOperationTrigger implementation

+ **Extension Package:** A set of extensions that when combined enable a custom end to end POS scenario
    +  Ex. A package that contains an operation that navigates to a new

### Types of Extensions

At a high level POS extensions can be classified into two different types of extensions. Extensions that Extend existing POS functionality and extensions that Create entirely new functionality. Extend extensions modify POS by modifying existing pages or workflows. Create extensions supplement POS by introducing new pages or workflows that do not exist “out of the box”. The distinction between Extend and Create extensions is incorporated throughout the POS extensibility framework so when developing an extension it can be helpful to think: “Am I extending an existing POS component or creating entirely new functionality?”

### POS API

The POS API library contains a set of modules that are organized based on how the module will be used by the extension.

+ **Extend** – Modules that help extensions extend POS components and workflows.
    + Subdirectories are organized based on the type of component to be extended and then the feature area to be extended.
      Ex. “PosApi/Extend/Views/CustomerDetailsView”, “PosApi/Extend/Triggers/ProductTriggers”

+ **Create** – Modules that help extensions create new components and functionality.
    + Subdirectories under this node are organized based on the type of component to be created
      Ex. “PosApi/Create/Views”

+ **Consume**– Modules that allow extensions to execute POS functionality. 

The complete list of APIs and the type declarations for the modules in the POS API library can be found in Pos.Api.d.ts which is distributed with the Microsoft.Dynamics.Commerce.Sdk.Pos Nuget package.

### Manifest.json

Each extension package is required to have a manifest.json file in the extension packages root directory. This manifest file contains important information about the extension package and defines the list of extensions contained in the package. The manifest.json file must follow the manifest schema that is provided in the Microsoft.Dynamics.Commerce.Sdk.Pos Nuget package for POS to load the extensions.

## Fields:

+ **name:** The name of the extension package.
+ **description:** A description of the extension package's functionality.
+ **publisher:** The name of the extension package publisher or organization.
+ **version:** The extension package version. This must follow semantic versioning pattern.
+ **minimumPosVersion:** The minimum POS version required to run this extension package. This version number depends on POS NuGet package you are consuming, and the POS application installed. Ex: Extension project should not use POS APIs, extension artifacts from version higher than the POS App installed. During runtime, the POS Application will check the version of the extension package, if its higher than the installed POS Application then the extension package will not be loaded.
+ **supportedCountryRegions:** The optional list of country region codes in which to load the extension package. If this is not specified then the extension package will be loaded regardless of the current POS country region.
+ **components:** The node containing the list of extensions contained in the extension package.

```XML
Ex:
{
  "$schema": "./devDependencies/schemas/manifestSchema.json",
  "name": "Contoso.Pos.Developer.Samples",
  "publisher": "Contoso",
  "version": "1.0.0",
  "minimumPosVersion": "9.28.0.0",
  "description": "An extension package containing POS developer samples to showcase various types of POS extensions.",
}
```

### Anatomy of an Extension

Each POS extension is comprised of one or more TypeScript modules, and extension classes must inherit from the applicable base class exposed from the POS API.
The components and types in the POS API can be imported into the extension module using a non-relative import of a POS API module. 

```JavaScript
import { ApplicationStartTrigger } from “PosApi/Extend/Triggers/ApplicationTriggers”;
```
Each extension module should contain a single, default export of the extension class as shown below.

```JavaScript 
import { ApplicationStartTrigger } from “PosApi/Extend/Triggers/ApplicationTriggers”;
export default class MyCustomApplicationStartTrigger extends ApplicationStartTrigger {
    public execute(options): Promise<void> {
        return Promise.resolve();
    }
}
````
### Configuring Extension Packages

POS will load the list of configured extension package definitions from the Headless Commerce Engine by calling the GetExtensionPackageDefinitions API. The GetExtensionPackageDefinitions API will then execute the GetExtensionPackageDefinitions Commerce Runtime request. To configure POS to load your extension package you should add a Commerce Runtime Trigger for the GetExtensionPackageDefinitionsRequest and add your extension package definition to the list of definitions in the GetExtensionPackageDefinitionsResponse as shown in the code snippet below.
The fields in ExtensionPackageDefinition should match the values used when creating the POS extension package. 
•	Name: The value of this field should match the PackageName for the extension package project. 
o	This value is used to locate and load the POS extension package so the values must match exactly.
•	Publisher: The value of this field should match the publisher specified in the extension package’s manifest.json. 

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
