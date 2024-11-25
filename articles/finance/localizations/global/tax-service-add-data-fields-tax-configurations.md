---
title: Add data fields in tax configurations
description: Learn how to customize tax configurations by adding data fields, including step-by-step processes for customizing tax data models and tax configurations.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/01/2024
ms.reviewer: johnmichalak 
ms.search.region: Global
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.18
---

# Add data fields in tax configurations

[!include [banner](../../includes/banner.md)]

This article explains how to customize tax configurations by using [data fields that are added in the tax integration](tax-service-add-data-fields-tax-integration-by-extension.md).

## Customize the tax data model

1. In Microsoft Dynamics 365 Finance, go to **Electronic Reporting** > **Tax configurations**.
2. In the configuration tree, select **Tax Calculation Data Model**. Then, on the Action Pane, select **Create configuration**. 

  > [!NOTE] 
  > If there is no configuration provider available, create one and make it active for your tax configuration. For more information, see [Create configuration providers and mark them as active](../../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md).
  
3. In the drop-down dialog box, select **Taxable document model derived from Name: Tax Calculation Data Model, Microsoft**, enter a name for the new tax data model, and then select **Create configuration**.
4. Select the tax data model that you just created, and then, on the Action Pane, select **Designer**.
5. Expand the data model tree, select **Lines**, and then select **New**.
6. In the **Create node** dialog box, enter a name, specify the item type, and then select **Add**.
7. Add any required columns.
8. On the Action Pane, select **Save**, and then select **Complete**.
9. Close the page, and view the completed version of your tax data model.

## Customize the tax configuration

1. In Finance, go to **Electronic reporting** > **Tax configurations**.
2. In the configuration tree, select **Tax Calculation Configuration**. Then, on the Action Pane, select **Create configuration**.
3. In the drop-down dialog box, select **Tax service configuration derived from Name: Tax Calculation Configuration, Microsoft**, enter a name for the new tax configuration, and then select **Create configuration**.
4. Select the tax configuration that you just created, and then, on the Action Pane, select **Designer**.
5. In the **Properties** section, in the **Data model** field, select the customized tax data model that you created earlier.
6. In the **Data model version** field, select the completed version of the tax data model.
7. Select **Add**, and add the required tax measures.
8. On the Action Pane, select **Save**, and then select **Complete**.
9. Close the page, and view the completed version of your tax configuration.

## Implement tax features in the customized tax configuration

1. In Regulatory Configuration Service (RCS), go to **Globalization Features** > **Tax**.
2. Select **Add**, enter information about the new feature, and then select **Create feature**.
3. On the **Versions** tab, select the feature, and then select **Edit**.
4. On the **General** tab, in the **Configuration version** field, select the customized tax configuration and version.
5. In the **Manage columns** dialog box, select the header and line columns that you want to include in your customized tax measure, and then select the right arrow button to add them to the **Selected columns** list.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
