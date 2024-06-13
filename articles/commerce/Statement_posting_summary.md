---
# required metadata

title: Statement posting summary
description: This topic describes the copilot capabilities for the Statement posting process.
author: Shajain
ms.date: 06/12/2024
ms.topic: article
ms.collection: bap-ai-copilot

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chrgriffin
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: shajain
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.38


---

# Statement posting summary
This article explains how to enable the AI generated summary on the Store financials workspace and Statements form in Dynamics 365 Commerce.

## Prerequisites

To use the AI generated summaries for Statement posting, the Dynamics 365 Commerce system must meet the following requirements:
- Version 10.0.38 with proactive quality update 5 (PQU-5) or later
- Version 10.0.39 with PQU-3 or later
- Any build of version 10.0.40 or later

Additionally, Copilot capabilities should be enabled in Finance and Operations application. Refer the article:
[Enable Copilot in Finance and Operations](/dynamics365/fin-ops-core/dev-itpro/copilot/enable-copilot)


## Turn on AI generated summary for Statements
The AI generated summary related to statement posting is displayed on two forms namely Store financials workspace and Statements form. To display the AI generated summary on Store financials workspace enable the feature **"Enable Copilot based summary and insights for Calculated and Posted statements"** and to show the AI generated summary on Statements form, enable the feature **"Enable summarized insights for unposted statements"** from the Feature management workspace.
> Note
> The above mentioned features are enabled by default so if a user does not want to see the AI generated summary then they can collapse the summary section, or the admins can disable the corresponding features from the Feature management workspace.

## AI generated summary on Store financials workspace
This feature leverages Copilot to offer a comprehensive summary of insights derived from posted and unposted statements and transactions from the last 7 days. The summary has two sections, namely **Status** and **Risks**.
The **Status** section includes insights such as count of transactions stuck in the calculated state, total sales amount of these statements, oldest transaction date currently in statements which are not yet posted, and total unposted shifts. The **Risks** section include the information about stores which have not posted statements for more than a day, information about the store associates which have performed transactions such as returns without receipts, expense transactions and transactions with price overrides. 

## AI generated summary on Statements form

This feature leverages copilot to offer a comprehensive summary of insights derived from the unposted statement. 
The summary has two sections, namely **Status** and **Risks**. The **Status** section includes insights such as total sales amount of transactions within this statement, date for which most of the transactions belong in this statement, statement failure reason and failed state.  The **Risks** section include the information about the store associates which have performed transactions such as returns without receipts, expense transactions and transactions with price overrides. 


