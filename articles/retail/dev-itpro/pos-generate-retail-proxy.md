---
# required metadata

title: How to generate the Retail proxy for POS and E-commerce
description:
author: mugunthanm
manager: AnnBe
ms.date: 12/08/2017
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
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 83892
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2017-12-01
ms.dyn365.ops.version: AX 7.0.0, Retail September 2017 update

---

# How to generate the Retail proxy for POS and E-commerce

Whenever you create a new Retail server API controller or extend the existing controller then you need to generate the Retail proxy by using the tools available part of the Retail SDK. For example, if you added a new API for customer entity by extending the Customer controller, the you would have to generate the Retail proxy.

## What is the Retail proxy and when should you use it

All clients use the proxy API to interact with the Retail server. The Retail proxy abstracts the interface between Retail server (RS) and Commerce Runtime (CRT). For example, suppose that you created a CRT entity or added some business logics using request/response in CRT and added a new Retail server API to expose those entities and the request/response. Now you want to access those request/responses and the entities in POS to do some client logic. To access them, you could manually create all those entities and request metadata in POS and access the retail server with right parameters. However, there a lot of additional overhead because you need to duplicate the entities, manage the request/response code in two places, and you also need to write lot of code. The Retail proxy reduces this effort by auto-generating the proxy for all the custom entities and request/responses added in Retail server. The proxy tool will generate all the necessary interfaces, metadata, and abstracts of the implementation so that you can include these files in the extension projects. Then you can access the retail server APIs and entities using the metadata and interface generated.

## Types of proxy

There two types of proxy to support cross platform:
- Typescript proxy
- C# proxy

The Typescript and C# proxies are different, and they are generated differently.

### Typescript proxy
The typescript proxy is used by both POS and E-commerce to access any Retail server APIs and CRT entities. If the POS is using Retail server then it needs the Typescript proxy. Without the Typescript proxy POS will not be able to commumicate with Retail server for any operations or workflow. E-commerce controls also uses the Typescript proxy.

### C# proxy
The C# proxy is used by POS when its offline (POS directly talks to CRT without Retail Server) and e-commerce. If you want your customization to work in offline POS and want your E-commerce core to access the Retail Server APIs then you need to generate the C# proxy.

## Generate the Typescript proxy

The steps are applicable only for Dynamics 365 for Retail and Finance and Operation, Enterprise edition (Dec 2017 release).

### Generate the proxy for Retail Server
The **CommerceProxyGenerator.exe** application in the **Retail SDK\Reference** folder generates the Typescript proxy for POS.

1. Copy the following libraries to the **Retail SDK\Reference** folder before generating the proxy. These libraries are in the  **Retail SDK\Reference\...** folder. 
    - Microsoft.OData.Core.dll@ 6.11.0.0
    - Microsoft.OData.Edm.dll@ 6.11.0.0
    - Microsoft.Spatial.dll@ 6.11.0.0
    - System.Web.Http.dll@ 5.2.2.0
    - System.Web.OData.dll@ 5.5.1.0
2. Copy the customized Retail Server and CRT libraries to **Retail SDK\reference** folder.
3. Open the command prompt in administrator mode and navigate to the **...\Retail SDK\Reference** folder. Run the following command to generate the proxy. The proxy files will be generated in the same folder.
    ```
    CommerceProxyGenerator.exe <Path>\Microsoft.Dynamics.Retail.RetailServerLibrary.dll     <FilePathNameForRetailServerExtensionDLL> /application:typescriptextensions
    ```
    An example of running this command is:
    ```
    CommerceProxyGenerator.exe C:\RetailSDK\Refernce\Microsoft.Dynamics.Retail.RetailServerLibrary.dll C:\RetailSDK\Reference\Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll /application:typescriptextensions
    ```
    You would replace **Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll** with your custom retail server extension library name.
4. Include the generated files in your POS project. Two files will be generated based on your extension libraries, **DataServiceEntities.g.ts** and **DataServiceRequests.g.ts**. 
5. Similarly, generate proxies for all your Retail Server extensions.

