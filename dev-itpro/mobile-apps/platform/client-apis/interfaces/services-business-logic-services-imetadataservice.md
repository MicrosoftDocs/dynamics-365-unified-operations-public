---
# required metadata
title: MetadataService
description: Provides ability to access and configure various metadata elements under the application workspace.
author: shadykdc
manager: AnnBe
ms.date: 
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 
# optional metadata
# ms.search.form:
audience: Developer
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: kashea
ms.search.validFrom:
ms.dyn365.ops.version:
---

# MetadataService Type
Provides ability to access and configure various metadata elements under the application workspace.

### Hierarchy

MetadataService <br>

## Index

### Properties

* [version](services-business-logic-services-imetadataservice.md#version)

### Methods

* [addControl](services-business-logic-services-imetadataservice.md#addcontrol)
* [compareVersion](services-business-logic-services-imetadataservice.md#compareversion)
* [configureAction](services-business-logic-services-imetadataservice.md#configureaction)
* [configureControl](services-business-logic-services-imetadataservice.md#configurecontrol)
* [configureEntity](services-business-logic-services-imetadataservice.md#configureentity)
* [configureLookup](services-business-logic-services-imetadataservice.md#configurelookup)
* [configurePage](services-business-logic-services-imetadataservice.md#configurepage)
* [configureWorkspace](services-business-logic-services-imetadataservice.md#configureworkspace)
* [findAction](services-business-logic-services-imetadataservice.md#findaction)
* [findControl](services-business-logic-services-imetadataservice.md#findcontrol)
* [findPage](services-business-logic-services-imetadataservice.md#findpage)
* [getFilterExpression](services-business-logic-services-imetadataservice.md#getfilterexpression)
* [getFormReference](services-business-logic-services-imetadataservice.md#getformreference)
* [hideNavigation](services-business-logic-services-imetadataservice.md#hidenavigation)

## Properties

### version

version: string

(Read-only) Gets the version of the platform currently running.


## Methods

### addControl


addControl(componentName: string, controlName: string, controlType: [ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype), parentContainerName?: string, options?: [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md)): any




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| componentName|string||
| controlName|string||
| controlType|[ControlType](../modules/view-model-control-basecontrol-icontrol.md#controltype)||
| parentContainerName?|string||
| options?|[ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md)||

#### Returns any

### compareVersion


compareVersion(versionToCompare: string): 1 &#124; -1

Compares the current platform version with a reference version.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| versionToCompare|string|The reference version to compare with|

#### Returns 1 &#124; -1
1 to indicate the platform version is older than than the reference version,
-1 to indicate that the platform version is newer or same as the reference version

### configureAction


configureAction(actionName: string, options: [PageMetadata](view-model-ipage-ipagemetadata.md)): any




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| actionName|string||
| options|[PageMetadata](view-model-ipage-ipagemetadata.md)||

#### Returns any

### configureControl


configureControl(componentName: string, controlName: string, options: [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md)): any




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| componentName|string||
| controlName|string||
| options|[ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md)||

#### Returns any

### configureEntity


configureEntity(entityName: string, options: any): any




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| entityName|string||
| options|any||

#### Returns any

### configureLookup


configureLookup(taskName: string, lookupControlName: string, options: [LookupMetadata](view-model-control-lookup-ilookup-ilookupmetadata.md)): any




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| taskName|string||
| lookupControlName|string||
| options|[LookupMetadata](view-model-control-lookup-ilookup-ilookupmetadata.md)||

#### Returns any

### configurePage


configurePage(pageName: string, options: [PageMetadata](view-model-ipage-ipagemetadata.md)): any




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pageName|string||
| options|[PageMetadata](view-model-ipage-ipagemetadata.md)||

#### Returns any

### configureWorkspace


configureWorkspace(options: [PageMetadata](view-model-ipage-ipagemetadata.md)): any




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| options|[PageMetadata](view-model-ipage-ipagemetadata.md)||

#### Returns any

### findAction


findAction(taskName: string): [PageMetadata](view-model-ipage-ipagemetadata.md)




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| taskName|string||

#### Returns [PageMetadata](view-model-ipage-ipagemetadata.md)

### findControl


findControl(componentMetadata: any, controlName: string): [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md)




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| componentMetadata|any||
| controlName|string||

#### Returns [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md)

### findPage


findPage(pageName: string): [PageMetadata](view-model-ipage-ipagemetadata.md)




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pageName|string||

#### Returns [PageMetadata](view-model-ipage-ipagemetadata.md)

### getFilterExpression


getFilterExpression(pageName: string, listControlName: string, controlName: string, operator: [ExpressionOperator](../modules/services-business-logic-services.md#expressionoperator), value: any): DataFilter




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pageName|string||
| listControlName|string||
| controlName|string||
| operator|[ExpressionOperator](../modules/services-business-logic-services.md#expressionoperator)||
| value|any||

#### Returns DataFilter

### getFormReference


getFormReference(componentName: string, filterContext: any, excludeContext: boolean, filterLocalOnly?: boolean): [NavigationArgs](view-model-ipage-inavigationargs.md)




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| componentName|string||
| filterContext|any||
| excludeContext|boolean||
| filterLocalOnly?|boolean||

#### Returns [NavigationArgs](view-model-ipage-inavigationargs.md)

### hideNavigation


hideNavigation(pageNamesToHide: string [ ]): any




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pageNamesToHide|string [ ]||

#### Returns any

