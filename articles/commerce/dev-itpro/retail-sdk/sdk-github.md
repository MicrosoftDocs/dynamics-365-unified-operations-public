---
# required metadata

title: Download Retail SDK samples and reference packages from GitHub and NuGet
description: This topic explains to how to download Retail software development kit (SDK) samples from GitHub and reference packages from NuGet.
author: mugunthanm
manager: AnnBe
ms.date: 11/04/2020
ms.topic: article
ms.prod:
ms.service: dynamics-365-commerce
ms.technology:

# optional metadata

# ms.search.form:
# ROBOTS:
audience: Developer
# ms.devlang:
ms.reviewer: rhaertle
# ms.search.scope: Operations, Retail
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

This topic explains to how to download Retail software development kit (SDK) samples from GitHub and reference packages from NuGet. The Retail SDK includes the code samples, templates, and tools that are required to extend or customize Microsoft Dynamics 365 Commerce functionality. The SDK is published in different repositories (repos) in GitHub, depending on the extension components.

This topic applies to Retail SDK version 10.0.16 or later. For more information about how to download earlier versions of the Retail SDK, see [Retail software development kit (SDK)](retail-sdk-overview.md).

## Commerce.ScaleUnit repo

The **Commerce.ScaleUnit** repo contains the sample code for customizing the Commerce runtime (CRT), Retail Server, and the channel database.

