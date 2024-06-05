---
title: Customer page summary responsible AI FAQ
description: This article answers some frequently asked questions about the customer page summary feature in Microsoft Dynamics 365 Finance.
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

# Customer page summary: FAQ

This article answers some frequently asked questions about the customer page summary feature in Microsoft Dynamics 365 Finance.

## What is customer page summary?

Customer page summary is a feature of Dynamics 365 Finance powered by Azure Open AI's large language model. It shows AI-generated summary text on the **Customer page**. The summary information is displayed at the top of the customer page when the user opens it.

## What does the customer page summary display? 

It uses historical customer invoices, customer payments, sales orders, sales agreements, rebates, overdue invoices, delayed order lines as inputs. The data comes from customer’s Dynamics 365 Finance environment only. The **Customer page summary** displays a summary of current customer status and selective insights about the customer account.

## What is the customer page summary’s intended use?

The intended use is for the users having access to the customer page to quickly get a summary of the customer status and insights. It reduces the time spent on switching between modules to query relevant customer transactions and improve operational efficiency.

## How was customer page summary evaluated? What metrics are used to measure performance?

The AI-generated summary was evaluated based on the existing transaction data (customer invoices, customer payments, sales orders, sales agreements, rebates, overdue invoices, and delayed order lines). All calculations are done in Finance, not through Azure Open AI, and verified against the same data during the testing process. 

## What are the limitations of customer page summary? How can users minimize the impact of customer page summary’s limitations?

The summary provides a comprehensive view of the past year’s customer transactions, starting from the session date. It includes yearly aggregated data of customer invoices, customer payments, sales orders, overdue invoices, delayed order lines. It doesn’t encompass the full range of these transactions.

This Copilot feature was validated for [these languages](https://go.microsoft.com/fwlink/?linkid=2270154). While it can be used in other languages, it may not function as intended. Language quality may vary based on the user’s interaction or system settings which may impact accuracy and the user experience. 

## What operational factors and settings allow for effective and responsible use of customer page summary?

Processing of the customer transaction data (customer invoices, customer payments, sales orders, sales agreements, rebates, overdue invoices, and delayed order lines) can't be changed by the end users. This processing is performed by Dynamics 365 Finance using Azure Open AI's large language model.

This feature can be turned off or on by the system administrator in **Feature management** using the **Customer page summary**.

## See also

- [Customer page summary](CustomerPageSummary.md)
