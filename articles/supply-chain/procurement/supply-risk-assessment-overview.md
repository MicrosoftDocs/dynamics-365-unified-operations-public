---
title: Supply Risk Assessment overview
description: The Supply Risk Assessment workspace helps supply managers understand the risk of encountering sourcing shortages and delays.
author: cabeln
ms.author: cabeln
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: overview 
ms.date: 10/17/2022 
ms.custom: bap-template
---

# Supply Risk Assessment overview

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Supply Risk Assessment for Dynamics 365 Supply Chain Management lets you identify supply risks to prevent supply chain disruptions.

The [Supply Risk Assessment workspace](supply-risk-assessment-workspace.md) helps you as a supply managers to understand the risk of encountering sourcing shortages and delays, enabling businesses to take proactive actions to balance cost and resilience when optimizing the supply chain.

The workspace is composed of actionable items lists and embedded Power Bi reports, shows metric like On-Time In-Full (OTIF) ratings for vendor and product ranking. And it represents the past performance as a risk for future supply. Using planned purchase orders, risks can be quantified in quantity and amount at risk if the same performance and trend continues into the future.

To mitigate discovered risks you can take different approaches, such as diversifying vendors, planning with different shipping methods or sourcing locations. Once you have updated the plan you would reassess the supply risks and validate the improvements.

<!--Introductory paragraph. Required. Lead with a light intro that describes what the article covers. Answer the fundamental questions, "why would I want to know this and what is the business value?". Keep it short.-->
<!--add your intro paragraph here-->

<!--H2s. Required. Give each H2 a heading that sets expectations for the content that follows. Follow the H2 headings with a sentence about how the section contributes to the whole.-->
## Get started

### Enable the capability

You must first enable the supply risk assessment capability in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). The feature is named “Assess supply risks to prevent supply chain disruptions".
Once enabled you can configure individual risk thresholds, access the workspace and  embedded Power BI reports.
thresholds

### Configure thresholds

Navigate to the page called “Supply risk assessment parameters” to change minimum rates used to calculate risks. The system uses 4 metrics to assess risks.

- Requested delivery date acceptance rate
- In-Full delivery rate (IT)
- On-Time delivery  rate (OT)
- On-Time In-Full delivery rate (OTIF)

:::image type="content" source="media/sra-parameters-general.png" alt-text="Supply risk assessment parameters form screenshot":::

Each metric is calculated as a rate against within a current scope of analysis. Set the rate which you regard a risk for your business. By default the threshold is set to a rate of 96%.

<!--Next steps Required. Provide at least one next step and no more than three. Include some context so the customer can determine why they would click the link.-->
## Next steps

### Access the risk assessment workspace

Navigate then to the “Supply risk assessment” workspace to start your discovery of products and vendors with low ratings in the past and access the Power BI reports for performance and supply risk analysis.

Please note that you might need to use the “Refresh data” link to immediately see the updated data in the workspace. If this link is not accessible for you, navigate to the “Data set cache configuration” from the search bar and you will see the cache consumer “VendSupplyRiskCacheDataSet”, which you may edit and enable for manual refresh.
