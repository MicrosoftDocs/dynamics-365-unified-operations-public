---
title: Configure connections for Chilean electronic invoicing
description: This article explains how to set up Dynamics 365 Finance and RCS to use Chilean electronic invoices formats. 
author: Fhernandez0088 
ms.date: 10/17/2023 
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Connection configuration for Chilean electronic invoicing

[!include [banner](../../includes/banner.md)]

This article explains how to set up Dynamics 365 Finance and the Regulatory Configuration Service (RCS) to use Chilean electronic invoices formats.

## In this article
1. [Prerequisites](#prerequisites)
2. [Country/region-specific configuration for the Electronic invoicing for Chile feature](#countryregion)
3. [Finance configuration](#finance)
4. [Issue electronic invoices](#issue)

This article provides information that will help you get started with Electronic invoicing for Chile. It guides you through the configuration steps that are country/region-dependent in Regulatory Configuration Service (RCS) and in Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management. These steps complement the steps that are described in [Set up Electronic invoicing](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/e-invoicing-set-up-overview).

## <a name="prerequisites"></a> Prerequisites

Before you begin the procedures in this article, the following prerequisites must be met:

- Familiarity with and understanding of Electronic invoicing as it's described in [Electronic invoicing overview](../global/e-invoicing-service-overview.md).
- Sign up for RCS, and set up Electronic invoicing. For more information, see the following articles:

    - [Sign up for and install the Electronic Invoicing service](../global/e-invoicing-sign-up-install.md)
    - [Set up Azure resources for Electronic invoicing](../global/e-invoicing-set-up-azure-resources.md)
    - [Install the add-in for microservices in Lifecycle Services](../global/e-invoicing-install-add-in-microservices-lcs.md)

- Activate the integration between your Finance or Dynamics 365 Supply Chain Management app and the Electronic Invoicing service. To learn more, see [Activate and setup integration with Electronic invoicing](../global/e-invoicing-activate-setup-integration.md).
- Make sure that the following Electronic reporting (ER) format configurations are imported. For more information, see [Import Electronic reporting (ER) configurations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations.md).

     - Inventory e-invoice (C
     - E-shipping guide (CL)
     - Project e-invoice (CL)
     - Project e-shipping guide (CL)

     > [!NOTE]
     > These formats are based on the corresponding **LATAM** format configurations that use the **Invoice model** and **Invoice model mapping** configurations. All required additional configurations are automatically imported.

## <a name="countryregion"></a> Country/region-specific configuration for the Electronic invoicing for Chile
Some parameters in the **Electronic invoicing for Chile** feature are published with default values. Before you deploy the electronic invoicing feature to the service environment, review the default values, and update them as required so that they better reflect your business operations.

1. Import the latest version of the **Electronic invoicing for Chile** Globalization feature. To learn more, see [Import features from the Global repository](../global/e-invoicing-import-feature-global-repository.md).
2. Create a copy of the imported Globalization feature, and select your configuration provider. For more details, see [Create a Globalization feature](../global/e-invoicing-create-new-globalization-feature.md).

    > [!NOTE]
    > The **Electronic invoicing for Chile** feature is provided by Microsoft. The feature is ready to use and requires no additional configuration. For information about how to configure invoicing features if you must apply changes, see [**Work with feature setups**](../global/e-invoicing-feature-setup.md). For example, you can filter specific legal entities so that they're processed in applicability rules. By default, the feature is applicable to all legal entities that have a primary address in Chile.

3. The copy of the feature is always created as a **Draft** version. Regardless of whether you made changes, you must complete, publish, and deploy the feature as described in the article [Complete, publish, and deploy a Globalization feature](../global/e-invoicing-complete-publish-deploy-globalization-feature.md).

## <a name="finance"></a> Finance configuration

There are some additional parameters that must be configured directly in Finance.

1. Make sure that the country/region-specific ER configurations for the document context and electronic document model mapping that are required for Chile are imported. For more information, see [Set up Electronic invoicing parameters](../global/e-invoicing-set-up-parameters#set-up-electronic-document-parameters.md).

    > [!NOTE]
    > After you import the feature, **Electronic invoicing for Chile**, electronic documents are configured by default. If you must make changes, complete the following steps.

2. Go to **Organization administration** > **Setup** > **Electronic document parameters**.
3. In the **Electronic document** section, add records for the **Customer Invoice journal**, **Customer packing slip journal** and **Project invoice** table names.
4. For each table name, set the **Document context** and **Electronic document model mapping** fields in accordance with step 1.
5. Save your changes, and close the page.

## <a name="issue"></a> Issue electronic invoices

When you complete all the required configuration steps, you can generate electronic invoices for posted invoices. You can inquire about the results of the submission by going to **Organization administration** > **Periodic** > **Electronic documents** > **Electronic document submission log** and selecting the required document type.

To download the XML files of electronic invoices for successfully processed invoices, select **Electronic document** > **Download file**.

## More resources

* [Electronic invoicing overview](../global/e-invoicing-service-overview.md)
* [Get started with Electronic invoicing service administration](../global/e-invoicing-get-started-service-administration.md)
* [Get started with Electronic invoicing](../global/e-invoicing-get-started.md)



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
