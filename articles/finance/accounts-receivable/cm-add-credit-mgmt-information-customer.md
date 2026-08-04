---
title: Add credit management information for customers
description: Learn about how to add credit management information for a customer, including outlines on customer information and temporary credit limits.
author: JodiChristiansen
ms.author: twheeloc
ms.topic: how-to
ms.date: 07/28/2026
ms.custom: 
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom:
ms.search.form: 
ms.dyn365.ops.version: 
---

# Add credit management information for customers

[!include [banner](../includes/banner.md)]

After you set up the parameters that control credit management, add more details for each customer. These details control the credit management processes, and they also provide additional information that helps members of the collections team manage customers.

## Customer information

Add the customer details on the **Credit and collections** FastTab of the **All customers** page (**Account receivable > Customers > All customers**).

1. Set the **Unlimited credit limit** option to **Yes** if the customer shouldn't be limited by any credit limit tests.
1. Set the **Exclude from credit management** option to **Yes** to exclude the customer from any actions that usually occur during credit management processes.
1. Select the credit management group for the customer.
1. To calculate the credit limit in the customer's currency, in the **Credit limit in customer's currency** field, enter the customer's credit limit. The system converts the credit limit in the company currency by using the exchange rates that are defined by the credit limit exchange rate type that you select in the **Credit management parameters**.
1. In the **Last review date** field, enter the date when the customer's credit limit was last reviewed by a credit manager.
1. In the **Next scheduled review date** field, enter the date when the customer is scheduled for credit review and update.
1. In the **Eligible credit limit** field, enter the highest credit limit that you can assign to the customer, based on your review of that customer's credit history. The eligible credit limit can differ from the credit limit that is shown on the **Credit and collections** FastTab.
1. In the **Eligible credit limit currency** field, enter the currency of the eligible credit limit.
1. In the **Eligible credit limit date** field, enter the date when the eligible credit limit was created.
1. In the **Credit account status** field, enter the credit account status of the customer.
1. In the **Status reason** field, enter the reason that is associated the account status.
1. Set the **With agency** option to **Yes** to indicate that the customer is currently assigned to a credit agency. This value is for informational purposes only. It isn't used in any credit management processes.
1. Set the **Title held** option to **Yes** to indicate that a title is held for the company. This value is for informational purposes only. It isn't used in any credit management process.
1. In the **Business started date** field, enter the date when the customer first started to do business. This information is used when risk scores are created.
1. In the **Customer since** field, enter the date when the first transactions were processed for the customer. This information is used when risk scores are created.
1. Enter notes that the credit team can use to further evaluate the customer's credit worthiness.

> [!NOTE]
> Another process creates some of the information that is shown on the **Customer** page:

> - The **Credit limit expiration date** field shows the date when the credit limit expires. If you don't set this field, the customer's credit limit doesn't expire.
> - The **Credit limit date** field shows the date when the credit limit was created. This field is updated whenever the credit limit is adjusted.
> - Temporary credit limits override the customer credit limit for a period. They are used instead of the credit limit to calculate the total credit limit. This information is shown only if there's an active credit limit. You can add temporary credit limits through credit limit adjustments.
> - The **Insurance and guarantees** field shows the total value of insurance and guarantees that can increase the credit limit for the customer.
> - The **Total credit limit** field shows the final credit limit for the customer. The total credit limit includes insurance and guarantees, and temporary credit limits.

## Temporary credit limits

Temporary credit limits override customer credit limits for a defined period. You can add temporary credit limits by using credit limit adjustments. Credit limit adjustments let credit managers update the credit limits and expiration dates of a single customer, a group of customers, or all customers through a posting process.

You can create credit limit adjustment entries on the **Credit limit adjustments** page (**Credit management \> Credit limit adjustments \> Credit limit adjustments**).

## Create insurance policies and guarantees

Create one or more insurance policies and guarantees for each customer. Use them to calculate the exposure that your company has when it offers credit to a customer. Include insurance policies and guarantees in the credit limit for a customer.

Create insurance policies and guarantees on the **All customers** page (**Accounts receivable \> Customers \> All customers**). Select a customer, and then, on the Action Pane, on the **Credit management** tab, select **Insurance and guarantees**.

> [!NOTE]
> In the following procedure, you select an insurer or guarantor from the global address book. Therefore, before you begin this procedure, make sure that the insurers and guarantors are added to the global address book.

1. In the **Identifier** field, enter **Guarantee** or **Insurance**.
1. In the **Guarantee/Insurance type** field, select one of the guarantee or insurance types that you previously set up.
1. In the **Insurer/Guarantor** field, select the insurer or guarantor from the global address book.
1. If you selected **Insurance** in the **Identifier** field, in the **Policy coverage type** field, select one of the coverage types that you previously set up. You can't select a policy coverage type for a guarantee.
1. In the **Identification** field, enter the ID of the policy. This ID is usually a policy number.
1. In the **Effective** field, enter the start date of the insurance policy or guarantee.
1. In the **Expiration** field, enter the date when the insurance policy or guarantee expires.
1. In the **Value** field, enter the value of the insurance policy or guarantee. This value is the full value of the policy.
1. In the **Currency** field, select the currency for the policy value.
1. In the **Update credit limit** field, specify a percentage between **0** and **100**. This percentage is applied to the policy value, and the resulting amount is used to increase the credit limit that is used in credit limit calculations. The calculated value is shown under **Total credit limit, Insurance and Guarantees** on the **Credit and collections** FastTab of the **Customers** page.

    Here's an example:

    - The credit limit (A) is 100,000.
    - The policy value (B) is 50,000.
    - The **Update credit limit** percentage (C) is 50.00.

    In this case, the effective credit limit is 125,000 (= A + \[B × C\]).

1. Select the **Included in exposure** check box to reduce the credit limit that is used in credit limit calculations by the full value of the policy. If you select this check box, the value that is calculated when the **Update credit limit** percentage is specified isn't used in credit limit calculations.

    Here's an example:

    - The credit limit (A) is 100,000.
    - The policy value (B) is 50,000.
    - The **Update credit limit** percentage (C) is 50.00.

    In this case, the effective credit limit is 125,000 (= A + \[B × C\]).

    However, if you select the **Included in exposure** check box, the **Update credit limit** value of 50,000 (= 50.00 percent of 100,000) is removed, and the exposure value is 75,000 (= A + \[B × C\] – B).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
