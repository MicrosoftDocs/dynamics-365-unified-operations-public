---
title: Enable Copilot statement posting summaries
description: This article describes how to enable Copilot-generated statement posting summaries in Microsoft Dynamics 365 Commerce.
author: Shajain
ms.date: 06/13/2024
ms.topic: how-to
ms.collection: 
  - bap-ai-copilot
ms.custom: 
  - bap-template
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2021-11-05
---

# Enable Copilot statement posting summaries

[!include [banner](includes/banner.md)]

This article describes how to enable Copilot AI-generated statement posting summaries in Microsoft Dynamics 365 Commerce.

## Prerequisites

To use Copilot AI-generated summaries for statement posting, your Dynamics 365 Commerce system must meet the following requirements:
- Commerce version 10.0.38 with proactive quality update 5 (PQU-5) or later.
- Commerce version 10.0.39 with PQU-3 or later.
- Any build of Commerce version 10.0.40 or later.

Also, Copilot capabilities should be enabled in finance and operations applications. For more information, see [Enable Copilot capabilities in finance and operations apps](/dynamics365/fin-ops-core/dev-itpro/copilot/enable-copilot).

## Turn on AI-generated summaries for statements

Copilot AI-generated summaries related to statement posting are displayed on two forms: the **Store financials** workspace form and the **Statements** form. To display AI-generated summaries on the **Store financials** workspace form, enable the **Enable Copilot based summary and insights for Calculated and Posted statements** feature in the Commerce headquarters **Feature management** workspace. To display AI-generated summaries on the **Statements** form, enable the **Enable summarized insights for unposted statements** feature in the **Feature management** workspace.

> [!NOTE]
> The **Enable Copilot based summary and insights for Calculated and Posted statements** and **Enable summarized insights for unposted statements** features are enabled by default in headquarters. If a user doesn't want to see an AI-generated summary, they can collapse the summary section. To turn off AI-generated summaries globally, administrators can disable the features from the **Feature management** workspace.

## AI-generated summaries on the Store financials workspace form

The **Enable Copilot based summary and insights for Calculated and Posted statements** feature uses Copilot to offer a comprehensive summary of insights derived from posted and unposted statements and transactions from the last seven days. The summary has two sections: **Status** and **Risks**.
- The **Status** section includes insights such as the count of transactions stuck in the calculated state, the total sales amount of these statements, the oldest transaction date currently in statements that aren't yet posted, and the total number of unposted shifts.
- The **Risks** section includes information about stores that haven't posted statements for more than a day, and information about store associates who perform transactions such as returns without receipts, expense transactions, and transactions with price overrides. 

## AI-generated summaries on the Statements form

The **Enable summarized insights for unposted statements** feature uses Copilot to generate a comprehensive summary of insights derived from the unposted statement. 
The summary has two sections: **Status** and **Risks**. 
- The **Status** section includes insights such as the total sales amount of transactions within this statement, the date to which most of the transactions belong in this statement, and the statement failure state and reason.
- The **Risks** section includes information about store associates who perform transactions such as returns without receipts, expense transactions, and transactions with price overrides. 


[!INCLUDE[footer-include](../includes/footer-banner.md)]
