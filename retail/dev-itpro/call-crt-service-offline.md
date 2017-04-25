---
# required metadata

title: Call CRT service in offline mode
description: This topic describes how provide offline support for point of sale (POS).
author: josaw1
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 69834
ms.assetid: 4f4dbdd3-e48c-417c-b8bb-f7fd6628bd9b
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Call CRT service in offline mode

[!include[banner](../includes/banner.md)]


This topic describes how provide offline support for point of sale (POS).

When a point of sale (POS) device goes offline (in other words, when it isn't connected to Retail Server), the POS automatically switches to the local commerce runtime (CRT). The POS client communicates with the local CRT by using the Retail proxy. To enable the proxy to understand your custom service, you must extend the Retail proxy project to support your request type.

1.  In Microsoft Visual Studio, from the Retail SDK\\Proxies folder, open Proxies.RetailProxy.csproj.
2.  Update RetailSDK\\Proxies\\RetailProxy\\Adapters\\UsingStatements.Extensions with the new namespace that you defined for the new entity/complex types that were introduced in CRT extension projects. These projects or dynamics-link libraries (DLLs) must first be referenced by Proxies.RetailProxy.csproj.
3.  Compile the Proxies.RetailProxy project. During compilation, Adapters\\Interfaces.g.cs is updated with your new entity and interface information. Don't modify this automatically generated class.
4.  Add your new manager class to the Adapters folder, and call your CRT service from that manager. The standard entity manager classes, such as **SalesOrderManager** and **PurchaseOrderManager**, are available in the Adapters folder. **Note:** All the libraries that are used in the project must be portable and signed. (Any custom CRT service that is referenced must be a portable library.)
5.  Update the public key in the CRT configuration file, because a new public key is generated after compilation.
6.  Build and replace the new proxy DLL in the Microsoft Dynamics AX\\70\\Retail Modern POS\\ClientBroker folder. Additionally, drop the custom CRT extension library into the Microsoft Dynamics AX\\70\\Retail Modern POS\\ClientBroker folder. (All libraries that are referenced should be dropped into this folder.)
7.  In the DllHost.exe.config file, update **RetailProxyAssemblyName** and **AdaptorCallerFullTypeName** with the new proxy DLL and adapter name.

        <add key="RetailProxyAssemblyName" value="Contoso.Commerce.RetailProxy" />
        <add key="AdaptorCallerFullTypeName" value="Contoso.Commerce.RetailProxy.Adapters.AdaptorCaller" />

8.  In the CommerceRuntime.MPOSOffline.config file, in the **&lt;composition&gt;** element, update the new CRT DLL information as for the commerceRuntime.config file.

        <add source="assembly" value="Contoso.Commerce.Runtime.Services" />

9.  Restart dllhost.exe. (You should restart the dllhost.exe for MPOS to read the new config file, this will be required even when you do any upgrade if it has config file changes.)




