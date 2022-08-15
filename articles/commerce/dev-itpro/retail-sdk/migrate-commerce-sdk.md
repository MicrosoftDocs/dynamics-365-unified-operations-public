---
title: Migrate to the Commerce SDK
description: This article explains how to migrate to the Commerce software development kit (SDK).
author: josaw1
ms.date: 05/31/2022
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2021-02-11
ms.dyn365.ops.version: AX 10.0.19
---

# Migrate to the Commerce SDK

[!include [banner](../../includes/banner.md)]

The Commerce software development kit (SDK) and sealed installers simplify the Commerce developer and upgrade experience. The new Commerce SDK minimizes the effort that is involved in upgrades, and helps reduce the time and effort that must be spent on the upgrade process. Additionally, integration with Git, Microsoft Azure DevOps, and Visual Studio Code brings the .NET development experience to the Commerce SDK.

The main difference between the Commerce SDK and the older (legacy) Retail SDK is that extensions can be independently developed and deployed. This process reduces the upgrade and deployment time, and the new sealed installers separate the extension from the base installers. Therefore, the base and extension installers can be independently installed and serviced. You don't need a code merge or combined packaging.

In the Retail SDK, you need the Core POS app projects to develop a Point of Sale (POS) extension, and extensions must use those projects to develop extensions. If multiple independent software vendor (ISV), partner, or customers extensions are involved, they must all be merged to the Core POS app extension project. That project is integrated into one build pipeline to generate the combined package or installers that include the Core POS app and the extension. If the new Microsoft upgrade for POS is available, the extensions must be merged with the Core POS app to generate the combined installers. This process is time consuming, involves development effort, and must be repeated for every upgrade.

The Commerce SDK and sealed installers address the preceding issue by isolating the base app and extensions. Extensions can be independently developed by consuming the packages that are available in a public feed. They don't require any of the Core POS app or core classes from the Commerce runtime (CRT) or Retail Server.

An extension can be developed as an add-in. The new sealed installer framework enables it to be independently developed and deployed. Extensions can create their own headless installers for extension code. Multiple extensions can be installed separately, except Microsoft–hosted Cloud Scale Unit extension packages. In a self-hosted Cloud Scale Unit, multiple extensions can be independently installed and deployed.

The Commerce SDK samples and packages are published on [GitHub](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.33/src/ScaleUnitSample) and in a [public feed](https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/nuget/v3/index.json), for easier consumption. You don't have to access Microsoft Dynamics Lifecycle Services (LCS) to get the latest update. It can take several hours to download the latest update of the SDK through LCS. However, the new approach lets you download the latest SDK or packages in just a few steps. The GitHub repository (repo) is a sample repo. Therefore, you don't have to clone it to create your extension development. All extensions can be developed by consuming the packages from the public feed.

## Benefits of the Commerce SDK

The Commerce SDK provides these benefits:

- The update experience is seamless. The core application and extensions can be independently updated without a code merge. You don't have to update extensions to update the core applications. This new process reduces the time that is spent on updates.
- Performance is improved. If extensions are migrated to the Commerce SDK and .NET Standard 2.0, the Cloud Scale Unit can be upgraded to the new ASP.NET Core 3.1, which provides better application programming interface (API) performance.
- Extensions are published to GitHub and a public feed. You can download the SDK within minutes instead of hours.
- The new sealed installers are headless (that is, there is no user interface). Sealed installers work great for mass deployment.
- Separate headless installers for extensions use the new installer framework.
- Packaging and configuration of CRT and Hardware station extensions for Modern POS are automated.
- Build times are improved.
- The developer experience is improved. CSU extensions can be developed by using Visual Studio Code, Git for source code management, and Azure DevOps for build automation.

## Comparison of the Commerce and Retail SDKs

| Component | Commerce SDK (new) | Retail SDK (legacy) |
|---|---|---|
| Samples | Samples are published on GitHub. | Samples are published in the \Sample extension folder in the Retail SDK. |
| Getting the SDK | The SDK is available on GitHub and in a public feed. | The SDK is available on the LCS development virtual machine (VM). |
| Packages or reference libraries | Packages are published to the public feed and can be consumed via NuGet. | Reference libraries and packages that are required for Commerce development are available in the /Pkgs folder in the Retail SDK. |
| Deployable packages | There are separate packages and installers for Cloud and on-premises components. You don't have to update any configuration files for extensions. Configuration files are automatically generated. Packages can be generated by consuming the packages in the public feed. There is no dependency with any samples or projects on GitHub. | There is one combined deployable package. You must update several configuration files to generate that package. |
| Installers | There are separate installers for core applications and extensions. The Commerce SDK uses the new sealed installer framework to generate the installers. It works only with the new sealed installer. Installers can be generated by consuming the packages in the public feed. There is no dependency with any samples or projects on GitHub. | There are combined installers for extensions and core applications. For example, there is one combined Modern POS installer for Core POS and extensions. |
| Build pipeline | Sample YAML files that are available on GitHub can be used to set up the pipeline. However, the Commerce SDK is designed to work with your own Azure DevOps pipeline setup. | The build pipeline is based on the dirs.proj file that is available in the Retail SDK. |
| Updates | To update the extensions, consume the latest package that is available in the public feed. | Updates must be done from LCS. The LCS update process must be followed. |

