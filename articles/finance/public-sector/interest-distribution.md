---
# required metadata

title:  Set up interest distribution for cash accounts
description: This topic explains how to set up your participating cash accounts on the Interest distribution rules page. You must complete this setup before you distribute the interest.
author: v-kiarnd
ms.date: 12/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PSNLedgerInterestDistributionRules, PSNLedgerInterestDistributionResults
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
ms.search.industry: public sector
ms.author: v-kiarnd
ms.search.validFrom: 2019-6-30
ms.dyn365.ops.version: 10.0.3

---

# Set up interest distribution for cash accounts

[!include[banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Your agency can allocate (distribute) the interest on a bank account to specific General ledger accounts, based on the average daily balance in cash accounts. You can use this process to generate an advanced ledger entry for the interest amounts. Alternatively, you can generate the interest amounts for review, without posting them.

Before you distribute the interest, you must set up your participating cash accounts on the **Interest distribution rules** page. Each combination of a cash account and a grant can be used to calculate interest for a different interest account.

## Add a cash account for interest distribution

1. Go to **General ledger \> Setup \> Posting \> Interest distribution rules**.
2. Select **New** to add a row.
3. In the **Cash account** field, enter the cash account that contains part of the total pooled cash.
4. Optional: In the **Grant** field, enter the grant for grant-related transaction amounts that should be included in cash balance calculations for the associated cash account. If all grants for the cash account post interest to the same account, you can leave this field blank. However, if you enter an interest account for a specific grant, you must enter an interest account for each grant for the cash account.
5. Select the **Participate** check box to include the cash accounts in interest distribution. If this check box is cleared, you can't edit any other fields in the row. Cash accounts that don't participate are included in the inquiry page so that you can review the average daily balance. However, you can't distribute interest to those cash accounts.
6. Enter either a specific interest account or a project. The value that you enter determines the General ledger account that interest is posted to for the associated cash account.

    - In the **Interest account** field, enter a specific account.
    - In the **Project ID** field, enter a project to use as the basis for posting interest. This account is used in conjunction with other account factors to determine the complete account that is posted to.

7. Select the **Negative interest** check box to calculate a negative interest amount when the cash account has a negative balance. If this check box is cleared, the cash account reports the interest as 0 (zero) instead of a negative amount.
8. The interest account for one cash account can receive any penny difference amounts when interest distribution is calculated. Select the **Rounding** check box for that cash account. You can mark only one cash account as the rounding account.

## Distributing interest

1. Go to **General ledger \> Periodic \> Allocation \> Interest distribution**.
2. Select **Parameters**, and then set the following fields:

    - In **Total interest** field, enter the total amount of interest to disburse.
    - In the **From date** and **To date** fields, select the range of dates to calculate average daily balances for, based on transactions during that date range.

3. Select **Distribute**.
4. Review the calculated interest amounts that have been distributed to the accounts. You can update the amounts in the **Allocated interest** field.

    If you change the interest amounts, the **Total allocated** field must match the **Total interest** field before you can continue. The calculated interest amount might cause the total allocated amount to differ from the total interest amount. Usually, the difference is one cent. This difference is applied to the interest account for the cash account that is marked as the rounding account.

    > [!NOTE]
    > If you change the interest amounts but then want to reset them to the calculated interest amounts, select **Parameters**, and then select **Distribute** to generate the interest by using the original data.

5. To post the distributed interest, select **Post interest**, and then set the following fields:

    - In the **Accounting date** field, enter the accounting date for the Advanced ledger entry.
    - In the **Project category** field, select the project category to use for the items in the Advanced ledger entry. The project category also determines the main account that the Advanced ledger entry posts to.
    - In the **Posting definition** field, select the posting definition to use for the Advanced ledger entry.

6. Select **OK**. A message shows the number of the Advanced ledger entry that is automatically created.

## Pre-processing for increased performance

If your organization frequently changes the chart of accounts or accounts that are related to cash accounts, the interest distribution process might take a significant amount of time to run. However, you can help reduce the time by using the **Use batch processing to update accounts for interest distribution** feature to set up pre-processing for those accounts. 
 
Before you can use the feature, it must be turned on in your system. Admins can use the **[Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)** workspace to check the status of the feature and turn it on if it's required. There, the feature is listed in the following way:
 
- **Module:** General ledger
- **Feature name:** Use batch processing to update accounts for interest distribution
 
When you turn the feature on, the system will set up two batch jobs. An initial batch job will be run once to pre-process the data and the rules that are used in the interest distribution process. A recurring batch job that is named **Run the scheduled preprocessing of ledger accounts used for interest distribution** will also be created. By default, the process will be rerun every evening. However, you can change the frequency in the batch jobs area.

## Calculated amounts

The interest distribution allocation process includes some calculated amounts.

| Amount                | Calculation |
|-----------------------|-------------|
| Average daily balance | The sum of daily balances for each day in the date range, divided by the number of days in the range for each combination of a cash account and a grant. The combinations are defined on the **Interest distribution rules** page. |
| Total daily average   | The sum of all average daily balances, except negative amounts for cash accounts that don't allow for negative interest and cash accounts that don't participate in interest distribution. |
| Percent of total      | The Average daily balance amount divided by the Total daily average amount for each combination of a cash account and a grant. |
| Allocated interest    | The total interest from the **Interest distribution parameters** page, multiplied by the Percent of total amount for the cash account. Interest isn't distributed to cash accounts that have negative amounts and that don't allow for negative interest. Interest also isn't distributed to cash accounts that don't participate in interest distribution. |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
