---
title: Credit management setup
description: Learn about the setup that is required for credit management, including overviews on credit management workflows, blocking rules, and account statuses.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 05/13/2024
ms.custom:  
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom:
ms.search.form:
ms.dyn365.ops.version: 
---

# Credit management setup 

[!include [banner](../includes/banner.md)]

## Credit management workflows

Go to **Credit and collections \> Setup \> Credit management workflows** to define the workflows that are used to manage credit limit adjustments.

- You can create a workflow that lets you approve a batch of credit limits adjustments through a single approval.
- You can add a workflow at the line level, so that credit limit adjustments can be approved individually.
- You can create a release workflow that automatically routes holds to a workflow process.

## Blocking rules

### Ranking payment terms

You can put a sales order on hold if the payment terms on the order don't match the default payment terms for the customer. However, sometimes the payment terms differ but are similar enough that you don't want to put the order on hold. You can rank payment terms so that some of them have the same rank, whereas others have a higher or lower rank.

If the rankings for payment terms are active, and if the payment terms on the order have a higher rank than the default payment terms for the customer, the sales order will be put on hold.

To set up the payment terms ranking go to **Credit and collections \> Setup \> Credit management setup \>Rank payment terms**.  

### Ranking settlement discounts

You can put a sales order on hold if the cash discount on the order doesn't match the default cash discount for the customer. However, sometimes the cash discounts differ but are similar enough that you don't want to put the order on hold. You can rank cash discounts so that some of them have the same rank, whereas others have a higher or lower rank.

If rankings for settlement discounts are active, and if the cash discount on the order has a higher rank than the default cash discount for the customer, the sales order will be put on hold.

To set up the payment terms ranking go to **Credit and collections \> Setup \> Credit management setup \>Rank settlement discounts**  

## Reasons

Several types of reasons are used in Credit management:

- Hold reasons indicate why a sales order was put on hold.
- Release reasons are assigned to an order when it's released from hold.
- Status reasons indicate why an account status was assigned to a customer.

You can set up reasons on the **Credit management reasons** page (**Credit and collections \> Setup \> Credit management setup \> Credit management reasons**).

1. In the **Reason type** field, select the type of reason: **Hold**, **Release**, or **Status**.
2. In the **Reason** field, enter a name for the reason.
3. In the **Description** field, enter a description of the reason code.

## Credit management groups

Credit management groups are used to identify customers or groups of customers that have the same credit management properties. For example, credit management groups can be used to determine the blocking and exclusion credit management rules for customers.

You can create credit management groups on the **Credit management groups** page (**Credit and collections \> Setup> Credit management setup \> Credit management groups**).

1. Select **New** to create a line.
2. Enter an ID for the group. The ID can have up to 10 characters.
3. In the **Description** field, enter a name for the group. The name can have up to 60 characters.

The credit management group is assigned to a customer on the **Credit and collections** FastTab of the **All customers** page (**Account receivable \> Customers \> All customers**).

## Account statuses

You can create account statuses to identify the credit standing of a customer account. You can define a status and its effect on the invoicing and delivery on-hold processes. Account statuses can also be used to determine blocking rules for a customer.

You can create account statuses on the **Account statuses** page (**Credit and collections \> Setup> Credit management setup \> Account statuses**).

1. Add an account status, and enter a description that represents the credit standing for a customer. For example, use **Normal** to indicate that a customer is in good standing and open orders are subject to standard credit management processing.
2. In the **Invoicing** and **Delivery on Hold** fields, select the type of hold that should occur for customers who have this account status. You can hold all processing, hold only invoice processing, or hold no processing when the credit limit rules are applied.

## Scoring groups

You can set up **Scoring groups** to define risk factors and the criteria that are used to measure them. When information about a customer is applied to a scoring group, a score is calculated for each risk factor and used to put the customer in a risk group. The risk group can be used to identify credit worthiness and calculate automatic credit limits.

