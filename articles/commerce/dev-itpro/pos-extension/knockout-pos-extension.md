---
title: How to consume external or third party libraries like Knockout.js in POS extensions
description: This article explains how to consume external or third party libraries like Knockout.js in Point of Sale (POS) extensions.
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

# Consume external or third party libraries like Knockout.js in POS extensions

[!include [banner](../../../includes/banner.md)]

This article shows some basic steps on how to use **Knockout.js** in Point of Sale (POS) extensions, the same pattern can be applied to other external or third party libraries . It applies to version 10.0.18 and later of the Retail software development kit (SDK).

1. Add a NuGet package reference for the **Knockout.js** library to your **Pos.Extensions** project.
2. Add an MSBuild target to copy the knockout library to your project directory during the build and include it in your package. The following example shows the XML.

    ```XML
    <Target Name="ContentIncludeKnockoutLibrary" BeforeTargets="AssignTargetPaths" DependsOnTargets="RunResolvePackageDependencies">
        <PropertyGroup>
            <KnockoutjsFile>Libraries/knockout.js</KnockoutjsFile>
            <KnockoutLibraryFilePath Condition="'%(PackageDefinitions.Name)' == 'knockoutjs'">%(PackageDefinitions.ResolvedPath)\Content\Scripts\knockout-%(PackageDefinitions.Version).js</KnockoutLibraryFilePath>
        </PropertyGroup>
        <Copy SourceFiles="$(KnockoutLibraryFilePath)" DestinationFiles="$(KnockoutjsFile)" SkipUnchangedFiles="true" /> <!-- Necessary for CPOS -->
        <ItemGroup>
            <Content Include="$(KnockoutjsFile)"></Content>
        </ItemGroup>
    </Target>
    ```

3. Update your package's **manifest.json** file so that it includes the knockout library as a dependency. Add a new entry for the knockout library in the **dependencies** array.

    > [!NOTE]
    > The **modulePath** value must match the **KnockoutjsFile** variable in the MSBuild target that you added in the previous step.

    ```JSON
    "dependencies": [
        {
          "alias": "knockout",
          "format": "amd",
          "modulePath": "Libraries/knockout"
        }
    ]
    ```
> [!NOTE]
> If the external libraries depends on other libraries, include all the dependent libraries in the package manifest and msbuild target to copy the dependencies.

4. Update your **Pos.Extensions** project file so that it includes the **Knockout.js** type declarations.

    1. Go to the knockout official releases.
    2. Download the source code (zip file) of the version that you included as a dependency in the **manifest.json** file.
    3. Extract the contents of the zip file. The types are located at **\<KNOCKOUT\_LIBRARY\_FOLDER\>\\build\\types\\knockout.d.ts**.
    4. Copy the **knockout.d.ts** file to any folder in the extension project.
    5. Update your **tsconfig.json** file so that it includes a **paths** alias for **Knockout.js**.

        > [!NOTE]
        > Replace **Libraries/knockout** in the following code example with the relative path that you copied the **knockout.d.ts** file to in the previous step.

        ```JSON
        {
          "extends": "./devDependencies/pos-tsconfig-base.json",
          "compilerOptions": {
            "baseUrl": ".",
            "paths": {
              "knockout": [ "Libraries/knockout" ]
            },
            "noImplicitAny": false
          }
        }
        ```

    6. Include the **knockout.d.ts** file in the project if it wasn't automatically included, and check it in to your source control system.

5. Create an **ApplicationStart** trigger to register the **\_\_posStopExtensionsBinding** handler. In this way, you help prevent collisions between the package's version of **Knockout.js** and other versions that might be loaded in POS. An example is available in the [POS extension samples](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.28/src/PosSample/Pos.Extension).
6. Use **Knockout.js** in your extension modules by importing the library as shown in the following example.

    ```TypeScript
    import ko from "knockout"; // The name of the import 'knockout' must match the one in the tsconfig and manifest file.
    ```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
