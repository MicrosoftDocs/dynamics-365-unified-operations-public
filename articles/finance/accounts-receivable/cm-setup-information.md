---
# required metadata

title: Customer credit management
description: 
author: mikefalkner
manager: AnnBe
ms.date: 09/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 
ms.dyn365.ops.version: 
---

# Credit management setup information 

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

## Credit management workflows
Select **Credit and collections > Setup > Credit management workflows** to define the workflows that are used to manage credit limit adjustments. 
- You can create a workflow that allows you to approve a batch of the credit limits adjustments with a single approval. 
- You can also add workflow at the line level so that credit limit adjustments can be approved individually.
- You can create a release workflow that will automatically route holds to a workflow process

## Blocking rules

### Rank payment terms

You can place a sales order on hold if the payment terms on the order don't match the default payment terms for the customer. Sometimes however, the payment terms are similar enough that you do not want to put the order on hold when they are different. You can rank payment terms so that some payment terms have the same rank and some payment terms have a higher or lower rank.

If the rankings for payment terms are active, the sales orders will be placed on hold if the payment term on the order has a higher rank than the default payment terms for the customer.

### Rank settlement discounts

You can place a sales order on hold if the cash discount on the order doesn't match the default cash discount for the customer. Sometimes however, the cash discounts are similar enough that you do not want to put the order on hold when they are different. You can rank cash discounts so that some cash discounts have the same rank and some cash discounts have a higher or lower rank.

If settlement discounts rankings are active, the sales orders will be placed on hold if the cash discount on the order has a higher rank than the default cash discount on the customer.

## Reasons

There are several types of reasons used in credit management:

- Hold reasons are used to define why a sales order was placed on hold
- Release reasons are assigned to an order when the order that was on hold is released
- Status reasons are used to indicate the reason that an account status was assigned to a customer

You can set up Reasons on the **Credit management > Setup > Credit management> Credit management reasons** page.

1. Select the **Reason type** for the reason. You can select Hold, Release, or Status
2. Enter the **Reason** name for the reason.
2. Enter the **Description** for the reason code.

## Credit management groups

Credit management groups are used to identify a customer or group of customers that have the same credit management properties. For example, the credit management group can be used to determine the blocking and exclusion credit management rules for the customer.

You can create the groups on the **Credit management > Setup> Groups setup> Credit management groups** page.

1.	Click **New** to create a new line.
2.	Enter a group ID, using up to 10 characters, and enter a group name using up to 60 characters in the description field.

The credit management group is assigned to a customer on the **Account receivable > Customers > All customers > Credit and collections** FastTab.

## Account statuses

You can create an account status to identify the credit standing of a customer account. You can define the status and its effect on the invoicing and delivery on hold processes. Account statuses can also be used to determine blocking rules for a customer.

You can create Account statuses from the **Credit management > Setup> Groups setup> Account statuses** page.

1. Add an account status and a description for the status that represents the credit standing for a customer. For example, use **Normal** to indicate that a customer is in good standing and open orders are subject to standard credit management processing.

2.	In the **Invoicing** and **Delivery on Hold** fields, select the type of hold that will occur for customers with this status. You can hold all processing, hold only invoice processing, or do no hold processing when executing the credit limit rules.

## Scoring Groups

You can set up scoring groups to define risk factors and the criteria for how these risk factors can be measured. When information about a customer is applied to a scoring group, a score is calculated for each risk factor and used to place the customer in a risk group. The risk group can be used for identifying credit worthiness and for calculating automatic credit limits.

You can create scoring groups on the **Credit management > Setup > Risk setup > Scoring groups** page.

1. Create a scoring group and enter a name for the group.
2. Enter a description to further describe the scoring group.
3. Select a group type from one of the eight predefined types that you're defining. You can also select **User defined** to define a group type that's better suited to your organization.
4. Enter a score type to define how the scoring group calculates the risk score. The options are:

   o	Use Range to define ranges of values that will calculate a score.
   o	Use User defined to define a list of values manually with the value that will be used for the score.

For range score types, add lines to define the range of values and the corresponding scores.

1. Enter the From value that is the lowest value in the range.
2. Enter the To value that is the highest value in the range.
3. Enter the Score that will be assigned when the value being provided falls within the from/to range.

For User defined score types, add lines to define the user defined values and the corresponding scores.

1. Enter the user defined Value that will be provided from the customer information.
2. Enter the Score that will be assigned when the value being provided falls within the from/to range.

## Risk Assessments

You can define risk assessments that can be assigned to customers based on their risk scores. A risk score is calculated by comparing customer information to each of the scoring groups. The scores are summed together and the total score is compared to the values in the risk group setup to identify the risk group the customer belongs to. The risk group score is then used to define credit management blocking and exclusion rules for the customer.

You can set up risk groups on the **Credit management > Setup > Risk setup > Risk assessments** page.

1. Enter a risk group identifier.
2. Enter a risk group description to further explain the group.
3. Enter a range of scores that determine which customers will fall into this risk group. 
4. Select a risk group indicator to identify an icon that represents the risk group.

## Guarantee/Insurance Types

You can set up guarantee/insurance types using the **Credit management > Setup > Guarantee/insurance setup > Guarantee/insurance types page**.

1.	Enter a guarantee or insurance type that identifies the name of the guarantor or insurance broker.

2.	Enter a description to describe the guarantor/insurance broker.

## Coverage Types

Coverage types can be used to further classify the insurance policy; they can't be used with guarantees. You can add coverage types on the **Credit management > Setup > Guarantee/insurance setup > Coverage types page**.

1.	Enter a coverage type to identify the type of coverage that will be added as insurance or a guarantee.

2.	Enter a description to describe of the coverage type.

## Automatic credit limits

You can create automatic credit limits criteria on the **Automatic credit limits** page (**Credit management > Setup > Risk setup > Automatic credit limits**).

1. Select a risk group to which the automatic credit limit is assigned.

2. Select the currency for the automatic credit limit. You can create multiple automatic credit limits for the same risk group for credit limits in different currencies.

3. Enter the revenue amount that represents the maximum company revenue that can be used for this automatic credit limit. When credit limits are created, the revenue amount is compared to a revenue value found on the **Financials** page (**Accounts Receivable > All customers> Select a customer > General > Statistics > Financial**). The system uses the latest value in the **Overview** section.

Complete the following steps to add lines that represent the credit limit that will be generated based on criteria selected.

1.	Select the scoring group that defines the customer information that will be used to calculate the credit limit.

2.	Select the comparison operator that will be used to define how the scoring group information will be evaluated.

3.	Enter the value that will be compared to scoring group value.

4.	Enter the credit limit that will be assigned if the customer information matches the value specified for the scoring group. For example, you can create an automatic credit limit for the Low scoring group. If the years in business is one of the scoring groups, you can define one line that will assign a 100,000 credit limit if the customer has been in business five years, and define another line that will assign a 200,000 credit limit if the customer has been in business for 10 years.
