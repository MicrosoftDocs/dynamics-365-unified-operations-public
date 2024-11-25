---
title: Enable Copilot statement posting summaries
description: This article describes how to enable Microsoft Copilot-generated statement posting summaries in Dynamics 365 Commerce.
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

This article describes how to enable Microsoft Copilot AI-generated statement posting summaries in Dynamics 365 Commerce.

## Prerequisites

Before you can use Copilot AI-generated summaries for statement posting, your Dynamics 365 Commerce system must meet the following requirements:

- Commerce version 10.0.38 with proactive quality update 5 (PQU-5) or later
- Commerce version 10.0.39 with PQU-3 or later
- Any build of Commerce version 10.0.40 or later

In addition, Copilot capabilities should be enabled in finance and operations apps. For more information, see [Enable Copilot capabilities in finance and operations apps](/dynamics365/fin-ops-core/dev-itpro/copilot/enable-copilot).

## Turn on AI-generated summaries for statements

Copilot AI-generated summaries that are related to statement posting can be shown on two pages: the **Store financials** workspace page and the **Statements** page.

- To show AI-generated summaries on the **Store financials** workspace page, enable the **Enable Copilot based summary and insights for Calculated and Posted statements** feature in the **Feature management** workspace in Commerce headquarters.
- To show AI-generated summaries on the **Statements** page, enable the **Enable summarized insights for unposted statements** feature in the **Feature management** workspace.

> [!NOTE]
> The **Enable Copilot based summary and insights for Calculated and Posted statements** and **Enable summarized insights for unposted statements** features are enabled by default in headquarters. Users who don't want to view an AI-generated summary can collapse the summary section. To turn off AI-generated summaries globally, administrators can disable the features in the **Feature management** workspace.

## AI-generated summaries on the Store financials workspace page

The **Enable Copilot based summary and insights for Calculated and Posted statements** feature uses Copilot to offer a comprehensive summary of insights that are derived from posted and unposted statements and transactions from the last seven days. The summary has two sections: **Status** and **Risks**.

- The **Status** section includes insights such as the number of transactions that are stuck in the calculated state, the total sales amount of those statements, the oldest transaction date that is currently found in unposted statements, and the total number of unposted shifts.
- The **Risks** section includes information about stores that haven't posted statements for more than a day, and also information about store associates who perform transactions such as returns without receipts, expense transactions, and transactions that have price overrides.

## AI-generated summaries on the Statements page

The **Enable summarized insights for unposted statements** feature uses Copilot to generate a comprehensive summary of insights that are derived from an unposted statement. The summary has two sections: **Status** and **Risks**.

- The **Status** section includes insights such as the total sales amount of transactions in the statement, the date that most of the transactions in the statement belong to, and the statement failure state and reason.
- The **Risks** section includes information about store associates who perform transactions such as returns without receipts, expense transactions, and transactions that have price overrides.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
