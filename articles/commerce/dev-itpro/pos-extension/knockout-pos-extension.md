---
# required metadata

title: Use Knockout.js in POS extensions
description: This topic walkthrough how to use Knockout.js in POS extensions.
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

# Use Knockout.js in POS extensions

[!include [banner](../../../includes/banner.md)]

This topic walkthrough some of the basic of using Knockout.js in POS extensions, this topic applies to Retail software development kit (SDK) version 10.0.18 and later.

1.	Add a Nuget Package Reference for the Knockout.js library to your Pos.Extensions project
2.	Add a MSBuild target to copy the knockout library to your project directory during the build and content include it in your package.

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

3.	Add the knockout library as a dependency in your package’s manifest.json file
    + Update the manifest.json to add a new entry in the “dependencies” array for Knockout library.
        + **Note:** The “modulePath” should match the “KnockoutjsFile” variable in the target shown above.
        
```JSON
"dependencies": [
    {
      "alias": "knockout",
      "format": "amd",
      "modulePath": "Libraries/knockout"
    }
]
```
4.	Update your Pos.Extensions project file to include the Knockout.js type declarations.
      + Access knockout official releases.
      + Download the source code (zip) of the version that was included as a dependency in the manifest.json.
      + Extract the content of the zip file. The types are localted at <KNOCKOUT_LIBRARY_FOLDER>\build\types\knockout.d.ts.
      + Copy the knockout.d.ts file to any folder in the extension project
      + Update your tsconfig.json file to include a paths alias for Knockout.js. 
          + Note: You should replace “Libraries/knockout” in the snippet below with the relative path to where you copied the knockout.d.ts file in the previous step.

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
   f. Include the knockout.d.ts file in the project in case it wasn't included automatically and check it in to your source control system.

5.	Create an ApplicationStart trigger to register the “__posStopExtensionsBinding” handler to prevent collisions between the package’s version of Knockout.js and others that might be loaded in POS.
a.	An example is available in our PosSamples.
6.	Use Knockout.js in your extension modules by importing the library as shown here and in the snippet below.

```TypeScript
import ko from "knockout"; // The name of the import 'knockout' must match the one in the tsconfig and manifest file.
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
