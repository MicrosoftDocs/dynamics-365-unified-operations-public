---
# required metadata

title: Extend the number sequence scope
description: This article explains how developers can extend number sequence scope.
author: RobinARH
manager: AnnBe
ms.date: 04/14/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 2051
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 10031
ms.assetid: 4be8b7a1-9632-4368-af41-6811cd100a37
ms.search.region: Global
# ms.search.industry: 
ms.author: lgou
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Extend the number sequence scope

This topic explains how developers can extend number sequence scope.

The scope of a number sequence defines which organization uses the number sequence. The scope can be **Shared**, **Company**, **Legal entity**, or **Operating unit**. **Legal entity** and **Company** scopes can be combined with fiscal calendar periods to create even more specific number sequences. New number sequence scopes can be added through extensions.  

## Create enum extension for NumberSeqParameterType enum. 

In the extension, add a new enum value that for the new scope type. 

## Create enum extension for NumberSequenceType enum 

Add a new enum value for the new scope type. NumberSequenceType enum is used in NumberSequenceTableEntity and NumberSequencesReferenceEntity.

## Create table extension for NumberSequenceScope table

Add a new field for the new scope type.

## Create extension class for NumberSeqScope class
1. Create a post handler for NumberSeqScope::getValidScopeTypes method. In the event handler method, add the new scope type to the valid scope types list.
2. Create an event handler for onGetFormatSegmentShortName delegate. In the event handler, return the short name for the new scope type.
3. Create a post handler for NumberSeqScope::find method and add logic for the new scope type so the corresponding NumberSeqScope instance can be found.   
4. Create a post handler for NumberSeqScope::getId method and add logic for the new scope type so the corresponding record can be found(or created if not exist) in NumberSequenceScope table. 

## Create extension class for NumberSequenceScopeFactory class
Add a method that initializes new NumberSeqScope that represents the new scope type.

## Create form extension for NumberSequenceDetails form
Add controls that shows the new scope type to the Scope tab page.

## Create extension class for NumberSequenceDetails form
1. Create post handler for updateScopeControlVisibility method to show the new scope type when the new scope type is selected in the Scope combo box
2. Create post handler for updateScopeControlValues method to update the values of the controls in the Scope tab
3. Create post handler for createScope method to initialize a NumberSeqScope instance when the new scope type is selected.
4. Create event handler for getShortNameForParameterType delegate to return the short name for the new scope type.

## Add extension class for NumberSequenceTableEntity and NumberSequencesReferenceEntity data entities

Create post handlers for GenerateNumberSequenceScopeTypes and GenerateNumberSequenceScopeValues methods to generate NumberSequenceScope for the new scope type.


