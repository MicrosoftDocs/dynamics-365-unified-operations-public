---
title: Nomenclature of product variant numbers and names
description: Learn how you can set up a product number nomenclature to replace the fixed [Product master number - Configuration - Size - Color - Style] format.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 11/03/2017
ms.reviewer: kamaybac
ms.search.form: EcoResNomenclature, EcoResProductDimensionGroup, EcoResProductVariantMaintainWorkspace, PCProductConfigurationModelDetails
ms.assetid: 3fe69fb7-5c32-423c-98a8-2f53186cda68
---

# Nomenclature of product variant numbers and names

[!include [banner](../includes/banner.md)]

This article describes how you can set up a product number nomenclature to replace the fixed [Product master number - Configuration - Size - Color - Style] format. The new nomenclature has a targeted format that includes the product master number, active product dimensions, and text delimiters of your choice. You can also create a nomenclature for product names. Finally, you can build a nomenclature to identify configurations that are created by the constraint-based product configurator. These nomenclatures can contain attributes of your choice.

The new nomenclatures for product variant numbers and product variant names let you include segments in the identifiers for product variants. These segments can include the product master number and name, product dimension IDs and names, number sequences, text constants, and attributes. This functionality lets you quickly find a specific product variant when you create a sales order or a purchase order. You create nomenclatures for both product variant numbers and product variant names by using the **Product nomenclature** page. To open this page, click **Product information management** &gt; **Setup**.

## Nomenclature of predefined product variants
Product variants are generated for product masters according to one of three configuration technologies:

-   Predefined variants
-   Constraint-based
-   Dimension-based

Each product variant has a number and a name, and the product variant identification nomenclatures let you select the segments that will be included in each product variant number or name. You can select the following segments on the **Product nomenclature** page:

-   Product master number
-   Product master name
-   Number sequence value
-   Text constant
-   Product dimensions
    -   Configuration ID or name
    -   Color ID or name
    -   Size ID or name
    -   Style ID or name

After you define a product variant identification number nomenclature, you can associate it with a product dimension group. All product masters that reference this product dimension group will then be assigned product variant numbers according to the nomenclature. However, product variant name nomenclatures can't be associated with product dimension groups. You can also assign a product variant identification nomenclature directly to a product master. In this case, the product variants that belong to the product master will be assigned product variant numbers and names according to the nomenclatures.

### Example

A T-shirt (TS1234) is produced in three sizes (S, M, L), four colors (Red, Green, Blue, Yellow), and two styles (Polo, V). Therefore, 24 product variants are possible (= 3 × 4 × 2). You create a product variant number nomenclature that has the following segments:

1.  Product master number
2.  Text constant: "-"
3.  Color
4.  Text constant: "-"
5.  Size
6.  Text constant: "-"
7.  Style

In this case, the product variant number for a red, small, polo T-shirt will be TS1234-Red-Small-Polo.

## Nomenclature of constraint-based configurations
For constraint-based configurations, you can create a dedicated nomenclature for the configuration product dimension. You can select the following segments on the **Product nomenclature** page:

-   Number sequence value
-   Text constant
-   Attribute value

Each component in a product configuration model can have its own configuration nomenclature. Only attributes that belong to the component can be used. Attributes from subcomponents or user requirements can't be used.

### Example

A product configuration model has a root component that has two attributes:

-   Material (Plastic, Wood, Steel)
-   Length (10...100)

You create a configuration nomenclature that has the following segments:

1.  Attribute value: Material
2.  Text constant: "AAA"
3.  Attribute value: Length

In this case, the configuration ID for wood material that has a length of 78 will be WoodAAA78.

## Nomenclature of dimension-based configurations
For dimension-based configurations, you can create a dedicated nomenclature for the configuration product dimension. You can select the following segments on the **Product nomenclature** page:

-   Number sequence value
-   Text constant
-   Configuration group item

You can define a configuration nomenclature for a bill of materials (BOM).

### Example

A BOM has four BOM lines that are divided into two configuration groups:

-   BOM line: M0007, Standard cabinet
    -   Configuration group: Cabinet
-   BOM line: M0008, High end cabinet
    -   Configuration group: Cabinet
-   BOM line: M0021, Front grill cloth
    -   Configuration group: Front grill
-   BOM line: M0022, Front grill metal
    -   Configuration group: Front grill

You create a configuration nomenclature that has the following segments:

1.  Configuration group: Cabinet
2.  Text constant: "&"
3.  Configuration group: Front grill

In this case, the configuration ID for a standard cabinet that has a cloth front grill will be M0007&M0021.

## Nomenclature for a combination of product variants and configurations
When you use either the constraint-based configuration technology or the dimension-based configuration technology to configure product variants for a product master, the product variant numbers of the product variants can include the nomenclature from the configuration dimension. Follow these steps to configure variants.

1.  On the **Product nomenclature** page, define a product variant number nomenclature that includes the configuration dimension.
2.  Assign the nomenclature to a product dimension group that has the configuration dimension.
3.  Define a configuration nomenclature for the components or BOMs that will be used to configure the product variants.

You can also create nomenclatures for the product variant names. The product variant names can be configured to include the configuration ID or name.

### Example for constraint-based configurations

For this example, you use a product variant number nomenclature that consists of the following segments:

1.  Product master number
2.  Text constant "\_"
3.  Configuration

The configuration nomenclature consists of the following segments:

1.  Attribute value: Material
2.  Text constant: "AAA"
3.  Attribute value: Length

You enter the following values for segments:

-   Product master number = **M0099**
-   Material = **Plastic**
-   Length = **12**

In this case, the product variant number will be M0099\_PlasticAAA12.

### Example for dimension-based configurations

For this example, you use a product variant number nomenclature that consists of the following segments:

1.  Product master number
2.  Text constant "//"
3.  Configuration

The configuration nomenclature consists of the following segments:

1.  Configuration group: Cabinet
2.  Text constant: "&"
3.  Configuration group: Front grill

You enter the following values for segments:

-   Product master number = **D0123**
-   Cabinet = **M0008**
-   Front grill = **M0022**

In this case, the product variant number will be D0123//M0008&M0022.

## Numbering conflicts
In some cases, a product variant number nomenclature that you set up might not produce unique product variant numbers. For example, the product variant numbers won't be unique if one active product dimension isn't included in the nomenclature for a product master that uses the predefined variant configuration technology. The way that you handle conflicts varies, depending on the configuration technology.

### Predefined variants

An error occurs if you try to manually create or automatically generate product variants, and more than one product variant ends up with the same product variant number. To avoid this scenario, you should use all active product dimensions in the product dimension group. Alternatively, include a number sequence to help guarantee that the product variant numbers are unique.

### Constraint-based configurations

Depending on the nomenclature, the system might try to assign a non-unique product variant number to a configuration. In this case, the system uses the number sequence for the configuration dimension as the product variant number instead, and you receive a warning. To avoid this scenario, you should include enough attributes in the nomenclature to help guarantee unique product variant numbers. You should also make sure that the **Reuse** option is turned on for the component.

### Dimension-based configurations

During one step of the configuration process, the system suggests a configuration value according to the nomenclature. In this step, you can manually change the configuration value. When you save the configuration, the system verifies that the configuration value is unique. If the value that you entered isn't unique, you receive an error message. To save the configuration, you must enter a unique configuration value.

## Related information

[Create a product number nomenclature for predefined product variants](tasks/create-product-number-nomenclature-predefined-variants-2016-11.md)

[Create a product number nomenclature for configured product variants](tasks/create-product-number-nomenclature-product-variants_2016_11.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]