---
# required metadata
title: Page
description: 
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

# Page Type


### Hierarchy

Page <br>

## Index

### Properties

* [children](view-model-ipage-ipage.md#children)
* [dataLoadedInitially](view-model-ipage-ipage.md#dataloadedinitially)
* [metadata](view-model-ipage-ipage.md#metadata)
* [metadataLoaded](view-model-ipage-ipage.md#metadataloaded)
* [pageContext](view-model-ipage-ipage.md#pagecontext)
* [pageFilter](view-model-ipage-ipage.md#pagefilter)
* [title](view-model-ipage-ipage.md#title)

### Methods

* [canSubmit](view-model-ipage-ipage.md#cansubmit)
* [close](view-model-ipage-ipage.md#close)
* [getAction](view-model-ipage-ipage.md#getaction)
* [getActions](view-model-ipage-ipage.md#getactions)
* [getControl](view-model-ipage-ipage.md#getcontrol)
* [getDesign](view-model-ipage-ipage.md#getdesign)
* [getEntityContext](view-model-ipage-ipage.md#getentitycontext)
* [getLoadState](view-model-ipage-ipage.md#getloadstate)
* [isEditable](view-model-ipage-ipage.md#iseditable)
* [refreshData](view-model-ipage-ipage.md#refreshdata)
* [resume](view-model-ipage-ipage.md#resume)
* [submit](view-model-ipage-ipage.md#submit)
* [suspend](view-model-ipage-ipage.md#suspend)

### Events

* [onClose](view-model-ipage-ipage.md#onclose)
* [onComplete](view-model-ipage-ipage.md#oncomplete)
* [onDataLoaded](view-model-ipage-ipage.md#ondataloaded)
* [onDataStateChanged](view-model-ipage-ipage.md#ondatastatechanged)
* [onInit](view-model-ipage-ipage.md#oninit)
* [onLoadStateChange](view-model-ipage-ipage.md#onloadstatechange)
* [onPreInit](view-model-ipage-ipage.md#onpreinit)
* [onRefresh](view-model-ipage-ipage.md#onrefresh)
* [onSubmit](view-model-ipage-ipage.md#onsubmit)
* [onSyncStatusChange](view-model-ipage-ipage.md#onsyncstatuschange)

## Properties

### children

children: [Control](view-model-control-basecontrol-icontrol-icontrol.md) [ ]




### dataLoadedInitially

dataLoadedInitially: Promise &lt;void&gt;




### metadata

metadata: [PageMetadata](view-model-ipage-ipagemetadata.md)




### metadataLoaded

metadataLoaded: Promise &lt;void&gt;




### pageContext

pageContext: string




### pageFilter

pageFilter: DataFilter




### title

title: string




## Methods

### canSubmit


canSubmit(): boolean



#### Returns boolean

### close


close(): void



#### Returns void

### getAction


getAction(actionName: string): [PageLink](view-model-control-pagelink-ipagelink-ipagelink.md)




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| actionName|string||

#### Returns [PageLink](view-model-control-pagelink-ipagelink-ipagelink.md)

### getActions


getActions(): [PageLink](view-model-control-pagelink-ipagelink-ipagelink.md) [ ]



#### Returns [PageLink](view-model-control-pagelink-ipagelink-ipagelink.md) [ ]

### getControl


getControl(controlName: string): [Control](view-model-control-basecontrol-icontrol-icontrol.md)




#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| controlName|string||

#### Returns [Control](view-model-control-basecontrol-icontrol-icontrol.md)

### getDesign


getDesign(): [Design](view-model-ipage-idesign.md)



#### Returns [Design](view-model-ipage-idesign.md)

### getEntityContext


getEntityContext(): EntityRef



#### Returns EntityRef

### getLoadState


getLoadState(): string



#### Returns string

### isEditable


isEditable(): boolean



#### Returns boolean

### refreshData


refreshData(): Promise &lt;void&gt;



#### Returns Promise &lt;void&gt;

### resume


resume(): Promise &lt;void&gt;



#### Returns Promise &lt;void&gt;

### submit


submit(): Promise &lt;[CompleteEventArgs](view-model-ipage-icompleteeventargs.md)&gt;



#### Returns Promise &lt;[CompleteEventArgs](view-model-ipage-icompleteeventargs.md)&gt;

### suspend


suspend(): void



#### Returns void

## Events

### onClose

onClose: [EventHook](event-ievent-ieventhook.md) &lt;null&gt;




### onComplete

onComplete: [EventHook](event-ievent-ieventhook.md) &lt;any&gt;




### onDataLoaded

onDataLoaded: [EventHook](event-ievent-ieventhook.md) &lt;any&gt;




### onDataStateChanged

onDataStateChanged: [EventHook](event-ievent-ieventhook.md) &lt;[PageDataState](../enums/view-model-ipage-pagedatastate.md)&gt;




### onInit

onInit: [EventHook](event-ievent-ieventhook.md) &lt;any&gt;




### onLoadStateChange

onLoadStateChange: [EventHook](event-ievent-ieventhook.md) &lt;null&gt;




### onPreInit

onPreInit: [EventHook](event-ievent-ieventhook.md) &lt;any&gt;




### onRefresh

onRefresh: [EventHook](event-ievent-ieventhook.md) &lt;null&gt;




### onSubmit

onSubmit: [EventHook](event-ievent-ieventhook.md) &lt;[PageSubmitArgs](view-model-ipage-ipagesubmitargs.md)&gt;




### onSyncStatusChange

onSyncStatusChange: [EventHook](event-ievent-ieventhook.md) &lt;null&gt;




