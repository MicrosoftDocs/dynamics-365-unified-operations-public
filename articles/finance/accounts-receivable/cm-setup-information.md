---
title: Credit management setup
description: Learn about the setup that is required for credit management, including overviews on credit management workflows, blocking rules, and account statuses.
author: twheeloc
ms.author: twheeloc
ms.topic: install-set-up-deploy
ms.date: 07/28/2026
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

Go to **Credit and collections > Setup > Credit management workflows** to define the workflows that manage credit limit adjustments.

- Create a workflow that approves a batch of credit limit adjustments through a single approval.
- Add a workflow at the line level, so that credit limit adjustments can be approved individually.
- Create a release workflow that automatically routes holds to a workflow process.

## Blocking rules

### Ranking payment terms

Put a sales order on hold if the payment terms on the order don't match the default payment terms for the customer. However, sometimes the payment terms differ but are similar enough that you don't want to put the order on hold. You can rank payment terms so that some of them have the same rank, whereas others have a higher or lower rank.

If the rankings for payment terms are active, and if the payment terms on the order have a higher rank than the default payment terms for the customer, the sales order is put on hold.

To set up the payment terms ranking, go to **Credit and collections > Setup > Credit management setup > Rank payment terms**.  

### Ranking settlement discounts

Put a sales order on hold if the cash discount on the order doesn't match the default cash discount for the customer. However, sometimes the cash discounts differ but are similar enough that you don't want to put the order on hold. You can rank cash discounts so that some of them have the same rank, whereas others have a higher or lower rank.

If rankings for settlement discounts are active, and if the cash discount on the order has a higher rank than the default cash discount for the customer, the sales order is put on hold.

To set up the payment terms ranking, go to **Credit and collections > Setup > Credit management setup > Rank settlement discounts**.  

## Reasons

Credit management uses several types of reasons:

- **Hold reasons** explain why a sales order is on hold.
- **Release reasons** explain why an order is released from hold.
- **Status reasons** explain why an account status is assigned to a customer.

Set up reasons on the **Credit management reasons** page (**Credit and collections > Setup > Credit management setup > Credit management reasons**).

1. In the **Reason type** field, select the type of reason: **Hold**, **Release**, or **Status**.
1. In the **Reason** field, enter a name for the reason.
1. In the **Description** field, enter a description of the reason code.

## Credit management groups

Use credit management groups to identify customers or groups of customers that have the same credit management properties. For example, use credit management groups to determine the blocking and exclusion credit management rules for customers.

Create credit management groups on the **Credit management groups** page (**Credit and collections > Setup > Credit management setup > Credit management groups**).

1. Select **New** to create a line.
1. Enter an ID for the group. The ID can have up to 10 characters.
1. In the **Description** field, enter a name for the group. The name can have up to 60 characters.

Assign the credit management group to a customer on the **Credit and collections** FastTab of the **All customers** page (**Account receivable > Customers > All customers**).

## Account statuses

Create account statuses to identify the credit standing of a customer account. Define a status and its effect on the invoicing and delivery on-hold processes. Use account statuses to determine blocking rules for a customer.

Create account statuses on the **Account statuses** page (**Credit and collections \> Setup> Credit management setup \> Account statuses**).

1. Add an account status, and enter a description that represents the credit standing for a customer. For example, use **Normal** to indicate that a customer is in good standing and open orders are subject to standard credit management processing.
1. In the **Invoicing** and **Delivery on Hold** fields, select the type of hold that should occur for customers who have this account status. You can hold all processing, hold only invoice processing, or hold no processing when the credit limit rules are applied.

## Scoring groups

Set up **Scoring groups** to define risk factors and the criteria used to measure them. When you apply customer information to a scoring group, the system calculates a score for each risk factor and places the customer in a risk group. Use the risk group to identify creditworthiness and calculate automatic credit limits.

You can create scoring groups on the **Scoring groups** page. Go to **Credit and collections \> Setup \> Credit management setup \> Risk \> Scoring groups**.

1. Create a scoring group, and enter a name for it.
1. Enter a description to further describe the scoring group.
1. Select a group type. Choose from eight predefined types, or select **User defined** to define a group type that better suits your organization.
1. Select a score type to define how the scoring group calculates the risk score. The following options are available:

    - **Range** – Use this option to define a range of values that the system uses to calculate a score.
    - **User defined** – Use this option to manually define a list of values that the system uses for the score.

1. If you select **Range** as the score type, add lines to define the range of values and the corresponding scores.

    1. In the **From value** field, specify the lowest value in the range.
    1. In the **To value** field, specify the highest value in the range.
    1. In the **Score** field, enter the score that the system assigns when the value is in the "from"/"to" range.

    1. If you select **User defined** as the score type, add lines to define the user-defined values and the corresponding scores.

    1. In the **Value** field, enter the user-defined value that the system provides from the customer information.
    1. In the **Score** field, enter the score that the system assigns when the value is in the "from"/"to" range.

## Risk classification

Define risk assessments that you can assign to customers based on their risk score. Calculate a risk score by comparing customer information to each scoring group. Sum the scores, and compare the total score to the values in the risk group setup to identify the risk group that the customer belongs to. Use the risk group score to define credit management blocking and exclusion rules for the customer.

Set up risk groups on the **Risk assessments** page (**Credit and collections \> Setup \> Credit management setup \> Risk \> Risk classification**).

1. Enter a risk group ID.
1. Enter a description to further explain the risk group.
1. Enter a range of scores that determines which customers belong to the risk group.
1. Select a risk group indicator to specify the symbol that represents the risk group.

## Guarantee and insurance types

Set up guarantee and insurance types on the **Guarantee/insurance types** page (**Credit and collections \> Setup \> Credit management setup \> Insurance and guarantees \> Insurance and guarantee types**).

1. Enter a guarantee or insurance type that identifies the name of the guarantor or insurance broker.
1. Enter a description to describe the guarantor or insurance broker.

## Coverage types

Use coverage types to further classify insurance policies. You can't use them with guarantees.

Add coverage types on the **Coverage types** page (**Credit and collections \> Setup \> Credit management setup \> Insurance and guarantees \> Coverage types**).

1. Enter a coverage type to identify the type of coverage that you add as insurance or a guarantee.
1. Enter a description to describe the coverage type.

## Automatic credit limits

You can create criteria for automatic credit limits on the **Automatic credit limits** page (**Credit and collections \> Setup \> Credit management setup \> Risk \> Automatic credit limits**).

1. Select a risk group that you want to assign the automatic credit limit to.
1. Select the currency for the automatic credit limit. You can create multiple automatic credit limits in different currencies for the same risk group.
1. Enter the revenue amount that represents the maximum company revenue that you can use for this automatic credit limit. When you create credit limits, the system compares the revenue amount to a revenue value that it finds on the **Financials** page (**Accounts receivable \> All customers \> Select a customer \> General \> Statistics \> Financial**). The system uses the latest value in the **Overview** section.

To add lines that represent the credit limit that the system generates based on the selected criteria, follow these steps:

1. Select the scoring group that defines the customer information that the system should use to calculate the credit limit.
1. Select the comparison operator that defines how the scoring group information should be evaluated.
1. Enter the value that you want to compare to the value that you specify for the scoring group.
1. Enter the credit limit that you want to assign if the customer information matches the value that you specify for the scoring group. For example, you create an automatic credit limit for the **Low** scoring group. If the years in business is one of the scoring groups, you can define one line that assigns a 100,000 credit limit if the customer has been in business five years and another line that assigns a 200,000 credit limit if the customer has been in business for 10 years.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
