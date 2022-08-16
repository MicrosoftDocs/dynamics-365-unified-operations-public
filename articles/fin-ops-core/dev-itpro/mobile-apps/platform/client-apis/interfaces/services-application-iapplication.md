---
title: Application type
description: Represents a runtime instance of an application.
author: jasongre
ms.date: 05/24/2022
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
---

# Application type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Represents a runtime instance of an application.

### Hierarchy

Application <br>

## Index

### Properties

* [minVersion](services-application-iapplication.md#minversion)

### Methods

* [appInit](services-application-iapplication.md#appinit)

## Properties

### minVersion

minVersion: string (optional) 

An optional marker to indicate the minimum platform version required by this component. When this is specified and the component is
attempted to be loaded in an older version of the platform, the corresponding workspace is not loaded and user is directed to install a newer version of the platform.


## Methods

### appInit


appInit(metadata: [ApplicationMetadata](services-application-iapplicationmetadata.md)): any

This method is invoked at the point the application is about to run, with the instance of the application metadata loaded.
The metadata passed in can be still modified to change behaviors before this method returns.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| metadata|[ApplicationMetadata](services-application-iapplicationmetadata.md)||

#### Returns any



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
