---
title: Actionable workspace to discover and handle supplier risks #Required; page title displayed in search results. Don't enclose in quotation marks. 
description: Concept description #Required; article description that's displayed in search results. Don't enclose in quotation marks. Do end with a period.
author: rhanajoy #Required; your GitHub user alias, with correct capitalization. 
ms.author: cabeln #Required; your Microsoft alias; optional team alias. 
ms.reviewer: kfend #Required; Microsoft alias of content publishing team member.
ms.service: dynamics-365 #Required; per approved Microsoft taxonomy (https://taxonomy.docs.microsoft.com/TaxonomyServiceAdminPage/#/taxonomy/detail/2022-04-07T09:00:02.5587920Z!a892accc-6925-4c06-8723-fb5e30ba7ca3/product).
ms.topic: conceptual #Required; don't change. 
ms.date: 10/17/2022 #Required; mm/dd/yyyy format.
ms.custom: bap-template #Required; don't change.
---

<!--Remove all the comments in this template before you sign-off or merge to the main branch.-->

<!--This template provides the basic structure of a concept article. See [Write a concept article](write-a-concept-article.md) in the contributor guide. To provide feedback on this template contact [bace feedback team](mailto:templateswg@microsoft.com).-->

<!--H1 - Required. This should match the title you entered in the metadata. Set expectations for what the content covers, so customers know the content meets their needs. Should NOT begin with a verb.-->
# Actionable workspace to discover and handle supplier risks

The Supply risk assessment workspace gives you a direct view on top key insights related to supplier performance and related risks. It also provides [embedded reports](supplier-risk-assessment-reports.md) for detailed performance and risk analysis.
:::image type="content" source="media/SRA-Workspace.png" alt-text="Supply Risk Assessment workspace screenshot":::
<!--Introductory paragraph - Required. Lead with a light intro that describes what the article covers. Answer the fundamental "What is X and how will learning this help me accomplish Y?" question. A good lead is a sentence in the form, "X is a (type of) Y that does Z." Keep this paragraph short.-->
<!--add your intro paragraph here-->

<!--H2s - Required. Give each H2 a heading that sets expectations for the content that follows. Follow H2 headings with a sentence about how the section contributes to the whole.-->
## Workspace content

The workspace is grouped into three sections, for direct actionable navigation and embedded analytic reporting using Power BI.

- Overview
- Performance
- Risk

### Overview section

The Overview sections contains metrics and actionable content that allows you to navigate to views and records in Dynamics 365, such as planned orders, products, vendors and more. The data shown in the overview section are filtered by the currently selected legal entity.

#### Metrics

The following metrics are calculated for the scope of the work center:

- "Late confirmed": the number of purchase order lines that have a later confirmed delivery data than the requested date.
- "Not on time": The number of purchase order lines that have not been delivered on time.
- "Not in full": The number of purchase order lines that have not been delivered in full.
- "Single sourced": The number of planned order items that have only one vendor assigned and potentially indicating increased risk
Each of above metrics represents a view, that you may navigate to to get detailed lists of records represented.

:::image type="content" source="media/SRA-SingleSourcedPlannedItems.png" alt-text="Single sourced Items view screenshot":::

In this view the On-Time In-Full rating is highlighted and visually indicates whether the rating meets the expected rate as [configured](supplier-risk-assessment-overview.md#configure-thresholds) in the supply risk assessment parameters.

#### Details and impact

The section provides the actionable galley view of Products and Vendors that have not meet the OTIF rate expectations based on purchase orders in the past.

Each Product or vendor shown informs about the number of items ordered and the number of items delivered in the relevant unit of measure. The header of each items shows the number of relevant order lines for this calculation.

:::image type="content" source="media/SRA-DetailsImpact.png" alt-text="Details and Impact view screenshot":::

You can navigate from each item shown to the list of order lines represented.

### Performance and Risk sections

In these sections you will find in-depth [analytics reports](supplier-risk-assessment-reports.md) of your vendor and supply performance and calculated risks for your planned supply orders.

<!--Next steps - Required. Provide at least one next step and no more than three. Include some context so the customer can determine why they would click the link.-->
## Next steps

Explore how the purchase order fulfillment history from the perspective of products or vendors can be used to calculate future risk for your supply.

Aside to the embedded performance and risk reports you can also open the Power BI report in a combined full page experience. 

> [!NOTE]
> The combined performance-risk reports filters the performance reports to items that are also planned.