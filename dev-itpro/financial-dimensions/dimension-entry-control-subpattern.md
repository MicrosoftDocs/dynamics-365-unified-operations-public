---
# required metadata

title: Dimension entry control subpattern
description: This article provides information about the Dimension Entry Control subpattern. This subpattern is used when you have a group or tab page that uses the Dimension Entry control (DEC). 
author: jasongre
manager: AnnBe
ms.date: 2015-12-03 21 - 38 - 48
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
# audience: 
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 15951
ms.assetid: 47452033-6991-450b-b0e2-9f5b79ee65d3
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Dimension entry control subpattern

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