## Overview of the migration steps

1. Set up your [local development environment](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/blob/release/9.33/src/ScaleUnitSample/Readme.md), or configure the [LCS development environment](../../../fin-ops-core/dev-itpro/dev-tools/access-instances.md).
2. Uninstall the Modern POS, Hardware Station, and Cloud Scale Unit - Self-hosted that were installed by using the legacy installers. Then install the required application by using the [new sealed installers](https://community.dynamics.com/ax/b/axforretail/posts/introducing-sealed-installers).
3. Migrate the CRT, API, channel database, proxy, POS, and Hardware Station extensions by using the Commerce SDK.

    Most of the code that was written by using the Retail SDK can easily be migrated. You don't have to rewrite it. For example, the CRT extension can be updated by changing the project to **NET standard 2.0** and updating the reference package so that it's consumed from the public feed. The API extension can be updated by using new interface and removing the **EDMModel** extender code, because it's automated in the back end.

4. Package the extensions for Cloud or on-premises by using the new [installer](https://community.dynamics.com/ax/b/axforretail/posts/introducing-sealed-installers) and [packaging framework](retail-sdk-packaging.md#deployable-package-types).
5. Deploy the extensions.

## How to migrate

### Developer environment changes

The LCS 10.0.21 developer VM doesn't have Visual Studio 2017. Therefore, manually install Visual Studio 2017 and the dependencies as described in the "Prerequisites" section of [Retail software development kit (SDK)](retail-sdk-overview.md#prerequisites), or set up a [local development environment](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/blob/release/9.33/src/ScaleUnitSample/Readme.md). We recommend that you set up a local development environment. Eventually, Commerce components won't be available on the LCS VM. You can either manually install those components on the LCS developer VM or use your own local development machine.

### CRT extensions

In the Retail SDK, CRT extensions use the packages or reference libraries from the \Pkgs folder. However, in the Commerce SDK, all the required packages are published to the [public feed](https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/nuget/v3/index.json), and CRT samples are available for reference on [GitHub](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.33/src/ScaleUnitSample).

Your extension code must use the packages from the public feed instead of the Retail SDK \Pkgs folder, and you must update the project to .NET Standard 2.0. If you followed the best practices, no changes should be required in the core business logic or contracts. The packages in the public feed won't have any services or workflow classes. Your extension must not consume those classes.

Edit your project file, and manually add the package reference or use the NuGet manager to consume the packages, as shown in the following XML example.

```xml
<PackageReference Include="Microsoft.Dynamics.Commerce.Sdk.Runtime" Version="$(CommerceSdkPackagesVersion)" />
```

Packages that are available in the public feed for extensions to consume can be found on [GitHub](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/blob/release/9.33/README.md).

#### Why we made this change to CRT extensions

This new implementation simplifies the upgrade and development process. To download the latest version of the packages, you no longer have to use LCS to upgrade the SDK. That upgrade process can take several hours. Instead, select the latest version in your package management solution (for example, NuGet). 

Development of Commerce extensions for CRT is more streamlined and follows the standard best practices for .NET development.

### Reference package difference between legacy Retail SDK and Commerce SDK

| Legacy SDK package |  Commerce SDK (new) |
|--------------------| -------------------|
|Microsoft.Dynamics.Commerce.Runtime.Services, Microsoft.Dynamics.Commerce.Runtime.TransactionService, Microsoft.Dynamics.Commerce.Runtime.Workflow, Microsoft.Dynamics.Commerce.Runtime.Services.Messages, Microsoft.Dynamics.Commerce.Runtime.Data |Microsoft.Dynamics.Commerce.Sdk.Runtime |
| Microsoft.Dynamics.Commerce.Runtime.Services.PricingEngine | Microsoft.Dynamics.Commerce.Runtime.Services.PricingEngine.Contracts |

### Sample code to migrate the helper classes consumed in legacy SDK to Commerce SDK

<table>
<tr>
    <td><b>Legacy SDK helper methods</b></td><td><b>Commerce SDK (Request/Response)</b></td>
</tr>
<tr>
    <td> TransactionServiceClient</br></br>

```C#
TransactionServiceClient transactionService = new TransactionServiceClient(request.RequestContext);
transactionService.InvokeExtensionMethod("getSalesOrderDetails")
``` 

</td>
<td>

```C#
InvokeExtensionMethodRealtimeRequest extensionRequest = new InvokeExtensionMethodRealtimeRequest("getSalesOrderDetails ")
        InvokeExtensionMethodRealtimeResponse response = await request.RequestContext.ExecuteAsync<InvokeExtensionMethodRealtimeResponse>   (extensionRequest).ConfigureAwait(false); 
``` 
    
</td>
</tr>
<tr>
<td> LoadSalesTransactionForReturn </td>
<td> 

```C#
var request = new GetSalesOrderDetailsByTransactionIdServiceRequest(transactionIdToLoad, SearchLocation.Local);
                     response = await context.ExecuteAsync<GetSalesOrderDetailsServiceResponse>(request).ConfigureAwait(false);
```   

</td>
</tr>
<tr>
<td> GetProductsInCartLines </td>
<td> 

```C#
var serviceRequest = new GetProductsInCartLinesServiceRequest(request.CartLines);
                 var serviceResponce = await request.RequestContext.ExecuteAsync<GetProductsInCartLinesServiceResponse>(serviceRequest).ConfigureAwait(false);
                 return new GetProductsInCartLinesResponse(serviceResponce.ProductsByRecordId);
```  

</td>
</tr>
<tr>
<td> LoadSalesTransaction </td>
<td>

```C#
 var getCartRequest = new GetCartRequest(
                new CartSearchCriteria(cartId, cartVersion),
                QueryResultSettings.SingleRecord,
                includeHistoricalTenderLines: false,
                ignoreProductDiscontinuedNotification: ignoreProductDiscontinuedNotification);

var getCartResponse = await context.ExecuteAsync<GetCartResponse>(getCartRequest).ConfigureAwait(false);
```    

</td>
</tr>
<tr>
<td> SaveSalesTransaction </td>
<td>

```C#
var saveTransactionRequest = new SaveSalesTransactionDataRequest(transaction);
 await request.RequestContext.Runtime.ExecuteAsync<NullResponse>(saveTransactionRequest, request.RequestContext).ConfigureAwait(false);
``` 

</td>
</tr>
<tr>
<td> CartWorkflowHelper.PerformSaveCartOperations </td>
<td>

```C#
var saveCartRequest = new SaveCartRequest(cart, calculationModes: null, isGiftCardOperation: isGiftCardOperation, isTransactionResume: true);
saveCartRequest.SalesTransaction = transaction;
cart = (await request.RequestContext.ExecuteAsync<SaveCartResponse>(saveCartRequest).ConfigureAwait(false)).Cart;
```    

</td>
</tr>
<tr>
<td> CartWorkflowHelper.ConvertToCart </td>
<td>

```C#
ConvertSalesTransactionToCartServiceRequest serviceRequest = new ConvertSalesTransactionToCartServiceRequest(salesTransaction);
return (await context.ExecuteAsync<UpdateCartServiceResponse>(serviceRequest).ConfigureAwait(false)).Cart;
```    

</td>
</tr>
<tr>
<td> RuntimeReceiptLocalizer.GetLocalizedString </td>
<td>

```C#
var request = new GetLocalizedTextsDataRequest(cultureName, textId, QueryResultSettings.SingleRecord);
var response = isAsync ?
                await requestContext.ExecuteAsync<EntityDataServiceResponse<LocalizedText>>(request).ConfigureAwait(false) :
var result = response.PagedEntityCollection;
if (!result.IsNullOrEmpty())
{
   LocalizedText text = result.FirstOrDefault();
   return text.Text;
}
```    

</td>
</tr>
<tr>
<td> DataCacheAccessor </td>
<td>

DataCacheAccessor is internal. Use .NET memory cache or a similar approach.

</td>
<tr>
<td> PricingEngine </td>
<td> Extensions should not call PricingEngine directly and instead should use CalculatePricesServiceRequest, CalculateDiscountsServiceRequest. </td>
</tr>
<tr>
<td> PricingDatabaseAccessor </td>
<td> Obsolete since version 10.0.1, use the relevant CRT data requests. </td>
</tr>
</table>

### Retail Server or Headless Commerce API extensions

In older versions of Retail SDK extensions, you must use the packages from the Retail SDK \Pkgs folder and extend from the `CommerceController` class to create new API extensions. In the Commerce SDK, an extension uses the packages from the public feed and extends the API controller class from the `IController` interface. For more information, see [Create a Retail Server extension API (Retail SDK version 10.0.11 and later)](../retail-server-icontroller-extension.md).

#### Why we made this change to the API extensions

This change removes the need to create the `EdmModel` factory and extender. It was complex for the extensions to add this factory and extender, and to set appropriate attributes. The whole Entity Data Model (EDM) process is now automated, and you don't have to generate a separate offline proxy library for Modern POS. The API extension library can be used directly offline, and the proxy generation process is simplified.

### Channel database

No changes are required in the offline database scripts that are created for extensions. However, you must create a channel database project and include the script in it for packaging. The sample project can be found on [GitHub](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/tree/release/9.33/src/ScaleUnitSample/ChannelDatabase).

### Offline

Previously, you had to create a separate Modern POS C# proxy library to consume the API and CRT extensions. However, in the new API extension model, you can directly use the Headless Commerce API.

### Hardware Station

In older versions of Retail SDK extension, you must use the packages from the Retail SDK \Pkgs folder and extend from the `HardwareStationController` class to create new Hardware Station extensions. When you use the Commerce SDK, an extension must use the packages from the public feed and extend the Hardware Station controller class by using the `IController` interface. For more information, see [Integrate the POS with a new hardware device and generate the extension installer](../hardware-device-extension.md).

### New sealed installers

You can download the new sealed installers from LCS by going to the [Shared Asset Library](https://lcs.dynamics.com/V2/SharedAssetLibrary) and selecting **Retail Self-service package** as the asset type. The legacy installers or the apps (Modern POS, Hardware Station, Cloud Scale Unit - Self-hosted) must be uninstalled before you install the new sealed installers. The Commerce SDK for POS will work only with the sealed installers.

### POS

In the Commerce SDK, a few improvements that have been made to the development process for POS extensions will require changes when you migrate existing extensions. The following table summarizes the most important changes. For a complete list of changes and steps to migrate an extension, see [Migrate a POS extension to the independent packaging model](../pos-extension/migrate-pos-extension.md).

| Change | Description | Purpose |
|---|---|---|
| Removal of POS app code from the SDK | In older versions of the Retail SDK, the POS extension solution contains both Microsoft-developed code and the extensions. In the Commerce SDK, we changed this model. The extension solutions now include only the POS extensions code. | This change simplifies the update process by removing the need for a code merge. It also enables the POS main package to be updated independently from the extension packages. Finally, it enables POS to support multiple extension packages without requiring a code merge. |
| POS API updates | <p>In addition to the packaging changes, we made two main changes to the POS API:</p><ul><li>We removed all references to knockout.js from the POS public contracts. As part of this change, we enabled an extension's user interface to use common POS controls through a new set of APIs under PosApi/Consume/Controls. The availability of these new APIs has made the Pos.UI.Sdk library obsolete. Therefore, that library isn't found in the Commerce SDK.</li><li>We introduced a simplified API to create custom views. | The removal of references to the knockout.js library from the POS public contracts enables us to iterate and improve the POS control implementations without the risk of breaking any extensions. This capability is especially important because the upgrade process no longer requires that the POS main package and extensions be recompiled together. Nevertheless, extensions can still use knockout.js. For more information about how to use knockout.js with the Commerce SDK, see [Consume external or third party libraries like Knockout.js in POS extensions](../pos-extension/knockout-pos-extension.md). |

### Build pipeline

For information about how to set up the build pipeline for the Commerce SDK, see [Set up a build pipeline for the independent-packaging SDK](../build-pipeline.md). To simplify the setup, YAML and script files are added as a sample. Additionally, steps for using the certificate from Azure Key Vault and signing the build artifacts are added.

### Package deployment

A new packaging type is added to separate the self-service components from the Cloud Scale Unit extensions. The new ScaleUnit package will contain only the Cloud Scale Unit components. You can upload the self-service components to LCS by using the build pipeline. Alternatively, they can be manually uploaded and synced to the back office.

If you use the Retail SDK to generate the package, you must update the **Customization.Settings** file and the extension configuration files. In the Commerce SDK packaging, all these steps are automated. Therefore, you don't have to include or update the configuration files.

For more information, see [Generate a separate package for Commerce Cloud Scale Unit (CSU)](retail-sdk-packaging.md#generate-a-separate-package-for-commerce-cloud-scale-unit-csu).

## FAQ

### Do I have to migrate?

The Commerce SDK provides several benefits that the Retail SDK doesn't provide, such as a simplified development and update experience, and improved performance. The Retail SDK and installers will be deprecated in October 2023, and all extensions must be migrated before then. After October 2023, the Retail SDK will no longer be released or supported.

### When do I have to migrate?

Extensions must be migrated to the new Commerce SDK and new installers by October 2023.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
