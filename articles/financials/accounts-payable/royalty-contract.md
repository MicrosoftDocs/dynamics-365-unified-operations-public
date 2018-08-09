---
# required metadata

title: Royalty contract management
description: This topic describes royalty contract management for Microsoft Dynamics 365 for Finance and Operations.
author: t-benebo
manager: AnnBe
ms.date: 08/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: t-benebo
ms.search.validFrom: 2018-01-31
ms.dyn365.ops.version: July 2017 update
---

# Royalty contract management

[!include [banner](../includes/banner.md)]

Royalty contract management is intended for companies that exercise the right to use a third party's assets and/or intellectual property. It helps companies better manage their royalty agreements by automating tasks that are involved in administering, tracking, and making royalty payments.

This topic provides a broad overview of the typical process for handling royalty fees:

- Register details of the negotiated royalty contract.
- Run negotiated contracts through ongoing sales, and generate royalty claims.
- Approve and process the generated claims, so that they can be passed on to Accounts payable (A/P) for payment.

## Audience and purpose

The information in this topic is intended for business decision makers in enterprise companies, in capacities such as sales manager, accounting manager, and A/P manager, who have the following responsibilities:

- Negotiating contracts with the licensor
- Recording royalty agreement terms and fee rates in the system
- Managing staff that processes royalty claims and makes fee payments

People in these roles are looking for ways to achieve these goals:

- Flexibly accommodate different definitions of royalty contracts and their conditions.
- Reduce the administrative burden and errors that are associated with tracking and processing royalty claims.
- Improve cash flow forecasts by accruing for future payables and avoiding interest on delayed payments.

## Royalty contract

A royalty contract is a record of an agreement with an asset or intellectual property owner. It specifies the negotiated terms and conditions for the licensor to qualify for a monetary reward when the licensee uses its property to obtain revenue.

Royalty contracts are registered on the **Royalty contracts** page. To open the **Royalty contracts** page, select **Accounts payable \> Broker and royalties \> Royalty agreements**.

![Royalty agreements page](./media/royalty-contract-management-royalty-agreements-page.png "Royalty agreements page")

The **Selection** tab in the lower part of the page shows the products that qualify for a royalty fee.

On the **General** tab in the upper part of the page, several fields provide more details about the agreement's conditions as they were negotiated with the licensor:

- The **Cumulate sales by** field indicates the period that a royalty amount will be calculated for, based on cumulative sales. For example, the period might be a month.
- If the **Approval required** option is set to **Yes**, a royalty program owner must approve the claims before a royalty can be turned into an invoice that is payable to the licensor.
- The **Accrual account** and **Expense account** fields must specify account numbers that will receive accrued amounts during the intermediate stage between approval and processing.

Alternatively, to calculate the royalty amount every time that a sales order line is invoiced, select **Invoice**.

Royalty rates are set up on the **Royalty amounts** tab. They can be expressed as tiers adding lines and **From value** and **To value** fields. 

> [!NOTE]
> In order to make an agreement valid, you need to click **Validation** on the Action Pane. as a result, in the **Overview** section, on the **General** tab, the **Validated** slider will to be set to **Yes**. 

## Sell products that qualify for a royalty fee and generate a claim

When a sales processor creates a sales order for a product that the company has a royalty contract for, if the order line's details qualify for the royalty, the program identifies the future royalty fee.

To see whether an order line qualifies for a royalty fee, select **Sales order line \> View \> Price details**. On the **Price details** page, select the **Royalty** FastTab.

![Royalty FastTab on the Price details page](./media/royalty-contract-management-price-details.png "Royalty FastTab on the Price details page")

On the **Price details** page, you can see the fee from the valid contract code that is applied to a line. Additionally, on the **Detail** FastTab, under **Margin estimation**, the **Royalty amount** field shows the royalty fee per product unit.

> [!NOTE]
>To see the **Price details** page, on the **Accounts receivable parameters** page, on the **Prices** tab, select the **Enable price details** check box.

The royalty claim is created when the sales order is invoiced.

## Process claims and pass them as payable to A/R

Royalty claims that are generated represent future payments to the licensor. The contract owner cumulates the claims for the relevant period and then creates an interim liability to the licensor by approving those claims.

The royalty agreement owner is responsible for periodically reviewing and, as required by the company's policy, approving the claims that are generated. After the claims are approved, the A/P administrator passes them as purchase invoices to the regular payable processing.

To view all the claims go to **Accounts payable \> Broker and royalties \> Royalty claims**. 

In the royalty claim page, the **Starting royalty amount** field specifies the fee amount that, when is approved and processed, will be paid to the vendor as a royalty.

The fields in the **Sales** section of the page specify the details about the originating sales invoice, such as number, invoice line net amount, and quantity.

Note that, when a claim is generated on a time basis, its status is set to **To be calculated**. This status is used because the royalty is granted on that time basis and won't be included in the cumulative calculation, together with other claims, until the end of the period. 

If there are multiple sales orders for the same vendor, the claims must be recalculated to account for any cumulative effect. On the Action Pane, click **Cumulate**. 

As a result of running **Cumulate** action, an accrual journal for the claim amounts is posted. To see the details of the posting, find the claim in the royalty claim list, and on the Action Pane, select **Royalty transactions** to see and navigate to the accrual jounal. 

The posted voucher specifies that the royalty accrual account is credited for the expected royalty fee, and the interim accrued royalty  expense account for the expected expense is debited. 

To move the claims to the regular A/P process, the A/P clerk must complete the royalty claim. In the royalty claim list, on the Action Pane, click **Process**. 

The claim's status is now changed to **Completed** and the following events have occurred:

- A Royalty accrual journal posting has reversed the previous interim amounts on the accrual payable and expense amounts.
- A vendor invoice for the royalty amount has been created and posted.
- As a result, the vendor's payable account has been credited, and the royalty fees account has been debited. 

> [!NOTE]
> The account number for royalty fees is specified for the procurement category that is used on the purchase invoice line for the royalty.The procurement category, in turn, is set on the **Broker and royalty** tab of the **Accounts payable parameters** page. 

To see the vendor invoice number, open the **Royalty transactions** page from the royalty claim.

## Summary

The process for handling royalties involves multiple manual tracking tasks that are often tedious. By automating these tasks, the royalty contract management feature helps to move through the following process:

- Generating accurate royalty claims
- Accruing the expected payables and interim expense in the general ledger
- Updating the vendor balance and the income statement with the royalties that are due

In this way, the royalty contract management feature helps to avoid potential errors and interest on unpaid royalties, and contributes to a timely cash flow forecast for the company.
