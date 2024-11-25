---
title: PageSubmitArgs type
description: Learn about the PageSubmitArgs type, which includes the dataValues and sender properties and the addMessage, cancel, getMessages, isCancelled, and wait methods.
author: jasongre
ms.author: jasongre
ms.topic: article
ms.date: 05/26/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
---

# PageSubmitArgs type

[!include [banner](../../../../includes/banner.md)]
[!include [mobile app deprecated](../../../../includes/mobile-app-deprecation-banner.md)]

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



[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]
