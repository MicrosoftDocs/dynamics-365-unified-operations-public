---
# required metadata

title: Electronic invoicing for Egypt
description: This topic provides information that will help you get started with Electronic invoicing for Egypt in Finance and Supply Chain Management.
author: gionoder, dkalyuzh
ms.date: 04/20/2021
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

This topic provides information that will help you get started with Electronic invoicing for Egypt. The topic guides you through the configuration steps that are country-dependent in Regulatory Configuration Services (RCS), and complement the steps described in [Electronic invoicing setup overview](e-inv_tut-setup-electronic-invoicing_overview.md).

## Prerequisites
Before you complete the procedure in this article, you must:
- Get familiar with Electronic invoicing as described in [Electronic invoicing setup overview](e-inv_tut-setup-electronic-invoicing_overview.md).
- Sign up to Regulatory Configuration service (RCS) and setup Electronic invoicing as described in articles:
  - [Sign up and install Electronic invoicing](e-inv_tut-setup-electronic-invoicing_sign-up_overview.md)
  - [Setup Azure resources](e-inv_tut-setup-electronic-invoicing_azure_overview.md)
  - [Setup Environments](e-inv_tut-setup-electronic-invoicing_setup-env_overview.md)
	
- Activate integration of your Dynamics 365 Finance and Supply Chain management applications with Electronic invoicing service as described in article [Activate and setup integration with Electronic invoicing](e-inv_tut-setup-Finance_setup-finance_activate-integration.md).

- Create a digital certificate secret in Azure Key Vault, and setup it as described in [Customer certificates and secrets](e-inv_tut-setup-electronic-invoicing_setup-env_cert-and-secrets.md). For testing purposes, the Egyptian tax authority provides specific test digital certificates that must be used only during testing and solution validation phases. For more information, consult the Egyptian tax authority website using the link provided in the [Egyptian e-invoicing SDK](https://sdk.sit.invoicing.eta.gov.eg/faq/).

## Country-specific configuration for Egyptian electronic invoice (EG) feature
Some of the parameters from the ***Egyptian electronic invoice (EG)*** Electronic invoicing feature are published with default values. Review the values and if necessary, update the values to better reflect your business operation before you deploy the Electronic invoicing feature to the Service environment.
	
 1. Import the latest version of ***Egyptian electronic invoice (EG)*** globalization feature as described in article [Import feature from Global repository](e-inv_tut-setup-electronic-invoicing_global-feature_import.md). 
 2. Create a copy of the imported globalization feature with your Configuration provider as described in the article [Create new feature](e-inv_tut-setup-electronic-invoicing_global-feature_create-new.md)(Based on existing feature).
 3. On the **Versions** tab, verify the **Draft** version is selected.
 4. On the **Setups** tab, in the grid, select ***Sales invoice derived*** feature setup.
 5. Select **Edit**, and on the **Processing pipeline** tab in the **Processing pipeline** field group, select **Sign json document for Egyptian Tax Authority** action.
   - In the **Parameters** field group, select parameter **Certificate name** and select the name of the digital certificate created earlier.
 6. In the **Processing pipeline** field group, select **Integrate with Egyptian ETA service** action. Repeat this step for the two occurrences of this action.
   - In the **Parameters** field group, select **Web service URL** and **Login service URL** and, if necessary, review the URL parameters. Consult the Egyptian tax authority website to get the Testing and Production URL, using the link provided in the [Egyptian e-invoicing SDK](https://sdk.sit.invoicing.eta.gov.eg/faq/).
 7. Select **Save** and close the page.
 8. Repeat the steps 4 - 7 for feature setup ***Project invoice derived***.


## Country-specific configuration for the Egyptian electronic invoice (EG) application setup 
There are parameters that must be setup in you Dynamics 365 Finance and Supply Chain management. There are two options where you can do this setup:
 - Directly in your Finance and Supply Chain management applications. See details: [Setup Electronic Invoicing parameters](e-inv_tut-setup-Finance_setup-finance_setup-parameters.md).
 - In RCS in scope of Electronic invoicing feature setup you can define all parameters, and then deploy them directly to your Finance and Supply Chain management environments during Electronic invoicing feature deployment.

For both options the parameters are the same. If this is your first feature that you setup in Electronic invoicing service, we recommend to follow the steps below to setup parameters in RCS and then deploy them to your connected application.

> [!NOTE]
> Some Electronic invoicing feature versions may contain predefined set of Application specific parameters for Finance and Supply Chain management applications. In this case you need to verify the correctness of the data. Otherwise, you must enter parameters manually. 

 1. Locate to your copy of ***Egyptian electronic invoice (EG)*** globalization feature created in the previous steps.
 2. On the **Versions** tab, verify that the **Draft** version is selected.
 3. On the **Setups** tab, select **Application setup** and in the **Connected applications** field select an application where you want to deploy the parameters.
 4. In **Electronic document types** add new record by selecting **Add** button.
 5. In the **Table name** field, add table name ***CustInvoiceJour***.
 6. In the **Context** field, add reference to ***Customer invoice context*** mapping name, configuration is ***Customer invoice context model***.
 7. In the **Electronic document mapping** field, add reference to ***Customer invoice*** mapping name, configuration is ***Invoice model mapping***.
 8. Select **Save**.
 9. In **Response types** select **Add**.
 10. In the **Response type** field, enter "Response" and in the **Description** field, enter "Process response".
 11. In the **Submission status** field, select **Pending**.
 12. In the **Model mapping** field, select ***Response message import*** mapping name, configuration is ***Egypt response message import (EG)***.
 13. Select **Save**.
 14. In **Response types** select **Add**.
 15. In the **Response type** field, enter "ResponseData" as a fixed value. In the **Description** field, enter "Process response data".
 16. In the **Submission status** field, select **Pending**.
 17. In the **Data entity name** field, select ***SalesInvoiceHeaderV2Entity***.
 18. In the **Model mapping** field, select ***Response data import*** mapping name, configuration is ***Egypt response data import format (EG)***.
 19. Select **Save** and close the form.
 20. Close the form.

To deploy feature to the Service environment and application setup to the Finance or Supply Chain management connected application, see [Complete, publish and deploy](e-inv_tut-setup-electronic-invoicing_global-feature_complete-publish.md)

## Privacy notice

Enabling the **Egyptian electronic invoice (EG)** feature may require sending limited data, including the organization tax registration ID. This data will be transmitted to third-party agencies authorized by the tax authority for the purpose of sending electronic invoices to this tax authority in the predefined format that's required for integration with the government's web service. An administrator can enable and disable the feature by navigating to **Organization administration** > **Setup** > **Electronic document parameters**. On the **Features** tab, select the row that contains the **Egyptian electronic invoice (EG)** feature, and then make the appropriate selection. Data imported from these external systems into this Dynamics 365 online service are subject to our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=512132). Consult the Privacy notice sections in country-specific feature documentation for more information.

## Additional resources

- [Electronic invoicing overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](e-invoicing-get-started.md)
- [Customer electronic invoices in Egypt](emea-egy-e-invoices.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
