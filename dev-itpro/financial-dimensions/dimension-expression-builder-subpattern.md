---
# required metadata

title: Dimension Expression Builder subpattern | Microsoft Docs
description: This article describes the Dimension Expression Builder subpattern, which is applied to container controls that use the Dimension Expression Builder control.  
author: jasongre
manager: AnnBe
ms.date: 2016-01-12 22:34:57
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 29451
ms.assetid: a9c95197-d056-4239-b46a-3c963ba302ce
ms.region: Global
# ms.industry: 
ms.author: jasongre

---

# Dimension Expression Builder subpattern

This article describes the Dimension Expression Builder subpattern, which is applied to container controls that use the Dimension Expression Builder control.  

Usage
-----

The Dimension Expression Builder pattern is used when you have a group or tab page that uses the Dimension Expression Builder control.

## Wireframe
[![dimensionExpressionBuilderWireframe](./media/dimensionexpressionbuilderwireframe.png)](./media/dimensionexpressionbuilderwireframe.png)

## Model
### High-level structure

TabPage | Group

*TopFieldGroup (Group) \[Optional\]* – **Note:** A field subpattern is used.

*DEBGroup (Group) \[0..N\]*

Dimension Expression Builder

*Dimension Expression Builder \[0..N\]*

### Core components

-   Apply the Dimension Expression Builder subpattern to the TabPage or Group control.

## UX guidelines
None

## Examples
Form: **BudgetControlConfiguration (RulesDetailsCriteriaFastTabPage)** (**Budgeting** &gt; **Setup** &gt; **Budget control** &gt; **Budget control configuration**) [![dimensionExpressionBuilderExample](./media/dimensionexpressionbuilderexample.png)](./media/dimensionexpressionbuilderexample.png)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

None

