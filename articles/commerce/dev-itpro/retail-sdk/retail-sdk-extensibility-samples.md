---
title: Retail software development kit (SDK) extensibility samples
description: The Retail SDK includes extensibility samples. These samples are a good way to learn about different ways to customize Commerce.
author: josaw1
ms.date: 05/03/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.custom: 89803
ms.assetid: 565d9e98-77eb-4495-987a-ad9e2de303cc
ms.search.industry: Retail
---

# Retail software development kit (SDK) extensibility samples

[!include [banner](../../includes/banner.md)]
[!include [banner](../../includes/retail-sdk-deprecation-banner.md)]

The Retail software development kit (SDK) includes extensibility samples. These samples are a good way to learn about different ways to customize Microsoft Dynamics 365 Commerce.

The Retail SDK includes extensibility samples. You can also use these projects as boilerplate projects to get started with a specific customization. For example, to start a new commerce runtime (CRT) extension, you can just copy one of the CommerceRuntime sample projects into a new folder, adjust the project import paths, and then start working in the project. For most of the samples, additional step-by-step instructions are available in the Retail SDK\\Documents folder. The following table provides a high-level list of the samples.

| Sample name                     | Description | Tasks that are demonstrated |
| ------------------------------- | ----------- | --------------------------- |
| CrossLoyalty                    | This sample includes two retailers, AdventureWorks and Contoso. The Contoso retailer accepts loyalty points that customers earn from AdventureWorks. The sample shows how to create a simple new CRT service and call it when a button in Retail Modern Point of Sale (POS) is selected. It simulates the cross-loyalty scenario. There are changes to the configuration, CRT, Commerce Scale Unit, Commerce Proxy, and POS (both Modern POS and Cloud POS). This sample supports offline mode for Modern POS. | <ul><li>Create a new CRT and Commerce Scale Unit extension, or a new service.</li><li>Create a new operation as a separate project.</li></ul> |
| EmailPreference                 | This sample shows how to use extension properties to extend an entity. The extended entity is persisted in both the Commerce database and the channel database, and the POS client enables access to the value. The new value is written synchronously to Commerce via the RetailRealtimeTransaction service. No customization is required in the CRT or the Commerce Scale Unit, because extension properties flow automatically. There are changes to pages, tables, the Real-time Service (RTS) client, Commerce Data Exchange (CDX), the channel database, and the POS (both Modern POS and Cloud POS). This sample doesn't support offline mode. | <ul><li>Modify an existing Modern POS or Cloud POS view or page.</li><li>Extend the RTS.</li><li> Use extension properties to store custom field values in the database.</li></ul> |
| StoreHours                      | This sample shows how to create a new business entity (StoreHours) across both Commerce and the channel. There are changes to tables, CDX, the channel database, the CRT, the Commerce Scale Unit, and the POS (both Modern POS and Cloud POS). This sample supports offline mode for Modern POS. | <ul><li>Create a new CRT and Commerce Scale Unit extension, or a new service.</li><li>Modify an existing MPOS or Cloud POS view or page.</li><li>Send the custom table data to the channel by using CDX.</li></ul> |
| HealthCheck                     | This sample shows how to expand an existing CRT service by adding functionality. In this case, the health of some other system can be checked as part of the RunHealthCheckServiceRequest service that already exists. There are changes to the CRT and CRT Test Host. | |
| ExtensionProperties             | <p>This sample shows the following customization strategies for the CRT:</p><ul><li>Extension properties for the service, entity, request, and response</li><li>Triggers</li><li>Notifications</li><li>Notification handlers</li></ul> | Use extension properties to store custom field values in a database. |
| CommerceRuntime Test Host       | <p>This sample is a tool that mimics a typical CRT host that resembles Commerce Scale Unit. It supports simple testing of CRT extensions that doesn't require changes in Commerce Scale Unit or user interface (UI) clients. You just register the services that are required for the CRT, and run it.</p><p>**Note:** RealTimeTransaction service calls that might be part of a CRT extension won't work correctly. To test these service calls, use the RetailServer Test Client sample instead.</p> | |
| RetailServer Test Client        | This sample is a simple application that you can use to make Commerce Scale Unit calls, offline mode calls through the Commerce Proxy, or both. The application acts as a client. It resembles the POS clients but requires no UI changes. Therefore, it supports rapid testing and development. You can use it to verify customizations of the channel database, RTS, CRT, and/or Commerce Scale Unit before you hand them off to the UI team. | |
| OnlineStore                     | This sample is an ASP.NET implementation that showcases the use of the Ecommerce SDK. It includes both a store front and a publishing job. | |
| OpenIdConnectUtility            | This sample lets you call Commerce Scale Unit in a customer context (C2) by using a Google Identity. | |
| CashDispenser (HardwareStation) | This sample shows how to customize Retail Hardware Station so that a cash dispenser can be integrated. | Create a new Hardware Station project and support for new peripherals. |
| Rambler (HardwareStation)       | This sample shows how to customize Hardware Station so that a Rambler Mobile Card Reader can be integrated. | Create a new Hardware Station project and support for new peripherals. |
| AbandonedCartConnector          | <p>This sample provides a framework for retrieving carts from Retail Server and sending notifications to customers at time intervals that you define. The sample includes integration for Azure Cosmos DB to track cart IDs and timestamps. It also includes integration for Emarsys to send emails.</p><p>For more information about this sample, see [Detect abandoned carts and send notifications to customers](../abandoned-cart-sample-app.md).</p> | <ul><li>Retrieve carts from Retail Server that haven't been modified within a definable time window.</li><li>Augment cart product IDs with additional product data, such as the product name, price, and image.</li><li>Send an email by calling an email marketing provider with cart and customer data.</li></ul> |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
