---
title: TypeScript and C# proxies for Retail point of sale (POS)
description: This article provides information about the Commerce proxy and explains how to generate it.
author: josaw1
ms.date: 08/26/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2017-10-20
ms.dyn365.ops.version: AX 7.0.0, Retail October 2017 update
ms.custom: 83892
---

# TypeScript and C# proxies for Retail point of sale (POS)

[!include [banner](../../includes/banner.md)]

When you create a new Retail Server API, you must generate the Commerce proxy by using the tools that are available as part of the Retail software development kit (SDK). For example, you must generate the Commerce proxy if you add a new Retail Server API.

## The Commerce proxy and when to use it

All clients use the proxy API to interact with Retail Server. The Commerce proxy abstracts the interface between Retail Server and the Commerce runtime (CRT). For example, you create a new entity and some business logic as request/response operations in CRT, and you add a new Retail Server API to expose that entity and those request/response operations. You now want to access the entity and the request/response operations in the point of sale (POS) to do some client logic. You can manually create all the entities and request/response metadata in the POS, and access the Retail Server API by using the correct parameters. However, this approach involves lots of additional overhead, because you must duplicate the entities, manager, and request/response code in two places, and you must also write lots of code.

The Commerce proxy reduces this effort by automatically generating the proxy for all the custom entities and request/response operations that are added in Retail Server. The proxy tool generates the required interface and all the required metadata, and abstracts the actual implementation. In that way, you can include the files in the extension projects, and can access the Retail Server APIs and the entities by using the metadata and interface that are generated.

## Proxy types

There two types of proxy to support cross-platform scenarios:

- **TypeScript proxy** – The POS uses the TypeScript proxy to access the Retail Server APIs and CRT entities. If the POS uses Retail Server, it requires the TypeScript proxy. Otherwise, the POS can't communicate with the Retail Server for any operations or workflows.
- **C# proxy** – The POS uses the C# proxy when it's offline. (When the POS is offline, it communicates directly with CRT, without using Retail Server.) The POS also uses this proxy for the Dynamics e-Commerce platform. If you want your customization to work when the POS is offline, and you want your e-Commerce client to access the Retail Server APIs, you must generate the C# proxy.

The steps to generate the TypeScript proxy and the C# proxy differ. The rest of this article explains how to generate each type of proxy.

## Generate the TypeScript proxy (10.0.11 or lower) Retail Server

If you are using Microsoft Dynamics Commerce version 10.0.12 or greater, follow the steps mentioned in [Create a new Retail Server extension API](retail-server-icontroller-extension.md).

> [!IMPORTANT]
> Run MSBuild from the Retail SDK root folder to restore the CommerceProxyGenerator.exe package. Use the Visual Studio developer command prompt or MSBuild command prompt to restore all the packages in the reference folder before generating the proxy. If you do not perform this step, the CommerceProxyGenerator.exe package will not be available in the RetailSDK\Reference folder.

Use the CommerceProxyGenerator.exe file from the Retail SDK\\Reference\\Microsoft.Dynamics.Commerce.Tools.CoreProxyGenerator.<version_number>\tools folder to generate the typescript proxy for the POS.

1. Before you generate the proxy, copy the customized Retail Server API, CRT, and other dependent libraries to the **Retail SDK\\Reference** folder.
2. Open a Command Prompt window as an administrator, and go to the **...\\Retail SDK\\Reference\\Microsoft.Dynamics.Commerce.Tools.CoreProxyGenerator\<version_number>\tools** folder. Run the following command to generate the proxy. The proxy files will be generated in the same folder.

  
  POS TypeScript proxy
```Console 
    CommerceProxyGenerator.exe <Path>\Microsoft.Dynamics.Retail.RetailServerLibrary.dll <FilePathNameForRetailServerExtensionDLL> /application:typescriptextensions
```
 e-Commerce TypeScript proxy
 ```Console 
    CommerceProxyGenerator.exe <Path>\Microsoft.Dynamics.Retail.RetailServerLibrary.dll <FilePathNameForRetailServerExtensionDLL> /application:typescriptmoduleextensions
```

> [!NOTE]
> Use the Microsoft.Dynamics.Retail.RetailServerLibrary.dll file from \RetailSDK\References\Microsoft.Dynamics.Commerce.Tools.ExtensionsProxyGenerator.<version_number>\build.

```Console
Example
CommerceProxyGenerator.exe C:\\RetailSDK\\References\\Microsoft.Dynamics.Commerce.Tools.ExtensionsProxyGenerator.9.21.20042.5\\build\\Microsoft.Dynamics.Retail.RetailServerLibrary.dll C:\\RetailSDK\\References\\Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll /a:typescriptextensions
```

In the above command, replace **Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll** with the name of your custom Retail Server extension library. Include the generated files in your POS project. The command generates two files that are based on your extension libraries: DataServiceEntities.g.ts and DataServiceRequests.g.ts.

## Generate the C# proxy (Commerce version 10.0.11 or lower)

