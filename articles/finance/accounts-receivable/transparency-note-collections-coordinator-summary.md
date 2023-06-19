---
title: Transparency note for Collections coordinator summary
description: This article is the transparency note that describes the AI impact of the Collections coordinator summary feature in Microsoft Dynamics 365 Finance.
ms.date: 6/15/2023
ms.custom: transparency-note
ms.topic: article
author: JodiChristiansen
ms.author: jchrist
ms.reviewer: twheeloc
---

# Transparency note for Collections coordinator summary

This transparency note describes the AI impact of the Collections coordinator summary feature in Microsoft Dynamics 365 Finance.

## What is Collections coordinator summary?

Collections coordinator summary is a feature of Dynamics 365 that shows AI-generated summary text in the **Collections coordinator** workspace and generates a reminder letter that contains AI-generated text. As input, this feature uses your Finance data, such as aged balances, overdue invoices, and payment history. The first output is a summary of overdue amounts, overdue balances, and payment history that's shown in the workspace. The second output is an AI-generated email in the form of a collection letter.

## What are the system's capabilities?

The feature is powered by Azure Open AI's large language model and uses the customer name and Finance data as input. The summary gives the collections coordinator information about the payment history and revenue. The AI-generated email can be sent to the customer to remind them about an overdue balance.

## What is the system's intended use?

The feature has two intended uses:

- Summarize Finance customer data such as aged balances, overdue invoices, and payment history.
- Based on this data, generate a draft email in reminder letter format.

## How was Collections coordinator summary evaluated? What metrics are used to measure performance?

The AI-generated summary was evaluated based on the customer's existing Finance data, such as aged balances, overdue invoices, and payment history. All calculations are done in Finance, not through Azure OpenAI.

All emails are based on Finance data, such as aged balances, overdue invoices, and payment history. They were verified against the same data during the testing process.

## What are the limitations of Collections coordinator summary? How can users minimize the impact of those limitations when they use the system?

If the same customer exists in multiple legal entities in Finance, the data that's returned in the **Collections coordinator** workspace is based only on the legal entity that the collections coordinator is using. Therefore, the feature might not give a full picture of the customer's account across all entities.

## What operational factors and settings allow for effective and responsible use of the system?

Processing of the customer's data, such as aged balances, overdue invoices, and payment history, is configured by using the prompt inside Finance. The configuration can't be changed or modified.

The AI-generated summary and email are generated inside Finance by using customer data such as aged balances, overdue invoices, and payment history. No text can be entered by the user and processed through Azure OpenAI. Only the customer's name and data that's found in Finance, such as aged balances, overdue invoices, and payment history, are processed through Azure OpenAI and returned as a summary or used to generate a draft email. You can edit the draft email before you send it.

## See also

- [Collections coordinator summary](accounts-receivable/CollectionsCoordinatorSummary.md)
