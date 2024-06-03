---
title: Customer page summary
description: Learn about how the customer page summary feature shows AI-generated text in the customer page form.
author: EricWang
ms.author: wangchen
ms.topic: conceptual
ms.date: 04/25/2024
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

Enable the **Customer page summary** feature to get an AI-generated summary of a customer's account in the **All Customers** form. This feature is powered by Microsoft Azure Open AI's large language model and is designed to reduce the time that you must spend reviewing transaction details for your customers.

This feature has two purposes:

- Provide customer account status, outliers, and risks.
- Help you make better decisions about your customers.

## Prerequisites

### Version requirements

Customer page summary requires the latest hotfix on Dynamics 365 Finance version 10.0.38.

### Language requirements

The following languages are supported in this feature: English, Danish, Dutch, French, German, Italian, Japanese, Portuguese (Brazil), Spanish, Chinese (Simplified), Czech, Finnish, Greek, Korean, Norwegian (Bokmål), Polish, Russian, Swedish, Thai, Turkish. 

To utilize this feature, please ensure to update your preferred language in Dynamics 365 Finance to one of these supported languages.

### Role requirements

The user must have at least one of the following menu item accesses to view the summary data:

- Customer transactions
- Sales transactions 

### Enable Customer page summary

1. In Finance, open the **Feature management** workspace.
1. On the **All** tab, search for and select **Customer page summary**.
1. Select **Learn more** to learn more about the AI terms.
1. Select **Enable**.

## View summary text

As soon as a customer is selected in the **All customers** workspace, the AI-generated content appears on the **Summary** fast tab. Azure Open AI is used to generate the results, based on data in Finance and the provided prompts. 

It uses historical customer invoices, customer payments, sales orders, outstanding invoices, delayed order lines as inputs. These data come from customer’s Dynamics 365 Finance environment only. All calculations are done in Finance. 

It gives three outputs. The first output is a summary of current customer status. The second output is outliers for unusual activities under this customer account. The third output is risk analysis based on the recent customer activities.

For additional information, see

- [Transparency FAQ](collections-coordinator-summary-faq.md)
- [Legal information](https://go.microsoft.com/fwlink/?linkid=2173149)