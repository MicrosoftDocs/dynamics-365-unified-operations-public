---
# required metadata

title: Formulas and formula versions
description: enter a key sentence
author: YuyuScheller 
manager: AnnBe
ms.date: 06/01/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: enter AOT form names (PlanActivity, ReqSupplyDemandSchedule)
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: YuyuScheller
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: conradv
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Formulas and formula versions

[!include[banner](../includes/banner.md)]

A formula defines the materials, ingredients and outcomes of a specific process manufacturing process. Together with the correspondent route, the manufacturing process is defined as a whole. Formulas are required to plan and produce the production of products in the process industries.

A formula consists of the required ingredients and quantities that are required to produce a determined quantity of a formula item. Depending on the task that you perform, you can access formula functionality from **Inventory and warehouse management** or **Product information management**.

## Formulas and formula lines

In Process manufacturing production and logistics, a formula consists of one or more formula lines, which identify the ingredients or items that make up the formula. A formula line may contain BOM items, formula items, catch weight items, purchased items, co-products, or by-products. Because many items are used in multiple products, an item may be used in more than one formula.

An example of a formula might be a chocolate chip cookie formula. The ingredients for that formula use multiple lines, such as flour, sugar, eggs, butter, and chocolate chips. The chocolate chip cookie formula contains ingredients that are most likely used in other formulas. For example, while you make the chocolate chip cookies, there might be leftovers, such as crumbs, or some of the cookies may be over or under baked. These items could be set up as co-products or by-products depending on the production operations.

When you create a formula line, you use the line type to indicate how you want the program to handle the line. This is when you run master planning and producing batch orders. Each line type gives a different result. You can select from the following line types. 

| Line type     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Item          | Select **Item** when the item is a raw material or a semi-finished item that is picked from inventory or when the item is a service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Phantom       | Select **Phantom** when you want to explode any lower-level formula items that are contained in formula lines. When you estimate the batch order and the formula items are exploded, the component items are listed as formula lines in the batch order. Also, the corresponding routes are added to the production route. Formula items are exploded using the current configuration. When you use the phantom line type, you can handle production and measurement configurations that occur at different formula levels.  If you select **Phantom** for a product on the **Engineer** FastTab in the **Released product details** form and then use this product in a formula, the formula line type changes to **Phantom**. You cannot select **Phantom** for a catch weight item or for items where the production type is **Co-product**, **By-product**, or **Planning item**. |
| Pegged supply | Select **Pegged supply** to create a batch order for any formula items that are contained in formula lines. The batch order is created when you estimate the batch order. The required item quantities are reserved for the batch order.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Vendor        | Select Vendor if the production process uses a subcontractor and you want to create a sub production or a purchase order for the subcontractor. The service or work that is performed by the subcontractor must be created by using a Formula or Service item. You can attach it to the parent item as a formula line. The route must contain an operation that is assigned to the subcontractor’s operations resource. This operation is attached to the formula line using the **Oper. No. field**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |


## Formula versions

To create a new formula, you must first create a formula version before you add the formula line items with their specific characteristics. Every formula must have at least one version. The **Approved** button on a formula version becomes available only after a version record has been successfully saved. Each formula version record is associated with one or many co-products and by-products that can be produced as you produce the finished product. Many products can be made from the same ingredients in different batch sizes, multiples, or using different yields. You can create as many versions of a formula as needed.

To manage multiple active formula versions, use effective date ranges or from quantity fields. Multiple active formula versions can exist only if the date range and from quantity do not overlap.

Different to BOM versions, where it is common that one Bill of Material (BOM) might be associated to many BOM versions, it is typical for formulas, that only one version exists per Formula. Remember that only one formula version can be activated per coverage dimensions and quantity for a given product, but many formula versions might exist for other reasons, that can be selected manually when creating a batch order.

## Approve and activate formulas and formula versions

Formulas and formula versions must be approved before they can be used for planning and production. Although formulas are usually activated before they are used, you can select a formula version during production that is approved, but not activated.

To secure a formula or formula version, you can set **Block editing** and **Block removal of approval parameters** in the **Production control parameters** form.

If you select **Block editing** and the formula is approved, no fields in the formula lines can be deleted or edited. However, if you remove the approval of the formula, you can delete and modify the formula lines. You can also create new formulas and new formula versions.

If you select **Block removal of approval**, you cannot un-approve an approved formula or formula version. However, you can create new formulas and new formula versions, and you can remove activation of the formula version.

You can add more levels of control by using electronic signature functionality. When a user is set up to require electronic signature on formula approval, a **Signature** form is displayed at activation of the formula. You must be authorized to sign electronically and the certificate must be successfully validated for the change to be committed. If your signature cannot be authenticated, the approval or removal of approval is denied and the change that initiated it is returned to its original state.


## Use the Scalable feature
The Scalable feature is available only if all item components in the formula are set to **Variable consumption**. It is not available for **Fixed consumption** or **Step consumption**. By using the scalable feature, any change that you make to an ingredient in a formula will also adjust the quantity of the other ingredients that you select. The size of the formula is also adjusted. Likewise, any change in the formula size will change the quantity of all ingredients that are scalable. This feature is specifically for formula creation and maintenance and does not indicate whether the ingredient quantity will scale up or down on a batch order.


## Use Step consumption
Step consumption eliminates the requirement to enter a quantity on the **Formula line** tab for an ingredient. Instead, Step consumption is configured to have a **From series** and a **Quantity**. Based on the batch order quantity, the information from the Step consumption per series record that satisfies this quantity is selected. This is useful where the consumption rate is not linear with the batch order size and only increases the requirement when a certain quantity threshold is met. To enable this feature for a new formula, change the formula setting under the **Consumption calculation group** from **Standard** to **Step** for the applicable ingredient. You specify this consumption method on the **Setup** tab in the **Formula line** form.

