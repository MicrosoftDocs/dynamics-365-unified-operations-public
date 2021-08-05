---
# required metadata

title: Download Retail SDK samples and reference packages from GitHub and NuGet
description: This topic explains to how to download Retail software development kit (SDK) samples from GitHub and reference packages from public feed.
author: mugunthanm
ms.date: 12/07/2020
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
ms.custom:
ms.assetid:
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2020-11-10
ms.dyn365.ops.version: 10.0.16
---

# Download Retail SDK samples and reference packages from GitHub and NuGet

[!include [banner](../../includes/banner.md)]

This topic explains to how to download Retail software development kit (SDK) samples from GitHub and reference packages from public feed. The Retail SDK includes the code samples, templates, and tools that are required to extend or customize Microsoft Dynamics 365 Commerce functionality. The SDK is published in different repositories (repos) in GitHub, depending on the extension components.

This topic applies to Retail SDK version 10.0.16 or later. For more information about how to download earlier versions of the Retail SDK, see [Retail software development kit (SDK)](retail-sdk-overview.md).

The below sample repo contains code samples, templates, and tools that are required to extend or customize existing Commerce functionality, samples are published into different repos in GitHub based on the Commerce extension components, its not required to clone these repos, if required download and consume the samples and template projects.

## Dynamics365Commerce.ScaleUnit repo:

The [Dynamics365Commerce.ScaleUnit](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit) repo contains the sample code for customizing the Commerce runtime (CRT), Retail Server, and the channel database.

The samples in the repo are organized by Dynamics 365 Commerce application release, each branch in the repo points to an application release of Dynamics 365 Commerce, use the right release branch based on your go-live version.

> [!Note]
> The repo contains only samples, so its not required to clone this repo.

| Release branch name                                                                          | version | Application release version |
| -------------------------------------------------------------------------------------------- | ------- | --------------------------- |
| [Release/9.26](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.26) | 9.26.\* | 10.0.16                     |
| [Release/9.27](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.27) | 9.27.\* | 10.0.17                     |
| [Release/9.28](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.28) | 9.28.\* | 10.0.18                     |
| [Release/9.29](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.29) | 9.29.\* | 10.0.19                     |
| [Release/9.30](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.30) | 9.30.\* | 10.0.20                     |
| [Release/9.31](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.31) | 9.31.\* | 10.0.21                     |


### Extension repository:

Extension code or repository if required can download and consume the samples and templates from [microsoft](https://github.com/microsoft)/[Dynamics365Commerce.ScaleUnit](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit), the sample scale unit repo contains nuget.config, repo.props, CustomizationPackage.props and build pipelines script which provide guidance on how extension can setup the repo metadata files.

### Dynamics365Commerce.ScaleUnit repo folders and projects:

| Folder                                                                     | Project                                                                                                           | Description                                                                                                                                          |
| -------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Channel Database](./src/ScaleUnitSample/ChannelDatabase)                  | [ChannelDatabase.csproj](./src/ScaleUnitSample/ChannelDatabase/ChannelDatabase.csproj)                            | This project contains samples on how to create Commerce Runtime database extensions.                                                                 |
| [CommerceRuntime](./src/ScaleUnitSample/CommerceRuntime)                   | [CommerceRuntime.csproj](./src/ScaleUnitSample/CommerceRuntime/CommerceRuntime.csproj)                            | Controller – Sample code for how to implement new RS APIs.Entities, Messages and RequestHandlers – Sample code for how to implement new CRT service. |
| [ScaleUnit](./src/ScaleUnitSample/ScaleUnit)                               | [ScaleUnit.csproj](./src/ScaleUnitSample/ScaleUnit/ScaleUnit.csproj)                                              | Sample project on how to generate the CSU                                                                                                            |
| [ScaleUnit.Installer](./src/ScaleUnitSample/Installer)                     | [ScaleUnit.csproj](./src/ScaleUnitSample/Installer/ScaleUnit.Installer.csproj)                                    | Sample project on how to generate the CSU installer.                                                                                                 |
| [POS](./src/ScaleUnitSample/POS)                                           | [POS.csproj](./src/ScaleUnitSample/POS/POS.csproj)                                                                | Contains samples on how to create POS extensions.                                                                                                    |
| [E-CommerceProxyGenerator](./src/ScaleUnitSample/E-CommerceProxyGenerator) | [E-CommerceProxyGenerator.csproj](./src/ScaleUnitSample/E-CommerceProxyGenerator/E-CommerceProxyGenerator.csproj) | Contains a sample on how to generate extension proxies for E-Commerce Application.                                                                   |

