---
# required metadata

title: Create a new Electronic invoicing feature
description: This topic explains how to create a new Electronic invoicing feature when no configurable featue is available out-of-the-box for your country/region.
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

This topic explains how to create a new Electronic invoicing feature, when your country's configurable Electronic invoicing feature isn't provided out-of-the-box.

To create a new Electronic invoicing feature, you will:

- Create a new file format configuration using the invoice model configuration provided and leveraging the existing invoice mapping for the feature you want to create.
- Add the file format configurations to the Electronic invoicing feature configurations.
- Create the Electronic invoicing feature setup.
- Complete and publish the new Electronic invoicing feature to the Global repository for your organization.
- Deploy the new Electronic invoicing feature to the Service environment.

## Create new file format configurations derived from the existing invoice model

In this procedure, you will create the file format configurations required for the new Electronic invoicing feature you want to create. You can create the electronic invoice file format configuration and any other file format configurations your new Electronic invoicing feature may require.

Before you begin the steps in this procedure, sign in to your Regulatory Configuration Service (RCS) account. 

1. In Dynamiocs 365 Finance, in the **Electronic reporting** workspace, select **Repositories** from **Microsoft** Configuration provider.
2. Select **Global**, select **Open**, and in the left panel, select the **Invoice model** configuration. 

    > [!IMPORTANT]
    > For Brazil, select the **Fiscal documents** model configuration instead.
    
3. On **Configurations** tab, select **Import**.
4. Close the page.
5. Close the page.
6. Select **Reporting configurations** tile and then select the invoice model you imported.
7. Select **Create configuration**, and then select **Format based on invoice context model**.
8. Enter the name and a description of the format configuration.
9. In the **Format type** field, select the file extension type.
10. Select **Create configuration**, and then select the format configuration you created.
11. Select **Designer**, and use the Format designer tool to configure the file layout to meet the file format specifications. Close the page.
12. On **Versions** tab, select **Change status** to **Complete**.
13. On **Versions** tab, select **Change status** to **Share** to publish in the Global repository.

The new file format configuration must be shared with the Microsoft domain before the configuration can be consumed by the Electronic invoicing service.

1. Select the format configuration you are working on. The status of the configuration must be **Shared**.
2. On the **Versions** tab, select **Advanced sharing** > **Global repository**.
3. On the **Shared with** tab, select **+Organization**.
4. In the **Parameters** field, enter **Microsoft.com** to share with the Microsoft domain and then select **OK**.

## Create the new Electronic invoicing feature

1. In RCS, in the **Globalization features** workspace, in the **Features** section, select the **Electronic invoicing** tile.
2. Select **Add**, and then select **New feature**.
3. Enter the name and a description of the Electronic invoicing feature.
4. Select **Create feature**.

## Add Electronic invoicing feature Configurations

1. Select the Electronic invoicing feature you are working on.
2. On the **Configurations** tab, select **Add**.
3. In the **Configurations** grid, browse and select the file format configurations your Electronic invoicing feature requires to generate the electronic invoice file.
4. Select **OK**.

## Add Electronic invoicing feature setups

1. On the **Setups** tab, select **Add** and then select **Custom setup.**
2. Enter a name and description of the feature setup.
3. In the **Setup type** field, select **Processing pipeline** and then select **Create**.
4. Select the setup you are working on, and then select **Edit**.
5. On the **Processing pipeline** tab, select **New** to add new pipeline action. For more information about pipelines, see [Actions](e-invoicing-configuration-rcs.md#actions).
6. On the **Applicability rules** tab, select **New** to add new applicability rules clauses. For more information about applicability rules, see [Applicability rules](e-invoicing-configuration-rcs.md#applicability-rules).
7. On the **Variables** tab, select **New** to add new variables as needed.
8. Select **Save**, and then select **Validate** to check the consistency of the configuration.
9. Close the page.

## Deploy the Electronic invoicing feature to the service environment

For information about how to complete this procedure, see [Deploy the Electronic invoicing feature to Service environment](e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-service-environment).

## Deploy the Electronic invoicing feature to a connected application

For information about how to complete this procedure, see [Configure the application setup](e-invoicing-get-started.md#configure-the-application-setup) and [Deploy the Electronic invoicing feature to Connected application](e-invoicing-get-started.md#deploy-the-electronic-invoicing-feature-to-connected-application).

