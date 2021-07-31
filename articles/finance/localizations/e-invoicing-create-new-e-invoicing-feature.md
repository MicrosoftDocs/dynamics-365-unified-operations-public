---
# required metadata

title: Create a new Electronic invoicing feature
description: This topic explains how to create a new Electronic invoicing feature when no configurable feature is available for your country or region out of the box.
author: gionoder
ms.date: 07/21/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2021-07-21
ms.dyn365.ops.version: AX 10.0.12

---

# Create a new Electronic invoicing feature

[!include [banner](../includes/banner.md)]

This topic explains how to create a new Electronic invoicing feature when no configurable feature is available for your country or region out of the box.

To create a new Electronic invoicing feature, complete these tasks:

1. Create a new file format configuration by using the invoice model configuration that is provided and taking advantage of the existing invoice mapping for the feature that you want to create.
2. Add the file format configurations to the Electronic invoicing feature configurations.
3. Create the Electronic invoicing feature setup.
4. Complete the new Electronic invoicing feature, and publish it to the Global repository for your organization.
5. Deploy the new Electronic invoicing feature to the Service environment.

## Create new file format configurations that are derived from the existing invoice model

In this procedure, you will create the file format configurations that are required for the new Electronic invoicing feature that you want to create. You can create the electronic invoice file format configuration and any other file format configurations that your new Electronic invoicing feature might require.

Before you begin this procedure, sign in to your Regulatory Configuration Service (RCS) account.

1. In Microsoft Dynamics 365 Finance, in the **Electronic reporting** workspace, select **Repositories** for the **Microsoft** configuration provider.
2. Select **Global**, select **Open**, and then, in the left pane, select the **Invoice model** configuration.

    > [!IMPORTANT]
    > For Brazil, select the **Fiscal documents** model configuration instead.

3. On the **Configurations** tab, select **Import**.
4. Close the page.
5. Close the page.
6. Select the **Reporting configurations** tile, and then select the invoice model that you imported.
7. Select **Create configuration**, and then select **Format based on invoice context model**.
8. Enter a name and description for the format configuration.
9. In the **Format type** field, select the file extension type.
10. Select **Create configuration**, and then select the format configuration that you created.
11. Select **Designer**, and use the Format designer tool to configure the file layout so that it meets the file format specifications.
12. Close the page.
13. On the **Versions** tab, select **Change status** \> **Complete**.
14. Select **Change status** \> **Share** to publish the format configuration to the Global repository.

The new file format configuration must be shared with the Microsoft domain before the configuration can be consumed by the Electronic invoicing service.

1. Select the format configuration that you're working on. The status of the configuration must be **Shared**.
2. On the **Versions** tab, select **Advanced sharing** \> **Global repository**.
3. On the **Shared with** tab, select **Organization**.
4. In the **Parameters** field, enter **Microsoft.com** to share the format configuration with the Microsoft domain.
5. Select **OK**.

## Create the new Electronic invoicing feature

1. In RCS, in the **Globalization features** workspace, in the **Features** section, select the **Electronic invoicing** tile.
2. Select **Add**, and then select **New feature**.
3. Enter a name and description for the Electronic invoicing feature.
4. Select **Create feature**.

## Add Electronic invoicing feature configurations

1. Select the Electronic invoicing feature that you're working on.
2. On the **Configurations** tab, select **Add**.
3. In the **Configurations** grid, browse and select the file format configurations that your Electronic invoicing feature requires to generate the electronic invoice file.
4. Select **OK**.

## Add Electronic invoicing feature setups

1. On the **Setups** tab, select **Add**, and then select **Custom setup**.
2. Enter a name and description for the feature setup.
3. In the **Setup type** field, select **Processing pipeline**.
4. Select **Create**.
5. Select the setup that you're working on, and then select **Edit**.
6. On the **Processing pipeline** tab, select **New** to add a pipeline action. For more information about pipelines, see [Actions](e-invoicing-configuration-rcs.md#actions).
7. On the **Applicability rules** tab, select **New** to add applicability rule clauses. For more information about applicability rules, see [Applicability rules](e-invoicing-configuration-rcs.md#applicability-rules).
8. On the **Variables** tab, select **New** to add variables as required.
9. Select **Save**, and then select **Validate** to check the consistency of the configuration.
10. Close the page.

## Deploy the Electronic invoicing feature to the Service environment

For information about how to complete this task, see [Deploy the Electronic invoicing feature to Service environment](e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-service-environment).

## Deploy the Electronic invoicing feature to a connected application

For information about how to complete this task, see [Configure the application setup](e-invoicing-get-started.md#configure-the-application-setup) and [Deploy the Electronic invoicing feature to Connected application](e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-connected-application).
