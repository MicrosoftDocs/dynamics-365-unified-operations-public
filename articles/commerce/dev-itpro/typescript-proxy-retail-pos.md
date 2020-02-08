---
# required metadata

title: Typescript and C# proxies for Retail point of sale (POS)
description: This topic provides information about the Commerce proxy and explains how to generate it.
author: mugunthanm
manager: AnnBe
ms.date: 01/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 83892
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2017-10-20
ms.dyn365.ops.version: AX 7.0.0, Retail October 2017 update

---

# Typescript and C# proxies for Retail point of sale (POS)

[!include [banner](../../includes/banner.md)]

When you create a new controller for Commerce Scale Unit application programming interfaces (APIs) or extend the existing controller, you must generate the Commerce proxy by using the tools that are available as part of the Retail software development kit (SDK). For example, you must generate the Commerce proxy if you add a new API for the Customer entity by extending the Customer controller.

## What is the Commerce proxy used for and when should you use it?

All the clients use the proxy API to interact with Commerce Scale Unit. The Commerce proxy abstracts the interface between Commerce Scale Unit and the Commerce runtime (CRT). For example, you create a new entity and some business logic as request/response operations in CRT, and you add a new Commerce Scale Unit API to expose that entity and those request/response operations. You now want to access the entity and the request/response operations in the point of sale (POS) to do some client logic. You can manually create all the entities and request/response metadata in the POS, and access the Commerce Scale Unit by using the correct parameters. However, this approach involves lots of additional overhead, because you must duplicate the entities, manager, and request/response code in two places, and you must also write lots of code.

The Commerce proxy reduces this effort by automatically generating the proxy for all the custom entities and request/response operations that are added in Commerce Scale Unit. The proxy tool generates the required interface and all the required metadata, and abstracts the actual implementation. In that way, you can include the files in the extension projects, and can access the Commerce Scale Unit APIs and the entities by using the metadata and interface that are generated.

## Proxy types

There two types of proxy to support cross-platform scenarios:

- **Typescript proxy** – The POS uses the Typescript proxy to access the Commerce Scale Unit APIs and CRT entities. If the POS uses Commerce Scale Unit, it requires the Typescript proxy. Otherwise, the POS can't communicate with the Commerce Scale Unit for any operations or workflows.
- **C# proxy** – The POS uses the C# proxy when it's offline. (When the POS is offline, it communicates directly with CRT, without using Commerce Scale Unit.) The POS also uses this proxy for the Dynamics e-Commerce platform. If you want your customization to work when the POS is offline, and you want your e-Commerce client to access the Commerce Scale Unit APIs, you must generate the C# proxy.

The steps to generate the Typescript proxy and the C# proxy differ. The rest of this topic explains how to generate each type of proxy.

## Generate the Typescript proxy

> [!IMPORTANT]
> The following procedure applies only to Microsoft Dynamics 365 Retail (July 2017 release) and Microsoft Dynamics 365 Finance.

Use the CommerceProxyGenerator.exe file from the Retail SDK\\Reference\\CommerceProxyGenerator.<version_number> folder to generate the typescript proxy for the POS.

1. Before you generate the proxy, copy the customized Commerce Scale Unit, CRT, and other dependent libraries to the **Retail SDK\\Reference** folder.
2. Open a Command Prompt window as an administrator, and go to the **...\\Retail SDK\\Reference** folder. Run the following command to generate the proxy. The proxy files will be generated in the same folder.


```
CommerceProxyGenerator.exe <Path>\Microsoft.Dynamics.Retail.RetailServerLibrary.dll <FilePathNameForRetailServerExtensionDLL> /application:typescriptextensions

```

> [!NOTE]
> Use the Microsoft.Dynamics.Retail.RetailServerLibrary.dll file from \RetailSDK\References\Microsoft.Dynamics.Retail.Proxies.ExtensionsGenerator.<version_number>\build\

``` 
Ex:
CommerceProxyGenerator.exe C:\\RetailSDK\\References\\Microsoft.Dynamics.Retail.Proxies.ExtensionsGenerator.9.18.19299.3\\build\Microsoft.Dynamics.Retail.RetailServerLibrary.dll C:\\RetailSDK\\References\\Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll /a:typescriptextensions
```
In the above command, replace **Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll** with the name of your custom Commerce Scale Unit extension library. Include the generated files in your POS project. The command generates two files that are based on your extension libraries: DataServiceEntities.g.ts and DataServiceRequests.g.ts.

> [!NOTE]
> You must generate the proxy for all Commerce Scale Unit extensions.

## Generate the C# proxy (7.1 and 7.2)

> [!IMPORTANT]
> The following procedure doesn't apply to version 7.3 and later.

1. Open the **Customization.settings** file from **...Retail SDK\\BuildTools**.
2. Under the **RetailServerLibraryPathForProxyGeneration** node, include all your custom Retail Server extension libraries, as shown here.

    ```
    <RetailServerLibraryPathForProxyGeneration Include="$(SdkReferencesPath)\\Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll"/>;
    ```

    In this example, there is just one custom library, **Microsoft.Dynamics.RetailServer.CrossLoyaltySample.dll**. However, be sure to include all your custom Retail Server extension libraries.

3. Open **RetailSDK\\Proxies\\RetailProxy\\Proxies.RetailProxy.csproj**.
4. Include your custom CRT project library as a reference to **Proxies.RetailProxy.csproj**.
5. Open **RetailSDK\\Proxies\\RetailProxy\\Adapters\\UsingStatements.Extensions.txt** in the solution.
6. In **UsingStatements.Extensions.txt**, add the **using** statement for your CRT entity namespace and request/response namespace. For example, if you use the **Contoso.Commerce.Runtime.DataModel** namespace in your CRT extension, add that namespace in **UsingStatements.Extensions.txt** to generate the proxy, as shown here.

    ```
    using Contoso.Commerce.Runtime.DataModel;
    ```

7. Build the project.
8. Add a new class under the **Adapters** folder. Use any other manager class from the adapter folder as a template, so that the whole namespace is included.
9. Extend the class from the interface manager, and implement only the required interface methods.
  
    To learn how generate the interface and manager classes, see the Store Hours sample in the Retail SDK. The instructions are in the **RetailSDK\\Code\\Documents\\SampleExtensionsInstructions\\StoreHours\\readme.txt** file.

## Generate the C# proxy (7.3)

> [!IMPORTANT]
> The following procedure applies to both the POS and e-Commerce.

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

    ```
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

    ```
    <add source="assembly" value="Contoso.Commerce.RetailProxy.StoreHoursSample" />
    ```

    In this example, the proxy library is named **Contoso.Commerce.RetailProxy.StoreHoursSample**. You should specify the name of your proxy library in the **value** field.

20. For manual testing, open the **RetailProxy.MPOSOffline.ext.config** file under **C:\\Program Files (x86)\\Microsoft Dynamics 365\\70\\Retail Modern POS\\ClientBroker\\ext**. Update the **composition** section with the name of the custom proxy library.

    Here is an example.

    ```
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
