---
# required metadata

title: Engineering attributes and engineering attribute search
description: To ensure that the all product master data can be registered in the system, specify all non-standard characteristics using engineering attributes. With the engineering attribute search, you can easily find products based on these registered characteristics.
author: XXXX
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

To ensure that the all product master data can be registered in the system, specify all non-standard characteristics using engineering attributes. With the engineering attribute search, you can easily find products based on these registered characteristics.

## Engineering attributes

Engineering products typically have a large number of characteristics and properties that you need to capture. You'll be able to register some of these properties using the standard product fields, but you can also create new engineering properties as needed. With *engineering attributes*, you can define your own engineering attributes and make them part of the product definition.

### Creating engineering attributes and attribute types

Each engineering attribute must belong to an attribute type. This is required because each engineering attribute must have a *data type* that defines which types of values it can hold. Each engineering type might be a standard type (such as free text, integer, or decimal) or a custom type (such as text with a specific set of values to choose from). You can reuse each engineering type with any number of engineering attributes.

#### Work with engineering type

To view, create, or edit an engineering type:

1. Go to **Project Oaktree > Setup > Attributes > Attribute types**.
1. Select an existing type from the list pane, or select **New** on the Action Pane to create a new one.
1. Make the following settings:
    - **Attribute type name** - Enter a name for the attribute type.
    - **Type** - Choose a standard data type (*Currency*, *DateTime*, *Decimal*, *Integer*, *Text*, *Boolean*, or *Reference*). <!-- KFM: What is "reference" for? -->
    - **Fixed list** - If you set **Type** to *Text*, then you can set this option. Set this to *Yes* to define specific values for attributes of this type (this will create a drop-down list). Set this to *No* to allow users to enter any value (this will create an input field). If you set this to *Yes*, then use the **Value** FastTab to establish the values available for this attribute type.
    - **Value range** - If you set **Type** to *Integer*, *Decimal*, or *Currency* then you can set this option. Set this to *Yes* to establish minimum and maximum values that will be accepter for attributes that use this type. Set it to *No* to accept any value. If you set this to *Yes*, then use the **Range** FastTab to establish the minimum and maximum values, and (for currency) the currency that applies for the limits you entered.
    - **Unit of measure** - If you set **Type** to *Integer* or *Decimal*, then you can set this option. Select the unit of measure that applies for this attribute type. Leave it blank if no unit is needed. <!-- KFM: What affects might this have? Conversions? Packing/shipping limits? -->

#### Set up engineering attributes

To view, create, or edit an engineering attribute:

1. Go to **Project Oaktree > Setup > Attributes > Engineering attributes**.
1. Select an existing attribute from the list pane, or select **New** on the Action Pane to create a new one.
1. Make the following settings:
    - **Name** - Enter a name for the attribute. <!-- KFM: Where does this appear--just here on this page? -->
    - **Attribute type** - Select an attribute type defined on the Attribute types page (see also the previous section).
    - **Friendly name** - Enter a name to identify this attribute in the user interface elsewhere in the system. <!-- KFM: Where does this appear--everywhere else? -->
    - **Description** - Enter a description of the attribute. <!-- KFM: Where does this appear--just here on this page? -->
    - **Help text** - Enter help text that will be displayed as a tool tip for this attribute. <!-- KFM: Correct? -->
    - **Default value** - Enter or select a default value for the attribute. The options presented here will depend on the **Attribute type** you selected.
    - **Currency** - If the **Attribute type** you selected is a currency, then select the currency in which this attribute will accept and display values.
1. If the **Attribute type** you selected is an integer or decimal, then the **Range** FastType is shown. Make the following settings here as needed:
    - **Tolerance action** - Choose how the system should respond when a user enters a value outside of the range specified here. Choose *Warning* to display a warning but allow the user to save the value. Choose *Not allowed* to show a warning and also disallow saving until the user corrects the value. <!-- KFM: Correct? -->
    - **Minimum** - Enter the minimum recommended or accepted value.
    - **Maximum** -  Enter the maximum recommended or accepted value. <!-- KFM: Set to zero to disable? -->
    - **Increment** - <!-- KFM: What does this do? Set to zero to disable? -->

### Connect engineering attributes to an engineering product type

Some engineering attributes apply to all products, but not all products will need the same engineering attributes. Fo example, you won't need electrical related attributes on mechanical products. Therefore, you can assign per engineering product type, which engineering products are relevant and must be part of the product definition. You can also choose which engineering attributes are **mandatory** and if there is a **default value**.

<!-- KFM: Where are these settings? On the **Engineering product category details** page? -->

### Populate engineering attributes with values

The engineering attributes connected to the engineering product type, will appear in the engineering product creation dialog. Here you can populate them with values. Afterwards, the values can be changed in the engineering version form or as part of engineering change management in the engineering change order. For more information, see [Engineering change management](engineering-change-management.md).

## Engineering attribute search

With the engineering attribute search, you can search on products that meet the engineering attributes values as you define them. This will enable you to find the existing engineering products easily based on their characteristics. You can search within products of an engineering product type, or you leave it empty to search across all engineering products. The search is available from product master data forms, and from transactional places in the system, such as sales orders. On a transactional form like a sales order, you can even use the engineering attribute form to search and create new lines with the **Add as new line** button.
