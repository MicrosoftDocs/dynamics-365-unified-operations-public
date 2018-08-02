---
# required metadata

title: Broker contract management
description: This topic describes Broker contract management for Microsoft Dynamics 365 for Finance and Operations.
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
ms.reviewer: shylaw
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: t-benebo
ms.search.validFrom: 2018-01-31
ms.dyn365.ops.version: July 2017 update
---

# Broker contract management

[!include [banner](../includes/banner.md)]

Broker contract management helps companies better manage their brokerage agreements by automating tasks that are involved in administering, tracking, and paying the fees that are due to the brokers. 

The information in this document provides a broad overview of the typical process for handling broker fees: 
- Registering details of the negotiated broker contract 
- Running the negotiated contracts through ongoing sales and generating broker claims 
- Approving the generated claims, so that they can be passed on to Accounts payable (A/P) for payment 
- Handling situations for partial claim approval and differential accounting 

## Audience and purpose

The information in this document is intended for business decision makers in enterprise companies, in capacities such as sales manager, accounting manager, and A/P manager, who have the following responsibilities: 
- Negotiating contracts with brokers 
- Managing staff that processes broker claims and makes fee payments 

People in these roles are looking for ways to achieve these goals:

- Flexibly accommodate different definitions of broker contracts and their conditions. 
- Reduce the administrative burden and errors that are associated with tracking and processing broker claims. 
- Improve cash flow forecasts by accruing for future payables. 

## Review details of a broken contract

A broker contract is a record of an agreement with a broker that specifies the negotiated terms and conditions under which the brokerage company qualifies for a monetary reward in return for achieving preset sales targets. **Broker contracts** are registered on the Broker contracts page. 

To open the **Broker contracts** page, select **Accounts payable** > **Broker and royalties** > **Broker contracts**. 


![Broker Claims Page](./media/broker-contract-management-contract-page.png  "Broker Claims Page")


On the contract details the conditions and the item that qualifies for brokerage can be found. The monetary reward the broker will receive for achieving the sales objective is found in the page under **Break**. 

The setup of the **Broker Fees** charge indicates that the selling company will incur the broker fee as a sales expense, rather than the customer.

**Note**: If a contract stipulates that the customer will incur the fee for the broker services, the associated charge must be set up so that the **Type** field in the **Debit** section is set to **Customer/Vendor**. In this case, company first receives the fee payment from the customer and then pays its liability to the broker.

## Identify products that qualify for broker comission and generate a claim

When creating a sales order with lines that fulfills the requirements of the broker contract, you can see the related information on the **Sales order** page and clicking on **Sales order line** > **View** > **Broker commissions**.

Because broker fee accruals are handled as a charge, the same broker commission can also be accessed from the sales order through the standard charge page. To open it, select the order line, and then click **Sales order line** > **Financials** > **Manage charges**.

When posting the invoice for the sales order, in addition to the regular sales invoice transactions, the following postings have occurred: 
- The broker claim has been generated for the invoice line. 
- The accrued charge that represents the broker fee has been posted to the interim liability and expense accounts, as appropriate. 

## Review and process claims

After claims are approved, either fully or partially, the vendor invoice is created and posted, if posting is supported by the A/P policy, so that the vendor credit is passed to the regular payable processing. 

All the claims can be seen on the Broker claims page. For each fee, the **Qualified** field specifies the fee amount of that, when it’s approved, will be paid to vendor for its brokerage services.

Note that the fields in the lower section of the page specify details about the originating sales invoice, such as the invoice number, invoice line net amount, and associated customer transactions.

To approve a claim in the **Mark** column, select the check box for the line and on the Action Pane, click **Approve**. 

Message bars inform the sales manager that the following events have occurred: 
- An Expense journal posting has reversed the previous interim amount on both the accrual liability account and the accrual expense account. 
- A broker claim (vendor) invoice for the approved broker fee amount has been created. 

**Note**: A broker claim invoice can be posted either automatically as part of the claim approval process or manually. The policy that controls the posting behavior is specified by the **Manual posting** field on the **Broker and royalty** tab of the **Accounts payable parameters** page. 

- As a result of broker claim invoice posting, the expense account has been debited, and the vendor payable account has been credited. 

**Note**: The expense account number is specified for the procurement category when purchase expenditure for expense posting is set up for purchase orders. The procurement category itself is defined on the **Broker and royalty** tab of the **Accounts payable parameters** page.

## Partially process claims

Assume that the customer has returned some units of a sales order. As a result, the broker no longer qualifies for the fee that is related to the returned quantity. To handle this situation, the user must approve the second claim for the partial amount. 

To manage this case, find the claim under **Accounts payable** > **Broker and royalties** > **Broker claims** and in the **Approving** field, enter the result quantity, the total quantity subtracting the returned units. Then, click **Approve** on the Action Pane. 

![Broker contract management process claim](./media/broker-contract-management-process-claim.png  "Broker contract management process claim")

Note that the difference between the values in the **Approved** field and in the **Qualified** field is recorded in the **Difference** field. These values indicate that the claim is still outstanding, and that the difference must be handled before the claim can be considered closed.

The system will identify that the claim still has an outstanding number of units and prompts the user to enter the differential reason code.
