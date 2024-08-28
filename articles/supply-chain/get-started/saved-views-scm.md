---
title: Standard saved views for Supply Chain Management
description: Learn about the standard saved views that are available and explains how to enable them with an outline on customizing the standard saved views.
author: kamaybac
ms.author: kamaybac
ms.topic: how-to
ms.date: 04/19/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Standard saved views for Supply Chain Management

[!include [banner](../../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management includes several saved views that you can enable and use as needed. Some of these standard saved views are optimized and named for a specific role or task (for example, "Quality control" or "Receiving"). Others are optimized so that they include only the fields and settings that Microsoft usage statistics indicate are most often used by customers. These saved views are typically referred to as *simplified* views. This article describes the standard saved views that are available, and explains how to enable and customize them.

For complete details about how to work with saved views, including the standard saved views, after you enable them, see [Saved views](../../fin-ops-core/fin-ops/get-started/saved-views.md?toc=/dynamics365/supply-chain/toc.json).

## Customizing the standard saved views

You can customize the standard saved views, just as you can customize your own saved views. However, when you customize a standard saved view, we strongly recommend that you save your custom version under a new name. Otherwise, your customizations could be overwritten when you update Supply Chain Management.

For more information about how to customize and rename saved views, see [Saved views](../../fin-ops-core/fin-ops/get-started/saved-views.md?toc=/dynamics365/supply-chain/toc.json).

## Available saved views and how to enable them

To use any saved views, regardless of whether you will use the standard saved views, you must turn on the *Saved views* feature in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) (as of version 10.0.21, this feature is enabled by default).

The remaining sections of this article provide tables that describe the standard saved views that are currently available for each relevant module. Each table shows the name of each saved view, the page where you can find it, and a description of it. Each table also shows the name of the feature that includes the saved view. To see a standard saved view in your system, you must turn on the specified feature in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of version 10.0.25, all of the listed views are turned on by default.

## Saved views for the Inventory management module

The following table describes the saved views available for the Inventory management module.

| Page | View name | View description | Feature name |
|---|---|---|---|
| On-hand list | Financials | This simplified view lets you focus on financial information while you manage on-hand inventory. | Saved views for Inventory management<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |
| On-hand list | Quality control | This simplified view lets you focus on quality control while you manage on-hand inventory. | Saved views for Inventory management<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |
| On-hand list | Receiving | This simplified view lets you focus on receiving operations while you manage on-hand inventory. | Saved views for Inventory management<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |
| On-hand list | Shipping | This simplified view lets you focus on shipping operations while you manage on-hand inventory. | Saved views for Inventory management<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |
| Transactions | Simplified | This simplified view lets you review inventory status without being distracted by financial information and other fields that are used less often. | Saved views for Inventory management<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |
| Transfer orders | Shipping | This simplified view lets you focus on shipping operations while you manage transfer orders. | Saved views for Inventory management<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |
| Transfer orders | Receiving | This simplified view lets you focus on receiving operations while you manage transfer orders. | Saved views for Inventory management<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |
| Transfer orders | Quality control | This simplified view lets you focus on quality control while you manage transfer orders. | Saved views for Inventory management<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |
| Transfer orders | Financials | This simplified view lets you focus on financial information while you manage transfer orders. | Saved views for Inventory management<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |

## Saved views for the Master planning module

The following table describes the saved views available for the Master planning module.

| Page | View name | View description | Feature name |
|---|---|---|---|
| Planned orders: Planned order details page | Simplified | This simplified view includes only the fields that are most often used to work with the details of a single planned order. In this way, it provides a quicker overview and a streamlined work process. | Saved views for planned orders<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |
| Planned orders: Planned orders list page | Simplified | This simplified view includes only the fields that are most often used to work with the list of planned orders. In this way, it provides a quicker overview and a streamlined work process. | Saved views for planned orders<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |

## Saved views for the Procurement and sourcing module

The following table describes the saved views available for the Procurement and sourcing module.

| Page | View name | View description | Feature name |
|---|---|---|---|
| Purchase order details | Order creation | This simplified view is optimized for creating new purchase orders. | Saved views for purchase orders<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |
| Purchase order details | Inventory management | This simplified view is optimized for performing inventory-related activities, such as following up on inventory that has been received, receiving inventory, checking net requirements, and adjusting order quantities. | Saved views for purchase orders<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |
| Purchase order details | Financial management | This simplified view is optimized for performing finance-related activities, such as invoicing and checking prices, totals, and charges. | Saved views for purchase orders<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |
| Purchase order details | Order approval | This simplified view is optimized for approving purchase orders. | Saved views for purchase orders<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |

## Saved views for the Product information management module

The following table describes the saved views available for the Product information management module.

| Page | View name | View description | Feature name |
|---|---|---|---|
| Released products list | Product creation | A simplified page view that only includes the fields most often used when creating products. | Saved views for released products<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |
| Released product details | Product creation | A simplified page view that only includes the fields most often used when creating products. | Saved views for released products<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |
| Released product details | Logistical information management | A simplified page view that only includes the fields most often used when managing logistical information for products. | Saved views for released products<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |
| Released product details | Purchase information management | A simplified page view that only includes the fields most often used when managing purchase information for products. | Saved views for released products<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |
| Released product details | Sales information management | A simplified page view that only includes the fields most often used when managing sales-related information for products. | Saved views for released products<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |

## Saved views for the Production control module

The following table describes the saved views available for the Production control module.

| Page | View name | View description | Feature name |
|---|---|---|---|
| Production order BOM page | Simplified | This simplified view includes only the fields that are most often used. In this way, it provides a quicker overview and a streamlined work process. | Saved views for production control<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |
| Production order details page | Simplified | This simplified view includes only the fields that are most often used. In this way, it provides a quicker overview and a streamlined work process. | Saved views for production control<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |
| Production order picking list page | Simplified | This simplified view includes only the fields that are most often used. In this way, it provides a quicker overview and a streamlined work process. | Saved views for production control<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |
| Production orders list page | Simplified | This simplified view includes only the fields that are most often used. In this way, it provides a quicker overview and a streamlined work process. | Saved views for production control<br><br>(On by default as of version 10.0.21. Mandatory as of version 10.0.29.) |

## Saved views for the Sales and marketing module

The following table describes the saved views available for the Sales and marketing module.

| Page | View name | View description | Feature name |
|---|---|---|---|
| Packing slip journal | Journal review | This simplified view includes only the fields that are most often used to review packing slip journals. | Saved views for sales and marketing<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |
| Sales order | Order creation | This simplified view includes only the fields that are most often used to create sales orders. | Saved views for sales and marketing<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |
| Sales order | Order review | This simplified view includes only the fields that are most often used to review sales orders. | Saved views for sales and marketing<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |
| Sales quotation | Quote creation | This simplified view includes only the fields that are most often used to create sales quotations. | Saved views for sales and marketing<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |

## Saved views for the Warehouse management module

The following table describes the saved views available for the Warehouse management module.

| Page | View name | View description | Feature name |
|---|---|---|---|
| All loads | Inbound processing | This simplified view includes only the fields that are most often used to process inbound loads. | Saved views for load processing<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |
| All loads | Outbound processing | This simplified view includes only the fields that are most often used to process outbound loads. | Saved views for load processing<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |
| All shipments | Inbound processing | This simplified view includes only the fields that are most often used to process inbound shipments. | Saved views for shipment processing<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |
| All shipments | Outbound processing | This simplified view includes only the fields that are most often used to process outbound shipments. | Saved views for shipment processing<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |
| All waves | Simplified | This simplified view includes only the fields that are most often used. In this way, it provides a quicker overview and a streamlined work process. | Saved view for wave processing<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |
| Load planning workbench | Simplified | This simplified view includes only the fields that are most often used. In this way, it provides a quicker overview and a streamlined work process. | Saved view for the load planning workbench<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |
| Work details | Simplified | This simplified view includes only the fields that are most often used. In this way, it provides a quicker overview and a streamlined work process. | Saved view for the work details page<br><br>(On by default as of version 10.0.25. Mandatory as of version 10.0.29.) |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
