---
title: Store report insights using Copilot
description: This article describes how Copilot generated insights for store reports simplifies the process of measuring the performance of your retail channels.
author: ashishmsft
ms.date: 07/19/2024
ms.topic: article
audience: Application user
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.collection:
  - bap-ai-copilot
---

# Store report insights using Copilot

Store report insights using Copilot is a feature that uses artificial intelligence to generate natural language summaries of store reports in Store Commerce app. Copilot helps you quickly understand the key insights and trends from your channel sales and store performance data. You can customize the prompts to generate reports that suit your needs and preferences. Copilot summaries are available for both out-of-box reports and custom-store-reports that you create in Store Commerce app.

![Top 10 products Report insights using Copilot in Store Commerce App](./media/StoreReportInsightsUsingCopilot.png)

## Why use store report insights by Copilot? 

It enhances store associate efficiency by providing real-time analysis of your store data. You can access Copilot generated summaries every time you load a report in Store Commerce app, without having to spend time on manual data interpretation. Copilot summaries are also governed by data access control settings, so you can ensure that only authorized users can view the reports. For example, a store cashier can analyze or view reports related to their own point-of-sale (POS) activity, while a store manager has broader permissions to access reports for the entire store's POS activity. Copilot can generate narrative summaries for channel reports, providing you with a clear and concise overview of your key indicators, such as sales, revenue, profit, margin, and overall store performance. You can also get real-time analysis, as Copilot updates the summaries as new data comes in.

## How to enable Copilot?
To use Store report insights by Copilot in Store Commerce app, you need to follow these three steps:
1.	From feature management workspace, enable the temporary flag "Enable Copilot in Store Commerce" giving governing control to your organization's administrators to control the roll-out of Copilot features in Store Commerce app. This flag will eventually be retired in future, as with any other feature management workspace based feature flags. These settings are off by default and can be turned on or off as per your business needs.
2.	From Commerce shared parameters, enable the permanent flag "Enable Copilot in Store Commerce" giving additional governing control to your organization's administrators to control the availability of Copilot features in Store Commerce app. This flag will get automatically enabled once you enable the temporary flag, and shall continue to be available even after temporary flag is retired. 
3.	From POS functionality profile, you would notice new fast-tab for "Copilot" settings, enable "Report insights" to get Store reports insights by Copilot in Store Commerce app and run CDX jobs for these updated settings to be synced to Channel database for it to take effect.

This capability is available for Dynamics 365 Commerce customers on following versions - 

- 10.0.39, PQU-4 onwards (CSU : 9.49.24184.3, Store Comm. App 9.49.24193.1)
- 10.0.40, PQU-1 onwards (CSU : 9.50.24184.2, Store Comm. App 9.50.24189.1)


> [!Note]
> AI-generated maybe incorrect. [Learn more](https://aka.ms/BusinessApplicationLegal)
>
> For Copilot experiences in Store Commerce app, it depends on your Dataverse instance being linked to your environment. For this, Copilot capabilities should be enabled in your finance and operations apps. For more information, see [Enable Copilot capabilities in finance and operations apps](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/copilot/enable-copilot).
> 
> Lastly, if your hosting environment is in one of the regions where Azure Open AI is currently not available, then through Power Platform Admin Center (PPAC) consider enabling "Move data across regions". If your Dynamics 365 environments are hosted in the EU Data Boundary, we use an Azure OpenAI endpoint in the same boundary.If the required AI services are already available in your Dataverse region, you don't have to set up support for cross-region calls. If cross-region data movement is required but is disabled, users won't be able to view Copilot generated summaries in Store Commerce app[Learn more](https://learn.microsoft.com/en-us/power-platform/admin/geographical-availability-copilot)
>
> 
