---
title: Customer page summary responsible AI FAQ
description: This article answers some frequently asked questions about the Customer page summary feature in Microsoft Dynamics 365 Finance.
author: EricWang
ms.author: wangchen
ms.topic: conceptual
ms.date: 06/03/2024
ms.reviewer: twheeloc
ms.collection: bap-ai-copilot
audience: Application User
ms.search.scope: Core, Operations
ms.search.region: Global
ms.search.validFrom: 2024-06-01
ms.dyn365.ops.version: 10.0.39
ms.search.form:    
---

# Customer page summary responsible AI FAQ

This article answers some frequently asked questions about the **Customer page summary** feature in Microsoft Dynamics 365 Finance.

## What is Customer page summary?

Customer page summary is a feature in Dynamics 365 Finance that is powered by Azure OpenAI Service's large language model. It shows AI-generated summary text at the top of the customer page when a user opens it.

## What does Customer page summary show?

Customer page summary uses historical customer invoices, customer payments, sales orders, sales agreements, rebates, overdue invoices, and delayed order lines as inputs. This data comes only from the customer's Finance environment. Customer page summary shows a summary of the current customer status and selected insights into the customer account.

## What is Customer page summary's intended use?

Users who have access to the customer page can quickly get a summary of the customer status and insights. The feature reduces the time that users must spend switching between modules to query relevant customer transactions and helps improve operational efficiency.

## How was Customer page summary evaluated? What metrics are used to measure performance?

The AI-generated summary was evaluated based on the existing transaction data (customer invoices, customer payments, sales orders, sales agreements, rebates, overdue invoices, and delayed order lines). All calculations are done in Finance, not through Azure OpenAI, and are verified against the same data during the testing process.

## What are the limitations of Customer page summary? How can users minimize the impact of those limitations?

The summary provides a comprehensive view of the past year's customer transactions, starting from the session date. It includes yearly aggregated data of customer invoices, customer payments, sales orders, overdue invoices, and delayed order lines. It doesn't encompass the full range of these transactions.

This Copilot feature was validated for [these languages](https://go.microsoft.com/fwlink/?linkid=2270154). Although it can be used in other languages, it might not work as intended. Language quality might vary, based on the user's interactions or system settings, and might therefore affect accuracy and the user experience.

## What operational factors and settings allow for effective and responsible use of Customer page summary?

System users can't change the processing of the customer transaction data (customer invoices, customer payments, sales orders, sales agreements, rebates, overdue invoices, and delayed order lines). Dynamics 365 Finance performs this processing by using Azure OpenAI's large language model.

The system administrator can turn this feature off or on in Feature management by using the **Customer page summary** feature.

## See also

- [Customer page summary](CustomerPageSummary.md)
