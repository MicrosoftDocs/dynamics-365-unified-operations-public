---
# required metadata

title: Typescript proxy for Retail POS
description: 
author: mugunthanm
manager: AnnBe
ms.date: 10/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations, Retail, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 83892
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2017-10-20
ms.dyn365.ops.version: AX 7.0.0, Retail October 2017 update

---

# Retail Typescript and C# proxy

Whenever you create a new Retail server API controller or extend the existing controller, you need to generate the Retail proxy by using the tools available part of the Retail SDK. For example, you would need to generate the proxy if you added a new API for the Customer entity by extending the Customer controller.

## What is the use of Retail proxy and when should you use it?

All the clients use the proxy API to interact with the Retail server. The Retail proxy abstracts the interface between the Retail server (RS) and the Commerce Runtime (CRT). Suppose that you create a new entity and some business logics as request/response in CRT and add a new Retail server API to expose those entities and request/response operations. Now you want to access those request/response and the entities in POS to do some client logic. You can manually create all those entities and request/response metadata in POS and access the retail server with right parameters, but there a lot of additional overhead because you need to duplicate the entities, manager, and request/response code in two places and you also need to write lot of code.

The Retail proxy reduces this effort by auto generating the proxy for all the custom entities and request/response added in Retail server. The proxy tool will generate all the necessary interface, metadata and abstracts the actual implementation so that you can include these files in the extension projects and access the retail server APIs, entities using the metadata and interface generated.

## Types of proxy

There two types of proxy to support cross platform:

- Typescript proxy: The Typescript proxy is used by the POS to access any Retail server APIs and CRT entities. If the POS is using Retail server then it needs the typescript proxy. Without the typescript proxy, POS will not be able to communicate with the Retail server for any operations/workflow.
- C# proxy: The C# proxy is used by POS when its offline (POS directly talks to CRT without Retail Server) and e-commerce. If you want your customization to work in offline (POS) and want your e-commerce client to access the RS APIs then you need to generate the C\# proxy.

[!NOTE] The Typescript proxy and C# proxy are different and the steps to create them are different.

## Generate Typescript proxy

The steps are applicable only for Dynamics 365 for Retail (July 2017 release) and Finance and Operation, Enterprise edition.

Use the CommerceProxyGenerator.exe from Retail SDK\\Reference folder to generate the typescript proxy for POS.

1. Copy these libraries to Retail SDK\\Reference folder before generating the proxy. You can find these libraries from **Retail SDK\\Reference\\...**.

    - Microsoft.OData.Core.dll@ 6.11.0.0
    - Microsoft.OData.Edm.dll@ 6.11.0.0
    - Microsoft.Spatial.dll@ 6.11.0.0
    - System.Web.Http.dll@ 5.2.2.0
    - System.Web.OData.dll@ 5.5.1.0

2. Copy the customized RS/CRT libraries to the **Retail SDK\\reference** folder.
3. Open the command prompt in admin and navigate to the **...\\Retail SDK\\Reference** folder and run the below command to generate the proxy, the proxy files will be generated in the same folder.

    ```
    CommerceProxyGenerator.exe <Path>\\Microsoft.Dynamics.Retail.RetailServerLibrary.dll <FilePathNameForRetailServerExtensionDLL> /application:typescriptextensions
    ```
    For example:
    ``` 
    CommerceProxyGenerator.exe C:\\RetailSDK\\Refernce\\Microsoft.Dynamics.Retail.RetailServerLibrary.dll C:\\RetailSDK\\Refernce\\**Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll** /application:typescriptextensions
    ```

4. Replace **Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll** with your custom retail server extension library name. Include the generated files in your POS project. It will generate two files based on your extension libraries: DataServiceEntities.g.ts and DataServiceRequests.g.ts

    [!NOTE] You have to generate proxy for all RS extensions.

## Generate C# proxy

1.  Open the Customization.settings files from **…Retail SDK\\BuildTools**.
2.  Below the **RetailServerLibraryPathForProxyGeneration** node, include all custom Retail server extension libraries as shown here:

    ```
    <RetailServerLibraryPathForProxyGeneration Include="$(SdkReferencesPath)\\Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll"/>;
    ```
    In this case Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll is the custom library.

    [!NOTE] Add all your custom retail server extension libraries.

3.  Open **RetailSDK\\Proxies\\RetailProxy\\Proxies.RetailProxy.csproj**.
4.  Include your custom CRT project library as a reference to the **Proxies.RetailProxy.csproj**.
5.  Open **RetailSDK\\Proxies\\RetailProxy\\Adapters\\UsingStatements.Extensions.txt** in the solution.
6.  Add your CRT entity namespace and request/response namespace **using** statement in **UsingStatements.Extensions.txt**. For example, If you used the namespace **Contoso.Commerce.Runtime.DataModel** in your CRT extension then add that in the       **UsingStatements.Extensions.txt** to generate the proxy.
    ```
    using Contoso.Commerce.Runtime.DataModel;
    ```
    
7.  Build the project.
8.  Add a new class under the **Adapters** folder. Use any other manager class from the adapter folder as template so that all the namespace is included.
9.  Extend the class from the interface manager and implement only the required interface methods.
10. Check the Store Hours sample in Retail SDK for how to generate the interface and manager classes. The instructions are in  **RetailSDK\\Code\\Documents\\SampleExtensionsInstructions\\StoreHours\\readme.txt**.
