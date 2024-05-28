---
title: Set up electronic invoicing in Costa Rica
description: Learn how to set up Microsoft Dynamics 365 Finance and Regulatory Configuration Service (RCS) to use electronic invoice formats for Costa Rica.
author: Cpicon85
ms.author: v-cpicon
ms.topic: article
ms.date: 02/15/2024 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Connection configuration for Costa Rica electronic invoicing

[!include [banner](../../includes/banner.md)]

This article provides information to help you get started with Electronic invoicing for Costa Rica. It guides you through the configuration steps that are country/region-dependent in Regulatory Configuration Service (RCS) and in Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management. These steps complement the steps that are described in [Electronic invoicing setup](../global/e-invoicing-set-up-overview.md).

## Prerequisites

Before you begin the procedures in this article, the following prerequisites must be met:

- Become familiar with Electronic invoicing. For more information, see [Electronic invoicing overview](../global/e-invoicing-service-overview.md).
- Sign up for RCS, and set up Electronic invoicing. For more information, see the following articles:

    - [Sign up for and install the Electronic Invoicing service](../global/e-invoicing-sign-up-install.md)
    - [Set up Azure resources for Electronic invoicing](../global/e-invoicing-set-up-azure-resources.md)
    - [Install the add-in for microservices in Lifecycle Services](../global/e-invoicing-install-add-in-microservices-lcs.md)

- Activate the integration between your Finance or Supply Chain Management app and the Electronic Invoicing service as described in [Activate and set up integration with Electronic invoicing](../global/e-invoicing-activate-setup-integration.md).
- Make sure that the following Electronic reporting (ER) format configurations are imported. For more information, see [Import Electronic reporting (ER) configurations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations.md).

    - Inventory e-invoice (CRI)
    - Inventory Credit Note (CRI)
    - Inventory Debit Note (CRI)
    - Project e-invoice (CRI)
    - Project Credit Note (CRI)
    - Project Debit Note (CRI)

    > [!NOTE]
    > These formats are based on the corresponding **LATAM** format configurations that use the **Invoice model** and **Invoice model mapping** configurations. All additional configurations that are required are automatically imported.

## Country/region-specific configuration for Electronic invoicing for Costa Rica

Some of the parameters from the **Electronic invoicing for Costa Rica** feature are published with default values. Before you deploy the electronic invoicing feature to the service environment, review the default values, and update them as required so that they better reflect your business operations.

1. Import the latest version of the **Electronic invoicing for Costa Rica** Globalization feature as described in [Import features from the Global repository](../global/e-invoicing-import-feature-global-repository.md).
2. Create a copy of the imported Globalization feature, and select your configuration provider for it. For more information, see [Create a Globalization feature](../global/e-invoicing-create-new-globalization-feature.md).

    > [!NOTE]
    > The **Electronic invoicing for Costa Rica** feature is provided by Microsoft. The feature is ready to use and requires no additional configuration. For information about how to configure invoicing features if you must apply changes, see [Work with feature setups](../global/e-invoicing-feature-setup.md). For example, you can filter specific legal entities so that they're processed in applicability rules. By default, the feature is applicable to all legal entities that have a primary address in Costa Rica.

3. The copy of the feature is always created as a **Draft** version. Regardless of whether you made changes, you must complete, publish, and deploy the feature as described in [Complete, publish, and deploy a Globalization feature](../global/e-invoicing-complete-publish-deploy-globalization-feature.md).

## Finance configuration

Some additional parameters must be configured directly in Finance.

1. Make sure that the country/region-specific ER configurations for the document context and electronic document model mapping that are required for Costa Rica are imported. For more information, see [Set up Electronic document parameters](../global/e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).

    > [!NOTE]
    > After you import the **Electronic invoicing for Costa Rica** electronic invoicing feature, electronic documents are configured by default. If you must make changes, complete the remaining steps of this procedure.

2. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
3. In the **Electronic document** section, add records for the **Customer Invoice journal** and **Project invoice** table names.
4. For each table name, set the **Document context** and **Electronic document model mapping** fields in accordance with step 1.
5. Save your changes, and close the page.

## Issue electronic invoices

When you've completed all the required configuration steps, you can generate electronic invoices for posted invoices.

You can inquire about the results of the submission by going to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log** and selecting the required document type.

To download the XML files of electronic invoices for successfully processed invoices, select **Electronic document** \> **Download file**.

> [!IMPORTANT]
> In current implementations, the standard submission procedure described above only generates electronic invoices and stores their XML files on the service side, but it doesn't submit the invoices. For the submission of Costa Rican electronic invoices, integration with the [Electronic Invoicing service ISV last-mile connector](../global/e-invoicing-isv-connector.md) is required. However, this connector hasn't been released yet.

## More resources

- [Electronic invoicing overview](../global/e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](../e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](../e-invoicing-get-started.md)
- [Electronic Invoicing service independent software vendor (ISV) last-mile connector](../global/e-invoicing-isv-connector.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
