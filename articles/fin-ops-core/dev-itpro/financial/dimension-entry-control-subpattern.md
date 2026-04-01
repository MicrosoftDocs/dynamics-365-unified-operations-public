---
title: Dimension Entry Control subpattern
description: Learn about the Dimension Entry Control subpattern, including outlines on usage, the model's high-level structure, UX guidelines, and examples.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 03/27/2026
ms.reviewer: johnmichalak
ms.assetid: 6baee22e-2a86-428c-b9e2-178581c57830
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Dimension Entry Control subpattern

[!include [banner](../includes/banner.md)]

This article provides information about the Dimension Entry Control subpattern. Use this subpattern when you have a group or tab page that uses the Dimension Entry control (DEC).

## Usage

Use the Dimension Entry Control pattern when you have a group or tab page that uses the Dimension Entry control (DEC).

## Wireframe

:::image type="content" source="media/decwireframe.png" alt-text="Screenshot of the wireframe for Dimension Entry Control subpattern.":::

## Model

### High-level structure

TabPage | Group *TopFieldGroup (Group) \[Optional\]* – **Note:** A field subpattern is used.

*DECGroup (Group) \[0..N\]* Dimension Entry Control *Dimension Entry Control \[0..N\]* *BottomFieldGroup (Group) \[Optional\]* – **Note:** A field subpattern is used.

### Core components

- Apply the Dimension Entry Control subpattern to the TabPage control.

## UX guidelines

None.

## Examples

Form: **CustTable (TabFinancialDimensions)**

:::image type="content" source="media/decexample.png" alt-text="Screenshot of the example for CustTable using TabFinancialDimensions.":::

## Appendix

### Frequently asked questions

This section contains answers to frequently asked questions that are related to this guideline or pattern.

### Open issues

None.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
