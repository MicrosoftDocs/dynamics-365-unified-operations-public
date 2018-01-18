---
# required metadata

title: Generate the Retail proxy for POS and e-Commerce
description: When you create a new Retail server API controller or extend the existing controller, you need to generate the Retail proxy by using the tools available in the Retail SDK.
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
ms.search.scope: Operations, Retail, Retail
# ms.tgt_pltfrm: 
ms.custom: 83892
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2017-12-01
ms.dyn365.ops.version: AX 7.0.0, Retail September 2017 update

---

# Generate the Retail proxy for POS and e-Commerce

When you create a new Retail server API controller, or extend the existing controller, you need to generate the Retail proxy by using the tools available in the Retail SDK. For example, if you added a new API for a customer entity by extending the customer controller, then you would need to generate the Retail proxy.

## What is the Retail proxy and when should you use it

All clients use the proxy API to interact with the Retail server. The Retail proxy abstracts the interface between Retail server and Commerce Runtime (CRT). For example, suppose that you created a CRT entity or added some business logics using request/response in CRT and added a new Retail server API to expose those entities and the request/response. Now you want to access those requests/responses and the entities in POS to do some client logic. To access them, you could manually create all those entities and request metadata in POS and access the Retail server with correct parameters. However, there is a lot of additional overhead because you need to duplicate the entities, manage the request/response code in two places, and write lot of code. The Retail proxy reduces this effort by auto-generating the proxy for all the custom entities and requests/responses added in Retail server. The proxy tool will generate all the necessary interfaces, metadata, and abstracts of the implementation so that you can include these files in the extension projects. You can access the Retail server APIs and entities using the metadata and interface that is generated.

## Types of proxy

There two types of proxy to support cross platform:
- Typescript proxy
- C# proxy

These proxies are different, and they are generated differently.

### Typescript proxy
The typescript proxy is used by both POS and e-Commerce to access any Retail server APIs and CRT entities. If the POS is using Retail server then it needs the typescript proxy. Without the typescript proxy, POS will not be able to communicate with Retail server for any operations or workflow. e-Commerce controls also uses the typescript proxy.

### C# proxy
The C# proxy is used by POS when its offline (POS directly communications with CRT without Retail server) and e-Commerce. If you want your customization to work in offline POS and want your e-Commerce core to access the Retail Server APIs, then you need to generate the C# proxy.

## Generate the typescript proxy

The following steps are applicable only for Dynamics 365 for Retail, and Dynamics 365 for Finance and Operation, Enterprise edition 7.3.

### Generate the proxy for Retail server
The **CommerceProxyGenerator.exe** application in the **Retail SDK\Reference** folder generates the typescript proxy for POS.

1. Copy the following libraries to the **Retail SDK\Reference** folder before generating the proxy. These libraries are in the **Retail SDK\Reference\...** folder. 
    - Microsoft.OData.Core.dll@ 6.11.0.0
    - Microsoft.OData.Edm.dll@ 6.11.0.0
    - Microsoft.Spatial.dll@ 6.11.0.0
    - System.Web.Http.dll@ 5.2.2.0
    - System.Web.OData.dll@ 5.5.1.0
2. Copy the customized Retail server and CRT libraries to the **Retail SDK\reference** folder.
3. Open the command prompt in administrator mode and navigate to the **...\Retail SDK\Reference** folder. Run the following command to generate the proxy. The proxy files will be generated in the same folder.
    ```
    CommerceProxyGenerator.exe <Path>\Microsoft.Dynamics.Retail.RetailServerLibrary.dll     <FilePathNameForRetailServerExtensionDLL> /application:typescriptextensions
    ```
    An example of running this command is:
    ```
    CommerceProxyGenerator.exe C:\RetailSDK\Refernce\Microsoft.Dynamics.Retail.RetailServerLibrary.dll C:\RetailSDK\Reference\Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll /application:typescriptextensions
    ```
    You need to replace **Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll** with your custom Retail server extension library name.
4. Include the generated files in your POS project. Two files will be generated based on your extension libraries, **DataServiceEntities.g.ts** and **DataServiceRequests.g.ts**. 
5. Similarly, generate proxies for all your Retail server extensions.

