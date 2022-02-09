---
# required metadata

title: Electronic invoicing for Egypt
description: This topic provides information that will help you get started with Electronic invoicing for Egypt in Finance and Supply Chain Management.
author: gionoder
ms.date: 02/09/2022
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
ms.custom: ["97423", "intro-internal"]
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Electronic invoicing for Egypt

[!include [banner](../includes/banner.md)]

This topic provides information that will help you get started with Electronic invoicing for Egypt. The topic guides you through the configuration steps that are country-dependent in the Regulatory Configuration Services (RCS), and complement the steps described in the topic, [Set up Electronic invoicing](e-invoicing-set-up-overview.md).

## Prerequisites
Before you complete the procedures in this topic:

- Get familiar with Electronic invoicing as described in the topic, [Electronic invoicing overview](e-invoicing-service-overview.md).
- Sign up to Regulatory Configuration service (RCS) and setup Electronic invoicing. For more information, see:
 
  - [Electronic invoicing sign up and installation overview](e-invoicing-sign-up-install.md)
  - [Setup Azure resources for Electronic invoicing](e-invoicing-set-up-azure-resources.md)
  - [Install the add-in for microservices in Lifecycle Services](e-invoicing-install-add-in-microservices-lcs.md)
	
- Activate integration between your Dynamics 365 Finance or Dynamics 365 Supply Chain management application and the Electronic invoicing service as described in the topic, [Activate and setup integration with Electronic invoicing](e-invoicing-activate-setup-integration.md).

- Create a digital certificate secret in Azure Key Vault, and set it up it as described in the topic, [Customer certificates and secrets](e-invoicing-customer-certificates-secrets.md). For testing purposes, the Egyptian tax authority provides specific test digital certificates that must be used only during testing and solution validation phases. For more information, consult the Egyptian tax authority website using the link provided in the [Egyptian e-invoicing SDK](https://sdk.sit.invoicing.eta.gov.eg/faq/).

## Country-specific configuration for Egyptian electronic invoice (EG) feature
Some of the parameters from the **Egyptian electronic invoice (EG)** Electronic invoicing feature are published with default values. Review the values and if necessary, update the values to better reflect your business operation before you deploy the Electronic invoicing feature to the service environment.

 1. Import the latest version of **Egyptian electronic invoice (EG)** globalization feature as described in topic, [Import feature from Global repository](e-invoicing-import-feature-global-repository.md). 
 2. Create a copy of the imported globalization feature with your configuration provider as described in the topic, [Create a new globalizationfeature](e-invoicing-create-new-globalization-feature.md).
 3. On the **Versions** tab, verify the **Draft** version is selected.
 4. On the **Setups** tab, in the grid, select the feature setup, **Sales invoice derived**.
 5. Select **Edit**, and on the **Processing pipeline** tab, in the **Processing pipeline** field group, select **Sign json document for Egyptian Tax Authority**.
 6. In the **Parameters** field group, select **Certificate name** and then select the name of the digital certificate you created.
 7. In the **Processing pipeline** field group, select **Integrate with Egyptian ETA service**. Repeat this step for the two occurrences of this action.
 8. In the **Parameters** field group, select **Web service URL**, **Login service URL** and if necessary, review the URL parameters. Consult the Egyptian tax authority website to get the Testing and Production URL, using the link provided in the [Egyptian e-invoicing SDK](https://sdk.sit.invoicing.eta.gov.eg/faq/).
 9. Select **Save** and close the page.
 10. Repeat the steps 4 - 9 to set up the feature, **Project invoice derived**.

## Country-specific configuration for the Egyptian electronic invoice (EG) application setup 
There are parameters that must be set up in your Finance or Supply Chain Management environment. There are two places where you can do this setup:

- Directly in your Finance or Supply Chain Management environment. For more information, see [Setup Electronic Invoicing parameters](e-invoicing-set-up-parameters.md).
- In RCS. In the scope of Electronic invoicing feature setup, you can define all parameters and then deploy them directly to your Finance or Supply Chain management environment when you deploy the Electronic invoicing feature.

For both options, the parameters are the same. If this is your first feature that you have set up in the Electronic invoicing service, we recommend that you follow the steps below to set up parameters in RCS and then deploy them to your connected application.

> [!NOTE]
> Some Electronic invoicing feature versions may contain a pre-defined set of application-specific parameters for Finance pr Supply Chain Management. In this scenario, verify the correctness of the data. Otherwise, enter parameters manually. 

 1. Locate to your copy of the **Egyptian electronic invoice (EG)** globalization feature you created.
 2. On the **Versions** tab, verify that the **Draft** version is selected.
 3. On the **Setups** tab, select **Application setup** and in the **Connected applications** field, select the application where you want to deploy the parameters.
 4. On the **Electronic document types** page, select **Add** to create a new record.
 5. In the **Table name** field, add table name, **CustInvoiceJour**.
 6. In the **Context** field, add reference to the mapping name, **Customer invoice context**. The configuration is **Customer invoice context model**.
 7. In the **Electronic document mapping** field, add a reference to the **Customer invoice** mapping name. The configuration is **Invoice model mapping**. Select **Save**.
 8. In **Response types** select **Add**.
 9. In the **Response type** field, enter **Response**, and in the **Description** field, enter **Process response**.
 10. In the **Submission status** field, select **Pending**.
 11. In the **Model mapping** field, select the **Response message impor*** mapping name. The configuration is **Egypt response message import (EG)**. Select **Save**.
 12. On the **Response types** page, select **Add**.
 13. In the **Response type** field, enter **ResponseData**, and in the **Description** field, enter **Process response data**.
 14. In the **Submission status** field, select **Pending**.
 15. In the **Data entity name** field, select **SalesInvoiceHeaderV2Entity**.
 16. In the **Model mapping** field, select **Response data import**. The configuration is **Egypt response data import format (EG)**.
 17. Select **Save** and close the page.
 18. Close the page.

To deploy a feature to the service environment and application setup to the Finance or Supply Chain management connected application, see [Complete, publish, and deploy a globalization feature](e-invoicing-complete-publish-deploy-globalization-feature.md)

## Privacy notice

Enabling the **Egyptian electronic invoice (EG)** feature may require sending limited data, including the organization tax registration ID. This data will be transmitted to third-party agencies authorized by the tax authority for the purpose of sending electronic invoices to this tax authority in the predefined format that's required for integration with the government's web service. An administrator can enable and disable the feature by navigating to **Organization administration** > **Setup** > **Electronic document parameters**. On the **Features** tab, select the row that contains the **Egyptian electronic invoice (EG)** feature, and then make the appropriate selection. Data imported from these external systems into this Dynamics 365 online service are subject to our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=512132). Consult the Privacy notice sections in country-specific feature documentation for more information.

## Additional resources

- [Electronic invoicing overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](e-invoicing-get-started.md)
- [Customer electronic invoices in Egypt](emea-egy-e-invoices.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