> [!IMPORTANT]
> Retail Server extension built using this the Microsoft.Dynamics.Commerce.Runtime.Hosting.Contracts API can be used in and offline implementation, no need to generate separate C# proxy library. This step is required only for Commerce version 10.0.11 or lower or Retail Server extensions not using the Microsoft.Dynamics.Commerce.Runtime.Hosting.Contracts.

For each Retail Server extension, you must generate a separate proxy.

1. Navigate to **RetailSDK\\SampleExtensions\\RetailProxy\\RetailProxy.Extensions.StoreHoursSample**.
2. In Microsoft Visual Studio, open the **Proxies.RetailProxy.Extensions.StoreHoursSample** project file.
3. Right-click, and select to unload the project.
4. Right-click the project, and select to edit the **Proxies.RetailProxy.Extensions.StoreHoursSample.csproj** file.
5. In the first property group section, update the following nodes:

    - **&lt;RootNamespace&gt;** – Specify your custom namespace.
    - **&lt;AssemblyName&gt;** – Specify your custom output library name for the proxy.

6. Update the **CommerceProxyGeneratorExtendedAssemblyPaths** element by specifying the name of your Retail Server extension library.

    Here is an example.

    ```xml
    <CommerceProxyGeneratorExtendedAssemblyPaths Include="..\..\RetailServer\Extensions.StoreHoursSample\bin\$(Configuration)\net451\$(AssemblyNamePrefix).RetailServer.StoreHoursSample.dll" />
    ```

    > [!NOTE]
    > **.RetailServer.StoreHoursSample.dll** is the name of the Retail Server extension assembly, and the rest of the value is the prefix (if there is a prefix) and the path of the assembly where the proxy engine can find this assembly. The proxy is generated based on this assembly.

7. Save the file, and load the project again.
8. Rename the project according to your extension pattern.
9. After the project is loaded, delete the **StoreDayHoursManager.cs** file from the **Adapters** folder.
10. Add all the relevant CRT and Retail Server libraries to the proxy project as project or assembly references.
11. Rebuild the project.

    You will see that a new Interfaces.g.cs file is generated inside the Adapters folder.

    > [!NOTE]
    > Before you build the proxy project, rebuild all your CRT and Retail Server extension libraries, and drop them into the **RetailSDK\\References** folder.

12. Include the new **Interfaces.g.cs** file in the proxy project. However, don't modify this file.
13. Under the **Adapters** folder, add a new class file, and name it according to your extension pattern.
14. Extend the class from the interface manager class, and implement only the interface methods that are required.

    > [!NOTE]
    > You can find the name of the interface manager class in the Interfaces.g.cs. file.

    In the following example, **IStoreDayHoursManager** is the name of the interface.

    ```C#
    public interface IStoreDayHoursManager : Microsoft.Dynamics.Commerce.RetailProxy.IEntityManager
    {
    }
    ```

    For the full sample code, see the **Proxies.RetailProxy.Extensions.StoreHoursSample** project under **RetailSDK\\SampleExtensions\\RetailProxy\\RetailProxy.Extensions.StoreHoursSample**.

15. Inside the methods you will call the actual CRT request/response. Avoid including any logic in the proxy project. The proxy project should just call the CRT request/response.
16. Build the project.
17. Copy the output assembly, and paste it in the **RetailSDK\\References** folder.
18. Navigate to the **RetailSDK\\Assets** folder, and open the **RetailProxy.MPOSOffline.ext.config** file.
19. In the **composition** section, register the name of your new proxy library (that is, the assembly that was generated after you built your proxy project).

    Here is an example.

    ```xml
    <add source="assembly" value="Contoso.Commerce.RetailProxy.StoreHoursSample" />
    ```

    In this example, the proxy library is named **Contoso.Commerce.RetailProxy.StoreHoursSample**. You should specify the name of your proxy library in the **value** field.

20. For manual testing, open the **RetailProxy.MPOSOffline.ext.config** file under **C:\\Program Files (x86)\\Microsoft Dynamics 365\\70\\Retail Modern POS\\ClientBroker\\ext**. Update the **composition** section with the name of the custom proxy library.

    Here is an example.

    ```xml
    <add source="assembly" value="Contoso.Commerce.RetailProxy.StoreHoursSample" />
    ```

21. For e-Commerce, you must initialize the proxy for the extensions before you call it from your e-Commerce project. In your e-Commerce **Startup.cs** file (or an equivalent, such as web project initialization), initialize **RetailServerContext** with the Extended data model(EDM) model for your Retail proxy extension. Otherwise, you will receive a runtime error when you try to call the proxy. You must complete this step only one time.

    Here is an example.

    ```C#
    RetailServerContext.Initialize(newIEdmModelExtension[]
    {
        // /* BEGIN SDKSAMPLE_STOREHOURS
        new Contoso.Commerce.RetailProxy.StoreHoursSample.EdmModel(),
        // END SDKSAMPLE_STOREHOURS */
    });
    ```


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
