---
# required metadata

title: Retail software development kit (SDK) extensibility samples
description: The Retail SDK includes extensibility samples. These samples are a good way to learn about different ways to customize Commerce.  
author: mugunthanm
manager: AnnBe
ms.date: 06/20/2017
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
ms.custom: 89803
ms.assetid: 565d9e98-77eb-4495-987a-ad9e2de303cc
ms.search.region: Global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Retail software development kit (SDK) extensibility samples

[!include [banner](../../includes/banner.md)]

The Retail software development kit (SDK) includes extensibility samples. These samples are a good way to learn about different ways to customize Dynamics 365 Commerce.

The Retail SDK includes extensibility samples. You can also use these projects as boilerplate projects to get started with a specific customization. For example, to start a new commerce runtime (CRT) extension, you can just copy one of the CommerceRuntime sample projects into a new folder, adjust the project import paths, and then start working in the project. For most of the samples, additional step-by-step instructions are available in the Retail SDK\\Documents folder. The following table provides a high-level list of the samples.

<table>
<thead>
<tr>
<th>Sample name</th>
<th>Description</th>
<th>Tasks that are demonstrated</th>
</tr>
</thead>
<tbody>
<tr>
<td>CrossLoyalty</td>
<td>This sample includes two retailers, AdventureWorks and Contoso. The Contoso retailer accepts loyalty points that customers earn from AdventureWorks. The sample shows how to create a simple new CRT service and call it when a button in Retail Modern POS is clicked. It simulates the cross-loyalty scenario. There are changes to the configuration, CRT, Commerce Scale Unit, Commerce Proxy, and point of sale (POS) (both Modern POS and Cloud POS). This sample supports offline mode for Modern POS.</td>
<td>
<ul>
<li>Create a new CRT and Commerce Scale Unit extension, or a new service.</li>
<li>Create a new operation as a separate project.</li>
</ul>
</td>
</tr>
<tr>
<td>EmailPreference</td>
<td>This sample shows how to use extension properties to extend an entity. The extended entity is persisted in both the Commerce and channel databases, and the POS client enables access to the value. The new value is written synchronously to Commerce via the RetailRealtimeTransaction service. No customization is required in the CRT or Commerce Scale Unit, because extension properties flow automatically. There are changes to pages, tables, the Real-time Service (RTS) client, Commerce Data Exchange (CDX), the channel database, and the POS (both Modern POS and Cloud POS). This sample doesn't support offline mode.</td>
<td>
<ul>
<li>Modify an existing Modern POS/Cloud POS view or page.</li>
<li>Extend the Real-time Service.</li>
<li>Use extension properties to store custom field values in the database.</li>
</ul>
</td>
</tr>
<tr>
<td>StoreHours</td>
<td>This sample shows how to create a new business entity (StoreHours) across both Commerce and the channel. There are changes to tables, CDX, the channel database, the CRT, Commerce Scale Unit, and the POS (both Modern POS and Cloud POS). This sample supports offline mode for Modern POS.</td>
<td>
<ul>
<li>Create a new CRT and Commerce Scale Unit extension, or a new service.</li>
<li>Modify an existing MPOS/Cloud POS view or page.</li>
<li>Send the custom table data to the channel by using CDX.</li>
</ul>
</td>
</tr>
<tr>
<td>HealthCheck</td>
<td>This sample shows how to expand an existing CRT service by adding functionality. In this case, the health of some other system can be checked as part of the RunHealthCheckServiceRequest service that already exists. There are changes to the CRT and CRT Test Host.</td>
<td></td>
</tr>
<tr>
<td>ExtensionProperties</td>
<td>This sample shows the following customization strategies for the CRT:
<ul>
<li>Extension properties for service, entity, request, and response</li>
<li>Triggers</li>
<li>Notifications</li>
<li>Notification handlers</li>
</ul>
</td>
<td>Use extension properties to store custom field values in a database.</td>
</tr>
<tr>
<td>CommerceRuntime Test Host</td>
<td>This tool mimics a typical CRT host that resembles Commerce Scale Unit. It supports simple testing of CRT extensions that doesn't require changes in Commerce Scale Unit or UI clients. You just register the services that are required for the CRT and run it.
<p><strong>Note:</strong> RealTimeTransaction service calls that might be part of a CRT extension won't work correctly. To test these service calls, use the RetailServer Test Client sample instead.</p>
</td>
<td></td>
</tr>
<tr>
<td>RetailServer Test Client</td>
<td>You can use this simple application to make Commerce Scale Unit calls, offline mode calls through the Commerce Proxy, or both. This sample application acts as a client. It resembles the POS clients but requires no UI changes. Therefore, it supports rapid testing and development. You can use this tool to verify customizations of the channel database, RTS, CRT, and/or Commerce Scale Unit before you hand them off to the UI team.</td>
<td></td>
</tr>
<tr>
<td>OnlineStore</td>
<td>This sample is an ASP.NET implementation that showcases the use of the Ecommerce SDK. It includes both a store front and a publishing job.</td>
<td></td>
</tr>
<tr>
<td>OpenIdConnectUtility</td>
<td>This sample lets you call Commerce Scale Unit in a customer context (C2) by using a Google Identity.</td>
<td></td>
</tr>
<tr>
<td>CashDispenser (HardwareStation)</td>
<td>This sample shows how to customize Retail Hardware Station so that a cash dispenser can be integrated.</td>
<td>Create a new Hardware Station project and support for new peripherals.</td>
</tr>
<tr>
<td>Rambler (HardwareStation)</td>
<td>This sample shows how to customize Hardware Station so that a Rambler Mobile Card Reader can be integrated.</td>
<td>Create a new Hardware Station project and support for new peripherals.</td>
</tr>
</tbody>
</table>
