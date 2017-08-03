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

# Page 


## Index

### Enumerations

* [PageDataState](../enums/view-model-ipage-pagedatastate.md)
* [PageLoadState](../enums/view-model-ipage-pageloadstate.md)

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


### PageDataState

#### Enumeration members

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [error](../enums/view-model-ipage-pagedatastate.md#error) |error:  <br>10|  |
| [loaded](../enums/view-model-ipage-pagedatastate.md#loaded) |loaded:  <br>3|  |
| [loading](../enums/view-model-ipage-pagedatastate.md#loading) |loading:  <br>2|  |
| [offline](../enums/view-model-ipage-pagedatastate.md#offline) |offline:  <br>1|  |
| [refreshing](../enums/view-model-ipage-pagedatastate.md#refreshing) |refreshing:  <br>4|  |


### PageLoadState

#### Enumeration members

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [dataLoaded](../enums/view-model-ipage-pageloadstate.md#dataloaded) |dataLoaded:  <br>|  |
| [initializing](../enums/view-model-ipage-pageloadstate.md#initializing) |initializing:  <br>|  |
| [metatdataLoaded](../enums/view-model-ipage-pageloadstate.md#metatdataloaded) |metatdataLoaded:  <br>|  |

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
| [flexSize](../interfaces/view-model-ipage-idesign.md#flexsize) |flexSize: "medium" &#124; "xx-small" &#124; "x-small" &#124; "small" &#124; "large" &#124; "x-large" &#124; "xx-large" (optional)  <br>|This property is an alias for the CSS property "flex".<br>  |
| [fontSize](../interfaces/view-model-ipage-idesign.md#fontsize) |fontSize: string (optional)  <br>|A number written as a string. E.g. "3".<br>  |
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
| [replace](../interfaces/view-model-ipage-inavigationargs.md#replace) |replace: boolean (optional)  <br>|  |
| [to](../interfaces/view-model-ipage-inavigationargs.md#to) |to: string (optional)  <br>|  Inherited from [PageTarget](../interfaces/view-model-ipage-ipagetarget.md).[to](../interfaces/view-model-ipage-ipagetarget.md#to) <br> |
| [url](../interfaces/view-model-ipage-inavigationargs.md#url) |url: string (optional)  <br>|  |


### Page

#### Hierarchy

Page <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [children](../interfaces/view-model-ipage-ipage.md#children) |children: [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md) \[ \] <br>|  |
| [dataLoadedInitially](../interfaces/view-model-ipage-ipage.md#dataloadedinitially) |dataLoadedInitially: Promise &lt;void&gt; <br>|  |
| [metadata](../interfaces/view-model-ipage-ipage.md#metadata) |metadata: [PageMetadata](../interfaces/view-model-ipage-ipagemetadata.md) <br>|  |
| [metadataLoaded](../interfaces/view-model-ipage-ipage.md#metadataloaded) |metadataLoaded: Promise &lt;void&gt; <br>|  |
| [pageContext](../interfaces/view-model-ipage-ipage.md#pagecontext) |pageContext: string <br>|  |
| [pageFilter](../interfaces/view-model-ipage-ipage.md#pagefilter) |pageFilter: DataFilter <br>|  |
| [title](../interfaces/view-model-ipage-ipage.md#title) |title: string <br>|  |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [canSubmit](../interfaces/view-model-ipage-ipage.md#cansubmit) |canSubmit(): boolean|  |
| [close](../interfaces/view-model-ipage-ipage.md#close) |close(): void|  |
| [getAction](../interfaces/view-model-ipage-ipage.md#getaction) |getAction(actionName: string): [PageLink](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md)|  |
| [getActions](../interfaces/view-model-ipage-ipage.md#getactions) |getActions(): [PageLink](../interfaces/view-model-control-pagelink-ipagelink-ipagelink.md) \[ \]|  |
| [getControl](../interfaces/view-model-ipage-ipage.md#getcontrol) |getControl(controlName: string): [Control](../interfaces/view-model-control-basecontrol-icontrol-icontrol.md)|  |
| [getDesign](../interfaces/view-model-ipage-ipage.md#getdesign) |getDesign(): [Design](../interfaces/view-model-ipage-idesign.md)|  |
| [getEntityContext](../interfaces/view-model-ipage-ipage.md#getentitycontext) |getEntityContext(): EntityRef|  |
| [getLoadState](../interfaces/view-model-ipage-ipage.md#getloadstate) |getLoadState(): string|  |
| [isEditable](../interfaces/view-model-ipage-ipage.md#iseditable) |isEditable(): boolean|  |
| [refreshData](../interfaces/view-model-ipage-ipage.md#refreshdata) |refreshData(): Promise &lt;void&gt;|  |
| [resume](../interfaces/view-model-ipage-ipage.md#resume) |resume(): Promise &lt;void&gt;|  |
| [submit](../interfaces/view-model-ipage-ipage.md#submit) |submit(): Promise &lt;[CompleteEventArgs](../interfaces/view-model-ipage-icompleteeventargs.md)&gt;|  |
| [suspend](../interfaces/view-model-ipage-ipage.md#suspend) |suspend(): void|  |

#### Events

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [onClose](../interfaces/view-model-ipage-ipage.md#onclose) |onClose: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;null&gt; <br>|  |
| [onComplete](../interfaces/view-model-ipage-ipage.md#oncomplete) |onComplete: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;any&gt; <br>|  |
| [onDataLoaded](../interfaces/view-model-ipage-ipage.md#ondataloaded) |onDataLoaded: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;any&gt; <br>|  |
| [onDataStateChanged](../interfaces/view-model-ipage-ipage.md#ondatastatechanged) |onDataStateChanged: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;[PageDataState](../enums/view-model-ipage-pagedatastate.md)&gt; <br>|  |
| [onInit](../interfaces/view-model-ipage-ipage.md#oninit) |onInit: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;any&gt; <br>|  |
| [onLoadStateChange](../interfaces/view-model-ipage-ipage.md#onloadstatechange) |onLoadStateChange: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;null&gt; <br>|  |
| [onPreInit](../interfaces/view-model-ipage-ipage.md#onpreinit) |onPreInit: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;any&gt; <br>|  |
| [onRefresh](../interfaces/view-model-ipage-ipage.md#onrefresh) |onRefresh: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;null&gt; <br>|  |
| [onSubmit](../interfaces/view-model-ipage-ipage.md#onsubmit) |onSubmit: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;[PageSubmitArgs](../interfaces/view-model-ipage-ipagesubmitargs.md)&gt; <br>|  |
| [onSyncStatusChange](../interfaces/view-model-ipage-ipage.md#onsyncstatuschange) |onSyncStatusChange: [EventHook](../interfaces/event-ievent-ieventhook.md) &lt;null&gt; <br>|  |


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
| [dataValues](../interfaces/view-model-ipage-ipagesubmitargs.md#datavalues) |dataValues: any <br>|  |
| [sender](../interfaces/view-model-ipage-ipagesubmitargs.md#sender) |sender: [Page](../interfaces/view-model-ipage-ipage.md) <br>|  |

#### Methods

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [addMessage](../interfaces/view-model-ipage-ipagesubmitargs.md#addmessage) |addMessage(message: any, type: any): any|  |
| [cancel](../interfaces/view-model-ipage-ipagesubmitargs.md#cancel) |cancel(): any|  |
| [getMessages](../interfaces/view-model-ipage-ipagesubmitargs.md#getmessages) |getMessages(): string [ ]|  |
| [isCancelled](../interfaces/view-model-ipage-ipagesubmitargs.md#iscancelled) |isCancelled(): boolean|  |
| [wait](../interfaces/view-model-ipage-ipagesubmitargs.md#wait) |wait(promise: Promise &lt;any&gt;): any|Wait on a given promise before continuing with the submission.<br>  |


### PageTarget

#### Hierarchy

PageTarget <br>&nbsp;&nbsp;&nbsp;└─ [NavigationArgs](../interfaces/view-model-ipage-inavigationargs.md) <br>

#### Properties

| Name | Signature | Description |
| ---- | --------- | ----------- |
| [params](../interfaces/view-model-ipage-ipagetarget.md#params) |params: [PageOptions](../interfaces/view-model-ipage-ipageoptions.md) (optional)  <br>|  |
| [to](../interfaces/view-model-ipage-ipagetarget.md#to) |to: string (optional)  <br>|  |