### Generate the typescript proxy for e-Commerce

1. Go to the **RetailSDK\BuildTools** folder.
2. Open the **Customization.settings** file.
3. Find the **ItemGroup Condition** section.
    ```
    ItemGroup Condition="'@(RetailServerLibraryPathForProxyGeneration)' == ''" 
    ```
4. Find the line for **RetailServerLibraryPathForProxyGeneration**.
    ```
    <RetailServerLibraryPathForProxyGeneration Include="$(SdkReferencesPath)\Microsoft.Dynamics.Retail.RetailServerLibrary.dll"/>
    ```
4. Add your custom Retail server library information below that line. For example:
    ```
    <RetailServerLibraryPathForProxyGeneration Include="$(SdkReferencesPath)\Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll"/>
    ```
    Note: Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll is the custom library name in this example. In your scenario, you will add you own library name.
4.  Similarly, add all your custom Retail server extensions.
5.  Build the **Ecommerce Platform.Ecommerce.Sdk.Controls** and **Platform.Ecommerce.Sdk.Core** projects. The proxy will automatically be in the project.

## Generate C# proxy

This is applicable to both POS and e-Commerce.

1.  Navigate to the **RetailSDK\SampleExtensions\RetailProxy\RetailProxy.Extensions.StoreHours** sample.
2.  Open the **Proxies.RetailProxy.Extensions.StoreHoursSample** project file in Visual Studio.
3.  In Visual Studio, right-click and upload the project.
4.  Right-click the project and choose **Edit Proxies.RetailProxy.Extensions.StoreHoursSample.csproj file**.
5.  Update the following nodes under the first property group section:
    - **RootNamespace** - Update with your custom namespace.
    - **AssemblyName** - Update with your custom output library name for the proxy.
    - **RetailServerExtensionLibraryNoPrefixForRetailProxyCSharpExtensionGeneration** - Update with your retail server extension library name. The proxy is generated based on this extension library name.
6.  Save the project file and load the project again.
7.  Rename the project according to your extension pattern.
8.  After the project has loaded, delete the **StoreDayHoursManager.cs** file from the **Adapters** folder.
9.  Add all of the relevant CRT libraries as a project reference. These are the CRT libraries referred or used by your Retail server extension.
10. Rebuild all the CRT and Retail server extensions libraries and copy them to the **RetailSDK\References** folder.
11. Rebuild the project.
12. Add a new class file under the **Adapters** folder and name it according to your extension pattern.
13. Make sure that the namespace used in the CRT entity and the new class that you added in the previous step is same. For an example, review the store hours sample proxy and store hours CRT sample project.
14. Extend the class from the interface manager and implement the interface methods. Do this only for the required ones, leave the others as is. For a complete code example, review the **Proxies.RetailProxy.Extensions.StoreHoursSample** project under **RetailSDK\SampleExtensions\RetailProxy\RetailProxy.Extensions.StoreHoursSample**.
15. Inside the methods you will call the actual CRT request/response. Avoid adding any logic to the proxy project, it should only call the CRT request/response.
16. Build the project.
17. Copy the output assembly to the **RetailSDK\References** folder.
18. Navigate to the **RetailSDK\Assets** folder and open **RetailProxy.MPOSOffline.ext.config**.
19. Under the **composition** section, register your new proxy library name, which is the assembly generated after building your proxy project. In the **Value** field, add your proxy library name. In the following example, the proxy library name is **Contoso.Commerce.RetailProxy.StoreHoursSample**.
    ```
    <add source="assembly" value="Contoso.Commerce.RetailProxy.StoreHoursSample" />
    ```
19. For manual testing, update the **RetailProxy.MPOSOffline.ext.config** file, under **C:\Program Files (x86)\Microsoft Dynamics 365\70\Retail Modern POS\ClientBroker\ext**, with the custom proxy library name under the **composition** section. For example:
    ```
    <add source="assembly" value="Contoso.Commerce.RetailProxy.StoreHoursSample" />
    ```
