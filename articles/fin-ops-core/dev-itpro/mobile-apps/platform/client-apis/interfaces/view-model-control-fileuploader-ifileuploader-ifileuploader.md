---
title: FileUploader type
description: Learn about the FileUPloader type, afile uploader control type. A control for uploading files such as images and includes various properties and methods.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.date: 12/31/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.custom: 
  - bap-template
---

# FileUploader type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

File uploader control type.
A control for uploading files such as images.

### Hierarchy

[Value](view-model-control-value-ivalue-ivalue.md) <br>&nbsp;&nbsp;&nbsp;└─ FileUploader <br>

## Index

### Properties

* [container](view-model-control-fileuploader-ifileuploader-ifileuploader.md#container)
* [generic](view-model-control-fileuploader-ifileuploader-ifileuploader.md#generic)
* [getDataSource](view-model-control-fileuploader-ifileuploader-ifileuploader.md#getdatasource)
* [hidden](view-model-control-fileuploader-ifileuploader-ifileuploader.md#hidden)
* [image](view-model-control-fileuploader-ifileuploader-ifileuploader.md#image)

### Methods

* [applyDesign](view-model-control-fileuploader-ifileuploader-ifileuploader.md#applydesign)
* [canLoadFromDevice](view-model-control-fileuploader-ifileuploader-ifileuploader.md#canloadfromdevice)
* [dataContext](view-model-control-fileuploader-ifileuploader-ifileuploader.md#datacontext)
* [getDesign](view-model-control-fileuploader-ifileuploader-ifileuploader.md#getdesign)
* [getImage](view-model-control-fileuploader-ifileuploader-ifileuploader.md#getimage)
* [getValue](view-model-control-fileuploader-ifileuploader-ifileuploader.md#getvalue)
* [isEditable](view-model-control-fileuploader-ifileuploader-ifileuploader.md#iseditable)
* [loadFromFileSystem](view-model-control-fileuploader-ifileuploader-ifileuploader.md#loadfromfilesystem)
* [metadata](view-model-control-fileuploader-ifileuploader-ifileuploader.md#metadata)
* [parent](view-model-control-fileuploader-ifileuploader-ifileuploader.md#parent)
* [root](view-model-control-fileuploader-ifileuploader-ifileuploader.md#root)
* [setCamera](view-model-control-fileuploader-ifileuploader-ifileuploader.md#setcamera)
* [setValue](view-model-control-fileuploader-ifileuploader-ifileuploader.md#setvalue)

### Events

* [onDataChanged](view-model-control-fileuploader-ifileuploader-ifileuploader.md#ondatachanged)

## Properties

### container

container: boolean (optional) 

True if the control is a container.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[container](view-model-control-basecontrol-icontrol-icontrol.md#container)


### generic

generic: boolean (optional) 



> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[generic](view-model-control-basecontrol-icontrol-icontrol.md#generic)


### getDataSource

getDataSource: function(): any



> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[getDataSource](view-model-control-basecontrol-icontrol-icontrol.md#getdatasource)


### hidden

hidden: boolean

True if the control is hidden.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[hidden](view-model-control-basecontrol-icontrol-icontrol.md#hidden)


### image

image: [Image](view-model-control-image-iimage-iimage.md)




## Methods

### applyDesign


applyDesign(IDesign: [FileUploaderDesign](view-model-control-fileuploader-ifileuploader-ifileuploaderdesign.md)): void

Applies given design to the design on the control.
If a design already exists, the prototype chain of the design will be preserved.

> Overrides [Control](view-model-control-basecontrol-icontrol-icontrol.md).[applyDesign](view-model-control-basecontrol-icontrol-icontrol.md#applydesign)


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| IDesign|[FileUploaderDesign](view-model-control-fileuploader-ifileuploader-ifileuploaderdesign.md)|object containing design properties as keys|

#### Returns void

### canLoadFromDevice


canLoadFromDevice(): boolean

Returns true if the mobile phone has camera plugin.

#### Returns boolean



### dataContext


dataContext(): any



> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[dataContext](view-model-control-basecontrol-icontrol-icontrol.md#datacontext)

#### Returns any

### getDesign


getDesign(): [Design](view-model-ipage-idesign.md)

Returns the design object of this control.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[getDesign](view-model-control-basecontrol-icontrol-icontrol.md#getdesign)

#### Returns [Design](view-model-ipage-idesign.md)



### getImage


getImage(options: any): Promise &lt;string&gt;

Returns a promise of an object with image data.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| options|any|see [camera options](https://github.com/apache/cordova-plugin-camera#module_camera.CameraOptions)|

#### Returns Promise &lt;string&gt;



### getValue


getValue(): any

Gets the value of the entity that is bound to the control.

> Overrides [Value](view-model-control-value-ivalue-ivalue.md).[getValue](view-model-control-value-ivalue-ivalue.md#getvalue)

#### Returns any



### isEditable


isEditable(): boolean

Boolean indicating if the control is editable.
Returns false when either the control or its parent is not editable.
Returns true when both the control and its parent are editable.
Returns true when either the control or its parent is editable and the other is undefined.
Returns undefined if both the control's edit-ability and its parent's edit-ability is undefined.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[isEditable](view-model-control-basecontrol-icontrol-icontrol.md#iseditable)

#### Returns boolean



### loadFromFileSystem


loadFromFileSystem(file: Blob): Promise &lt;any&gt;




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| file|Blob||

#### Returns Promise &lt;any&gt;

### metadata


metadata(): [FileUploaderMetadata](view-model-control-fileuploader-ifileuploader-ifileuploadermetadata.md)

Returns the metadata object of this control.

> Overrides [Value](view-model-control-value-ivalue-ivalue.md).[metadata](view-model-control-value-ivalue-ivalue.md#metadata)

#### Returns [FileUploaderMetadata](view-model-control-fileuploader-ifileuploader-ifileuploadermetadata.md)



### parent


parent(): [Control](view-model-control-basecontrol-icontrol-icontrol.md) &#124; [Page](view-model-ipage-ipage.md)

Returns the parent (control or page) of this control.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[parent](view-model-control-basecontrol-icontrol-icontrol.md#parent)

#### Returns [Control](view-model-control-basecontrol-icontrol-icontrol.md) &#124; [Page](view-model-ipage-ipage.md)



### root


root(): [Page](view-model-ipage-ipage.md)

Returns the root form instance (page) of this control.

> Inherited from [Control](view-model-control-basecontrol-icontrol-icontrol.md).[root](view-model-control-basecontrol-icontrol-icontrol.md#root)

#### Returns [Page](view-model-ipage-ipage.md)



### setCamera


setCamera(camera: any): void

Set the camera object on the control.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| camera|any||

#### Returns void

### setValue


setValue(value: string): void

Sets the value of the control.

> Inherited from [Value](view-model-control-value-ivalue-ivalue.md).[setValue](view-model-control-value-ivalue-ivalue.md#setvalue)


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| value|string||

#### Returns void

## Events

### onDataChanged

onDataChanged: [EventHook](event-ievent-ieventhook.md) &lt;null&gt;

An event that is triggered when the input control's data changes.

> Inherited from [InputControl](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md).[onDataChanged](view-model-control-basecontrol-iinputcontrol-iinputcontrol.md#ondatachanged)




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
