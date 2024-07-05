---
title: Page type
description: Learn about the page object type, which includes the children, dataLoadedInitially, initialized, metadata, metadataLoaded, and other properties and methods.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 05/26/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
---

# Page type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

Page object type.

### Hierarchy

Page <br>

## Index

### Properties

* [children](view-model-ipage-ipage.md#children)
* [dataLoadedInitially](view-model-ipage-ipage.md#dataloadedinitially)
* [initialized](view-model-ipage-ipage.md#initialized)
* [metadata](view-model-ipage-ipage.md#metadata)
* [metadataLoaded](view-model-ipage-ipage.md#metadataloaded)
* [pageContext](view-model-ipage-ipage.md#pagecontext)
* [pageFilter](view-model-ipage-ipage.md#pagefilter)
* [state](view-model-ipage-ipage.md#state)
* [syncError](view-model-ipage-ipage.md#syncerror)
* [syncPending](view-model-ipage-ipage.md#syncpending)
* [syncProcessing](view-model-ipage-ipage.md#syncprocessing)
* [syncUnitEditable](view-model-ipage-ipage.md#syncuniteditable)
* [title](view-model-ipage-ipage.md#title)

### Methods

* [canSubmit](view-model-ipage-ipage.md#cansubmit)
* [close](view-model-ipage-ipage.md#close)
* [getAction](view-model-ipage-ipage.md#getaction)
* [getActions](view-model-ipage-ipage.md#getactions)
* [getControl](view-model-ipage-ipage.md#getcontrol)
* [getDesign](view-model-ipage-ipage.md#getdesign)
* [getEntityContext](view-model-ipage-ipage.md#getentitycontext)
* [isEditable](view-model-ipage-ipage.md#iseditable)
* [refreshData](view-model-ipage-ipage.md#refreshdata)
* [resume](view-model-ipage-ipage.md#resume)
* [submit](view-model-ipage-ipage.md#submit)
* [suspend](view-model-ipage-ipage.md#suspend)

### Events

* [onClose](view-model-ipage-ipage.md#onclose)
* [onComplete](view-model-ipage-ipage.md#oncomplete)
* [onDataLoaded](view-model-ipage-ipage.md#ondataloaded)
* [onInit](view-model-ipage-ipage.md#oninit)
* [onPreInit](view-model-ipage-ipage.md#onpreinit)
* [onRefresh](view-model-ipage-ipage.md#onrefresh)
* [onStateChange](view-model-ipage-ipage.md#onstatechange)
* [onSubmit](view-model-ipage-ipage.md#onsubmit)
* [onSyncStatusChange](view-model-ipage-ipage.md#onsyncstatuschange)

## Properties

### children

children: [Control](view-model-control-basecontrol-icontrol-icontrol.md) [ ]

(Read-only) The list of all direct children controls of the page.


### dataLoadedInitially

dataLoadedInitially: Promise &lt;void&gt;

(Read-only) A promise which resolves when the data has loaded for the first time.
The promise continues to stay resolved for the rest of the page life.


### initialized

initialized: boolean

(Read-only) True if the page instance has been initialized.


### metadata

metadata: [PageMetadata](view-model-ipage-ipagemetadata.md)

(Read-only) The page metadata.


### metadataLoaded

metadataLoaded: Promise &lt;void&gt;

(Read-only) A promise which resolves when the metadata has finished loading.


### pageContext

pageContext: string

The current page context.


### pageFilter

pageFilter: DataFilter

The current filter applied on the page.


### state

state: [PageState](../enums/view-model-ipage-pagestate.md)

(Read-only) The current state of the page.


### syncError

syncError: boolean

(Read-only) True if the page's submission is in error state.
This normally happens when the server rejects submissions due to validation errors.
Refer to [this article](../modules/view-model-ipage.md#page-data-synchronization) for a detailed explanation of page data synchronization.


### syncPending

syncPending: boolean

(Read-only) True if the page's submission is waiting to be synced.
Refer to [this article](../modules/view-model-ipage.md#page-data-synchronization) for a detailed explanation of page data synchronization.


### syncProcessing

syncProcessing: boolean

(Read-only) True if the page instance is currently syncing its submission.
Refer to [this article](../modules/view-model-ipage.md#page-data-synchronization) for a detailed explanation of page data synchronization.


### syncUnitEditable

syncUnitEditable: boolean

(Read-only) True if it's possible to edit a submission while it's waiting to be synchronized.
Refer to [this article](../modules/view-model-ipage.md#page-data-synchronization) for a detailed explanation of page data synchronization.


### title

title: string

(Read-only) The title of the page.


## Methods

### canSubmit


canSubmit(): boolean

Returns true if action page can be submitted
and there are no validation/error messages.

#### Returns boolean



### close


close(): void

Dispose the page instance and all its lifecycle events.

#### Returns void

### getAction


getAction(actionName: string): [PageLink](view-model-control-pagelink-ipagelink-ipagelink.md)

Get a page action by name.
These include the actions in the action sheet/menu.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| actionName|string||

#### Returns [PageLink](view-model-control-pagelink-ipagelink-ipagelink.md)



### getActions


getActions(): [PageLink](view-model-control-pagelink-ipagelink-ipagelink.md) [ ]

Get all page actions.
These include the actions in the action sheet/menu.

#### Returns [PageLink](view-model-control-pagelink-ipagelink-ipagelink.md) [ ]



### getControl


getControl(controlName: string): [Control](view-model-control-basecontrol-icontrol-icontrol.md)

Get a page control by name.
It recursively searches through all its children pages.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| controlName|string||

#### Returns [Control](view-model-control-basecontrol-icontrol-icontrol.md)



### getDesign


getDesign(): [Design](view-model-ipage-idesign.md)

Get the design object associated with the page.

#### Returns [Design](view-model-ipage-idesign.md)



### getEntityContext


getEntityContext(): EntityRef

Get current entity context.

#### Returns EntityRef



### isEditable


isEditable(): boolean

Returns true if the page is an Action Page

#### Returns boolean



### refreshData


refreshData(): Promise &lt;void&gt;

Force refresh page data.

#### Returns Promise &lt;void&gt;



### resume


resume(): Promise &lt;void&gt;

Resume a temporarily suspended page.

#### Returns Promise &lt;void&gt;



### submit


submit(): Promise &lt;[CompleteEventArgs](view-model-ipage-icompleteeventargs.md)&gt;

Submit an Action.

#### Returns Promise &lt;[CompleteEventArgs](view-model-ipage-icompleteeventargs.md)&gt;



### suspend


suspend(): void

Temporarily suspend a page.
For example, when the page is not the active view.

#### Returns void

## Events

### onClose

onClose: [EventHook](event-ievent-ieventhook.md) &lt;null&gt;

Event that is raised when a page is closed.


### onComplete

onComplete: [EventHook](event-ievent-ieventhook.md) &lt;any&gt;

Event that is raised when an action is completed.


### onDataLoaded

onDataLoaded: [EventHook](event-ievent-ieventhook.md) &lt;any&gt;

Event that fires when the page data has loaded.
The event may be fired multiple times - every time new data is loaded.


### onInit

onInit: [EventHook](event-ievent-ieventhook.md) &lt;any&gt;

Event that fires when a page instance has been initialized,
and the metadata has been loaded.


### onPreInit

onPreInit: [EventHook](event-ievent-ieventhook.md) &lt;any&gt;

Event that fires when a page instance has been initialized.
This is fired before the metadata has been loaded.


### onRefresh

onRefresh: [EventHook](event-ievent-ieventhook.md) &lt;null&gt;

Event that fires on forced page refresh, before new data has been loaded.


### onStateChange

onStateChange: [EventHook](event-ievent-ieventhook.md) &lt;null&gt;

Event that fires when the page state changes.


### onSubmit

onSubmit: [EventHook](event-ievent-ieventhook.md) &lt;[PageSubmitArgs](view-model-ipage-ipagesubmitargs.md)&gt;

Event that fires before an action is submitted.
It can be intercepted for action validation/deferring
Refer to IPageSubmitArgs to know more about the available options.


### onSyncStatusChange

onSyncStatusChange: [EventHook](event-ievent-ieventhook.md) &lt;null&gt;

Event that fires when the page sync status changes.




[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
