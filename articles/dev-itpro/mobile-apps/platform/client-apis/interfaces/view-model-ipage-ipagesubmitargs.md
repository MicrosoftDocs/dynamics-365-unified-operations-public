---
# required metadata
title: PageSubmitArgs
description: Args supplied to the OnSubmit event of the page.
author: shadykdc
manager: AnnBe
ms.date: 08/01/2017
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

# PageSubmitArgs Type
Args supplied to the OnSubmit event of the page.

### Hierarchy

PageSubmitArgs <br>

## Index

### Properties

* [dataValues](view-model-ipage-ipagesubmitargs.md#datavalues)
* [sender](view-model-ipage-ipagesubmitargs.md#sender)

### Methods

* [addMessage](view-model-ipage-ipagesubmitargs.md#addmessage)
* [cancel](view-model-ipage-ipagesubmitargs.md#cancel)
* [getMessages](view-model-ipage-ipagesubmitargs.md#getmessages)
* [isCancelled](view-model-ipage-ipagesubmitargs.md#iscancelled)
* [wait](view-model-ipage-ipagesubmitargs.md#wait)

## Properties

### dataValues

dataValues: any

Get the payload of the submit action.


### sender

sender: [Page](view-model-ipage-ipage.md)

Get the sender page instance of the submit action.


## Methods

### addMessage


addMessage(message: string, type: any): any

Add a validation/error message to be displayed.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| message|string||
| type|any||

#### Returns any

### cancel


cancel(): any

Prevent the action from submitting.

#### Returns any

### getMessages


getMessages(): string [ ]

Get all previously added messages

#### Returns string [ ]



### isCancelled


isCancelled(): boolean

Check if the submit action is cancelled.

#### Returns boolean



### wait


wait(promise: Promise &lt;any&gt;): any

Wait on a given promise before continuing with the submission.
All promises attached via wait must resolve before the submit action is performed.


#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| promise|Promise &lt;any&gt;||

#### Returns any

