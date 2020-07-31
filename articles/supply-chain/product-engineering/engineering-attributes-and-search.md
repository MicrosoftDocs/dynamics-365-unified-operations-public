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

1. Go to **Project Oaktree > Setup > Attributes > Attribute types**.
1. Select an existing type from the list pane, or select **New** on the Action Pane to create a new one.
1. Make the following settings:
    - **Attribute type name** - Enter a name for the attribute type.
    - **Type** - Choose a standard data type (*Currency*, *DateTime*, *Decimal*, *Integer*, *Text*, *Boolean*, or *Reference*). <!-- KFM: What is "reference" for? BNG we would need a developer to look into this, this is the standard attribute types, not direclty related to product engineering, we can leave this for a separate topic. Soren had the topic of attributes on him that wanted to write-->
    - **Fixed list** - If you set **Type** to *Text*, then you can set this option. Set this to *Yes* to define specific values for attributes of this type (this will create a drop-down list). Set this to *No* to allow users to enter any value (this will create an input field). If you set this to *Yes*, then use the **Value** FastTab to establish the values available for this attribute type.
    - **Value range** - If you set **Type** to *Integer*, *Decimal*, or *Currency* then you can set this option. Set this to *Yes* to establish minimum and maximum values that will be accepter for attributes that use this type. Set it to *No* to accept any value. If you set this to *Yes*, then use the **Range** FastTab to establish the minimum and maximum values, and (for currency) the currency that applies for the limits you entered.
    - **Unit of measure** - If you set **Type** to *Integer* or *Decimal*, then you can set this option. Select the unit of measure that applies for this attribute type. Leave it blank if no unit is needed. <!-- KFM: What affects might this have? Conversions? Packing/shipping limits? BNG it is the definition of the unit, mostly used for understanding what is happening on the unit. the attributes are not calculated values, so they are not any effects of the unit as such, is more of a measure, would impact things outside of D365 SCM -->

#### Set up engineering attributes

To view, create, or edit an engineering attribute:

1. Go to **Project Oaktree > Setup > Attributes > Engineering attributes**.
1. Select an existing attribute from the list pane, or select **New** on the Action Pane to create a new one.
1. Make the following settings:
    - **Name** - Enter a name for the attribute. <!-- KFM: Where does this appear, just here on this page?  BNG just on this page I believe, the friendly name is what is used in the rest of the page -->
    - **Attribute type** - Select an attribute type defined on the Attribute types page (see also the previous section).
    - **Friendly name** - Enter a name to identify this attribute in the user interface elsewhere in the system. <!-- KFM: Where does this appear, everywhere else? BNG yes-->
    - **Description** - Enter a description of the attribute. <!-- KFM: Where does this appear, just here on this page? BNG yes -->
    - **Help text** - Enter help text that will be displayed as a tool tip for this attribute. <!-- KFM: Correct? BNG I would assume yes, but this is an area we should document by itself, Soren is taking it-->
    - **Default value** - Enter or select a default value for the attribute. The options presented here will depend on the **Attribute type** you selected.
    - **Currency** - If the **Attribute type** you selected is a currency, then select the currency in which this attribute will accept and display values.
1. If the **Attribute type** you selected is an integer or decimal, then the **Range** FastTab is shown. Make the following settings here as needed:
    - **Tolerance action** - Choose how the system should respond when a user enters a value outside of the range specified here. Choose *Warning* to display a warning but allow the user to save the value. Choose *Not allowed* to show a warning and also disallow saving until the user corrects the value. <!-- KFM: Correct? BNG yes-->
    - **Minimum** - Enter the minimum recommended or accepted value.
    - **Maximum** -  Enter the maximum recommended or accepted value. <!-- KFM: Set to zero to disable? BNG separate topic for this -->
    - **Increment** - <!-- KFM: What does this do? Set to zero to disable? BNG separate topic for this-->

### Connect engineering attributes to an engineering product category

<!-- KFM: The original text seemed to be using "engineering product type" and "engineering product category" interchangeably, which confused me for hours. I finally decided that these were the same and changed to "category" everywhere. Please confirm that this is correct. BNG yes, we removed the "product type" concept and data model and changed it inot a "category"-->

Some engineering attributes apply to all products, while others will be specific to individual products or product categories. For example, you won't need electrical attributes on mechanical products. Therefore, you can set up *engineering product categories*, which establish the collection of engineering attributes that must be part of the definition for products belonging to that category. You can also choose which engineering attributes are **mandatory** and if there is a **default value**.

<!-- KFM: Where are these settings? On the **Engineering product category details** page? BNG yes-->

### Populate engineering attributes with values

The engineering attributes connected to an engineering product category are presented when you create a new engineering product based on that category. At that time, you can populate them with values. Afterwards, the values can be changed in the engineering version form or as part of engineering change management in an engineering change order. For more information, see [Engineering change management](engineering-change-management.md).

<!-- KFM: We should provide a procedure with more details about how to create a new engineering product. Where do we start? What do we need to do differently compared to creating a "standard" product. -->

<!-- KFM: BNG added here below but would probably need to be on another place -->

### Create an engineering product

To create an engineering product, go to the Released products form. On the top ribbon, in the Product tab, click on Engineering product, under the section New. 
You must specify the engineering category where this product belongs to. The category will set all the default values and characteristics for the product and set the attributes applicable to the product. Once the category is seleted, the attributes will be populated, and then you are able to modify its value. 


## Search for products using engineering attribute values

With the engineering attribute search, you can find products by searching for their engineering attributes values. This makes it easy to find engineering products based on their characteristics. You can search within products of an engineering product category, or across all engineering products. The search is available on product master data pages, and from transactional places in the system such as sales orders. On a transactional form like a sales order, you can even use the engineering attribute form to search and add the product to the sales order lines with the **Add as new line** button. The product result of the search can be directly added to the order.

<!-- KFM: How do we open this search form? What do we mean by "create new lines"?. BNG it is mentioned before that it can be opened from master data pages (released products form page, version page... and also from transactional pages as the sales order or purchase order. "create new lines" -- I have rephrased it, it adds lines to the sales order -->
