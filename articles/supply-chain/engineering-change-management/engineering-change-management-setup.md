---
# required metadata

title: Establish common values for engineering change management
description: This topic describes how to establish common values that are used for parameters in various parts of engineering change management.
author: t-benebo
ms.date: 09/28/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EngChgProductParameters, EngChgEcmSeverityTable, EngChgEcmSeverityRuleSet, EngChgEcmSeverityLookup,EngChgEcmSeverityChart,EngChgEcmRequestSeverityChart,EngChgEcmPriorityTable, EngChgEcmPriorityLookup, EngChgEcmPriorityChart, EngChgEcmMaterialDisposition, EngChgEcmEH
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-09-28
ms.dyn365.ops.version: 10.0.15
---

# Establish common values for engineering change management

[!include [banner](../includes/banner.md)]

When you set up engineering change management, you must establish several collections of values that will be used to fill in drop-down lists in other parts of the user interface (UI). You should specify these values according to the types of products that you produce and your specific business needs.

## Engineering change categories

You use engineering change categories to organize your engineering change orders, so that they are easier to manage and review. For example, you might find it useful to set up a workflow where, depending on the category, a specific department must review the proposed changes. Therefore, the engineering change order includes a **Category** field.

To establish the collection of engineering change categories that is used in your company, go to **Engineering change management \> Setup \> Engineering change management \> Engineering change categories**. You can then use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where they are shown.

## Engineering change priorities

You use engineering change priorities to indicate the importance or urgency of an engineering change order. They can help you keep track of the importance of an engineering change order, so that you can easily identify which orders should be processed first, and how quickly.

To establish the collection of engineering change priorities that is used in your company, go to **Engineering change management \> Setup \> Engineering change management \> Engineering change priorities**. You can then use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where they are shown.

## Engineering change reasons

Engineering change reasons indicate the cause or nature of the change in the change order.

To establish the collection of engineering change reasons that is used in your company, go to **Engineering change management \> Setup \> Engineering change management \> Engineering change reasons**. You can then use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where they are shown.

## Material disposal codes

You use material disposal codes to categorize materials that are used in your finished goods, or components that must be disposed of in a specific way or require some treatment before they can be added to your regular trash. When you add a relevant product to an engineering change order, you can assign a disposal code as part of the change details.

To establish the collection of material disposal codes that is used in your company, go to **Engineering change management \> Setup \> Engineering change management \> Material disposal codes**. You can then use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where they are shown.

## Received customer approval

When you design products for a specific customer, the design and specifications often must be validated before the product can be set as ready. The **Received customer approval** field lets you indicate how far in the customer approval process the product is and/or whether the approval has been received.

To establish the collection of received customer approval values that is used in your company, go to **Engineering change management \> Setup \> Engineering change management \> Received customer approval**. You can then use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where they are shown.

## Engineering change – Environmental health and safety codes

If any standard environmental health and safety regulations, or company-specific regulations or procedures, must be considered in the manufacture of a product, you can use the environmental health and safety codes to define them. In the engineering change order, you can indicate which codes apply to the manufacture of a product while you edit the details of the affected product.

To establish the collection of health and safety values that is used in your company, go to **Engineering change management \> Setup \> Engineering change management \> Engineering change - Environmental health and safety codes**. You can then use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where they are shown.

## Engineering change severities

You use engineering change severities to indicate the level of impact that applies to the products in an engineering change order.

To establish the collection of engineering change severities that is used in your company, go to **Engineering change management \> Setup \> Engineering change management \> Engineering change severities**. You can then use the buttons on the Action Pane to add, remove, and edit values, and to arrange them into the order in which they should appear in the drop-down lists where they are shown.

You can establish rules that apply to each severity level that you create. For more information about how to assign these rules, see the next section.

## Engineering change severity rule sets

You use engineering change severity rule sets to establish a group of rules that you can use to automatically calculate the severity of the change order, based on the type of changes in the affected products. To use the severity rules, open the **Engineering change management parameters** page, and set the **Severity rule** field to *Calculate* or *Calculate automatically*.

When the system evaluates severity, it processes the rules in the order in which they appear on the page, from top to bottom. For a rule to be selected and have its priority established, all the rules in a rule set must be met.

To set up the rules that apply to each change severity level that you've defined, go to **Engineering change management \> Setup \> Engineering change management \> Engineering change severity rule sets**. Then follow one of these steps.

- To create a new rule set, select **New** on the Action Pane, and then set the fields as described later in this section.
- To edit an existing rule set, select it in the list pane, select **Edit** on the Action Pane, and then set the fields as described later in this section.
- To delete an existing rule set, select it in the list pane, and then select **Delete** on the Action Pane.
- To rearrange the list of rule sets, select a rule set in the list pane, and then use the **Up** and **Down** buttons on the Action Pane to reposition it.

For each rule set, set the following field:

- **Severity** – Select the severity level to establish rules for. You use the **Engineering change severities** page to create and name the levels. (For more information, see the previous section.)

Use the buttons on the **Rules** FastTab to add or remove a rule for the current severity setting. Each rule has a **Rule** field and a **Name** field. The rules are established by the system and indicate the types of changes that a product can have. The name indicates the type of change.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]