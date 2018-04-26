---
# required metadata

title: Set up fraud alerts
description: This topic explains how to set up rules to alert customer service representatives of potentially fraudulent information when orders are processed. You can define specific codes to use to automatically or manually put suspicious orders on hold. 
author: josaw1
manager: AnnBe
ms.date: 04/26/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: SalesPostingHistory, MCRHoldCodeTrans, SysOperationTemplateForm
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 79103
ms.assetid: e342af8d-7498-4d20-8483-ab368429c578
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Set up and work with call center fraud alerts

[!INCLUDE [banner](includes/banner.md)]

This topic explains how to set up criteria and rules to place potentially fraudulent sales orders on hold for further review. Fraud review functionality is used to determine the validity of information in a sales order. If the information in the sales order appears to be questionable based on an organization’s fraud criteria and rules, the order may be put on hold for further review which will prevent the order from being released to the warehouse for further processing until the hold has been cleared.

> [!NOTE]
> This feature can only be used with Retail Call Center channel sales order processing. 

## Enabling fraud check capability

When the Call Center channel is [defined](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/set-up-order-processing-options),the **Enable order completion** flag on the channel must be set to **Yes** to use the fraud checking feature. When order completion is enabled, call center users must click the **Complete** action within the sales order form on all sales orders created.  The complete action triggers the **Sales order summary** form to open.  After the user enters required payment data in the **Sales order summary** form, the users clicks **Submit** to finalize the order. This submit process is when the fraud checking feature is triggered and any rules that are active in the system will be validated systematically. 

The call center user is also able to manually place the sales order on fraud review hold before clicking **Submit**.  This can be done by opening the drop down for the **Hold** menu that appears in the **Sales order summary** form and selecting the **Manual fraud hold** option. When placing an order on fraud hold manually, the user will be prompted to enter a comment to explain their reasoning for putting the order on hold.  This comment will be visible in the [order holds](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/work-with-order-holds) workbench to provide context to the user who may be reviewing the held orders and determining whether or not to release the order.  

In addition to configuring the **Enable order competion** setting on the channel, the fraud checking feature must be further configured in call center parameters.  Navigate to **Retail** \> **Channel setup** \> **Call center setup** \> **Call center parameters**.  

On the **Holds** tab of the **call center parameters** form, set the **Fraud check** parameter to **Yes** to enable the feature.  

On this same **Holds** parameter tab, users should define the [hold codes](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/work-with-order-holds) that will be applied to the order when the order is either manually or systematically put into fraud hold. Set the hold codes in the **Manual fraud hold code** and the **Fraud hold code** fields. It may be helpful to create two unique hold codes so that a user working the holds workbench can easily filter and identify a systematic hold from a manual hold.

The **Minimum score** field must also be defined for fraud checking to work effectively.  Every fraud criteria and rule that is defined in the system will have a score. When a sales order is checked for fraud matches, if one or more matches are found, those scores are added together to give a total fraud score to the order.  If the fraud score for the order is greater than the value entered in the **Minimum score** field, the order will be systematically held.  Additional score related fields in the **Holds** parameter tab to define **Email score**, **Phone score**, **ZIP/postal code score** and **Extended ZIP/postal code score** are optional.  When defining any of these static fraud criteria in the **Static fraud data** form, if a score has not been defined for the specific criteria configured, the system will score it using these default scores defined in the aforementioned parameters. 

Use the **Fraud comment type** setting in the call center parameters to indicate the document type to be used when comments are entered by a user when placing an order on manual fraud hold.  The most common setting for this field is **Note**. 

## Defining fraud criteria and rules

There are two types of fraud criteria that the system will reference to check if the order should be held for fraud review:

-   **Static fraud data** uses a specific value, such as a phone number that has been blacklisted or an email address that has been flagged as being known as used for past fraudulent transactions. Navigate to **Retail** \> **Channel setup** \> **Call center setup** \> **Fraud** \> **Static fraud data**.  From the **Static fraud data** page, fraud criteria can be added manually or through data import, with scores attached to the fraudulent information. If fraud checking is turned on, every sales order entered will be compared to the static data. If the data is found in either the customer’s billing or delivery address tied to the order header, or if the data is found in the delivery addresses linked to any of the lines on that sales order, the scores of all unique matches will be summed and compared to the **Minimum score** parameter setting to determine if the order should be placed on hold.  
-   **Fraud rules** are composed from user-defined variables and the conditions defined for those variables. Navigate to **Retail** \> **Channel setup** \> **Call center setup** \> **Fraud** \> **Rules** to create rules.  With fraud rules, a company can configure a more complex rule set that may include “AND/OR” statements to consider multiple conditions. For example, if a user wants to hold for fraud review all orders for customers that are tied to a specific customer group value and that ordered a specific product, the conditions to validate customer and validate products would be defined on the **Rules** page with an “AND” condition. The order would fall into fraud hold only if both conditions were true and if the score value assigned to the rule along with any other rules the order may have matched has put the order’s total fraud score over the **Minimum score** as defined in call center parameters.

> [!NOTE]
> Use of multiple rules or overly complex rules will result in poor system performance when sales orders are submitted. The fraud alert feature hasn't been optimized to handle a large volume of static fraud data entries and many active rules. It’s important to remember that every rule is evaluated during the submit function of call center sales order entry. The rules are evaluated against the sales order header and all order lines. The more rules there are and the more complex the rule statements are, the longer it will take to process. If you have a large number of line items on your order, and a large number of active rules and static data entries, this systematic process of reviewing and validating all of the data and calculating a fraud score can have a severe performance impact.  Organizations using this feature should always test and confirm that the order submission processing time is acceptable before applying any changes to rules or static fraud criteria into the production environment.

## Identifying orders held for fraud

At the time the call center user submits a sales order, if the order matches the fraud criteria or rules and the score is above the minimum, the user will be shown a warning message to indicate the order is on hold.  Users can close this message as it's for informational purposes only. Conveying this information to the customer is optional and the business should determine the protocol they wish to follow in this situation. Systematically, the application will save the order, but the **Do not process** flag will be set on the order which is what will ensure the order cannot be released to the warehouse.  Users may view the setting of the **Do not process** flag for any sales order at any time in the **Detailed status** form which is accessible from the **All sales order** and **Customer service** forms within the application.  The system will also update the **Detailed status** field for the order to: *Fraud hold*.  

Navigate to **Retail** \> **Customers** \> **Order Holds** to view and manage the orders held for fraud.  Selecting an entry in the **Order holds** form list and clicking the **Order hold** button from the toolbar provides a more detailed view and information as to why the order is on hold.  Navigate to the **Fraud details** fast tab of this form to view the systematic fraud criteria that was found to be a match for the order and the score(s) applied.  If the order was placed on manual fraud hold, view the **Fraud notes** section in the **Notes** fast tab of this form to review any comments entered by the user that placed the order on hold.

For more information on working with hold orders, review the information in the [order holds](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/work-with-order-holds) document.
