---
# required metadata

title: Establish common values for engineering change management
description: This topic describes how to establish common values used for parameters in various parts of engineering change management.
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

# Establish common values for engineering change management

[!include [banner](../includes/banner.md)]

When you set up engineering change management, you must establish several collections of values that will be used to populate drop-down lists in other parts of the interface. You should specify these values according to the types of products you produce and your specific business needs.

## Engineering change categories

Use engineering change categories to organize your various engineering change orders and make them easier to mange and review.  For example, it could be useful to set up a workflow where, depending on the category, a specific department needs to review the proposed changes. You will find the **Category** field on the engineering change order.

To establish the collection of engineering change categories in use at your company, go to **Project Oaktree \> Setup \> Engineering change management \> Engineering change categories**.

Use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where these values are shown.

## Engineering change priorities

Use engineering change priorities to indicate the importance or urgency of an engineering change order. These are helpful to keep track of the importance of an engineering change order so you can easily identify which orders to process first, and how quickly.

To establish the collection of engineering change priorities in use at your company, go to **Project Oaktree \> Setup \> Engineering change management \> Engineering change priorities**.

Use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where these values are shown.

## Engineering change reasons

Engineering change reasons indicate the cause or nature of the change in the change order.

To establish the collection of engineering change reasons in use at your company, go to **Project Oaktree \> Setup \> Engineering change management \> Engineering change reasons**.

Use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where these values are shown.

## Material disposal codes

Use material disposal codes to categorize materials used in your finished goods or components that need to be disposed of in a particular way, or that require some treatment before they can be added to your regular trash. When you add a relevant product to an engineering change order, you can assign a disposal code as part of the change details.

To establish the collection of material disposal codes in use at your company, go to **Project Oaktree \> Setup \> Engineering change management \> Material disposal codes**.

Use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where these values are shown.

## Received customer approval

When you design products for a specific customer, the design and specifications often need to be validated before the product can be set as ready. With the **Received customer approval** field, you can indicate how far in the customer approval process the product is and/or whether the approval has been received.

To establish the collection of received customer approval values in use at your company, go to **Project Oaktree \> Setup \> Engineering change management \> Received customer approval**.

Use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where these values are shown.

## Engineering change - Environmental health and safety codes

If the manufacturing of a product must take into account any standard environmental health and safety regulations, or any company-specific regulation or procedure, you can use the environmental health and safety codes to define them. You can indicate which codes apply to the manufacturing of the product in the engineering change order while editing the details of the impacted product.

To establish the collection of health and safety values in use at your company, go to **Project Oaktree \> Setup \> Engineering change management \> Engineering change - Environmental health and safety codes**.

Use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where these values are shown.

## Engineering change severities

Use engineering change severities to indicate the level of impact that will apply to the products in an engineering change order.

To establish the collection of engineering change severities in use at your company, go to **Project Oaktree \> Setup \> Engineering change management \> Engineering change severities**.

Use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where these values are shown.

You can establish rules that apply to each severity level you create here. See the next section for more information about how to assign these rules.

## Engineering change severity rule sets

Use engineering change severity rule sets to establish a group of rules that you can use to automatically calculate the severity of the change order based on the type of changes in the impacted products. To make use of the severity rules, open the **Project Oaktree parameters** page and set **Severity rule** to *Calculate* or *Calculate automatically*.

When evaluating the severity, the system will process the rules from top to bottom in the order shown in the form. All the rules in a rule set must be met for that rule to be selected and its priority to be established.

To set up the rules that apply to each change severity level that you have defined, go to **Project Oaktree \> Setup \> Engineering change management \> Engineering change severity rule sets**. Then do one of the following:

- To create a new rule set, select **New** from the Action Pane and then make settings as described in the following subsections.
- To edit a rule set, select it from the list pane, select **Edit** on the Action Pane, and then make settings as described in the following subsections.
- To delete an existing rule set, select it from the list pane and then select **Delete** on the Action Pane.
- To rearrange the list, select a rule set from the list pane and use **Up** and **Down** buttons on teh Action Pane to reposition it.

For each rule set, make the following settings:

- **Severity** - Select the severity level you want to establish rules for. Use the **Engineering change severities** page to create and name the levels (see the previous section).
- **Rules** - Use the buttons on toolbar on this fast tab to add or remove a rule for the current severity setting. Each rule has a **Rule** and a **Name**. The rules are established by the system and indicate the types of changes that a product can have. The name will indicate you the type of change.