### Generate the Typescript proxy for E-commerce

1. Navigate to the **RetailSDK\BuildTools* folder.
2. Open the **Customization.settings** file.
3. Find the **ItemGroup Condition** section.
    ```
    ItemGroup Condition="'@(RetailServerLibraryPathForProxyGeneration)' == ''" 
    ```
4. Find the line for **RetailServerLibraryPathForProxyGeneration**.
    ```
    <RetailServerLibraryPathForProxyGeneration Include="$(SdkReferencesPath)\Microsoft.Dynamics.Retail.RetailServerLibrary.dll"/>
    ```
4. Add your custom retail server library information below that line. For example:
    ```
    <RetailServerLibraryPathForProxyGeneration Include="$(SdkReferencesPath)\Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll"/>
    ```
Note: Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll is the custom library name in our example, in your scenario you will add you own library name.
4.  Similarly add all your custom retail server extensions.
5.  Build the **Ecommerce Platform.Ecommerce.Sdk.Controls** and **Platform.Ecommerce.Sdk.Core** projects. The proxy will be automatically in the project.

**How to generate C# proxy (this applicable for both POS and Ecommerce)**

1.  Navigate to RetailSDK\\SampleExtensions\\RetailProxy\\RetailProxy.Extensions. StoreHoursSample

2.  Open the Proxies.RetailProxy.Extensions.StoreHoursSample project file in visual studio.

3.  In visual studio, right click and unload the project.

4.  Right click the project and choose Edit Proxies.RetailProxy.Extensions.StoreHoursSample.csproj file.

5.  Update the below nodes under the first property group section:
```typescript
   <RootNamespace> - Update it with your custom namespace

    <AssemblyName> - Update it with your custom output library name for the proxy

    <RetailServerExtensionLibraryNoPrefixForRetailProxyCSharpExtensionGeneration> - Update it with your retail server extension library name.Proxy is generated based on this extension library name.
```

6.  Save the csproj file and load the project again.

7.  Rename the project according to your extension pattern.

8.  Once the project is loaded, delete the StoreDayHoursManager.cs file from the Adapters folder.

9.  Add all the relevant CRT library as project reference. (CRT libraries referred or used by your retail server extension)

10. Rebuild the project.

    Note: Before building the proxy project, please rebuild all our CRT and Retail server extensions libraries and drop it in RetailSDK\\References folder.

11. Add a new class file under Adapters folder and name it according to your extension pattern.

12. Please make sure the namespace used in the CRT entity and the new class you added in the previous step is same. (Check the store hours sample proxy and store hours CRT sample project for reference)

13. Extend the class from the interface manager and implement the interface methods, only the required ones leave others as is.

    Check the Proxies.RetailProxy.Extensions.StoreHoursSample proj under RetailSDK\\SampleExtensions\\RetailProxy\\RetailProxy.Extensions.StoreHoursSample for full code sample.

14. Inside the methods you will call the actual CRT request/response. Please avoid any logic in the proxy project, it should only call the CRT request/response.

15. Build the project.

16. Copy the output assembly and paste in RetailSDK\\References folder.

17. Navigate to RetailSDK\\Assets folder and open RetailProxy.MPOSOffline.ext.config

18. Under the composition section, register your new proxy library name. (The assembly generated after building your proxy project.

    Ex: 
```typescript
    <add source="assembly" value="Contoso.Commerce.RetailProxy.StoreHoursSample" />
```
Note: In the value field you will add your proxy library name, in the example we used Contoso.Commerce.RetailProxy.StoreHoursSample

19. For manual testing, update the RetailProxy.MPOSOffline.ext.config under the C:\\Program Files (x86)\\Microsoft Dynamics 365\\70\\Retail Modern POS\\ClientBroker\\ext with the custom proxy library name under the composition section.

    Ex:
```typescript
    <add source="assembly" value="Contoso.Commerce.RetailProxy.StoreHoursSample" />
```