Samples for instore components like Modern POS, Cloud POS, Hardware station and Cloud scale unit – Self hosted are published in the [Dynamics365Commerce.InStore](https://github.com/microsoft/Dynamics365Commerce.InStore) repo.

Readme file inside the Commerce Runtime, ChannelDatabase and ScaleUnit contain more details on how to run the samples.

## Dynamics365Commerce.InStore repo:

The [Dynamics365Commerce.InStore](https://github.com/microsoft/Dynamics365Commerce.InStore) repo contains the sample code for how to customize the POS, HWS and Commerce runtime (CRT), Headless Commerce APIs and channel database.

The samples in the repo are organized by Dynamics 365 Commerce application release, each branch in the repo points to an application release of Dynamics 365 Commerce, use the right release branch based on your go-live version. 

> [!Note]
> The repo contains only samples, so its not required to clone this repo.

| Release branch name                                                                          | version | Application release version |
| -------------------------------------------------------------------------------------------- | ------- | --------------------------- |
| [Release/9.28](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.28) | 9.28.\* | 10.0.18                     |
| [Release/9.29](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.29) | 9.29.\* | 10.0.19                     |
| [Release/9.30](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.30) | 9.30.\* | 10.0.20                     |
| [Release/9.31](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.31) | 9.31.\* | 10.0.21                     |

### Extension repository:

Extension code or repository if required can download and consume the samples and templates from [microsoft](https://github.com/microsoft)/[Dynamics365Commerce.InStore](https://github.com/microsoft/Dynamics365Commerce.InStore), the sample InStore repo contains nuget.config, repo.props, CustomizationPackage.props and build pipelines script which provide guidance on how extension can setup the repo metadata files.

### Dynamics365Commerce.InStore repo folders and projects:

| Folder           | Project              | Description                                   |
| ---------------- | ---------------------| --------------------------------------------- |
| HardwareStationSample | HardwareStation.Samples.sln| This project contains samples on how to create Hardware station, Payment extensions and extension installers.|  
| POSSample  | Pos.sln | This folder/project contains POS, CRT, Headless Commerce APIs and HWS extension and installer samples. | 

More samples for CSU – self hosted and Commerce Runtime and Headless Commerce APIs are published in the [Dynamics365Commerce.ScaleUnit](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit) repo.

Readme files inside the project folder contains more details on how to run these samples.


## Dynamics365Commerce.Solutions repo:

The [Dynamics365Commerce.Solutions](https://github.com/microsoft/Dynamics365Commerce.Solutions) repo contains the sample that demonstrates how to perform E2E business scenario customization in Commerce, there may be scenarios where you may need to customize POS, e-Commerce and Headless commerce engine, the samples in these repos will be provide guidance on how to do E2E business scenario customization. 

## Download reference packages for creating APIs, and for consuming messages, request, entities, and contracts

Commerce contracts, messages, entities, and request packages are published in this public feed for commerce extension code to consume and customize existing functionalities or build new functionalities for Dynamics 365 Commerce product.

Consume the packages from [https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/nuget/v3/index.json](https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/nuget/v3/index.json). You can add the package source location in the nuget.config file of your extension project file.

```xml
<packageSources>
    <add key="dynamics365-commerce" value="https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/nuget/v3/index.json" />
    <add key="nuget.org" value="https://api.nuget.org/v3/index.json" />
    </packageSources>
```

## Reference packages that are available in the public feed

| Package name                            | Description |
| --------------------------------------- | ----------- | 
| Microsoft.Dynamics.Commerce.Sdk.ChannelDatabase | This package is required to generate the DB packages with CSU.  |
| Microsoft.Dynamics.Commerce.Sdk.Runtime | This meta package contains all the required packages for implementing the CRT and Retail Server extensions. All the required contracts, messages, requests/responses, and entities are included in this package. |
| Microsoft.Dynamics.Commerce.Sdk.ScaleUnit | This package is required to generate the CSU package for deployment. |
| Microsoft.Dynamics.Commerce.Sdk.Installers.ScaleUnit|  This package is required to generate the ScaleUnit package for deployment |
| Microsoft.Dynamics.Commerce.Sdk.HardwareAndPeripherals|  This package contains all commerce Hardware station and peripherals libraries |
| Microsoft.Dynamics.Commerce.Sdk.Installers| This package contains all the installers libraries |
| Microsoft.Dynamics.Commerce.Sdk.Installers.HardwareStation| This package is required to generate the Hardware station package for deployment  |
| Microsoft.Dynamics.Commerce.Sdk.Pos| This package contains all POS libraries |
| Microsoft.Dynamics.Commerce.Sdk.Installers.ModernPos| This package is required to generate the POS extension installer for deployment |
| Microsoft.Dynamics.Commerce.Diagnostics| This package contains all the diagnostic libraries |
| Microsoft.Dynamics.Commerce.Runtime.Data| This package contains all data contract libraries |
| Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages| This package contains all data services message libraries |
| Microsoft.Dynamics.Commerce.Runtime.Entities| This package contains all commerce entities definition |
| Microsoft.Dynamics.Commerce.Runtime.Framework| This package contains all commerce framework libraries |
| Microsoft.Dynamics.Commerce.Runtime.Hosting.Contracts| This package contains all commerce controller libraries |
| Microsoft.Dynamics.Commerce.Runtime.Messages| This package contains all commerce runtime messages libraries |
| Microsoft.Dynamics.Commerce.Runtime.RealtimeServices.Messages| This package contains all the commerce real runtime libraries |
| Microsoft.Dynamics.Commerce.Runtime.Services.Messages| This package contains all the commerce service messages libraries |
| Microsoft.Dynamics.Commerce.HardwareStation.Core| This package contains all the HWS libraries |
| Microsoft.Dynamics.Commerce.HardwareStation.PeripheralRequests| This package contains all the HWS peripherals request libraries |
| Microsoft.Dynamics.Commerce.HardwareStation.Peripherals.Contracts| This package contains all the HWS peripherals contracts libraries |
| Microsoft.Dynamics.Commerce.HardwareStation.Peripherals.Entities| This package contains all the HWS peripherals entities libraries |
| Microsoft.Dynamics.Commerce.Installers.Framework|  This package contains all the installers framework libraries |
| Microsoft.Dynamics.Commerce.KeyVault.Contracts| This package contains all the key vault contract libraries |
| Microsoft.Dynamics.Commerce.PaymentSDK.Extensions.Portable| This package contains all the payment extension libraries |
| Microsoft.Dynamics.Commerce.PaymentSDK.Portable| This package contains all the payment libraries  |
| Microsoft.Dynamics.Commerce.Runtime.FIF.Connector.Messages| This package contains all the FIF connector libraries  |
| Microsoft.Dynamics.Commerce.Runtime.FIF.DocumentProvider.Messages|  This package contains all the FIF document provider libraries   |
| Microsoft.Dynamics.Commerce.Installers.Framework.DatabaseExtensions| This package contains all the database installer framework libraries |
| Microsoft.Dynamics.Commerce.Tools.DbUtilities| This package contains all the DB utilities libraries |
| Microsoft.Dynamics.Commerce.Tools.ExtensionsProxyGenerator.AspNetCore | This package contains all the extensions proxy generator utilities  |
| Microsoft.Dynamics.Commerce.Proxy.ScaleUnit                           | This package contains all the proxies class for extension applications to consume the Headless Commerce APIs in online mode (connected to Headless Commerce). |

## Package versioning:

| Package version  | Application release      |
| ---------------- | ------------------------ |
| 9.28.x.x-preview | 10.0.18 PEAP release     |
| 9.28.x.x         | 10.0.18 Customer preview |
| 9.28.x.x         | 10.0.18 GA               |
| 9.29.x.x-preview | 10.0.19 PEAP release     |
| 9.29.x.x         | 10.0.19 Customer preview |
| 9.29.x.x         | 10.0.19 GA               |
| 9.30.x.x-preview | 10.0.20 PEAP release     |
| 9.30.x.x         | 10.0.20 Customer preview |
| 9.30.x.x         | 10.0.20 GA               |
| 9.31.x.x-preview | 10.0.21 PEAP release     |
| 9.31.x.x         | 10.0.21 Customer preview |
| 9.31.x.x         | 10.0.21 GA               |

An extension project can consume the correct version if you add the package reference to the project and include the full version number. Alternatively, to make the extension project always get the latest version, use a wildcard character. We recommend that you use the full version number, and that you update the version, based on your go-live version. There are two options:

+ Without a wildcard character:

    ```xml
    <PackageReference Include="Microsoft.Dynamics.Commerce.Sdk.Runtime" Version="9.28" />;
    ```

+ With a wildcard character:

    ```xml
    <PackageReference Include="Microsoft.Dynamics.Commerce.Sdk.Runtime" Version="9.28.*" />;
    ```

With every hotfix and new application release, new version of the package will be published in the same public feed, consume the right package version based on the version required for your go live. Consuming the higher version of the package than your go-live application version may result in runtime and deployment failures.


## Setup Azure DevOps pipeline for build automation and package generation:

[Set up a build pipeline for the independent-packaging SDK](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/build-pipeline)

## Best practice and branching strategies:

Detailed information on git branching strategy refer [Git branching strategy](https://docs.microsoft.com/en-us/azure/devops/repos/git/git-branching-guidance?view=azure-devops) doc.

The following branching strategies are based on the way we use Git here at Microsoft. For more information, see [How we use Git at Microsoft](https://docs.microsoft.com/en-us/azure/devops/learn/devops-at-microsoft/use-git-microsoft).

Keep your branch strategy simple. Build your strategy from these three concepts:

- Use feature branches for all new features and bug fixes.
- Merge feature branches into the main branch using pull requests.
- Keep a high quality, up-to-date main branch.

**Create a new feature branch for development and bug fixes:**

Create a new feature main branch for our extension, follow the proper naming convention (refer the [Git branching doc for sample naming convention](https://docs.microsoft.com/en-us/azure/devops/repos/git/git-branching-guidance?view=azure-devops#name-your-feature-branches-by-convention))

** Create a new development branch:**

Create a private branch for the development:

- git checkout -b private/{username}/{feature/description}

Add and commit new changes to the development branch using git -add . and git commit -m&quot; commit message.&quot;

After the development is completed, tested, and validated push the changes to the main branch by doing git push \&lt;remote\&gt; \&lt;branch\&gt;

- git push origin {private branch name}

**Create a release branch after development:**

After the development changes pushed into the main branch, create a new release branch, and create the deployable packages from the release branch.

- Git checkout -b release/x.x.x

Merge the changes from the release branch back to main branch if any changes done in the release branch.

```

- git checkout master git merge release/x.x.x

```

**Extension hotfix branch:**

Like release branch, create hotfix branch for extension from main branch and release the fix and later merge the changes back to the main branch.

**Merge new release branch to main and development branch:**

After a new version of the samples released, if required merge your development branch with the new branch. The repo contains only samples, so it&#39;s not required to always get the updated changes from the branch.

```

- git checkout master git merge release/x.x.x

```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
