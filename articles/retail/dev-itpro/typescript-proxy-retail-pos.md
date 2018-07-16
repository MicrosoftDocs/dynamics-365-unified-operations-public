---
# required metadata

title: Typescript and C# proxies for Retail POS
description: This topic provides information about the Retail proxy and explains how to generate it.
author: mugunthanm
manager: AnnBe
ms.date: 05/01/2018
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
ms.search.validFrom: 2017-10-20
ms.dyn365.ops.version: AX 7.0.0, Retail October 2017 update

---

# Retail Typescript and C# proxies

[!include [banner](../../includes/banner.md)]

Whenever you create a new controller for Retail server application programming interfaces (APIs) or extend the existing controller, you must generate the Retail proxy by using the tools that are available as part of the Retail software development kit (SDK). For example, you must generate the Retail proxy if you add a new API for the Customer entity by extending the Customer controller.

## What is the Retail proxy used for and when should you use it?

All the clients use the proxy API to interact with Retail server. The Retail proxy abstracts the interface between Retail server and the Commerce runtime (CRT). For example, you create a new entity and some business logic as request/response operations in CRT, and you add a new Retail server API to expose that  entity and those request/response operations. You now want to access the entity and the request/response operations in the point of sale (POS) to do some client logic. You can manually create all the entities and request/response metadata in the POS, and access the Retail server by using the correct parameters. However, this approach involves lots of additional overhead, because you must duplicate the entities, manager, and request/response code in two places, and you must also write lots of code.

The Retail proxy reduces this effort by automatically generating the proxy for all the custom entities and request/response operations that are added in Retail server. The proxy tool generates the required interface and all the required metadata, and abstracts the actual implementation. In that way, you can include the files in the extension projects, and can access the Retail server APIs and the entities by using the metadata and interface that are generated.

## Proxy types

There two types of proxy to support cross-platform scenarios:

- **Typescript proxy** – The POS uses the Typescript proxy to access the Retail server APIs and CRT entities. If the POS is using Retail server, it requires the Typescript proxy. Otherwise, the POS won't be able to communicate with the Retail server for any operations or workflows.
- **C# proxy** – The POS uses the C# proxy when it's offline and for e-commerce. (When the POS is offline, it communicates directly with CRT, without using Retail server.) If you want your customization to work when the POS is offline, and you want your e-commerce client to access the Retail server APIs, you must generate the C# proxy.

> [!NOTE]
> The Typescript proxy and C# proxy differ, and the steps to create them also differ.

## Generate the Typescript proxy

The following steps apply only to Microsoft Dynamics 365 for Retail (July 2017 release) and Microsoft Dynamics 365 for Finance and Operation.

You use the CommerceProxyGenerator.exe file from the Retail SDK\Reference folder to generate the Typescript proxy for the POS.

1. Before you generate the proxy, copy the following libraries from **Retail SDK\Reference\...** to the **Retail SDK\Reference** folder:

    - Microsoft.OData.Core.dll@ 6.11.0.0
    - Microsoft.OData.Edm.dll@ 6.11.0.0
    - Microsoft.Spatial.dll@ 6.11.0.0
    - System.Web.Http.dll@ 5.2.2.0
    - System.Web.OData.dll@ 5.5.1.0

2. Copy the customized Retail server and CRT libraries to the **Retail SDK\Reference** folder.
3. Open a Command Prompt window as an administrator, and navigate to the **...\Retail SDK\Reference** folder. Run the following command to generate the proxy. The proxy files will be generated in the same folder.

    ```
    CommerceProxyGenerator.exe <Path>\\Microsoft.Dynamics.Retail.RetailServerLibrary.dll <FilePathNameForRetailServerExtensionDLL> /application:typescriptextensions
    ```

    Here is an example.

    ``` 
    CommerceProxyGenerator.exe C:\\RetailSDK\\Reference\\Microsoft.Dynamics.Retail.RetailServerLibrary.dll C:\\RetailSDK\\Reference\\Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll /application:typescriptextensions
    ```

    In the command that you run, replace **Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll** with the name of your custom Retail server extension library. Include the generated files in your POS project. The command will generate two files that are based on your extension libraries: DataServiceEntities.g.ts and DataServiceRequests.g.ts.

    > [!NOTE]
    > You must generate the proxy for all Retail server extensions.

## Generate the C# proxy (7.1 and 7.2) - These steps are not applicable for version 7.3 and higher

1. Open the **Customization.settings** files from **...Retail SDK\BuildTools**.
2. Under the **RetailServerLibraryPathForProxyGeneration** node, include all custom Retail server extension libraries, as shown here.

    ```
    <RetailServerLibraryPathForProxyGeneration Include="$(SdkReferencesPath)\\Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll"/>;
    ```

    In this example, **Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll** is the custom library.

    > [!NOTE]
    > Add all your custom Retail server extension libraries.

3. Open **RetailSDK\Proxies\RetailProxy\Proxies.RetailProxy.csproj**.
4. Include your custom CRT project library as a reference to **Proxies.RetailProxy.csproj**.
5. Open **RetailSDK\Proxies\RetailProxy\Adapters\UsingStatements.Extensions.txt** in the solution.
6. In **UsingStatements.Extensions.txt**, add the **using** statement for your CRT entity namespace and request/response namespace. For example, if you use the **Contoso.Commerce.Runtime.DataModel** namespace in your CRT extension, add that namespace in **UsingStatements.Extensions.txt** to generate the proxy.

    ```
    using Contoso.Commerce.Runtime.DataModel;
    ```

