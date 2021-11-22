---
title: MetadataService type
description: Provides ability to access and configure various metadata elements under the application workspace.
author: tonyafehr
ms.date: 08/01/2017
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
---

# MetadataService type

[!include [banner](../../../../includes/banner.md)]

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
1 to indicate the platform version is older than the reference version,
-1 to indicate that the platform version is newer or same as the reference version

### configureAction


configureAction(actionName: string, options: [PageMetadata](view-model-ipage-ipagemetadata.md)): any

Configuring an action allows specifying or overriding certain behaviors specific to actions.
Example:

```javascript
metadataService.configureAction('Edit-Reservation', { properties-to-set });
```


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| actionName|string|The action whose behavior is to be changed|
| options|[PageMetadata](view-model-ipage-ipagemetadata.md)|The property bag containing the properties to set on the action|

#### Returns any

### configureControl


configureControl(componentName: string, controlName: string, options: [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md)): any

Configuring a control allows specifying or overriding certain behaviors specific to the control. Note that the available behaviors vary by control type.
Example:

```javascript
metadataService.configureControl('All-Customers', 'FMCustomer_RecId', { properties-to-set });
```


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| componentName|string|A page or action that contains the control|
| controlName|string|The control whose behavior is to be changed|
| options|[ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md)|The property bag containing the properties to set on the control|

#### Returns any

### configureEntity


configureEntity(entityName: string, options: any): any

Configuring an entity allows specifying or overriding certain behaviors specific to the entity.
Example:

```javascript
metadataService.configureEntity("FMCustomer", { properties-to-set });
```


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| entityName|string|An entity name|
| options|any|The property bag containing the properties to set on the entity|

#### Returns any

### configureLookup


configureLookup(taskName: string, lookupControlName: string, options: [LookupMetadata](view-model-control-lookup-ilookup-ilookupmetadata.md)): any

Configures a field on an action to behave as a lookup. Requires using an existing page which contains a list control.
Example:

```javascript
metadataService.configureLookup('Add-Reservation', 'FMRental_Customer', { lookupPage: 'All-Customers', valueField: 'FMCustomer_RecId', displayField: 'FMCustomer_FullName'});
```


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| taskName|string|Action name|
| lookupControlName|string|The control name of the field to be given lookup behavior|
| options|[LookupMetadata](view-model-control-lookup-ilookup-ilookupmetadata.md)|Lookup configuration object|

#### Returns any

### configurePage


configurePage(pageName: string, options: [PageMetadata](view-model-ipage-ipagemetadata.md)): any

Configuring a Page allows specifying or overriding certain behaviors specific to the Page.
Example:

```javascript
metadataService.configurePage('Reservation-details', { properties-to-set });
```


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pageName|string|The page that contains the control|
| options|[PageMetadata](view-model-ipage-ipagemetadata.md)|The property bag containing the properties to set on the page|

#### Returns any

### configureWorkspace


configureWorkspace(options: [PageMetadata](view-model-ipage-ipagemetadata.md)): any

Configuring a workspace allows specifying or overriding certain behaviors specific to the workspace.
Example:

```javascript
metadataService.configureWorkspace({ properties-to-set });
```


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| options|[PageMetadata](view-model-ipage-ipagemetadata.md)|The property bag containing the properties to set on the workspace|

#### Returns any

### findAction


findAction(actionName: string): [PageMetadata](view-model-ipage-ipagemetadata.md)

Gets a copy of the current metadata instance of a specified Action, for the purpose of inspecting the metadata
(not to be used for changing the metadata).
Note: Since metadata can be changed at any time by business logic, you must be mindful of when you use this API to get a copy as
it will reflect the state of the metadata at the time the call is made.

Example:

```javascript
var newCustomerTaskMetadata = metadataService.findTask("New-customer");
```


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| actionName|string|An action name|

#### Returns [PageMetadata](view-model-ipage-ipagemetadata.md)



### findControl


findControl(componentMetadata: any, controlName: string): [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md)

Gets a copy of the current metadata instance of a specified control, for the purpose of inspecting the metadata
(not to be used for changing the metadata).
Note: Since metadata can be changed at any time by business logic, you must be mindful of when you use this API to get a copy
as it will reflect the state of the metadata at the time the call is made.

Example:

```javascript
var firstNameControl = metadataService.findControl(newCustomerTaskMetadata, 'FMCustomer_FirstName');
```


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| componentMetadata|any|A metadata instance of the page or action|
| controlName|string|A control name|

#### Returns [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md)



### findPage


findPage(pageName: string): [PageMetadata](view-model-ipage-ipagemetadata.md)

Gets a copy of the current metadata instance of a specified page, for the purpose of inspecting the metadata
(not to be used for changing the metadata).
Note: Since metadata can be changed at any time by business logic, you must be mindful of when you use this API to get a copy
as it will reflect the state of the metadata at the time the call is made.

Example:

```javascript
var reservationDetailsMetadata = metadataService.findPage("Reservation-details");
```


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pageName|string|A page name|

#### Returns [PageMetadata](view-model-ipage-ipagemetadata.md)



### getFilterExpression


getFilterExpression(pageName: string, listControlName: string, controlName: string, operator: [ExpressionOperator](../modules/services-business-logic-services.md#expressionoperator), value: string): DataFilter

Create a DataFilter object for a list control based on the provided options.
Example:
```javascript
var filter = metadataService.getFilterExpression(
 pageNames.AllCustomers, controlNames.CustomerList, controlNames.CustomerFullName, "Is", firstCustomerName),
```


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pageName|string||
| listControlName|string||
| controlName|string||
| operator|[ExpressionOperator](../modules/services-business-logic-services.md#expressionoperator)||
| value|string||

#### Returns DataFilter



### getFormReference


getFormReference(componentName: string, filterContext: DataFilter, excludeContext: boolean, filterLocalOnly?: boolean): [NavigationArgs](view-model-ipage-inavigationargs.md)

Create an INavigationArgs object for a specific page/action to be used with a navigation control.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| componentName|string|Name of the action/page|
| filterContext|DataFilter||
| excludeContext|boolean||
| filterLocalOnly?|boolean||

#### Returns [NavigationArgs](view-model-ipage-inavigationargs.md)



### hideNavigation


hideNavigation(pageNamesToHide: string [ ]): any

Hides the specified page(s) from the default landing page.
Example:

```javascript
metadataService.hideNavigation('Select-a-customer', 'Select-a-vehicle');
```


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| pageNamesToHide|string [ ]|Page name(s)|

#### Returns any



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]