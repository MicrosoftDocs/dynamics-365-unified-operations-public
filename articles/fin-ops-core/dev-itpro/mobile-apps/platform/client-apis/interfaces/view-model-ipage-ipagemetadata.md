---
title: PageMetadata type
description: PageMetadata type
author: tonyafehr
ms.date: 08/01/2017
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
---

# PageMetadata type

[!include [banner](../../../../includes/banner.md)]

### Hierarchy

PageMetadata

## Index

### Properties

* [Controls](view-model-ipage-ipagemetadata.md#controls)
* [Design](view-model-ipage-ipagemetadata.md#design)
* [ID](view-model-ipage-ipagemetadata.md#id)
* [QuickSubmit](view-model-ipage-ipagemetadata.md#quicksubmit)
* [SourcePageId](view-model-ipage-ipagemetadata.md#sourcepageid)
* [SubmitButtonDesign](view-model-ipage-ipagemetadata.md#submitbuttondesign)
* [Tasks](view-model-ipage-ipagemetadata.md#tasks)
* [Title](view-model-ipage-ipagemetadata.md#title)

### Events

* [OnDataLoaded](view-model-ipage-ipagemetadata.md#ondataloaded)
* [OnInit](view-model-ipage-ipagemetadata.md#oninit)
* [OnPreInit](view-model-ipage-ipagemetadata.md#onpreinit)
* [OnSubmit](view-model-ipage-ipagemetadata.md#onsubmit)
* [OnTaskSubmitted](view-model-ipage-ipagemetadata.md#ontasksubmitted)
* [OnTaskSubmitting](view-model-ipage-ipagemetadata.md#ontasksubmitting)

## Properties

### Controls

Controls: [ControlMetadata](view-model-control-basecontrol-icontrol-icontrolmetadata.md)\[\] (optional) 

### Design

Design: [Design](view-model-ipage-idesign.md) (optional) 




### ID

ID: string (optional) 




### QuickSubmit

QuickSubmit: boolean (optional) 




### SourcePageId

SourcePageId: string (optional) 




### SubmitButtonDesign

SubmitButtonDesign: [Design](view-model-ipage-idesign.md) (optional) 




### Tasks

Tasks: [PageMetadata](view-model-ipage-ipagemetadata.md)\[\] (optional) 




### Title

Title: string (optional) 




## Events

### OnDataLoaded

OnDataLoaded: function(sender: [Page](view-model-ipage-ipage.md), dataWrapper: any): void (optional) 




### OnInit

OnInit: function(sender: [Page](view-model-ipage-ipage.md)): void (optional) 




### OnPreInit

OnPreInit: function(sender: [Page](view-model-ipage-ipage.md)): void (optional) 




### OnSubmit

OnSubmit: function(dataValues: any, args: any): void (optional) 




### OnTaskSubmitted

OnTaskSubmitted: function(taskHandle: any, taskOptions: any): any (optional) 




### OnTaskSubmitting

OnTaskSubmitting: function(taskOptions: any): any (optional) 






[!INCLUDE[footer-include](../../../../../../includes/footer-banner.md)]