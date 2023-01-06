---
title: Formulas and formula versions
description: This article provides information about formulas and formula versions. A formula defines the materials, ingredients, and outcomes of a specific process in process manufacturing. Formulas are used to plan and produce products in process manufacturing.
author: johanhoffmann 
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: PlanActivity, ReqSupplyDemandSchedule, EcoResProductProdTypeFormulaNoActiveFormulaFormPart
ms.topic: conceptual
ms.date: 01/06/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Formulas and formula versions

[!include [banner](../includes/banner.md)]

A formula defines the materials, ingredients, and outcomes of a specific process in process manufacturing. Together with the corresponding route, the formula defines the whole process in process manufacturing. Formulas are used to plan and produce products in process manufacturing.

A formula consists of the ingredients and quantities that are required in order to produce a specific quantity of a formula item. Depending on the task that you perform, you can access formula functionality from Inventory and warehouse management or Product information management.

## Formulas and formula lines

A formula consists of one or more formula lines that identify the ingredients or items that make up the formula. A formula line can contain Bill of materials (BOM) items, formula items, catch-weight items, purchased items, co-products, or by-products. Because many items are used in multiple products, an item can be used in more than one formula.

An example of a formula is the formula for a chocolate chip cookie. The ingredients for this formula use multiple lines, such as flour, sugar, eggs, butter, and chocolate chips. The formula for the chocolate chip cookie contains ingredients that are likely used in other formulas. While you make the chocolate chip cookies, there might be leftovers, such as crumbs, or some of the cookies might be overbaked or undercooked. These items can be set up as co-products or by-products, depending on the production operations.

When you create a formula line, you use the line type to indicate how the system should handle the line when you run master planning and produce batch orders. Each line type gives a different result. The following table describes the line types that you can select.

| Line type     | Description  |
|---------------|--------------|
| Item          | Select *Item* when the item is a raw material or a semi-finished item that is picked from inventory or when the item is a service. |
| Phantom       | Select *Phantom* when you want to explode any lower-level formula items that are contained on formula lines. When you estimate the batch order, and the formula items are exploded, the component items are listed as formula lines on the batch order. Additionally, the corresponding routes are added to the production route. Formula items are exploded by using the current configuration. When you use the *Phantom* line type, you can handle production and measurement configurations that occur at different formula levels. If you select *Phantom* for a product on the **Engineer** FastTab of the **Released product details** page and then use this product in a formula, the line type of the formula line is changed to *Phantom*. You can't select *Phantom* for a catch-weight item, or for items where the production type is *Co-product*, *By-product*, or *Planning item*. |
| Pegged supply | Select *Pegged supply* to create a batch order, production order, kanban, transfer order, or purchase order for the ingredient that is contained on the formula line. The related order is determined based on the default order settings and the production type of the ingredient, and is created when you estimate the batch order. The required ingredient quantities are reserved for the batch order. |
| Vendor        | Select *Vendor* if the production process uses a subcontractor, and you want to create a subproduction or purchase order for the subcontractor. The service or work that the subcontractor performs must be created by using a formula item or service item. You can attach the item to the parent item as a formula line. The route must contain an operation that is assigned to the subcontractor's operations resource. This operation is attached to the formula line by using the **Oper. No.** field. |

## Formula versions

When you create a new formula, you must first create a formula version before you add the formula line items and their specific characteristics. Every formula must have at least one version. The **Approved** button on a formula version becomes available only after a version record has been successfully saved. Each formula version record is associated with one or many co-products and by-products that can be produced as you produce the finished product. Many products can be made from the same ingredients in different batch sizes, in multiples, or by using different yields. You can create as many versions of a formula as you require.

To manage multiple active formula versions, use effective date ranges or "from" quantity fields. Multiple active formula versions can exist only if the date range and "from" quantity don't overlap.

Unlike BOMs, where one BOM is often associated with many BOM versions, only one formula version typically exists per formula. Remember that only one formula version can be activated for the coverage dimensions and quantity for a given product. However, many formula versions might exist for other reasons, and you can manually select them when you create a batch order.

## Approve and activate formulas and formula versions

Formulas and formula versions must be approved before they can be used for planning and production. Formulas are usually activated before they're used. However, during production, you can select a formula version that is approved, but that isn't activated.

To help secure a formula or formula version, you can set the **Block editing** and **Block removal of approval** parameters on the **Production control parameters** page.

If you select **Block editing**, and the formula is approved, no fields on the formula lines can be deleted or edited. However, if you remove the approval of the formula, you can delete and modify the formula lines. You can also create new formulas and new formula versions.

If you select **Block removal of approval**, you can't remove the approval of an approved formula or formula version. However, you can create new formulas and new formula versions, and you can remove the activation of the formula version.

You can add more levels of control by using the electronic signature functionality. When a user is set up so that an electronic signature is required at the time of formula approval, a **Signature** page appears when the formula is activated. The user must be authorized to sign electronically, and the certificate must be successfully validated before the change can be committed. If the signature can't be authenticated, the approval or removal of approval is denied, and the change that initiated the approval or removal of approval is returned to its original state.

## Use the Scalable feature

The Scalable feature is available only if all the item components in the formula are set to **Variable consumption**. The feature isn't available if item components are set to **Fixed consumption** or **Step consumption**. When the Scalable feature is used, if you change an ingredient in a formula, the quantity of the other ingredients that you select is adjusted. The size of the formula is also adjusted. Likewise, if you change the formula size, the quantity of all scalable ingredients is changed. This feature is intended specifically for formula creation and maintenance. It doesn't indicate whether the quantity of an ingredient will be scaled up or down on a batch order.

## Use Step consumption

Step consumption eliminates the requirement that you must enter a quantity on the **Formula line** tab for an ingredient. Instead, Step consumption is configured so that it has a **From series** value and a **Quantity** value. The information from the Step consumption per series record that satisfies the quantity on the batch order is selected. Step consumption is useful when the consumption rate isn't linear with respect to the batch order size and only increases the requirement when a specific quantity threshold is met. To enable this feature for a new formula, under the **Consumption calculation** group, change the formula setting for the applicable ingredient from **Standard** to **Step**. You specify this consumption method on the **Setup** tab of the **Formula line** page.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]