7. Build the project.
8. Add a new class under the **Adapters** folder. Use any other manager class from the adapter folder as a template, so that the whole namespace is included.
9. Extend the class from the interface manager, and implement only the required interface methods.

    To learn how generate the interface and manager classes, see the Store Hours sample in the Retail SDK. The instructions are in the **RetailSDK\Code\Documents\SampleExtensionsInstructions\StoreHours\readme.txt** file.
    
## How to generate C# proxy (this applicable for both POS and Ecommerce) for 7.3:
For each RS extensions you must generate separate proxy.

1.  Navigate to RetailSDK\\SampleExtensions\\RetailProxy\\RetailProxy.Extensions. StoreHoursSample

2.  Open the Proxies.RetailProxy.Extensions.StoreHoursSample project file in visual studio.

3.  In visual studio, right click and unload the project.

4.  Right click the project and choose Edit Proxies.RetailProxy.Extensions.StoreHoursSample.csproj file.

5.  Update the below nodes under the first property group section:

    &lt;RootNamespace&gt; - Update it with your custom namespace

    &lt;AssemblyName&gt; - Update it with your custom output library name for the proxy

6. Update the Retail server assembly name in the CommerceProxyGeneratorExtendedAssemblyPaths tag.
    &lt;CommerceProxyGeneratorExtendedAssemblyPaths&gt; - Update it with your retail server extension library name.

    Ex: &lt;CommerceProxyGeneratorExtendedAssemblyPaths Include="..\..\RetailServer\Extensions.StoreHoursSample\bin\$(Configuration)\net451\$(AssemblyNamePrefix).RetailServer.StoreHoursSample.dll" /&gt;

    **Note:** .RetailServer.StoreHoursSample.dllProxy is the name of the retail server extension assembly and rest is the prefix if any and path of the assembly where proxy engine can find this assembly. Proxy is generated based on this assembly.

7.  Save the csproj file and load the project again.

8.  Rename the project according to your extension pattern.

9.  Once the project is loaded, delete the StoreDayHoursManager.cs file from the Adapters folder.

10.  Add all the relevant CRT and Retail server library as project or assembly reference to the proxy project. (CRT libraries referred or used by your retail server extension)

11. Rebuild the project.

12. After building the project you must find a new Interfaces.g.cs file generated inside the \Adapters folder.

    Note: Before building the proxy project, please rebuild all our CRT and Retail server extensions libraries and drop it in RetailSDK\\References folder.
    
13. Include the generated Interfaces.g.cs file in the proxy project and don't make any modification in this generated file.

13. Add a new class file under Adapters folder and name it according to your extension pattern.

14. Extend the class from the interface manager class and implement the interface methods, only the required ones leave others as is.

    **Note:** You can find the interface manager class name in the Interfaces.g.cs.
    
    **Ex:** IStoreDayHoursManager is the interface name in the below sample.
    
```C#
      public interface IStoreDayHoursManager : Microsoft.Dynamics.Commerce.RetailProxy.IEntityManager
    {
        
    }
```

Check the Proxies.RetailProxy.Extensions.StoreHoursSample proj under RetailSDK\\SampleExtensions\\RetailProxy\\RetailProxy.Extensions.StoreHoursSample for full code sample.
  
15. Inside the methods you will call the actual CRT request/response. Please avoid any logic in the proxy project, it should only call the CRT request/response.

16. Build the project.

17. Copy the output assembly and paste in RetailSDK\\References folder.

18. Navigate to RetailSDK\Assets folder and open RetailProxy.MPOSOffline.ext.config

19. Under the composition section, register your new proxy library name. (The assembly generated after building your proxy project.

    Ex: &lt;add source="assembly" value="Contoso.Commerce.RetailProxy.StoreHoursSample" /&gt;

    **Note:** In the value field you will add your proxy library name, in the example we used       Contoso.Commerce.RetailProxy.StoreHoursSample

20. For manual testing, update the RetailProxy.MPOSOffline.ext.config under the C:\\Program Files (x86)\\Microsoft Dynamics 365\\70\\Retail Modern POS\\ClientBroker\\ext with the custom proxy library name under the composition section.

    Ex: <add source="assembly" value="Contoso.Commerce.RetailProxy.StoreHoursSample" />

**Note:**
In case of e-commerce, you must perform one more additional step to initialize the proxy for the extensions before calling it from your e-commerce project:

1. In your e-commerce Startup.cs (or their equivalent like web project initialization etc.) you must initialize the RetailServerContext with the edm model for your retail proxy extension or else you will get runtime error if you try to call the proxy. You need to do this only once to initialize the RetailServerContext.
             
Ex:
```C#
  RetailServerContext.Initialize(newIEdmModelExtension[]
                {
                   // /* BEGIN SDKSAMPLE_STOREHOURS
 
                   new Contoso.Commerce.RetailProxy.StoreHoursSample.EdmModel(),
 
                    // END SDKSAMPLE_STOREHOURS */
                });
```
