---
# required metadata

title: Engineering attributes and engineering attribute search
description: This topic explains how you can use engineering attributes to specify all non-standard characteristics, to ensure that all product master data can be registered in the system. It also explains how you can use engineering attribute search to easily find products, based on those registered characteristics.
author: t-benebo
manager: tfehr
ms.date: 09/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  EngChgProductAttributeSearch, EngChgMaintainAttributeInheritance, EngChgAttribute
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-09-28
ms.dyn365.ops.version: Release 10.0.15
---

# Engineering attributes and engineering attribute search

[!include [banner](../includes/banner.md)]

To ensure that all product master data can be registered in the system, you should use engineering attributes to specify all non-standard characteristics. You can then use engineering attribute search to easily find products, based on those registered characteristics.

## Engineering attributes

Typically, engineering products have many characteristics and properties that you must capture. Although you can register some of the properties by using the standard product fields, you can also create new engineering properties as required. You can define your own *engineering attributes* and make them part of the product definition.

### Create engineering attributes and attribute types

Each engineering attribute must belong to an *attribute type*. This requirement exists because each engineering attribute must have a *data type* that defines the types of values that it can hold. An engineering attribute type can be a standard type (such as free text, integer, or decimal) or a custom type (such as text that has a specific set of values to select from). You can reuse each attribute type with any number of engineering attributes.

#### Set up engineering attribute types

To view, create, or edit an engineering attribute type, follow these steps.

1. Go to **Engineering change management \> Setup \> Attributes \> Attribute types**.
1. Select an existing attribute type in the list pane, or select **New** on the Action Pane to create a new attribute type.
1. Set the following fields:

    - **Attribute type name** – Enter a name for the attribute type.
    - **Type** – Select a standard data type (*Currency*, *DateTime*, *Decimal*, *Integer*, *Text*, *Boolean*, or *Reference*).
    - **Fixed list** – This option is available only if you set the **Type** field to *Text*. Set it to *Yes* to define specific values for attributes of this type. In this case, a drop-down list will be created. You use the **Value** FastTab to establish the values that are available for this attribute type. Set this option to *No* to allow users to enter any value. In this case, an input field will be created.
    - **Value range** – This option is available only if you set the **Type** field to *Integer*, *Decimal*, or *Currency*. Set it to *Yes* to establish minimum and maximum values that will be accepted for attributes of this type. You use the **Range** FastTab to establish the minimum and maximum values, and (for currency) the currency that applies for the limits that you entered. Set this option to *No* to accept any value. 
    - **Unit of measure** – This field is available only if you set the **Type** field to *Integer* or *Decimal*. Select the unit of measure that applies for this attribute type. If no unit is required, leave this field blank.

#### Set up engineering attributes

To view, create, or edit an engineering attribute, follow these steps.

1. Go to **Engineering change management \> Setup \> Attributes \> Engineering attributes**.
1. Select an existing attribute in the list pane, or select **New** on the Action Pane to create a new attribute.
1. Set the following fields:

    - **Name** – Enter a name for the attribute. This name appears only on the **Engineering attributes** page. Everywhere else in the system, the value of the **Friendly name** field is usually shown to identify the attribute.
    - **Attribute type** – Select an attribute type that you defined in the previous section.
    - **Friendly name** – Enter a name that will identify the attribute in the system (except on the **Engineering attributes** page). 
    - **Description** – Enter a description of the attribute.
    - **Help text** – Enter Help text that tells other users what the attribute is for.
    - **Default value** – Enter a default value for the attribute. The options that are presented depend on the attribute type that you selected.
    - **Currency** – If the attribute type that you selected is a currency, select the currency that the attribute will accept and show values in.

1. If the attribute type that you selected is an integer or a decimal, the **Range** FastTab is shown. On this FastTab, set the following fields as required:

    - **Tolerance action** – Select how the system should respond if a user enters a value outside the specified range. If you select *Warning*, a warning is shown, but the user can save the value. If you select *Not allowed*, a warning is shown, and the value can't be saved until the user corrects it.
    - **Minimum** – Enter the minimum recommended or accepted value.
    - **Maximum** – Enter the maximum recommended or accepted value.

### Connect engineering attributes to an engineering product category

Some engineering attributes apply to all products, whereas others are specific to individual products or product categories. For example, electrical attributes aren't required for mechanical products. Therefore, you can set up *engineering product categories*. An engineering product category establishes the collection of engineering attributes that must be part of the definition for products that belong to that category. You can also specify which engineering attributes are mandatory and whether there is a default value.

For more information about how to work with engineering product categories, including information about how to connect attributes to categories, see [Engineering versions and engineering product categories](engineering-versions-product-category.md).

### Set values for engineering attributes

The engineering attributes that are connected to an engineering product category are presented when you create a new engineering product that is based on that category. At that time, you can set values for the attributes. Later, those values can be changed on the **Engineering version** page or as part of engineering change management in an engineering change order. For more information, see [Manage changes to engineering products](engineering-change-management.md).

### Create an engineering product

To create an engineering product, open the **Released products** page. Then, on the Action Pane, on **Product** tab, in the **New** group, select **Engineering product**.

You must specify the engineering category that the product belongs to. The category will set all the default values and characteristics for the product. It will also set the attributes that are applicable to the product. After the category is selected, values will be set for the attributes. You can then modify those values.

## Search for products by using engineering attribute values

You can use engineering attribute search to find products by searching for their engineering attributes values. Therefore, you can easily find engineering products, based on their characteristics. You can search in the products that belong to an engineering product category, or you can search across all engineering products.

The search is available on product master data pages and from transactional items in the system, such as sales orders. For a transactional item, you can use the **Engineering attribute search** page to search for a product. You can then use the **Add as new line** button to add the product to the sales order lines. Products in the search results can also be added directly to the order.
