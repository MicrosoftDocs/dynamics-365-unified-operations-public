---
# required metadata

title: How to generate retail proxy for POS and E-commerce
description:
author: mugunthanm
manager: AnnBe
ms.date: 12/01/2017
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

# How to generate retail proxy for POS and E-commerce
**Retail proxy:**

Whenever you create a new Retail server API/controller or extended the existing controller (Ex: Added a new API for customer entity by extending Customer controller) then you need to generate the Retail proxy by using the tools available part of the Retail SDK.

**What is the use of Retail proxy and when should you use it:**

All the clients use the proxy API to interact with the Retail server. Retail proxy abstracts the interface between Retail server (RS) and Commerce Runtime (CRT).

Ex:

1.  If created a CRT entity or added some business logics as request/response in CRT and added a new Retail server API to expose those entities and request/response.

2.  Now you want to access those request/response and the entities in POS to do some client logic.

3.  In order to access it either you can manually create all those entities and request/response metadata in POS and access the retail server with right parameters but in this cause, there a lot of additional overhead because you need to duplicate the entities, manager and request/response code in two places and you also need to write lot of code.

The Retail proxy reduces this effort by auto generating the proxy for all the custom entities and request/response added in Retail server. The proxy tool will generate all the necessary interface, metadata and abstracts the actual implementation so that you can include these files in the extension projects and access the retail server APIs, entities using the metadata and interface generated.

**Types of proxy:**

There two types of proxy to support cross platform:

1.  Typescript proxy

2.  C# proxy

**Typescript proxy:**

The typescript proxy is used by both POS and Ecommerce to access any Retail server APIs and CRT entities. If the POS is using Retail server then it needs the typescript proxy without the typescript proxy POS will not be able to talk to Retail server for any operations/workflow. Ecommerce controls also uses the typescript proxy.

**C# proxy:**

The C# proxy is used by POS when its offline (POS directly talks to CRT without Retail Server) and e-commerce. If you want your customization to work in offline (POS) and want your e-commerce core to access the RS APIs then you need to generate the C# proxy.

**Note:** Typescript proxy and C# proxy are different, both are generated differently.

**How to generate Typescript proxy:**

The steps are applicable only for Dynamics 365 for Retail and Finance and Operation, Enterprise edition (Dec 2017 release)

**Typescript proxy for POS:**

Use the CommerceProxyGenerator.exe from Retail SDK\\Reference folder to generate the typescript proxy for POS.

1.  Copy the below libraries to Retail SDK\\Reference folder before generating the proxy:

    1.  Microsoft.OData.Core.dll@ 6.11.0.0
    2.  Microsoft.OData.Edm.dll@ 6.11.0.0
    3.  Microsoft.Spatial.dll@ 6.11.0.0
    4.  System.Web.Http.dll@ 5.2.2.0
    5.  System.Web.OData.dll@ 5.5.1.0

 **Note**: You can find these libraries from Retail SDK\\Reference\\.... Copy the libraries from the respective folder and paste it in    Retail SDK\\Reference\\ folder.

2. Copy the customized RS/CRT libraries to Retail SDK\\reference folder.

3. Open the command prompt in admin and navigate to the ...\\Retail SDK\\Reference folder and run the below command to generate the proxy, the proxy files will be generated in the same folder.
```typescript
 CommerceProxyGenerator.exe <Path>\Microsoft.Dynamics.Retail.RetailServerLibrary.dll <FilePathNameForRetailServerExtensionDLL> /application:typescriptextensions
```
 **Ex:** CommerceProxyGenerator.exe C:\\RetailSDK\\Refernce\\Microsoft.Dynamics.Retail.RetailServerLibrary.dll C:\\RetailSDK\\Refernce\\**Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll** /application:typescriptextensions

 Replace **Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll** with your custom retail server extension library name.

4. Include the generated files in your POS project. It will generate two files based on your extension libraries: DataServiceEntities.g.ts and DataServiceRequests.g.ts

 Note: You have to generate proxy for all RS extensions.

**Typescript proxy for Ecommerce:**

1.  Navigate to RetailSDK\\BuildTools folder.

2.  Open the Customization.settings file

3.  Under the ItemGroup Condition="'@(RetailServerLibraryPathForProxyGeneration)' == ''" section, add your custom retail server library information (below the <RetailServerLibraryPathForProxyGeneration Include="$(SdkReferencesPath)\\Microsoft.Dynamics.Retail.RetailServerLibrary.dll"/> line.

    Ex: 
```typescript
    <RetailServerLibraryPathForProxyGeneration Include="$(SdkReferencesPath)\\**Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll**"/>
```
Note: Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll is the custom library name in our example, in your scenario you will add you own library name.

4.  Similarly add all your custom retail server extension here to generate the proxy.

5.  Build the Ecommerce Platform.Ecommerce.Sdk.Controls and Platform.Ecommerce.Sdk.Core project, proxy will be automatically in the project.

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
