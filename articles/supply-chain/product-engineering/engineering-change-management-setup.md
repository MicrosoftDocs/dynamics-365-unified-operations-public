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

<!-- KFM Briefly describe what these values are used for and link to any topics where they come up. -->
Engineering change categories are used for organizing the different engineering change orders for easier manage or review of them.  For example it could be useful to setup a workflow where depending on the category a specific department needs to review the proposed changes. You will find the Category field in the engineering change order.

To establish the collection of engineering change categories in use at your organization, go to **Project Oaktree > Setup > Engineering change management > Engineering change categories**.

Use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where these values are shown.

## Engineering change priorities

<!-- KFM Briefly describe what these values are used for and link to any topics where they come up. -->
Engineering change priorities are used for indicating the importance or urgency of the engineering change order. These are helpful to keep track of the importance of the engineering change order so you identify those which need prioritization easily.

To establish the collection of engineering change priorities in use at your organization, go to **Project Oaktree > Setup > Engineering change management > Engineering change priorities**.

Use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where these values are shown.

## Engineering change reasons

<!-- KFM Briefly describe what these values are used for and link to any topics where they come up. -->
Engineering change reasons are useful to indicate the cause or nature of the change in the change order. 

To establish the collection of engineering change reasons in use at your organization, go to **Project Oaktree > Setup > Engineering change management > Engineering change reasons**.

Use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where these values are shown.

## Material disposal codes

<!-- KFM Briefly describe what these values are used for and link to any topics where they come up. -->
If the materials used in your finished goods or components need a particular way of being disposed or treated before they can be put together with the residues of your company, you an use the material disposal codes to keep track of the disposal. When you add the product in the engineering change order, in the change details you can set which is the disposal code for the product.

To establish the collection of material disposal codes in use at your organization, go to **Project Oaktree > Setup > Engineering change management > Material disposal codes**.

Use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where these values are shown.

## Received customer approval

<!-- KFM Briefly describe what these values are used for and link to any topics where they come up. -->
When you design products for a specific customer, it is common the design or other specifications need to be validated before the product can be set as ready. With the received customer approval field you can indicate how far in the customer approval process the product is and/or if the approval has been received.

To establish the collection of received customer approval values in use at your organization, go to **Project Oaktree > Setup > Engineering change management > Received customer approval**.

Use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where these values are shown.

## Engineering change - Environmental health and safety codes

<!-- KFM Briefly describe what these values are used for and link to any topics where they come up. -->


To establish the collection of health and safety values in use at your organization, go to **Project Oaktree > Setup > Engineering change management > Engineering change - Environmental health and safety codes**.

Use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where these values are shown.

## Engineering change severities

<!-- KFM Briefly describe what these values are used for and link to any topics where they come up. -->

To establish the collection of engineering change severities in use at your organization, go to **Project Oaktree > Setup > Engineering change management > Engineering change severities**.

Use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where these values are shown.

You can establish rules that apply to each severity level you create here. See the next section for more information about how to assign these rules.

## Engineering change severity rule sets

<!-- KFM Briefly describe what these settings do and link to any topics where they come up. -->

To set up the rules that apply to each change severity level that you have defined, go to **Project Oaktree > Setup > Engineering change management > Engineering change severity rule sets**. Then do one of the following:

- To create a new rule set, select **New** from the Action Pane and then make settings as described in the following subsections.
- To edit a rule set, select it from the list pane, select **Edit** on the Action Pane, and then make settings as described in the following subsections.
- To delete an existing rule set, select it from the list pane and then select **Delete** on the Action Pane.
- To rearrange the list, select a rule set from the list pane and use **Up** and **Down** buttons on teh Action Pane to reposition it.

For each rule set, make the following settings:

- **Severity** - Select the severity level you want to establish rules for. Use the **Engineering change severities** page to create and name the levels (see the previous section).
- **Rules** - Use the buttons on toolbar on this fast tab to add or remove a rule for the current severity setting. Each rule has a **Rule** and a **Name**. <!-- KFM Where do these rules come from? Should we define each of them here? What is the Name for? -->
