---
title: Customer page summary
description: This article describes how the customer page summary feature shows AI-generated text on the customer page.
author: EricWang
ms.author: wangchen
ms.topic: conceptual
ms.date: 01/31/2025
ms.reviewer: twheeloc
ms.collection: bap-ai-copilot
audience: Application User
ms.search.scope: Core, Operations
ms.search.region: Global
ms.search.validFrom: 2023-06-05
ms.dyn365.ops.version: 10.0.38
ms.search.form:    
---

# Customer page summary

This article describes how the **Customer page summary** feature shows AI-generated text on the customer page.

Enable the **Customer page summary** feature to get an AI-generated summary of a customer's account on the **All customers** page. This feature is powered by Microsoft Azure OpenAI Service's large language model. It's designed to reduce the time that you spend reviewing transaction details for your customers.

This feature provides the following benefits:

- Provide customer account status and insights.
- Help you make better decisions about customers.

## Prerequisites

### Version requirements

Customer page summary requires the latest hotfix for Dynamics 365 Finance version 10.0.39.

### Role requirements

To view the summary data, a user must have at least one of the following menu items:

- CustTrans
- SalesTable
- SalesAgreementListPage
- PDSRebateAgreements
- TAMRebateDeal

### Enable Customer page summary

1. In Finance, open the **Feature management** workspace.
1. On the **All** tab, select **Customer page summary**.
1. Select **Learn more** to learn more about the AI terms.
1. Select **Enable**.

## Turn AI summaries with Copilot on or off

Administrators can control if this AI summary feature is available. 
1. Go to **Feature management**.
2. Search for **Customer summary – Customer page summary**.
3. This feature is turned on by default, but it can be turned off.

For more informatoin, see [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).


## View summary text

When a customer is selected in the **All customers** workspace, the AI-generated content appears on the **Summary** FastTab. Azure OpenAI generates the results based on data in Finance and the provided prompts.

It uses the following transaction data as inputs:

- Customer invoices
- Customer payments
- Sales orders
- Sales agreements
- Rebates
- Outstanding invoices
- Delayed order lines

This data comes only from the customer's Finance environment. All calculations are done in Finance.

The results contain a summary of the current customer status and selected insights into the customer account.

For more information, see the following resources:

- [Transparency FAQ](CustomerPageSummaryFAQ.md)
- [Enable Copilot in Dynamics 365 Finance](https://go.microsoft.com/fwlink/?linkid=2274122)
- [Legal information](https://go.microsoft.com/fwlink/?linkid=2173149)
