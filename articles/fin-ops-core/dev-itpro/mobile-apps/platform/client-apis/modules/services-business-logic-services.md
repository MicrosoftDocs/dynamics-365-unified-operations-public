---
title: Services module
description: Various services that are available to the application in client runtime.
author: tonyafehr
ms.date: 08/01/2017
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
---

# Services module

[!include [banner](../../../../includes/banner.md)]

Various services that are available to the application in client runtime.

## Index

### Types

* [AsyncService](../interfaces/services-business-logic-services-iasyncservice.md)
* [CacheService](../interfaces/services-business-logic-services-icacheservice.md)
* [DataService](../interfaces/services-business-logic-services-idataservice.md)
* [MetadataService](../interfaces/services-business-logic-services-imetadataservice.md)
* [PageData](../interfaces/services-business-logic-services-ipagedata.md)

### Type aliases

* [ExpressionOperator](services-business-logic-services.md#expressionoperator)

## Types


### AsyncService

#### Hierarchy

AsyncService <br>

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [all](../interfaces/services-business-logic-services-iasyncservice.md#all) |all(...args: any [ ]): Promise &lt;any [ ]&gt;|  |
| [defer](../interfaces/services-business-logic-services-iasyncservice.md#defer) |defer &lt;T&gt;(): [Deferred](../interfaces/defer-ideferred.md) &lt;T&gt;|Creates a deferred object which can be used to return a promise from event handlers (where applicable) and resolve reject them asynchronously.<br>  |


### CacheService

#### Hierarchy

CacheService <br>

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [getData](../interfaces/services-business-logic-services-icacheservice.md#getdata) |getData(cacheKey: string): any|  |
| [setData](../interfaces/services-business-logic-services-icacheservice.md#setdata) |setData(cacheKey: string, data: any): any|  |


### DataService

#### Hierarchy

DataService <br>

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [findEntityData](../interfaces/services-business-logic-services-idataservice.md#findentitydata) |findEntityData(entityType: any, propertyName: string, propertyValue: any, includeChanges?: boolean): any|  |
| [getEntityData](../interfaces/services-business-logic-services-idataservice.md#getentitydata) |getEntityData(entityType: any, entityId: string): any|  |
| [getPageData](../interfaces/services-business-logic-services-idataservice.md#getpagedata) |getPageData(pageId: string, context: any, filter: any, allowedStaleness: number): Promise &lt;[PageData](../interfaces/services-business-logic-services-ipagedata.md)&gt;|  |


### MetadataService

#### Hierarchy

MetadataService <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [version](../interfaces/services-business-logic-services-imetadataservice.md#version) |version: string <br>|Gets the version of the platform currently running.<br>  |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [addControl](../interfaces/services-business-logic-services-imetadataservice.md#addcontrol) |addControl(componentName: string, controlName: string, controlType: [ControlType](view-model-control-basecontrol-icontrol.md#controltype), parentContainerName?: string, options?: [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md)): any|  |
| [compareVersion](../interfaces/services-business-logic-services-imetadataservice.md#compareversion) |compareVersion(versionToCompare: string): 1 &#124; -1|Compares the current platform version with a reference version.<br>  |
| [configureAction](../interfaces/services-business-logic-services-imetadataservice.md#configureaction) |configureAction(actionName: string, options: [PageMetadata](../interfaces/view-model-ipage-ipagemetadata.md)): any|Configuring an action allows specifying or overriding certain behaviors specific to actions.<br>  |
| [configureControl](../interfaces/services-business-logic-services-imetadataservice.md#configurecontrol) |configureControl(componentName: string, controlName: string, options: [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md)): any|Configuring a control allows specifying or overriding certain behaviors specific to the control. Note that the available behaviors vary by control type.<br>  |
| [configureEntity](../interfaces/services-business-logic-services-imetadataservice.md#configureentity) |configureEntity(entityName: string, options: any): any|Configuring an entity allows specifying or overriding certain behaviors specific to the entity.<br>  |
| [configureLookup](../interfaces/services-business-logic-services-imetadataservice.md#configurelookup) |configureLookup(taskName: string, lookupControlName: string, options: [LookupMetadata](../interfaces/view-model-control-lookup-ilookup-ilookupmetadata.md)): any|Configures a field on an action to behave as a lookup. Requires using an existing page which contains a list control.<br>  |
| [configurePage](../interfaces/services-business-logic-services-imetadataservice.md#configurepage) |configurePage(pageName: string, options: [PageMetadata](../interfaces/view-model-ipage-ipagemetadata.md)): any|Configuring a Page allows specifying or overriding certain behaviors specific to the Page.<br>  |
| [configureWorkspace](../interfaces/services-business-logic-services-imetadataservice.md#configureworkspace) |configureWorkspace(options: [PageMetadata](../interfaces/view-model-ipage-ipagemetadata.md)): any|Configuring a workspace allows specifying or overriding certain behaviors specific to the workspace.<br>  |
| [findAction](../interfaces/services-business-logic-services-imetadataservice.md#findaction) |findAction(actionName: string): [PageMetadata](../interfaces/view-model-ipage-ipagemetadata.md)|Gets a copy of the current metadata instance of a specified Action, for the purpose of inspecting the metadata (not to be used for changing the metadata).<br>  |
| [findControl](../interfaces/services-business-logic-services-imetadataservice.md#findcontrol) |findControl(componentMetadata: any, controlName: string): [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md)|Gets a copy of the current metadata instance of a specified control, for the purpose of inspecting the metadata (not to be used for changing the metadata).<br>  |
| [findPage](../interfaces/services-business-logic-services-imetadataservice.md#findpage) |findPage(pageName: string): [PageMetadata](../interfaces/view-model-ipage-ipagemetadata.md)|Gets a copy of the current metadata instance of a specified page, for the purpose of inspecting the metadata (not to be used for changing the metadata).<br>  |
| [getFilterExpression](../interfaces/services-business-logic-services-imetadataservice.md#getfilterexpression) |getFilterExpression(pageName: string, listControlName: string, controlName: string, operator: [ExpressionOperator](services-business-logic-services.md#expressionoperator), value: string): DataFilter|Create a DataFilter object for a list control based on the provided options.<br>  |
| [getFormReference](../interfaces/services-business-logic-services-imetadataservice.md#getformreference) |getFormReference(componentName: string, filterContext: DataFilter, excludeContext: boolean, filterLocalOnly?: boolean): [NavigationArgs](../interfaces/view-model-ipage-inavigationargs.md)|Create an INavigationArgs object for a specific page action to be used with a navigation control.<br>  |
| [hideNavigation](../interfaces/services-business-logic-services-imetadataservice.md#hidenavigation) |hideNavigation(pageNamesToHide: string [ ]): any|Hides the specified page(s) from the default landing page.<br>  |


### PageData

#### Hierarchy

PageData <br>

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [getControlValue](../interfaces/services-business-logic-services-ipagedata.md#getcontrolvalue) |getControlValue(controlName: string): any|Gets the value of a control directly from the data set loaded in the page.<br>  |
| [setControlValue](../interfaces/services-business-logic-services-ipagedata.md#setcontrolvalue) |setControlValue(controlName: string, value: any): any|Sets the value of a control directly into the data set loaded in the page.<br>  |

## Type aliases


### ExpressionOperator
ExpressionOperator: "Is" &#124; "IsNot" &#124; "Contains" &#124; "BeginsWith" &#124; "EndsWith" &#124; "GreaterThan" &#124; "LessThan" &#124; "GreaterThanOrEqual" &#124; "LessThanOrEqual"


Represents possible values for the expression operator used in defining filters and in other places



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]