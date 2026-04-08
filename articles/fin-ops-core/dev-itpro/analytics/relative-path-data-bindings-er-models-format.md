---
title: Use a relative path in data bindings of ER models and formats
description: Learn about how the Electronic reporting tool lets you define electronic format structures and then describe how those structures should be filled.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 04/08/2026
ms.reviewer: johnmichalak
audience:  Developer, IT Pro
ms.search.region: global
ms.search.validFrom: 
ms.search.form: ERSolutionTable, ERModelMappingDesigner, EROperationDesigner, ERExpressionDesignerFormula
ms.dyn365.ops.version: 
---

# Use a relative path in data bindings of ER models and formats

[!include[banner](../includes/banner.md)]

The Electronic reporting (ER) tool lets you define electronic format structures and then describe how to fill those structures by using data and algorithms that exist in the application. For more information, see [Create Electronic reporting (ER) configurations](electronic-reporting-configuration.md). To specify the data flow for retrieving finance and operations data and using it to generate an electronic document, complete the following steps:

- Bind configured data sources to elements of the designed domain-specific data model. The model structure and selected data sources might be part of a complex hierarchical structure. Because of this complexity, final bindings can be quite large and contain many elements of different types, such as relations, tables, and methods. The bindings can become less readable and quite complex to review and understand, especially for non-owners.
- Bind data model elements with format components to define what data populates from the data model to the generated format’s output.

To improve the usability of ER mapping designers, the [relative path](er-formula-language.md#relative-path) feature was released. By default, the relative path representation option is turned on for any new instance of the application where ER design experience is enabled (Microsoft Dynamics 365 Finance, Microsoft Regulatory Configuration Service). 
The relative path parameter enables users to keep using the full path when working with this presentation of ER bindings.

:::image type="content" source="./media/relative-path-01.png" alt-text="Screenshot of user parameters." lightbox="./media/relative-path-01.png":::

When you turn on the relative path usage parameter, a single `@` character replaces the path to the parent item in the binding of the current model element. The entire binding path becomes shorter, which makes the entire mapping more obvious and easier to understand. In most cases, no additional scrolling is required in the ER designer to view all the bindings of the data model.

:::image type="content" source="./media/relative-path-02.png" alt-text="Screenshot of the model mapping designer." lightbox="./media/relative-path-02.png":::

When you start designing a new ER expression, you need to enter only one character to define a binding to a field of the parent item.

:::image type="content" source="./media/relative-path-03.png" alt-text="Screenshot of the formula designer." lightbox="./media/relative-path-03.png":::

When you decide to change the data source of the parent model item, with absolute path usage, you have to manually rebind this model item, as well as all nested items, to a new data source. When you turn on relative path usage and select a new data source to bind to a parent item, you are offered an option to automatically rebind all nested elements of this parent item with one click.

:::image type="content" source="./media/relative-path-04.png" alt-text="Screenshot of the replace existing path message." lightbox="./media/relative-path-04.png":::

If you confirm rebinding of nested items, the new parent item is placed to the path of each nested item containing the existing parent item.
This feature doesn't break the backward compatibility of the ER framework. All previously designed ER configurations work with this new feature, and no upgrades or conversions are required.

> [!NOTE]
> All changes that are introduced by mass modification of bindings of nested elements in model mappings are correctly saved in a configuration delta (trace of changes). This process allows customers to rebase their derived version of model mappings to any new base version of it that is modified by using this new feature.

## Additional resources

[ER formula language](er-formula-language.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
