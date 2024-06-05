---
title: Customer page summary
description: This articles describes how the customer page summary feature shows AI-generated text in the customer page.
author: EricWang
ms.author: wangchen
ms.topic: conceptual
ms.date: 06/05/2024
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
This articles describes how the customer page summary feature shows AI-generated text in the customer page.
Enable the **Customer page summary** feature to get an AI-generated summary of a customer's account in the **All Customers** page. This feature is powered by Microsoft Azure Open AI's large language model and is designed to reduce the time needed to review transaction details for your customers.

This feature provide the following benefits: 
- Provides customer account status and insights.
- Helps make better decisions about customers.

## Prerequisites

### Version requirements

Customer page summary requires the latest hotfix on Dynamics 365 Finance version 10.0.39.

### Role requirements

The user must have at least one of the following menu item to view the summary data:

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

## View summary text

When a customer is selected in the **All customers** workspace, the AI-generated content appears on the **Summary** fast tab. Azure Open AI is used to generate the results, based on data in Finance and the provided prompts. 

It uses the following transaction data as inputs: 
 - customer invoices
 - customer payments
 - sales orders
 - sales agreements
 - rebates
 - outstanding invoices
 - delayed order lines

 This data comes from customer’s Dynamics 365 Finance environment only. All calculations are done in Finance. 

The results contains a summary of current customer status and selective insights about this customer account.

For additional information, see

- [Transparency FAQ](CustomerPageSummaryFAQ.md)
- [Enable Copilot in Dynamics 365 Finance](https://go.microsoft.com/fwlink/?linkid=2274122)
- [Legal information](https://go.microsoft.com/fwlink/?linkid=2173149)
