---
title: Connection configuration for Chilean electronic invoicing
description: This article explains how to set up Finance and RCS to use Chilean electronic invoices formats. 
author: Fhernandez0088 
ms.date: 10/17/2023 
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---

# Connection configuration for Chilean electronic invoicing
## In this article
1. [Prerequisites]()
2. [Country/region-specific configuration for the Electronic invoicing for Chile feature]()
3. [Finance configuration]()
4. [Issue electronic invoices]()
5. [Additional resources]()

This article provides information that will help you get started with Electronic invoicing for Chile. It guides you through the configuration steps that are country/region-dependent in Regulatory Configuration Service (RCS) and in Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management. These steps complement the steps that are described in [Set up Electronic invoicing](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/e-invoicing-set-up-overview).

## Prerequisites

Before you begin the procedures in this article, the following prerequisites must be met:

* Become familiar with Electronic invoicing as it's described in [Electronic invoicing overview](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/e-invoicing-service-overview).

* Sign up for RCS, and set up Electronic invoicing. For more information, see the following articles:
* [Sign up for and install the Electronic Invoicing service](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/e-invoicing-sign-up-install)
* [Set up Azure resources for Electronic invoicing](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/e-invoicing-set-up-azure-resources)
* [Install the add-in for microservices in Lifecycle Services](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/e-invoicing-install-add-in-microservices-lcs)

* Activate the integration between your Finance or Supply Chain Management app and the Electronic Invoicing service as described in [Activate and setup integration with Electronic invoicing](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/e-invoicing-activate-setup-integration).
* Make sure that the following Electronic reporting (ER) format configurations are imported. For more information, see [Import Electronic reporting (ER) configurations](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations).

* Inventory e-invoice (CL)
* E-shipping guide (CL)
* Project e-invoice (CL)
* Project e-shipping guide (CL)

    > [!NOTE]
    > These formats are based on the corresponding **LATAM** format configurations that use the **Invoice model** and **Invoice model mapping** configurations. All required additional configurations are automatically imported.

## Country/region-specific configuration for the Electronic invoicing for Chile
Some of the parameters from the **Electronic invoicing for Chile** feature are published with default values. Before you deploy the electronic invoicing feature to the service environment, review the default values, and update them as required so that they better reflect your business operations.

1. Import the latest version of the **Electronic invoicing for Chile** Globalization feature as described in [Import features from the Global repository](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/e-invoicing-import-feature-global-repository).

2. Create a copy of the imported Globalization feature, and select your configuration provider for it. For more information, see [Create a Globalization feature](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/e-invoicing-create-new-globalization-feature).

    > [!NOTE]
    > The **Electronic invoicing for Chile** feature is provided by Microsoft. It's ready to use and requires no additional configuration. For information about how to configure invoicing features if you must apply changes, see [**Work with feature setups**](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/e-invoicing-feature-setup). For example, you can filter specific legal entities so that they're processed in applicability rules. By default, the feature is applicable to all legal entities that have a primary address in Chile.


3. The copy of the feature is always created as a **Draft** version. Regardless of whether you made changes, complete, publish, and deploy the feature as described in [Complete, publish, and deploy a Globalization feature](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/e-invoicing-complete-publish-deploy-globalization-feature).

## Finance configuration

Some additional parameters must be configured directly in Finance.

1. Make sure that the country/region-specific ER configurations for the document context and electronic document model mapping that are required for Chile are imported. For more information, see [Set up Electronic invoicing parameters](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/e-invoicing-set-up-parameters#set-up-electronic-document-parameters).

    > [!NOTE]
    > After you import the **Electronic invoicing for Chile** electronic invoicing feature, electronic documents are configured by default. If you must make changes, complete the following steps.




2. Go to **Organization administration** > **Setup** > **Electronic document parameters**.

3. In the **Electronic document** section, add records for the **Customer Invoice journal**, **Customer packing slip journal** and **Project invoice** table names.

4. For each table name, set the **Document context** and **Electronic document model mapping** fields in accordance with step 1.

5. Save your changes, and close the page.

## Issue electronic invoices

When you've completed all the required configuration steps, you can generate electronic invoices for posted invoices. For more information about how to generate electronic invoices, see [Issue electronic invoices in Finance and Supply chain management](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-issuing-electronic-invoices-finance-supply-chain-management).

You can inquire about the results of the submission by going to **Organization administration** > **Periodic** > **Electronic documents** > **Electronic document submission log** and selecting the required document type.

To download the XML files of electronic invoices for successfully processed invoices, select **Electronic document** > **Download file**.

## Additional resources

* [Electronic invoicing overview](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/global/e-invoicing-service-overview)

* [Get started with Electronic invoicing service administration](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-get-started-service-administration)

* [Get started with Electronic invoicing](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-get-started)
