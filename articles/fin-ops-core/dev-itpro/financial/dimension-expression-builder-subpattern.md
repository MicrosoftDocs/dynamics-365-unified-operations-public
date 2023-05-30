---
# required metadata

title: Dimension Expression Builder subpattern
description: This article describes the Dimension Expression Builder subpattern, which is applied to container controls that use the Dimension Expression Builder control.  
author: RyanCCarlson2
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 6ab0f75d-3168-4dfe-b2ce-d17d3861216e
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Dimension Expression Builder subpattern

[!include [banner](../includes/banner.md)]

This article describes the Dimension Expression Builder subpattern, which is applied to container controls that use the Dimension Expression Builder control.  

## Usage

The Dimension Expression Builder pattern is used when you have a group or tab page that uses the Dimension Expression Builder control.

## Wireframe

[![Wireframe for container.](media/dimensionexpressionbuilderwireframe.png)](./media/dimensionexpressionbuilderwireframe.png)

## Model
### High-level structure

TabPage | Group

*TopFieldGroup (Group) \[Optional\]* – **Note:** A field subpattern is used.

*DEBGroup (Group) \[0..N\]*

Dimension Expression Builder

*Dimension Expression Builder \[0..N\]*

### Core components

-   Apply the Dimension Expression Builder subpattern to the TabPage or Group control.

## UX guidelines
None

## Examples
Form: **BudgetControlConfiguration (RulesDetailsCriteriaFastTabPage)** (**Budgeting** &gt; **Setup** &gt; **Budget control** &gt; **Budget control configuration**) [![Example of form.](media/dimensionexpressionbuilderexample.png)](./media/dimensionexpressionbuilderexample.png)

## Appendix
### Frequently asked questions

This section will have answers to frequently asked questions that are related to this guideline/pattern.

### Open issues

None

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
