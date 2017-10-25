---
# required metadata

title: Dimension entry control subpattern
description: This article provides information about the Dimension Entry Control subpattern. This subpattern is used when you have a group or tab page that uses the Dimension Entry control (DEC). 
author: jasongre
manager: AnnBe
ms.date: 06/20/2017
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
ms.custom: 15951
ms.assetid: 6baee22e-2a86-428c-b9e2-178581c57830
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Dimension entry control subpattern

[!include[banner](../includes/banner.md)]


This article provides information about the Dimension Entry Control subpattern. This subpattern is used when you have a group or tab page that uses the Dimension Entry control (DEC). 

Usage
-----

The Dimension Entry Control pattern is used when you have a group or tab page that uses the Dimension Entry control (DEC).

## Wireframe
[![decWireframe](./media/decwireframe.png)](./media/decwireframe.png)  

## Model
### High-level structure

TabPage | Group *TopFieldGroup (Group) \[Optional\]* – **Note:** A field subpattern is used. *DECGroup (Group) \[0..N\]* Dimension Entry Control *Dimension Entry Control \[0..N\]* *BottomFieldGroup (Group) \[Optional\]* – **Note:** A field subpattern is used.

### Core components

-   Apply the Dimension Entry Control subpattern to the TabPage control.

## UX guidelines
None.

## Examples
Form: **CustTable (TabFinancialDimensions)** [![decExample](./media/decexample.png)](./media/decexample.png)    

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

None.



