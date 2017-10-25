---
# required metadata

title: Extend the number sequence scope
description: This topic explains how developers can extend number sequence scope.
author: RobinARH
manager: AnnBe
ms.date: 04/14/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
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

This topic shows you how to extend the number sequence scope.

The scope of a number sequence defines which organization uses the number sequence. The scope can be **Shared**, **Company**, **Legal entity**, or **Operating unit**. **Company** and **Legal entity** scopes can be combined with fiscal calendar periods to create even more specific number sequences. New number sequence scopes can be added through extensions.  

To create a new scope and have it show up in the client, complete the following steps:

1. Create an enum extension for **NumberSeqParameterType**. In the extension, add a new enum value for the new scope type. 
1. Create an enum extension for **NumberSequenceType**. Add a new enum value for the new scope type. The **NumberSequenceType** enum is used in **NumberSequenceTableEntity** and **NumberSequencesReferenceEntity**.
1. Create a table extension for the **NumberSequenceScope** table. Add a new field for the new scope type.
1. Create an extension class for **NumberSeqScope** class.
  1. Create a post handler for the **NumberSeqScope::getValidScopeTypes** method. In the event handler method, add the new scope type to the valid scope types list.
  1. Create an event handler for the **onGetFormatSegmentShortName** delegate. In the event handler, return the short name for the new scope type.
  1. Create a post handler for the **NumberSeqScope::find** method and add logic for the new scope type so the corresponding **NumberSeqScope** instance can be found.   
  1. Create a post handler for the **NumberSeqScope::getId** method and add logic for the new scope type, so the corresponding record can be found (or created if it does not exist) in the **NumberSequenceScope** table. 
1. Create an extension class for the **NumberSequenceScopeFactory** class. Add a method that initializes the new **NumberSeqScope** that represents the new scope type.
1. Create a form extension for the **NumberSequenceDetails** form. Add controls that show the new scope type to the **Scope** tab.
1. Create an extension class for the **NumberSequenceDetails** form.
  1. Create a post handler for the **updateScopeControlVisibility** method to show the new scope type when the new scope type is selected in the **Scope** box.
  2. Create a post handler for the **updateScopeControlValues** method to update the values of the controls in the **Scope** tab.
  3. Create a post handler for the **createScope** method to initialize a **NumberSeqScope** instance when the new scope type is selected.
  4. Create an event handler for the **getShortNameForParameterType** delegate to return the short name for the new scope type.
1. Add an extension class for the **NumberSequenceTableEntity** and **NumberSequencesReferenceEntity** data entities. Create post handlers for the **GenerateNumberSequenceScopeTypes** and **GenerateNumberSequenceScopeValues** methods to generate the **NumberSequenceScope** for the new scope type.


