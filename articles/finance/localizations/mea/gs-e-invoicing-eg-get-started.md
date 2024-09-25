---
title: Electronic invoicing for Egypt
description: This article explains how to get started with electronic invoicing for Egypt in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
author: achansoriya
ms.author: achansoriya
ms.topic: how-to
ms.date: 09/19/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Egypt
ms.search.validFrom: 09/19/204
ms.dyn365.ops.version: AX 10.0.39
---

# Electronic invoicing in Egypt

[!include [banner](../../includes/banner.md)]

This article provides information that will help you get started with Electronic invoicing for Egypt. It guides you through the configuration steps that are country/region-dependent in Regulatory Configuration Service (RCS). These steps complement the steps that are described in [Set up Electronic invoicing](../global/e-invoicing-set-up-overview.md).

## Prerequisites

Before you begin the procedures in this article, complete the following prerequisites:

- Become familiar with Electronic invoicing as it's described in [Electronic Invoicing service overview](../global/gs-e-invoicing-service-overview.md).
- Do the common part of Electronic Invoicing service configuration as described in [Electronic invoicing configuration](../global/gs-e-invoicing-set-up-overview.md).
- Import the **Egyptian electronic invoice (EG)** version **20** or later, electronic invoicing features from the repository. For more information, see [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
- Configure Azure file share as described in [Configure Azure file share](../global/gs-e-invoicing-create-azure-file-share.md).

- Egyptian tax authority provides this certificate with the required key only as a hardware token device. Which cannot be added to the Azure key vault. Dynamics 365 Finance electronic invoicing provides capability of writing and reading files to/from Azure file share, which can be configured to enable external signing of electronic documents. For more information, go to the Egyptian tax authority website by using the link that is provided in [Egyptian e-invoicing SDK](https://sdk.invoicing.eta.gov.eg/faq/).

## Country/region-specific configuration for the Egyptian electronic invoice (EG) feature

Some of the parameters from the **Egyptian electronic invoice (EG)** electronic invoicing feature are published with default values. Before you deploy the electronic invoicing feature to the service environment, review the default values, and update them as required so that they better reflect your business operation.

1. Import the latest version of the **Egyptian electronic invoice (EG)** Globalization feature as described in [Import features from the Global repository](../global/gs-e-invoicing-import-feature-global-repository.md).
2. Create a copy of the imported Globalization feature, and select your configuration provider for it, as described in [Create a Globalization feature](../global/gs-e-invoicing-create-new-globalization-feature.md).
3. On the **Versions** tab, verify that the **Draft** version is selected.
4. On the **Feature parameters** tab, specify values for the following connection and integration parameters that are required for interoperation with Egyptian tax authority services:

    - **EgyptianETAClientID** – Enter the client ID provided by reglatory authority.
    - **EgyptianETAClientSecret** – Enter the secret provided by reglatory authority.
    - **EgyptianETAConnectionString** – Enter the connection string for Azure file share provisioned earlier using [Configure Azure file share](../global/gs-e-invoicing-create-azure-file-share.md).
    - **EgyptianETASendToFileShareDirectory** – Enter the name of Azure file share directory to write digital invoices for signing.
    - **EgyptianETAGetFromAzureFileShare** – Enter the name of Azure file share directory to read signed digital invoices.
    - **EgyptianETALoginserviceURL** – Egyptian tax authority login service url. Microsoft shipped feature points to pre-prod endpoint. 
    - **EgyptianETAWebserviceURL** – Egyptian tax authority web service url. Microsoft shipped feature points to pre-prod endpoint.
    
    The following illustration shows an example of a feature parameter setup that includes the URL for Egyptian tax authority pre-prod endpoint. 

      ![Screenshot that shows the Feature parameters tab configured for the Globalization feature for Egypt.](../media/eg-e-invoice-glob-feature-parameters.png)

5. Complete and deploy the **Egyptian electronic invoice (EG)** feature to the service. For more information, see [Complete and deploy a Globalization feature](../global/gs-e-invoicing-complete-publish-deploy-globalization-feature.md).

> [!NOTE]
> Since external signing is involved, feature published by Microsoft will continue to check the availability of signed invoice repeteadly until a maximum limit is reached. To re-configure retry action you configure the feature setup as follows:
>
> On the **Setups** tab, select **Sales invoice** or **Project invoice** depending on the scenario. Click **edit**.
>
> Pipeline action **Get from Azure file share**, configure **Retry parameters**.


## Country/region-specific configuration for the Egyptian electronic invoice (EG) application setup

There are parameters that must be set up in your Finance or Supply Chain Management environment. You can complete this setup in either of two places:

- Directly in your Finance or Supply Chain Management environment. For more information, see [Setup Electronic Invoicing parameters](../global/e-invoicing-set-up-parameters.md).
- In Globalization studio. In the scope of electronic invoicing feature setup, you can define all parameters and then deploy them directly to your Finance or Supply Chain Management environment when you deploy the electronic invoicing feature.

For both options, the parameters are the same. If you're setting up your first feature in the Electronic Invoicing service, we recommend that you follow these steps to set up the parameters in Globalization studio and then deploy them to your connected application.

> [!NOTE]
> Some electronic invoicing feature versions might contain a predefined set of application-specific parameters for Finance or Supply Chain Management. In this case, you should verify that the data is correct. Otherwise, manually set the parameters.

1. Find the copy of the **Egyptian electronic invoice (EG)** Globalization feature that you created.
2. On the **Versions** tab, verify that the **Draft** version is selected.
3. On the **Setups** tab, select **Application setup**.
4. In the **Connected applications** field, select the application where you want to deploy the parameters.
5. On the **Electronic document types** page, select **Add** to create a record.
6. In the **Table name** field, add **CustInvoiceJour**.
7. In the **Context** field, add a reference to the **Customer invoice context** mapping name. The configuration is **Customer invoice context model**.
8. In the **Electronic document mapping** field, add a reference to the **Customer invoice** mapping name. The configuration is **Invoice model mapping**.
9. Select **Save**.
10. On **Response types** page, select **Add**.
11. In the **Response type** field, enter **Response**.
12. In the **Description** field, enter **Process response**.
13. In the **Submission status** field, select **Pending**.
14. In the **Model mapping** field, select **Response message import**. The configuration is **Egypt response message import (EG)**.
15. Select **Save**.
16. Select **Add**.
17. In the **Response type** field, enter **ResponseData**.
18. In the **Description** field, enter **Process response data**.
19. In the **Submission status** field, select **Pending**.
20. In the **Data entity name** field, select **SalesInvoiceHeaderV2Entity**.
21. In the **Model mapping** field, select **Response data import**. The configuration is **Egypt response data import format (EG)**.
22. Select **Save**, and close the page.
23. Close the page.

To deploy a feature to the service environment and an application setup to the Finance or Supply Chain Management connected application, see [Complete, publish, and deploy a Globalization feature](../global/e-invoicing-complete-publish-deploy-globalization-feature.md)

## Privacy notice

Enabling the **Egyptian electronic invoice (EG)** feature might require that limited data be sent. This data includes the organization's tax registration ID. The data will be transmitted to third-party agencies that have been authorized by the tax authority to send electronic invoices to that tax authority in the predefined format that is required for integration with the government's web service. An administrator can enable and disable the feature by going to **Organization administration** \> **Setup** \> **Electronic document parameters**. On the **Features** tab, select the row that contains the **Egyptian electronic invoice (EG)** feature, and then make the appropriate selection. Data that is imported from external systems into this Dynamics 365 online service are subject to our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=512132). For more information, see the "Privacy notice" section in country/region-specific feature documentation.

## Additional resources

- [Electronic invoicing overview](../global/e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](../e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](../e-invoicing-get-started.md)
- [Customer electronic invoices in Egypt](emea-egy-e-invoices.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
