---
title: Page module
description: Learn about the Page module, an interface that encapsulates the various properties, life cycle and event hooks associated with a page in a workspace.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 05/26/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
---

# Page module

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

The IPage interface encapsulates the various properties, life cycle and event hooks associated with a page in a workspace.
### Page data Synchronization
Pages that can submit changes (also referred to as actions) go through various stages before they're completely in sync with the server.
As soon as a page is [submitted](../interfaces/view-model-ipage-ipage.md#submit), there are three possible consequences:
* It fails client-side validation: The client logic might prevent the page from being submitted.
* The client is online: The submission is processed as soon as the application-wide sync queue is cleared.
* The client is offline: The submission is added to the application-wide sync queue and stays there as long as the client is offline.

While a submission is waiting to be synchronized, it can be in one of these states:
* Pending: The submission is still pending and can still be edited.
* Processing: The submission is currently being synchronized. In this state, any further edits are not allowed on the page.

After a submission goes through to the server, it can be in one of these states:
* Synchronized: The submission is accepted by the server and is synchronized.
* Error: The server rejects the submission and the page enters an error state.

Multiple pending submissions for a given page and context might be clubbed (and sent) together if the page is deemed to be idempotent.
This implies that the server need not process all submissions in any order and depends on the design of the page on the server.

## Index

### Enumerations

* [PageState](../enums/view-model-ipage-pagestate.md)

### Types

* [CompleteEventArgs](../interfaces/view-model-ipage-icompleteeventargs.md)
* [Design](../interfaces/view-model-ipage-idesign.md)
* [NavigationArgs](../interfaces/view-model-ipage-inavigationargs.md)
* [Page](../interfaces/view-model-ipage-ipage.md)
* [PageMetadata](../interfaces/view-model-ipage-ipagemetadata.md)
* [PageOptions](../interfaces/view-model-ipage-ipageoptions.md)
* [PageSubmitArgs](../interfaces/view-model-ipage-ipagesubmitargs.md)
* [PageTarget](../interfaces/view-model-ipage-ipagetarget.md)

## Enumerations


### PageState

#### Enumeration members

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [error](../enums/view-model-ipage-pagestate.md#error) |error:  <br>10|The page is currently in the error state, but can be refreshed in an attempt to get out of this state.<br>  |
| [loaded](../enums/view-model-ipage-pagestate.md#loaded) |loaded:  <br>3|The page is fully loaded and can be refreshed and, if possible, submitted.<br>  |
| [loading](../enums/view-model-ipage-pagestate.md#loading) |loading:  <br>2|The page is currently being loaded.<br>  |
| [offline](../enums/view-model-ipage-pagestate.md#offline) |offline:  <br>1|The page was loaded in the offline mode, thus not refreshable.<br>  |
| [refreshing](../enums/view-model-ipage-pagestate.md#refreshing) |refreshing:  <br>4|The page is currently refreshing its data.<br>  |

## Types


### CompleteEventArgs

#### Hierarchy

CompleteEventArgs <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [error](../interfaces/view-model-ipage-icompleteeventargs.md#error) |error: boolean (optional)  <br>|  |
| [navigation](../interfaces/view-model-ipage-icompleteeventargs.md#navigation) |navigation: [NavigationArgs](../interfaces/view-model-ipage-inavigationargs.md) (optional)  <br>|  |
| [processed](../interfaces/view-model-ipage-icompleteeventargs.md#processed) |processed: boolean (optional)  <br>|  |


### Design

#### Hierarchy

Design <br>&nbsp;&nbsp;&nbsp;└─ [PageLinkDesign](../interfaces/view-model-control-pagelink-ipagelink-ipagelinkdesign.md) <br>&nbsp;&nbsp;&nbsp;└─ [ContainerControlDesign](../interfaces/view-model-control-container-icontainercontrol-icontainercontroldesign.md) <br>&nbsp;&nbsp;&nbsp;└─ [InputControlDesign](../interfaces/view-model-control-basecontrol-iinputcontrol-iinputcontroldesign.md) <br>&nbsp;&nbsp;&nbsp;└─ [ImageDesign](../interfaces/view-model-control-image-iimage-iimagedesign.md) <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [alignItems](../interfaces/view-model-ipage-idesign.md#alignitems) |alignItems: string (optional)  <br>|This property is an alias for the CSS property "align-items".<br>  |
| [alignSelf](../interfaces/view-model-ipage-idesign.md#alignself) |alignSelf: string (optional)  <br>|  |
| [bindings](../interfaces/view-model-ipage-idesign.md#bindings) |bindings: any (optional)  <br>|  |
| [border](../interfaces/view-model-ipage-idesign.md#border) |border: "none" &#124; "solid" &#124; "left" &#124; "right" &#124; "top" &#124; "bottom" (optional)  <br>|The border behavior of a control. This property will not be inherited by the children.<br>  |
| [color](../interfaces/view-model-ipage-idesign.md#color) |color: string (optional)  <br>|The foreground color of the container.<br>  |
| [flexFlow](../interfaces/view-model-ipage-idesign.md#flexflow) |flexFlow: string (optional)  <br>|Specifying this property makes the component a flex container component.<br>  |
| [flexSize](../interfaces/view-model-ipage-idesign.md#flexsize) |flexSize: string (optional)  <br>|One number or two numbers written as a string. For example, "(size to grow) [(size-to-shrink)]" to accommodate available space in the immediate flex container.<br>  |
| [fontSize](../interfaces/view-model-ipage-idesign.md#fontsize) |fontSize: "medium" &#124; "xx-small" &#124; "x-small" &#124; "small" &#124; "large" &#124; "x-large" &#124; "xx-large" (optional)  <br>|The proportional text size<br>  |
| [fontWeight](../interfaces/view-model-ipage-idesign.md#fontweight) |fontWeight: "normal" &#124; "bold" (optional)  <br>|Normal or bold text.<br>  |
| [justifyItems](../interfaces/view-model-ipage-idesign.md#justifyitems) |justifyItems: "flex-start" &#124; "flex-end" &#124; "center" &#124; "space-between" (optional)  <br>|This property is an alias for the CSS property "justify-content".<br>  |
| [label](../interfaces/view-model-ipage-idesign.md#label) |label: string (optional)  <br>|  |
| [labelPosition](../interfaces/view-model-ipage-idesign.md#labelposition) |labelPosition: "stacked" &#124; "hidden" &#124; "inline" (optional)  <br>|Determines how a label is positioned, if at all. By default, labelPosition is set to stacked.<br>  |
| [name](../interfaces/view-model-ipage-idesign.md#name) |name: string (optional)  <br>|  |
| [padding](../interfaces/view-model-ipage-idesign.md#padding) |padding: "none" &#124; "small" &#124; "std" (optional)  <br>|Allows specifying the component's padding behavior.<br>  |
| [type](../interfaces/view-model-ipage-idesign.md#type) |type: [ControlType](view-model-control-basecontrol-icontrol.md#controltype) (optional)  <br>|The type of the control as a string.<br>  |


### NavigationArgs

#### Hierarchy

[PageTarget](../interfaces/view-model-ipage-ipagetarget.md) <br>&nbsp;&nbsp;&nbsp;└─ NavigationArgs <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [label](../interfaces/view-model-ipage-inavigationargs.md#label) |label: string (optional)  <br>|  |
| [options](../interfaces/view-model-ipage-inavigationargs.md#options) |options: any (optional)  <br>|  |
| [params](../interfaces/view-model-ipage-inavigationargs.md#params) |params: [PageOptions](../interfaces/view-model-ipage-ipageoptions.md) (optional)  <br>|  Inherited from [PageTarget](../interfaces/view-model-ipage-ipagetarget.md).[params](../interfaces/view-model-ipage-ipagetarget.md#params) <br> |
| [replace](../interfaces/view-model-ipage-inavigationargs.md#replace) |replace: boolean (optional)  <br>|If set to true, removes current view firing navigation from navigation history stack.<br>  |
| [to](../interfaces/view-model-ipage-inavigationargs.md#to) |to: string (optional)  <br>|  Inherited from [PageTarget](../interfaces/view-model-ipage-ipagetarget.md).[to](../interfaces/view-model-ipage-ipagetarget.md#to) <br> |
| [url](../interfaces/view-model-ipage-inavigationargs.md#url) |url: string (optional)  <br>|If provided, this link is directly opened.<br>  |


### Page

#### Hierarchy

Page <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [children](../interfaces/view-model-ipage-ipage.md#children) |children: [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md) [ ] <br>|The list of all direct children controls of the page.<br>  |
| [dataLoadedInitially](../interfaces/view-model-ipage-ipage.md#dataloadedinitially) |dataLoadedInitially: Promise &lt;void&gt; <br>|A promise which resolves when the data has loaded for the first time.<br>  |
| [initialized](../interfaces/view-model-ipage-ipage.md#initialized) |initialized: boolean <br>|True if the page instance has been initialized.<br>  |
| [metadata](../interfaces/view-model-ipage-ipage.md#metadata) |metadata: [PageMetadata](../interfaces/view-model-ipage-ipagemetadata.md) <br>|The page metadata.<br>  |
| [metadataLoaded](../interfaces/view-model-ipage-ipage.md#metadataloaded) |metadataLoaded: Promise &lt;void&gt; <br>|A promise which resolves when the metadata has finished loading.<br>  |
| [pageContext](../interfaces/view-model-ipage-ipage.md#pagecontext) |pageContext: string <br>|The current page context.<br>  |
| [pageFilter](../interfaces/view-model-ipage-ipage.md#pagefilter) |pageFilter: DataFilter <br>|The current filter applied on the page.<br>  |
| [state](../interfaces/view-model-ipage-ipage.md#state) |state: [PageState](../enums/view-model-ipage-pagestate.md) <br>|The current state of the page.<br>  |
| [syncError](../interfaces/view-model-ipage-ipage.md#syncerror) |syncError: boolean <br>|True if the page's submission is in error state. This normally happens when the server rejects submissions due to validation errors.<br>  |
| [syncPending](../interfaces/view-model-ipage-ipage.md#syncpending) |syncPending: boolean <br>|True if the page's submission is waiting to be synced.<br>  |
| [syncProcessing](../interfaces/view-model-ipage-ipage.md#syncprocessing) |syncProcessing: boolean <br>|True if the page instance is currently syncing its submission.<br>  |
| [syncUnitEditable](../interfaces/view-model-ipage-ipage.md#syncuniteditable) |syncUnitEditable: boolean <br>|True if it's possible to edit a submission while it's waiting to be synchronized.<br>  |
| [title](../interfaces/view-model-ipage-ipage.md#title) |title: string <br>|The title of the page.<br>  |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [canSubmit](../interfaces/view-model-ipage-ipage.md#cansubmit) |canSubmit(): boolean|Returns true if action page can be submitted and there are no validation error messages.<br>  |
| [close](../interfaces/view-model-ipage-ipage.md#close) |close(): void|Dispose the page instance and all its lifecycle events.<br>  |
| [getAction](../interfaces/view-model-ipage-ipage.md#getaction) |getAction(actionName: string): [PageLink](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md)|Get a page action by name.<br>  |
| [getActions](../interfaces/view-model-ipage-ipage.md#getactions) |getActions(): [PageLink](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md) [ ]|Get all page actions.<br>  |
| [getControl](../interfaces/view-model-ipage-ipage.md#getcontrol) |getControl(controlName: string): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md)|Get a page control by name.<br>  |
| [getDesign](../interfaces/view-model-ipage-ipage.md#getdesign) |getDesign(): [Design](../interfaces/view-model-ipage-idesign.md)|Get the design object associated with the page.<br>  |
| [getEntityContext](../interfaces/view-model-ipage-ipage.md#getentitycontext) |getEntityContext(): EntityRef|Get current entity context.<br>  |
| [isEditable](../interfaces/view-model-ipage-ipage.md#iseditable) |isEditable(): boolean|Returns true if the page is an Action Page<br>  |
| [refreshData](../interfaces/view-model-ipage-ipage.md#refreshdata) |refreshData(): Promise &lt;void&gt;|Force refresh page data.<br>  |
| [resume](../interfaces/view-model-ipage-ipage.md#resume) |resume(): Promise &lt;void&gt;|Resume a temporarily suspended page.<br>  |
| [submit](../interfaces/view-model-ipage-ipage.md#submit) |submit(): Promise &lt;[CompleteEventArgs](../interfaces/view-model-ipage-icompleteeventargs.md)&gt;|Submit an Action.<br>  |
| [suspend](../interfaces/view-model-ipage-ipage.md#suspend) |suspend(): void|Temporarily suspend a page.<br>  |

#### Events

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [onClose](../interfaces/view-model-ipage-ipage.md#onclose) |onClose: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;null&gt; <br>|Event that is raised when a page is closed.<br>  |
| [onComplete](../interfaces/view-model-ipage-ipage.md#oncomplete) |onComplete: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;any&gt; <br>|Event that is raised when an action is completed.<br>  |
| [onDataLoaded](../interfaces/view-model-ipage-ipage.md#ondataloaded) |onDataLoaded: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;any&gt; <br>|Event that fires when the page data has loaded.<br>  |
| [onInit](../interfaces/view-model-ipage-ipage.md#oninit) |onInit: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;any&gt; <br>|Event that fires when a page instance has been initialized, and the metadata has been loaded.<br>  |
| [onPreInit](../interfaces/view-model-ipage-ipage.md#onpreinit) |onPreInit: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;any&gt; <br>|Event that fires when a page instance has been initialized.<br>  |
| [onRefresh](../interfaces/view-model-ipage-ipage.md#onrefresh) |onRefresh: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;null&gt; <br>|Event that fires on forced page refresh, before new data has been loaded.<br>  |
| [onStateChange](../interfaces/view-model-ipage-ipage.md#onstatechange) |onStateChange: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;null&gt; <br>|Event that fires when the page state changes.<br>  |
| [onSubmit](../interfaces/view-model-ipage-ipage.md#onsubmit) |onSubmit: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;[PageSubmitArgs](../interfaces/view-model-ipage-ipagesubmitargs.md)&gt; <br>|Event that fires before an action is submitted. It can be intercepted for action validation deferring<br>  |
| [onSyncStatusChange](../interfaces/view-model-ipage-ipage.md#onsyncstatuschange) |onSyncStatusChange: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;null&gt; <br>|Event that fires when the page sync status changes.<br>  |


### PageMetadata

#### Hierarchy

PageMetadata <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [Controls](../interfaces/view-model-ipage-ipagemetadata.md#controls) |Controls: [ControlMetadata](../interfaces/view-model-control-basecontrol-icontrol-icontrolmetadata.md) \[ \] (optional)  <br>|  |
| [Design](../interfaces/view-model-ipage-ipagemetadata.md#design) |Design: [Design](../interfaces/view-model-ipage-idesign.md) (optional)  <br>|  |
| [Id](../interfaces/view-model-ipage-ipagemetadata.md#id) |Id: string (optional)  <br>|  |
| [QuickSubmit](../interfaces/view-model-ipage-ipagemetadata.md#quicksubmit) |QuickSubmit: boolean (optional)  <br>|  |
| [SourcePageId](../interfaces/view-model-ipage-ipagemetadata.md#sourcepageid) |SourcePageId: string (optional)  <br>|  |
| [SubmitButtonDesign](../interfaces/view-model-ipage-ipagemetadata.md#submitbuttondesign) |SubmitButtonDesign: [Design](../interfaces/view-model-ipage-idesign.md) (optional)  <br>|  |
| [Tasks](../interfaces/view-model-ipage-ipagemetadata.md#tasks) |Tasks: [PageMetadata](../interfaces/view-model-ipage-ipagemetadata.md) \[ \] (optional)  <br>|  |
| [Title](../interfaces/view-model-ipage-ipagemetadata.md#title) |Title: string (optional)  <br>|  |

#### Events

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [OnDataLoaded](../interfaces/view-model-ipage-ipagemetadata.md#ondataloaded) |OnDataLoaded: function(sender: [Page](../interfaces/view-model-ipage-ipage.md), dataWrapper: any): void (optional)  <br>|  |
| [OnInit](../interfaces/view-model-ipage-ipagemetadata.md#oninit) |OnInit: function(sender: [Page](../interfaces/view-model-ipage-ipage.md)): void (optional)  <br>|  |
| [OnPreInit](../interfaces/view-model-ipage-ipagemetadata.md#onpreinit) |OnPreInit: function(sender: [Page](../interfaces/view-model-ipage-ipage.md)): void (optional)  <br>|  |
| [OnSubmit](../interfaces/view-model-ipage-ipagemetadata.md#onsubmit) |OnSubmit: function(dataValues: any, args: any): void (optional)  <br>|  |
| [OnTaskSubmitted](../interfaces/view-model-ipage-ipagemetadata.md#ontasksubmitted) |OnTaskSubmitted: function(taskHandle: any, taskOptions: any): any (optional)  <br>|  |
| [OnTaskSubmitting](../interfaces/view-model-ipage-ipagemetadata.md#ontasksubmitting) |OnTaskSubmitting: function(taskOptions: any): any (optional)  <br>|  |


### PageOptions

#### Hierarchy

PageOptions <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [appId](../interfaces/view-model-ipage-ipageoptions.md#appid) |appId: string (optional)  <br>|  |
| [design](../interfaces/view-model-ipage-ipageoptions.md#design) |design: [Design](../interfaces/view-model-ipage-idesign.md) (optional)  <br>|  |
| [excludeContext](../interfaces/view-model-ipage-ipageoptions.md#excludecontext) |excludeContext: boolean (optional)  <br>|  |
| [filter](../interfaces/view-model-ipage-ipageoptions.md#filter) |filter: DataFilter (optional)  <br>|  |
| [filterLocalOnly](../interfaces/view-model-ipage-ipageoptions.md#filterlocalonly) |filterLocalOnly: boolean (optional)  <br>|  |
| [pageContext](../interfaces/view-model-ipage-ipageoptions.md#pagecontext) |pageContext: string (optional)  <br>|  |
| [pageId](../interfaces/view-model-ipage-ipageoptions.md#pageid) |pageId: string (optional)  <br>|  |
| [readOptions](../interfaces/view-model-ipage-ipageoptions.md#readoptions) |readOptions: IReadOptions (optional)  <br>|  |


### PageSubmitArgs

#### Hierarchy

PageSubmitArgs <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [dataValues](../interfaces/view-model-ipage-ipagesubmitargs.md#datavalues) |dataValues: any <br>|Get the payload of the submit action.<br>  |
| [sender](../interfaces/view-model-ipage-ipagesubmitargs.md#sender) |sender: [Page](../interfaces/view-model-ipage-ipage.md) <br>|Get the sender page instance of the submit action.<br>  |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [addMessage](../interfaces/view-model-ipage-ipagesubmitargs.md#addmessage) |addMessage(message: string, type: any): any|Add a validation error message to be displayed.<br>  |
| [cancel](../interfaces/view-model-ipage-ipagesubmitargs.md#cancel) |cancel(): any|Prevent the action from submitting.<br>  |
| [getMessages](../interfaces/view-model-ipage-ipagesubmitargs.md#getmessages) |getMessages(): string [ ]|Get all previously added messages<br>  |
| [isCancelled](../interfaces/view-model-ipage-ipagesubmitargs.md#iscancelled) |isCancelled(): boolean|Check if the submit action is cancelled.<br>  |
| [wait](../interfaces/view-model-ipage-ipagesubmitargs.md#wait) |wait(promise: Promise &lt;any&gt;): any|Wait on a given promise before continuing with the submission.<br>  |


### PageTarget

#### Hierarchy

PageTarget <br>&nbsp;&nbsp;&nbsp;└─ [NavigationArgs](../interfaces/view-model-ipage-inavigationargs.md) <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [params](../interfaces/view-model-ipage-ipagetarget.md#params) |params: [PageOptions](../interfaces/view-model-ipage-ipageoptions.md) (optional)  <br>|  |
| [to](../interfaces/view-model-ipage-ipagetarget.md#to) |to: string (optional)  <br>|  |



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
