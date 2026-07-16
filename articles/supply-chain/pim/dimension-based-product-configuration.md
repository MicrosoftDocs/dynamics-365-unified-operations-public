---
title: Dimension-based product configuration overview
description: Dimension-based product configuration represents a simple solution for creating many product variants from a single product master and its bill of materials.
author: sgmsft
ms.author: shwgarg
ms.reviewer: kamaybac
ms.search.form: BOMConfigRule, BOMTable, ConfigChooseFromRoute, ConfigGroup, ConfigHierarchy, EcoResDimensionBasedConfiguration
ms.topic: overview
ms.date: 06/22/2026
ms.custom: 
  - bap-template
---

# Dimension-based product configuration overview

[!include [banner](../includes/banner.md)]

Dimension-based product configuration represents a simple solution for creating many product variants from a single product master and its bill of materials.

Dimension-based product configuration is one of the three built-in product configuration technologies. The two other technologies are predefined variants and constraint-based configuration. All three technologies use a product master as the starting point and let you create many product variants for one product master.

## Key concepts

Dimension-based product configuration is based on the following key concepts:

- Product masters
- Configuration product dimension
- Configuration groups
- Bill of materials (BOM)
- Configuration route
- Configuration rules

### Product masters

A product master is the starting point for any product configuration process. For the dimension-based product configuration, you need a product master with this particular configuration technology and a product dimension group that includes the configuration product dimension.

### Configuration product dimension

The configuration product dimension identifies the product variants for a product master that uses dimension-based configuration technology. Users enter the configuration dimension value to help identify the individual product variants.

### Configuration groups

Configuration groups are defined in a central repository and can be used for all dimension-based product configuration models. Configuration groups are associated with individual BOM lines and hold together a group of lines that are mutually exclusive. This means that only one line in a group can be selected for a single product variant.

### Bill of materials (BOM)

The BOM represents the building blocks for a dimension-based product configuration. It must include all the different products that you can use in any product variant. Each line in the BOM can reference a configuration group. If a line doesn't reference a configuration group, it's included in all product variants.

### Configuration route

The configuration route determines the sequence of the configuration groups, as they're displayed to the user during the product configuration process.

### Configuration rules

The configuration rules represent a mechanism for ensuring that a product included in one configuration group in a BOM enforces either an inclusion or an exclusion of a product in a different configuration group in the same BOM.

## Product modeling process

The natural sequence for building a product model for a dimension-based product starts with defining the relevant configuration groups. Ensure that all products used in the BOM have been released to the company that the product model is built for. With these building blocks in place, you can create the BOM and assign configuration groups to all relevant BOM lines. When the BOM is complete, define a configuration route to order the configuration groups in the proper sequence. [![Dimension-based product modeling process.](./media/dimension-based-product-modeling-process-v1.png)](./media/dimension-based-product-modeling-process-v1.png) If certain products from different configuration groups must or must not be used together, create configuration rules that enforce these product relationships. After the BOM has been tied together with a dimension-based product master through a BOM version and both have been approved and activated, you can create product configurations and enter a name for each configuration. Define the configurations before any transactions are generated, or do it when a specific configuration is needed.

### Suggested use

The dimension-based configuration technology works best for products with limited variability when the combination of the standard product dimensions size, color, style, and configuration is unsuitable for identifying a specific product variant. An example is a bicycle with frame height, wheel size, brake types, and different gears.

### <a name="sequence"></a>Next step

The following eight task guides are listed in the order in which you complete them.

1. [Create a dimension-based product master](tasks/create-dimension-based-product-master.md)
2. [Release a dimension-based product master](tasks/release-dimension-based-product-master.md)
3. [Complete basic setup of a released product master](tasks/complete-basic-setup-released-product-master.md)
4. [Define configuration groups](tasks/define-configuration-groups.md)
5. [Create a bill of materials for a dimension-based product master](tasks/create-bill-materials-dimension-based-product-master.md)
6. [Define configuration routes](tasks/define-configuration-route.md)
7. [Create configuration rules](tasks/create-configuration-rules.md)
8. [Create dimension-based configurations](tasks/create-dimension-based-configurations.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