Clone or download the repo from [Dynamics365 Commerce ScaleUnit Samples](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit). To clone the **Commerce.ScaleUnit** repo, use the following command. (This command works only if you have [Git tools](https://git-scm.com/downloads) installed.)

```DOS
git clone https://github.com/microsoft/Dynamics365Commerce.ScaleUnit.git
```

The repo contains multiple branches for each release. The release branch that you should use depends on your go-live version, as shown in the following table. Because the repo contains only samples, cloning it is optional.

| Release branch name | Version | Application release version |
|---|---|---|
| [Release/9.26](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.26) | 9.26.\* | 10.0.16 |
| [Release/9.27](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.26) | 9.27.\* | 10.0.17 |

To clone a single branch, use the following command.

```DOS
git clone --single-branch --branch release/9.26 https://github.com/microsoft/Dynamics365Commerce.ScaleUnit.git
```

### Commerce.ScaleUnit repo folders and projects

| Folder | Project | Contents | Description |
|---|---|---|---|
| Channel Database | ChannelDatabase.csproj | Contoso.ExampleTable.ChannelDatabase.sql | A sample database extension. |
| CommerceRuntime | CommerceRuntime.csproj | <ul><li><b>Controller</b> – Sample code for implement new Retail Server APIs.</li><li><b>Entities, messages, and request handlers</b> – Sample code for implementing the new CRT service.</li></ul> | Sample CRT extensions. |
| ScaleUnit | ScaleUnit.csproj | The project that is required to generate the Commerce Scale Unit (CSU) package | The project that is required to generate the CSU package. |

> [!NOTE]
> Repos aren't currently available for in-store components such as Modern point of sale (POS), Cloud POS, Hardware station, Retail scale unit, and other samples. However, Microsoft plans to make them available in later releases.

## Download reference packages for creating APIs, and for consuming messages, request, entities, and contracts

Contracts, messages, entities, and request packages are published in the public NuGet feed. You can use the extension code to consume and customize existing functionalities, or to build new functionalities.

Consume the packages from [https://msazure.pkgs.visualstudio.com/D365/\_packaging/Commerce-SDK-Feed/nuget/v3/index.json](https://msazure.pkgs.visualstudio.com/D365/_packaging/Commerce-SDK-Feed/nuget/v3/index.json). You can add the package source location in the nuget.config file of your extension project file.

```xml
<packageSources>
    <add key="Commerce-SDK-Feed" value="https://msazure.pkgs.visualstudio.com/D365/_packaging/Commerce-SDK-Feed/nuget/v3/index.json" />
    <add key="nuget.org" value="https://api.nuget.org/v3/index.json" />
    </packageSources>
```

## Reference packages that are available in the public NuGet feed

### Microsoft.Dynamics.Commerce.Sdk.Runtime package

This meta package contains all the required packages for implementing the CRT and Retail Server extensions. All the required contracts, messages, requests/responses, and entities are included in this package.

**Dependencies:**

+ Microsoft.Dynamics.Commerce.Diagnostics
+ Microsoft.Dynamics.Commerce.Runtime.Data
+ Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages
+ Microsoft.Dynamics.Commerce.Runtime.Entities
+ Microsoft.Dynamics.Commerce.Runtime.Framework
+ Microsoft.Dynamics.Commerce.Runtime.Hosting.Contracts
+ Microsoft.Dynamics.Commerce.Runtime.Messages
+ Microsoft.Dynamics.Commerce.Runtime.RealtimeServices.Messages
+ Microsoft.Dynamics.Commerce.Runtime.Services.Messages

### Microsoft.Dynamics.Commerce.Sdk.ScaleUnit package

This package is required to generate the CSU package for deployment.

**Dependencies:**

+ CSU packaging dependencies

### Microsoft.Dynamics.Commerce.Sdk.ChannelDatabase package

This package is required to generate the database packages with CSU.

**Dependencies:**

+ Channel database packaging dependencies

### Package versioning

| Package version | Application release      |
|-----------------|--------------------------|
| 9.26.x\_Preview | 10.016 PEAP release      |
| 9.26.x          | 10.0.16 Customer preview |
| 9.26.x          | 10.016 GA                |

An extension project can consume the correct version if you add the package reference to the project and include the full version number. Alternatively, to make the extension project always get the latest version, use a wildcard character. We recommend that you use the full version number, and that you update the version, based on your go-live version. There are two options:

+ Without a wildcard character:

    ```xml
    <PackageReference Include="Microsoft.Dynamics.Commerce.Sdk.Runtime" Version="9.26" />;
    ```

+ With a wildcard character:

    ```xml
    <PackageReference Include="Microsoft.Dynamics.Commerce.Sdk.Runtime" Version="9.26.*" />;
    ```

For every hotfix and new application release, a new version of the package will be published in the same public feed. Consume the package version that is based on the version that is required for your go-live. If the version of the package that is consumed is higher than the version of your go-live application, runtime and deployment failures will occur.

## Best practices and branching strategies

For detailed information about the Git branching strategy, see [Git branching strategy](https://docs.microsoft.com/azure/devops/repos/git/git-branching-guidance).

Keep your branch strategy simple, and follow these best practices:

+ Use feature branches for all new features and software updates.
+ Merge feature branches into the main branch by using pull requests.
+ Keep a high-quality, up-to-date main branch.

The following branching strategies are based on the way that Microsoft uses Git. For more information, see [How we use Git at Microsoft](https://docs.microsoft.com/azure/devops/learn/devops-at-microsoft/use-git-microsoft).

### Create a new feature branch for development and software updates

Create a new feature branch that is based on the Dynamics 365 Commerce release/x.x.x branch. Clone the release/x.x.x branch, and then create a new branch. Be sure to use the correct naming convention for the new branch. For more information, see [Git branching doc for sample naming convention](https://docs.microsoft.com/azure/devops/repos/git/git-branching-guidance#name-your-feature-branches-by-convention).

#### Clone the release/x.x.x branch and create a new branch

1. Create the clone.

    ```DOS
    git clone --single-branch --branch release/9.26 https://github.com/microsoft/Dynamics365Commerce.ScaleUnit.git

    git checkout -b private/{username}/{feature/description}
    ```

2. Add and commit new changes to the development branch.

    ```DOS
    git -add .
    git commit -m"commit message
    ```

3. After the development is completed, tested, and validated, push the changes to the main branch by using **git push \<remote\> \<branch\>**.

    ```DOS
    git push origin {private branch name}
    ```

### Create a release branch after development

1. After you push the development changes to the main branch, create a new release branch, and then create the deployable packages from it.

    ```DOS
    git checkout -b release/x.x.x
    ```

2. If any changes are made in the release branch, merge them from the release branch back to main branch.

    ```DOS
    git checkout master git merge release/x.x.x
    ```

### Create an extension hotfix branch

As you did for the release branch, create a hotfix branch for extension from the main branch, and then release the hotfix. Later, merge the changes back to the main branch.

### Merge the new SDK release branch to the main and development branches

After a new version of the SDK samples is released, you must merge it with your new branch. Because the SDK contains only samples, you don't have to get the updated changes from the new SDK release branch.

```DOS
git checkout master git merge release/x.x.x
```
