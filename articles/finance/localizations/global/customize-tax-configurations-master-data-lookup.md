---
title: Customize tax configurations for master data lookup
description: Learn how to customize tax configurations to extend master data lookup functionality, including a process for importing tax configurations from Microsoft.
author: kai-cloud
ms.author: pashao
ms.topic: how-to
ms.date: 03/13/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-04-01
---

# Customize tax configurations for master data lookup

[!include [banner](../../includes/banner.md)]

Follow the steps in this article to customize tax configurations to extend master data lookup functionality.

## Import a tax configuration provided by Microsoft

Follow the steps in [Import Electronic reporting (ER) configurations from Dataverse](./workspace/gsw-import-er-config-dataverse.md) and import the correct [tax configuration version](global-tax-calcuation-service-overview.md#versions), based on your Finance version.

> [!NOTE]
> By default, the Dataverse model mapping is imported. If you receive warning messages during the configuration import process, enable the virtual entities in Dataverse. For more information, see [Enable Dataverse virtual entities](../../../fin-ops-core/dev-itpro/power-platform/enable-virtual-entities.md).

## Create a customized data model configuration

1. In the **Electronic reporting** workspace, select **Tax configurations**, and then select the data model configuration to extend. For example, select **Tax Calculation Data Model**.
1. Select **Create configuration**.
1. Select **Taxable document model derived from Name: Tax Calculation Data Model, Microsoft**.
1. In the **Name** field, enter **Customization data model**.
1. Select **Create configuration**.

## Create customized reference models

1. On the **Tax configurations** page, select **Customization data model**, and then select **Designer**.
1. Select the ellipsis button (**...**), and then select the **Reference model** view.

   :::image type="content" source="../media/pic2.png" alt-text="Screenshot of the Reference model.":::

1. Create the customized reference model. The customized model is a root model. The customized entity is a record list. The customized field is a string field that you want to use in the lookup. You can add more fields as you require.
1. Select the ellipsis button (**...**), and then select the **Taxable document** view.
1. Select the attribute to bind to the customized reference model. For example, select **Customized attribute**, and then follow these steps:

    1. Select **Select reference model**.
    1. Select **Customized model**, and then select **OK**. The reference model name is updated to the value of the **Natural key** field.

       :::image type="content" source="../media/pic5.png" alt-text="Screenshot of the Select reference model dialog box.":::

    1. Select **Save**, and then select **Complete**.

## Create a customized model mapping configuration

1. In the **Electronic reporting** workspace, select **Tax configurations**, and then select the **Dataverse model mapping** configuration.
1. In the **Default for model mapping** field, select **No**.
1. Select **Create configuration**.
1. Select **Taxable document model mapping derived from Name: Dataverse Model Mapping, Microsoft**.
1. In the **Name** field, enter **Customization model mapping**.
1. In the **Target model** field, select the **Customization data model** data model.
1. Select **Create configuration**.

   :::image type="content" source="../media/pic6.png" alt-text="Screenshot of the Create configuration drop-down dialog box.":::

1. Select **Customization model mapping**, and set the **Connected application** field to the connection that you created in step 8 of [Set up an environment for master data lookup](tax-service-set-up-environment-master-data-lookup.md).
1. Set the **Default for model mapping** field to **Yes**.

## Create customized model mappings

1. On **Tax configurations**, select **Customization model mapping**.
1. Select **Designer**, and then select **Customization Model**.

   :::image type="content" source="../media/pic8.png" alt-text="Screenshot of the Customization Model.":::

## Map a model mapping to a Dataverse entity

1. On the **Model mapping designer** page, select **Customization Model**, and then select **Designer**.
1. In the **Data source types** tree, select **Dataverse Table**.
1. On the **Data sources** tab, select **Add root**.
1. In the **Name** field, enter **Customized Dataverse**.
1. In the second **Name** field, select an entity.
1. Select **OK**.

   :::image type="content" source="../media/pic9.png" alt-text="Screenshot of the Table data source properties dialog box.":::

1. Select **Customized Dataverse** and **Customized entity**, and then select **Bind**.

   :::image type="content" source="../media/pic10.png" alt-text="Screenshot of Customized Dataverse and Customized entity binding.":::

1. Under **Customized Dataverse** and **Customized field**, select a field, and then select **Bind**.

   :::image type="content" source="../media/pic11.png" alt-text="Screenshot of Customized Dataverse and a customized field binding.":::

1. Select **Save**, and then select **Complete**.

## Create a customized tax configuration

1. In the **Electronic reporting** workspace, select **Tax configurations**, and then select **Tax Calculation Configuration**.
1. Select **Create configuration**.
1. Select **Tax service configuration derived from Name: Tax Calculation Configuration, Microsoft**.
1. In the **Name** field, enter **Customization configuration**.
1. Select **Create configuration**.
1. Select **Customization configuration**, and then select **Designer**.
1. In the **Data model** field, select **Customization data model**.
1. In the **Data model version** field, select the corresponding data model version.

   :::image type="content" source="../media/pic13.png" alt-text="Screenshot of the Properties section.":::

1. Select **Complete**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