You can create scoring groups on the **Scoring groups** page (**Credit and collections \> Setup \> 
Credit management setup \> Risk \> Scoring groups**).

1. Create a scoring group, and enter a name for it.
2. Enter a description to further describe the scoring group.
3. Select a group type. There are eight predefined types. You can also select **User defined** to define a group type that's better suited to your organization.
4. Select a score type to define how the scoring group calculates the risk score. The following options are available:

    - **Range** – Use this option to define a range of values that should be used to calculate a score.
    - **User defined** – Use this option to manually define a list of values that should be used for the score.

5. If you selected **Range** as the score type, add lines to define the range of values and the corresponding scores.

    1. In the **From value** field, specify the lowest value in the range.
    2. In the **To value** field, specify the highest value in the range.
    3. In the **Score** field, enter the score that should be assigned when the value that is provided is in the "from"/"to" range.

    If you selected **User defined** as the score type, add lines to define the user-defined values and the corresponding scores.

    1. In the **Value** field, enter the user-defined value that should be provided from the customer information.
    2. In the **Score** field, enter the score that should be assigned when the value that is provided is in the "from"/"to" range.

## Risk classification

You can define risk assessments that can be assigned to customers, based on their risk score. A risk score is calculated by comparing customer information to each scoring group. The scores are summed, and the total score is compared to the values in the risk group setup to identify the risk group that the customer belongs to. The risk group score is then used to define credit management blocking and exclusion rules for the customer.

You can set up risk groups on the **Risk assessments** page (**Credit and collections \> Setup \> Credit management setup \> Risk \> Risk classification**).

1. Enter a risk group ID.
2. Enter a description to further explain the risk group.
3. Enter a range of scores that is used to determine which customers belong to the risk group.
4. Select a risk group indicator to specify the symbol that represents the risk group.

## Guarantee/insurance types

You can set up guarantee/insurance types on the **Guarantee/insurance types** page (**Credit and collections \> Setup \> Credit management setup \> Insurance and guarantees \> Insurance and guarantee types**).

1. Enter a guarantee or insurance type that identifies the name of the guarantor or insurance broker.
2. Enter a description to describe the guarantor/insurance broker.

## Coverage types

Coverage types can be used to further classify insurance policies. They can't be used with guarantees.

You can add coverage types on the **Coverage types** page (**Credit and collections \> Setup \> Credit management setup \> Insurance and guarantees \> Coverage types**).

1. Enter a coverage type to identify the type of coverage that should be added as insurance or a guarantee.
2. Enter a description to describe of the coverage type.

## Automatic credit limits

You can create criteria for automatic credit limits on the **Automatic credit limits** page (**Credit and collections \> Setup \> Credit management setup \> Risk \> Automatic credit limits**).

1. Select a risk group that the automatic credit limit should be assigned to.
2. Select the currency for the automatic credit limit. You can create multiple automatic credit limits in different currencies for the same risk group.
3. Enter the revenue amount that represents the maximum company revenue that can be used for this automatic credit limit. When credit limits are created, the revenue amount is compared to a revenue value that is found on the **Financials** page (**Accounts receivable \> All customers \> Select a customer \> General \> Statistics \> Financial**). The system uses the latest value in the **Overview** section.

Follow these steps to add lines that represent the credit limit that will be generated based on the selected criteria.

1. Select the scoring group that defines the customer information that should be used to calculate the credit limit.
2. Select the comparison operator that defines how the scoring group information should be evaluated.
3. Enter the value that should be compared to the value that is specified for the scoring group.
4. Enter the credit limit that should be assigned if the customer information matches the value that is specified for the scoring group. For example, you create an automatic credit limit for the **Low** scoring group. If the years in business is one of the scoring groups, you can define one line that assigns a 100,000 credit limit if the customer has been in business five years and another line that assigns a 200,000 credit limit if the customer has been in business for 10 years.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
