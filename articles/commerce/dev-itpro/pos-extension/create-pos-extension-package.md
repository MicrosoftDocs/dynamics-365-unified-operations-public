---
title: Create a POS extension package project 
description: This topic explains how to Create a POS extension package project.
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

# Create a POS extension package project

[!include [banner](../../includes/banner.md)]

The steps in this document describe how to create a POS extension package project, a set of extensions that when combined enable a custom end to end POS scenario using Visual Studio. POS extension package projects apply to both Modern POS and Cloud POS extension scenarios.

1. In Visual Studio, create a new .NET Standard Class Library Project with .NET Standard 2.0 and name it **POS.Extensions**.
2. Delete the class file that is created with the project.
3. Create a shared properties file (XML file) to be used by all projects in the customization package. This shared file can be used for different Commerce extensions including CRT, Retail Server, and Hardware Service. Name the file **CustomizationPackage.props**. (You can choose another name for the file.)

    1. Add the file to the same directory as the solution file created in the previous step.
    2. Add the following property values to the file:

        + **PackagePublisher**: The package publisher identity, for example, `CN=Contoso Ltd.`. If the package contains ModernPos extensions, this value must match the subject of the app signing certificate.
        + **PackagePublisherDisplayName**: The display name of the package publisher, for example, `Contoso Ltd.`.
        + **PackageVersion**: The customization package version. This must be a version string in quad notation where the major version is not 0, for example, `1.0.0.0`.
        + **PackageName**: The package name. This must be a string between 3 and 50 characters in length that consists of alpha-numeric and period or dash characters. The string cannot end in a period.
        + **PackageDisplayName**: The package display name.
        + **PackageDescription**: The package description.

    3. The Xml file looks like the following example:

        ```xml
        <Project>
          <PropertyGroup>
            <Version>1.0.0.0</Version>
            <PackagePublisher Condition="'$(PackagePublisher)' == ''">$(Publisher)</PackagePublisher>
            <PackagePublisherDisplayName Condition="'$(PackagePublisherDisplayName)' == ''">$(PublisherDisplayName)</PackagePublisherDisplayName>
            <PackageVersion Condition="'$(PackageVersion)' == ''">$(Version)</PackageVersion>
            <PackageName Condition="'$(PackageName)' == ''">Contoso.Commerce</PackageName>
            <PackageDisplayName Condition="'$(PackageDisplayName)' == ''">Contoso POS Commerce Customization</PackageDisplayName>
            <PackageDescription Condition="'$(PackageDescription)' == ''">Contoso POS Commerce Customization</PackageDescription>
          </PropertyGroup>
        </Project>
        ```

4. Edit the project file and add the **Import** statement to include the customization package **props** file created in the step above.

    ```xml
    <Import Project="..\CustomizationPackage.props" />
    ```

5. Enable TypeScript support for the project.

    1. Right-click the project Solution Explorer and select **Manage NuGet packages**.
    2. Select the **Browse** tab in the NuGet Package Manager window.
    3. Search for **Microsoft.TypeScript.MSBuild**.
    4. Select the package and select **Install**, then select the latest stable version.

        > [!TIP]
        > For the best IDE experience, make sure that the TypeScript Tools for Visual Studio version you have installed matches the TypeScript NuGet package version. If you selected Microsoft.TypeScript.MSBuild version 4.2.3, then you can install the Typescript 4.2.3 for Visual Studio.
        > Links for the Visual Studio Typescript tool can be found here: [Releases · microsoft/TypeScript (github.com)](https://github.com/microsoft/TypeScript/releases)

6. Add a reference to the Retails SDK NuGet Package.

    1. Right-click the project Solution Explorer and select **Manage NuGet packages**.
    2. Select the **Browse** tab in the NuGet Package Manager window.
    3. Search for **Microsoft.Dynamics.Commerce.Sdk.Pos**.
    4. Select the package and then select **Install**.

        > [!TIP]
        > All the Commerce NuGet packages can be found from this public repository:
        > [https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/nuget/v3/index.json](https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/nuget/v3/index.json).

    5. Add the package source location to the **nuget.config** file of your extension project file. (Create a new nuget.config file for your project if it’s not created already).

        ```xml
        <packageSources>
            <add key="dynamics365-commerce" value="https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/nuget/v3/index.json" />
            <add key="nuget.org" value="https://api.nuget.org/v3/index.json" />
            </packageSources>
        ```

7. Add a **tsconfig.json** file to your project, by following these steps:

    1. Right-click the project Solution Explorer and select **Add** and then **New item**.
    2. Search for **json** and select **TypeScript JSON Configuration File**. Name the file **tsconfig.json**, and then select **Add**.

        ![tsconfig.json](media/json-file.png)

    3. Remove all the fields from the JSON and make it extend from the **pos-tsconfig-base** **tsconfig** file by adding an **extends** field. The Xml file will look like the following example:

        ```JSON
        {
            "extends": "./devDependencies/pos-tsconfig-base.json"
        }
        ```

8. Build the project to copy the POS dependencies to the project directory.

9. Create the manifest file for your extension package.

    1. Right-click the project Solution Explorer and select **Add** and then **New item**.
    2. Search for **json** and select **JSON File**. Name the file **manifest.json**, and then select **Add**.
    3. Add the reference to the **POS Extension Manifest Schema** by adding the following JSON as the first line in **manifest.json**:

        ```JSON
        {
            "$schema": "./devDependencies/schemas/manifestSchema.json"
        }
        ```

    4. Add the package information in your **manifest.json** file.

        + **name**: The name of the extension package.
        + **description**: A description of the extension package's functionality.
        + **publisher**: The name of the extension package publisher or organization.
        + **version**: The extension package version. This must follow semantic versioning pattern.
        + **minimumPosVersion**: The minimum POS version required to run this extension package. This version number depends on POS NuGet package you are consuming, and the POS application installed. For example, the extension project should not use POS APIs, extension artifacts from version higher than the POS app that is installed. During runtime, the the POS app will check the version of the extension package. If it's higher than the installed POS app, then the extension package will not be loaded.

        This is an exampl of the manifest file:

        ```JSON
        {
            "$schema": "./devDependencies/schemas/manifestSchema.json",
            "name": "Contoso.Pos.Developer.Samples",
            "publisher": "Contoso",
            "version": "1.0.0",
            "minimumPosVersion": "9.28.0.0",
            "description": "An extension package containing POS developer samples to showcase various types of POS extensions.",
        }
        ```

10. If your solution contains Commerce Runtime extension projects, then add project references to each of the Commerce Runtime extension projects in the solution.

    1. Right-click the Modern POS project Solution Explorer and select **Add** and then **New item**.
    2. Select the **Projects** tab on the left side of the Reference Manager.
    3. Select the Commerce Runtime extension projects.

11. After you have created all the base metadata for the extension, add your extension and update the **manifest.json** to include your extension. For information about developing the extension UI and logic, see the samples in[Dynamics365Commerce.InStore](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.28/src/PosSample/Pos.Extension).

After creating the extensions, you must package them to be deployed to Cloud POS or MPOS. For more information, see:

+ [Create a Modern POS extension appx file](create-pos-extension-appx.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
