---
# required metadata

title: Set up and work with call center fraud alerts
description: This article explains how to set up rules to alert customer service representatives of potentially fraudulent information when orders are processed. You can define specific codes that are used to automatically or manually put suspicious orders on hold. 
author: josaw1
ms.date: 05/14/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SalesPostingHistory, MCRHoldCodeTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.assetid: e342af8d-7498-4d20-8483-ab368429c578
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Set up and work with call center fraud alerts

[!include [banner](includes/banner.md)]

This article explains how to set up criteria and rules to put potentially fraudulent sales orders on hold for further review. The fraud check feature is used to determine the validity of the information in a sales order. If the information in the sales order appears to be questionable, based on an organization's fraud criteria and rules, the order can be put on hold for further review. In this case, the order can't be released to the warehouse for further processing until the hold has been cleared.

> [!NOTE]
> This feature can be used only with sales order processing for the Commerce call center channel.

## Turning on the fraud check feature

To use the fraud check feature, you must set the **Enable order completion** option on the channel to **Yes** when the call center channel is [defined](/dynamics365/unified-operations/retail/set-up-order-processing-options). When order completion is turned on, call center users must select **Complete** on the sales order page for all sales orders that are created. The Complete action causes the **Sales order summary** page to open. After users enter the required payment data on the **Sales order summary** page, they select **Submit** to finalize the order. When the order is submitted, the fraud check feature is triggered, and any rules that are active in the system are automatically validated.

Call center users can also manually put sales orders on hold for fraud review before they select **Submit**. To manually put a sales order on hold, on the **Sales order summary** page, select **Hold** \> **Manual fraud hold**. You're then prompted to enter a comment to explain your reason for putting the order on hold. This comment will appear in the [order holds](/dynamics365/unified-operations/retail/work-with-order-holds) workbench to provide context to the user who reviews orders that are on hold to determine whether the order should be released.

In addition to configuring the **Enable order completion** option on the channel, you must configure the fraud check feature in the Call center parameters. Go to **Retail and Commerce** \> **Channel setup** \> **Call center setup** \> **Call center parameters**. On the **Call center parameters** page, on the **Holds** tab, set the **Fraud check** option to **Yes**.

On the **Holds** tab, you should also define the [hold codes](/dynamics365/unified-operations/retail/work-with-order-holds) that will be applied to an order that is either manually or automatically put on hold for fraud review. Set the hold codes in the **Manual fraud hold code** and **Fraud hold code** fields. You might find it helpful to create two unique hold codes, so that users who work in the holds workbench can easily filter and distinguish automatic holds from manual holds.

For the fraud check feature to work effectively, you must also set the **Minimum score** field. Every fraud criterion and rule that is defined in the system has a score. When a sales order is checked for fraud matches, if one or more matches are found, the scores are added together to give the order a total fraud score. If the total fraud score for an order exceeds the value of the **Minimum score** field, the order is automatically put on hold. You can optionally use the other score-related fields on the **Holds** tab to define the email score, phone score, ZIP/postal code score, and extended ZIP/postal code score. If you don't specify a score for any of these static fraud criteria when you define them on the **Static fraud data** page, the system will score them by using the default scores that you specify on the **Holds** tab of the **Call center parameters** page.

Finally, use the **Fraud comment type** field to specify the document type that should be used when users enter comments when they manually put an order on hold for fraud review. Most often, this field is set to **Note**.

## Defining fraud criteria and rules

The system references two types of fraud criteria to determine whether an order should be put on hold for fraud review:

- **Static fraud data** uses a specific value, such as a phone number that has been put on a list of blocked numbers or an email address that has been flagged because it's known to have been used for previous fraudulent transactions. To set up static fraud data, go to **Retail and Commerce** \> **Channel setup** \> **Call center setup** \> **Fraud** \> **Static fraud data**. On the **Static fraud data** page, you can add fraud criteria manually or through data import. Scores are attached to the fraudulent information. If the fraud check feature is turned on, every sales order that is entered is compared to the static data. If the data is found in either the customer's billing address or the delivery address that is linked to the order header, or if the data is found in the delivery addresses that are linked to any of the lines on that sales order, the scores of all unique matches are added together and compared to the **Minimum score** value to determine whether the order should be put on hold.

- **Fraud rules** consist of user-defined variables and the conditions that are defined for those variables. To create rules, go to **Retail and Commerce** \> **Channel setup** \> **Call center setup** \> **Fraud** \> **Rules**. Fraud rules let a company configure a more complex rule set that can include **AND** or **OR** statements to evaluate multiple conditions. For example, a user wants all orders for customers who belong to a specific customer group and who ordered a specific product to be put on hold for fraud review. In this case, conditions to validate the customer and products are defined on the **Rules** page, and an AND condition is used. An order is then put on hold only if both conditions are true, and if the score value that is assigned to this rule, plus the score value of any other rules that the order matches, causes the order's total fraud score to exceed the **Minimum score** value that is defined on the **Call center parameters** page.

> [!NOTE]
> Multiple rules or overly complex rules will affect system performance when sales orders are submitted. The fraud check feature hasn't been optimized to handle a large volume of static fraud data entries and many active rules. Remember that every rule is evaluated when call center users select **Submit** during sales order entry. The rules are evaluated against the sales order header and all order lines. The more rules there are and the more complex the rule statements are, the more time will be required for processing. If there are many line items on an order, and many active rules and static data entries, the automatic process of reviewing and validating all the data and calculating a fraud score can have a severe impact on performance. Organizations that use this feature should always test and confirm that the processing time for order submission is acceptable before they apply any changes to rules or static fraud criteria to the production environment.

## Identifying orders that are on hold for fraud review

When call center users submit a sales order, if the order matches the fraud criteria or rules, and if the score exceeds the minimum, the users receive a warning message that states that the order has been put on hold. Users can close this message, because it's for informational purposes only. Users can optionally communicate this information to the customer. The business should determine the protocol that users follow in this situation.

The order is saved, but the **Do not process** flag is set on it. This flag helps guarantee that the order can't be released to the warehouse. At any time, users can view the setting of the **Do not process** flag for any sales order on the **Detailed status** page. This page can be opened from the **All sales order** and **Customer service** pages. The system also updates the value of the **Detailed status** field for the order to **Fraud hold**.

To view and manage the orders that are on hold for fraud review, go to **Retail and Commerce** \> **Customers** \> **Order holds**. On the **Order holds** page, select an entry in the list, and then click **Order hold** to see a more detailed view that includes information about the reason for the hold. On the **Fraud details** FastTab, you can view the systematic fraud criteria that were found to be a match for the order and the scores that were applied. If the order was put on manual hold, you can review any comments that were entered by the user who put the order on hold by looking at the **Fraud notes** section on the **Notes** FastTab.

For more information about how to work with hold orders, see [Order holds](/dynamics365/unified-operations/retail/work-with-order-holds).


[!INCLUDE[footer-include](../includes/footer-banner.md)]