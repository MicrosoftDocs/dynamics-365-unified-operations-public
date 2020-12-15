---
# required metadata

title: Improve the prediction model (preview)
description: This topic describes features that you can use to improve the performance of prediction models.
author: ShivamPandey-msft
manager: AnnBe
ms.date: 05/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 14151
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-05-28
ms.dyn365.ops.version: AX 10.0.8

---

# Improve the prediction model (preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes features that you can use to improve the performance of prediction models. You start to improve your model in the **Customer payment predictions** workspace in Microsoft Dynamics 365 Finance. The improvement steps are then completed in AI Builder.

## Select historical outcomes

You first select one or more of the three possible outcomes for invoices: **On time**, **Late**, and **Very late**. All three outcomes should be selected. If you clear the selection of any of the outcomes, invoices will be filtered out of the training process and the accuracy of the prediction will be reduced.

[![Confirming outcomes](./media/confirm-3-outcomes.png)](./media/confirm-3-outcomes.png)

If your organization requires only two outcomes, change the **Late** and **Very late** thresholds to 0 (zero) days. In this way, you effectively collapse the prediction to a binary state of **On time** or **Late**.

## Select fields

When you're selecting fields to include in the model, be aware that the list includes all available fields in the Microsoft Dataverse table that is mapped to the data in the Azure data lake. Some of these fields should **not** be selected. The fields that should not be selected fall into one of three categories:

- The field is required for the Dataverse table, but there is no backing data for it in the data lake.
- The field is an ID and therefore doesn't make sense for a machine learning feature.
- The field represents information that won't be available during prediction.

The following sections show the fields that are available for the invoice and customer entities, and list the fields that should **not** be selected for training. The category that is specified for each of those fields refers to the categories in the preceding list.
 
### Invoice Dataverse table

The following illustration shows the fields that are available for the invoice table.

[![Available fields for the invoice table](./media/available-fields.png)](./media/available-fields.png)

The following fields should not be selected for training:

- **Invoice Account** (category 2)
- **Is closed** (category 3) – This field is used to filter invoices for training (closed) and prediction (not closed).
- **Name** (category 1)
- **Source Id** (category 2)
- **Source record** (category 2)
- **Source table** (category 2)

### Customer Dataverse table

The following illustration shows the fields that are available for the customer table.

[![Available fields for the customer table](./media/related-entities.png)](./media/related-entities.png)

The following field should not be selected for training:

- **Row Unique Key** (category 2)

## Filters

The filters don't currently support the Customer payment predictor scenario. Therefore, select **Skip this step**, and continue to the summary page.

[![Focus model with filters](./media/focus-model-with-filters.png)](./media/focus-model-with-filters.png)

#### Privacy notice
Previews (1) might use less privacy and fewer security measures than the Dynamics 365 Finance and Operations service, (2) aren't included in the service level agreement (SLA) for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) have limited support.
