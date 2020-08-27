---
# required metadata

title: Engineering attributes and engineering attribute search
description: To ensure that the all product master data can be registered in the system, specify all non-standard characteristics using engineering attributes. With the engineering attribute search, you can easily find products based on these registered characteristics.
author: t-benebo
manager: tfehr
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: Release 10.0.13
---

# Engineering attributes and engineering attribute search

[!include [banner](../includes/banner.md)]

To ensure that the all product master data can be registered in the system, specify all non-standard characteristics using engineering attributes. With the engineering attribute search, you can easily find products based on these registered characteristics.

## Engineering attributes

Engineering products typically have a large number of characteristics and properties that you need to capture. You'll be able to register some of these properties using the standard product fields, but you can also create new engineering properties as needed. With *engineering attributes*, you can define your own engineering attributes and make them part of the product definition.

### Creating engineering attributes and attribute types

Each engineering attribute must belong to an attribute type. This is required because each engineering attribute must have a *data type* that defines which types of values it can hold. Each engineering type might be a standard type (such as free text, integer, or decimal) or a custom type (such as text with a specific set of values to choose from). You can reuse each engineering type with any number of engineering attributes.

#### Set up engineering attribute types

To view, create, or edit an engineering attribute type:

1. Go to **Project Oaktree \> Setup \> Attributes \> Attribute types**.
1. Select an existing type from the list pane, or select **New** on the Action Pane to create a new one.
1. Make the following settings:
    - **Attribute type name** - Enter a name for the attribute type.
    - **Type** - Choose a standard data type (*Currency*, *DateTime*, *Decimal*, *Integer*, *Text*, *Boolean*, or *Reference*).
    - **Fixed list** - If you set **Type** to *Text*, then you can set this option. Set this to *Yes* to define specific values for attributes of this type (this will create a drop-down list). Set this to *No* to allow users to enter any value (this will create an input field). If you set this to *Yes*, then use the **Value** FastTab to establish the values available for this attribute type.
    - **Value range** - If you set **Type** to *Integer*, *Decimal*, or *Currency* then you can set this option. Set this to *Yes* to establish minimum and maximum values that will be accepter for attributes that use this type. Set it to *No* to accept any value. If you set this to *Yes*, then use the **Range** FastTab to establish the minimum and maximum values, and (for currency) the currency that applies for the limits you entered.
    - **Unit of measure** - If you set **Type** to *Integer* or *Decimal*, then you can set this option. Select the unit of measure that applies for this attribute type. Leave it blank if no unit is needed.

#### Set up engineering attributes

To view, create, or edit an engineering attribute:

1. Go to **Project Oaktree \> Setup \> Attributes \> Engineering attributes**.
1. Select an existing attribute from the list pane, or select **New** on the Action Pane to create a new one.
1. Make the following settings:
    - **Name** - Enter a name for the attribute. This name only appears on the **Engineering attributes** page; elsewhere in the system, the **Friendly name** is usually shown to identify the attribute.
    - **Attribute type** - Select an attribute type defined on the Attribute types page (see also the previous section).
    - **Friendly name** - Enter a name to identify this attribute in the user interface elsewhere in the system. 
    - **Description** - Enter a description of the attribute.
    - **Help text** - Enter help text to tell other users what this attribute is for. <!-- KFM: Maybe mention where this text is shown, if we can find out. -->
    - **Default value** - Enter or select a default value for the attribute. The options presented here will depend on the **Attribute type** you selected.
    - **Currency** - If the **Attribute type** you selected is a currency, then select the currency in which this attribute will accept and display values.
1. If the **Attribute type** you selected is an integer or decimal, then the **Range** FastTab is shown. Make the following settings here as needed:
    - **Tolerance action** - Choose how the system should respond when a user enters a value outside of the range specified here. Choose *Warning* to display a warning but allow the user to save the value. Choose *Not allowed* to show a warning and also disallow saving until the user corrects the value.
    - **Minimum** - Enter the minimum recommended or accepted value.
    - **Maximum** -  Enter the maximum recommended or accepted value.
    <!-- - **Increment** -  KFM: What does this do? Set to zero to disable? BNG separate topic for this. KFM: I think we should be able to provide a brief description here, but are you saying we should just remove this point? -->

### Connect engineering attributes to an engineering product category

Some engineering attributes apply to all products, while others will be specific to individual products or product categories. For example, you won't need electrical attributes on mechanical products. Therefore, you can set up *engineering product categories*, which establish the collection of engineering attributes that must be part of the definition for products belonging to that category. You can also choose which engineering attributes are **mandatory** and if there is a **default value**.

For more information about how work with engineering product categories, including how to connect attributes to categories, see [Engineering versions and engineering product categories](engineering-versions-product-category.md).

### Populate engineering attributes with values

The engineering attributes connected to an engineering product category are presented when you create a new engineering product based on that category. At that time, you can populate them with values. Afterwards, the values can be changed in the engineering version form or as part of engineering change management in an engineering change order. For more information, see [Engineering change management](engineering-change-management.md).

<!-- KFM: Add a link to the HOL procedure for creating an engineering product and/or category. -->

### Create an engineering product

To create an engineering product, go to the **Released products** page. On the Action Pane, open **Product** tab and, from the **New** group, select **Engineering product**.

You must specify the engineering category where this product belongs to. The category will set all the default values and characteristics for the product and set the attributes applicable to the product. Once the category is selected, the attributes will be populated, and then you are able to modify its value.

## Search for products using engineering attribute values

With the engineering attribute search, you can find products by searching for their engineering attributes values. This makes it easy to find engineering products based on their characteristics. You can search within products of an engineering product category, or across all engineering products. The search is available on product master data pages, and from transactional places in the system such as sales orders. On a transactional item, such as a sales order, you can even use the engineering attribute form to search and add the product to the sales order lines with the **Add as new line** button. The product result of the search can be directly added to the order.

<!-- KFM: We should provide just a bit more detail about where we find the search button. I think it's somewhere on the Action Pane. -->
