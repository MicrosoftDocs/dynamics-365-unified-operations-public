---
# required metadata
title: Application module
description: An application is a unit of runtime execution with sandboxing around concepts and data used inside of it. Each application consists of pages, actions, data queries and logic that glue them together. An application is primarily described with a declarative metadata system, and can have an accompanying imperative extension model.
author: shadykdc
manager: AnnBe
ms.date: 09/17/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 
# optional metadata
# ms.search.form:
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: kashea
ms.search.validFrom:
ms.dyn365.ops.version:
---

# Application module

[!include [banner](../../../../includes/banner.md)]

An application is a unit of runtime execution with sandboxing around concepts and data used inside of it.
Each application consists of pages, actions, data queries and logic that glue them together. An application
is primarily described with a declarative metadata system, and can have an accompanying imperative extension model. <br>
The imperative extension of the application is typically defined in a script module with a designated entry point,
the [main function](#main), which allows the imperative logic to integrate with the application life cycle.

## Index

### Types

* [Application](../interfaces/services-application-iapplication.md)
* [ApplicationMetadata](../interfaces/services-application-iapplicationmetadata.md)

### Functions

* [main](services-application.md#main)

## Types


### Application

#### Hierarchy

Application <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [minVersion](../interfaces/services-application-iapplication.md#minversion) |minVersion: string (optional)  <br>|An optional marker to indicate the minimum platform version required by this component. When this is specified and the component is attempted to be loaded in an older version of the platform, the corresponding workspace is not loaded and user is directed to install a newer version of the platform.<br>  |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [appInit](../interfaces/services-application-iapplication.md#appinit) |appInit(metadata: [ApplicationMetadata](../interfaces/services-application-iapplicationmetadata.md)): any|This method is invoked at the point the application is about to run, with the instance of the application metadata loaded. The metadata passed in can be still modified to change behaviors before this method returns.<br>  |


### ApplicationMetadata

#### Hierarchy

ApplicationMetadata <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [ColorName](../interfaces/services-application-iapplicationmetadata.md#colorname) |ColorName: string (optional)  <br>|The theme color of the application<br>  |
| [Configs](../interfaces/services-application-iapplicationmetadata.md#configs) |Configs: [name: string]: any (optional)  <br>|An application can have a set of named config supplied by the author or the resource provider<br>  |
| [Description](../interfaces/services-application-iapplicationmetadata.md#description) |Description: string (optional)  <br>|The description of the application<br>  |
| [IconName](../interfaces/services-application-iapplicationmetadata.md#iconname) |IconName: string (optional)  <br>|The representative icon of the application<br>  |
| [Id](../interfaces/services-application-iapplicationmetadata.md#id) |Id: string <br>|The unique identifier of the application<br>  |
| [Title](../interfaces/services-application-iapplicationmetadata.md#title) |Title: string <br>|The title of the application<br>  |

## Functions


### main
main(metadataService: [MetadataService](../interfaces/services-business-logic-services-imetadataservice.md), dataService: [DataService](../interfaces/services-business-logic-services-idataservice.md), cacheService: [CacheService](../interfaces/services-business-logic-services-icacheservice.md), asyncService: [AsyncService](../interfaces/services-business-logic-services-iasyncservice.md)): [Application](../interfaces/services-application-iapplication.md)

The main method of a business logic module. Each business logic module (as JavaScript file) must contain one main method. The method
is invoked when the module is loaded and is being initialized. The method must return the component to run from this module.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| metadataService|[MetadataService](../interfaces/services-business-logic-services-imetadataservice.md)||
| dataService|[DataService](../interfaces/services-business-logic-services-idataservice.md)||
| cacheService|[CacheService](../interfaces/services-business-logic-services-icacheservice.md)||
| asyncService|[AsyncService](../interfaces/services-business-logic-services-iasyncservice.md)||

#### Returns [Application](../interfaces/services-application-iapplication.md)

