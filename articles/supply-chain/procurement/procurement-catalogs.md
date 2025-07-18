---
title: Procurement catalogs overview
description: Learn how purchasing professionals can set up and maintain procurement catalogs, which define the services that company employees can order for internal use.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage, CatDisplayProductRelationAdd
ms.topic: overview
ms.date: 08/26/2024
ms.custom: 
  - bap-template
---

# Procurement catalogs overview

[!include [banner](../includes/banner.md)]

This article describes, at a high level, how purchasing professionals can set up and maintain procurement catalogs. Procurement catalogs define the items and services that company employees can order for internal use.

Purchasing professionals can create and maintain catalogs of the items and services that can be purchased for internal use in an organization. After catalogs are set up, company employees can create purchase requisitions to order from them. The catalogs can be used to enforce purchasing policies, so that employees can order only the items and services that are allowed for their buying legal entity. When you create a procurement catalog, you should consider the following tasks:

- Configure your procurement category hierarchy before you create the catalog.
- Determine which products you want your employees to be able to order. You can show or hide specific products in a catalog node, or you can show or hide all the products in a node.
- Determine how many procurement catalogs you require. Access to a procurement catalog is determined by the catalog policy rule that you configure for the legal entity and operating unit that an employee is assigned to.

Several factors determine the products that employees can order and the procurement categories that they can use when they create purchase requisitions:

- The category access policy rule in the purchasing policy determines which procurement categories are available in the purchase requisition. If no rule is defined, all procurement categories are available.
- Employees can order a product only if it's in the active procurement catalog for your organization, and if it's in an enabled node and not hidden. The product must also be in a category that a particular employee has access to according to the category access policy rule.
- The catalog policy rule specifies the catalog that is used. If no catalog policy rule is defined, the category access rule alone determines the products that an employee can order on the requisition.

## Prerequisites

The following table describes the tasks that must be completed before a purchasing professional can create a procurement catalog.

| Task | Role | Description |
|--|--|--|
| Set up a procurement category hierarchy. | Purchasing manager | Procurement category hierarchies classify items or transactions for reporting and analysis. By using a procurement category hierarchy, companies can strategically manage categories, products, vendors, and other procurement factors from a central location. One procurement category hierarchy is defined for a whole organization. The catalog is based on the procurement category hierarchy: the categories in the hierarchy become nodes in the catalog. The vendors and products are included in your catalog. |
| Add vendors and products to procurement categories. | Purchasing manager | When the procurement category hierarchy is created for your organization, each procurement category can be associated with specific vendors, products, and so on. These associations are copied automatically to the catalog. |

## Set up a catalog

After the prerequisites have been met, you can set up catalogs. You can create either one catalog that your whole organization uses or multiple catalogs that the various divisions in your organization use. If you create one catalog for the whole organization, access to the catalog is controlled by your purchasing policy rules.  

The catalog defines which products are available when purchase requisitions are created, but you can use category access policies rules to apply additional restrictions. Because the nodes in a catalog are procurement categories, they can be suppressed by a category access policy rule. In this case, the products in that category aren't available for employees to use on requisitions. You define category access policy rules on the **Purchasing policies** page. The following table describes the tasks that must be completed to set up a catalog.

| Task | Role | Description |
|--|--|--|
| Create a new catalog. | Purchasing agent | When you create a catalog, you specify a name and description for the catalog. You also define whether the catalog is updated manually or automatically, and specify the catalog owner. |
| Control whether products are available in the catalog. | Purchasing agent | Because the products are inherited from the procurement categories, they all appear in the appropriate catalog nodes. You can control whether all products in a node are hidden or shown when the catalog is used in a purchase requisition. You can also control whether individual products in a node are hidden or shown. |
| Publish the catalog. | Purchasing agent | Before a catalog is available for employees to use in a requisition, you must define a catalog policy rule for the catalog, set the catalog’s status to **Active**, and publish the catalog. You can deactivate catalogs that you no longer want to be available to your users. |

Updates are published either automatically or manually, depending on the option that you select for the catalog in the **Default update type** field on the **Catalogs** page. The following default update types are available for catalogs:

- *Dynamic* – The catalog is automatically updated whenever it's changed.
- *Static* – The catalogs must be manually updated.
- *Both* – If the catalog includes product categories that have a default update type of *Static*, it must be manually updated when these categories are updated. If the catalog includes product categories that have a default update type of *Dynamic*, it's automatically updated whenever it's changed.

## Related information

- [Set up a procurement category hierarchy](tasks/set-up-procurement-category-hierarchy.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]