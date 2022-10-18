---
title: Overview topic template #Required; page title displayed in search results. Don't enclose in quotation marks. 
description: Overview description #Required; article description that's displayed in search results. Don't enclose in quotation marks. Do end with a period.
author: rhanajoy #Required; your GitHub user alias, with correct capitalization. 
ms.author: rhcassid #Required; your Microsoft alias; optional team alias. 
ms.reviewer: kfend #Required; Microsoft alias of content publishing team member.
ms.service: dynamics-365 #Required; per approved Microsoft taxonomy (https://taxonomy.docs.microsoft.com/TaxonomyServiceAdminPage/#/taxonomy/detail/2022-04-07T09:00:02.5587920Z!a892accc-6925-4c06-8723-fb5e30ba7ca3/product).
ms.topic: overview #Required; don't change.
ms.date: 08/10/2022 #Required; mm/dd/yyyy format.
ms.custom: bap-template #Required; don't change.
---

<!--Remove all the comments in this template before you sign-off or merge to the main branch.-->

<!--This template provides the basic structure of a service/product overview article. See [Write an overview](write-an-overview.md) in the contributor guide. To provide feedback on this template contact [bace feedback team](mailto:templateswg@microsoft.com).-->

<!--H1. Required. Set expectations for what the content covers, so customers know the content meets their needs. H1 format is # What is {subject}?-->
# What is Supply Risk Assessment for Dynamics 365 Supply Chain Management?
With Supply Risk Assessment you can identify supply risks to prevent supply chain disruptions.

The “Supply Risk Assessment” workspace with helps you as a supply managers to understand the risk of encountering sourcing shortages and delays, enabling businesses to take proactive actions to balance cost and resilience when optimizing the supply chain.

The workspace is composed of actionable items lists and embedded Power Bi reports, shows metric like On-Time In-Full (OTIF) ratings for vendor and product ranking. And it represents the past performance as a risk for future supply. Using planned purchase orders, risks can be quantified in quantity and amount at risk if the same performance and trend continues into the future.

To mitigate discovered risks you can take different such as diversifying vendors, planning with different shipping methods or sourcing locations. Once you have updated the plan you would reassess the supply risks and validate the improvements.

<!--Introductory paragraph. Required. Lead with a light intro that describes what the article covers. Answer the fundamental questions, "why would I want to know this and what is the business value?". Keep it short.-->
<!--add your intro paragraph here-->

<!--H2s. Required. Give each H2 a heading that sets expectations for the content that follows. Follow the H2 headings with a sentence about how the section contributes to the whole.-->
## Get started
### Enable the capability

You must first enable the supply risk assessment capability in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). The feature is named “Assess supply risks to prevent supply chain disruptions".
Once enabled you can configure individual risk thresholds, access the workspace and  embedded Power BI reports.

### Configure threasholds
Navigate to the page called “Supply risk assessment parameters” to change minimum rates used to calculate risks. The system uses 4 metrics to assess risks.

- Purchase order delivery data confirmed as requested
- On-Time delivery (OT)
- On-Time In-Full deliveries (OTIF)
- In-Full delivery (IT)

Each metric is calculated as a rate against within a current scope of analysis. Set the rate which you regard a risk for your business. By default the threshold is set to a rate of 96%.


<!--Next steps Required. Provide at least one next step and no more than three. Include some context so the customer can determine why they would click the link.-->
## Next steps
### Access the risk assessment workspace
Navigate then to the “Supply risk assessment” workspace to start your discovery of products and vendors with low ratings in the past and access the Power BI reports for performance and supply risk analysis.

Please note that you might need to use the “Refresh data” link to immediately see the updated data in the workspace. If this link is not accessible for you, navigate to the “Data cache configuration” and you will see the cache consumer “VendSupplyRiskCacheDataSet”, which you may edit and enable for manual refresh.

