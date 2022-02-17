---
# required metadata

title: Get started with Electronic invoicing for Egypt
description: This topic provides information that will help you get started with Electronic invoicing for Egypt in Finance and Supply Chain Management.
author: gionoder
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
ms.custom: intro-internal
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Get started with Electronic invoicing for Egypt

[!include [banner](../includes/banner.md)]

This topic provides information that will help you get started with Electronic invoicing for Egypt. The topic guides you through the configuration steps that are country-dependent in Regulatory Configuration Services (RCS), and complement the steps described in [Get started with Electronic invoicing](e-invoicing-get-started.md).

## Country-specific configuration for Egyptian electronic invoice (EG) Electronic invoicing feature

Some of the parameters from the **Egyptian electronic invoice (EG) Electronic invoicing feature** are published with default values. Review the values and if necessary, update the values to better reflect your business operation before you deploy the Electronic invoicing feature to the Service environment.

This section complements the **Country-specific configuration for Electronic invoicing feature** section in the topic [Get started with Electronic invoicing](e-invoicing-get-started.md).

### Prerequisites

Before you complete the procedure in this section, you must:

- Create a digital certificate secret, as described in the **Create digital certificate secret** section in [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md). For testing purposes, the Egyptian tax authority provides specific test digital certificates that must be used only during testing and solution validation phases. For more information, consult the Egyptian tax authority website using the link provided in the [Egyptian e-invoicing SDK](https://sdk.sit.invoicing.eta.gov.eg/faq/).

1. In RCS, in the **Features** section of the **Globalization feature** workspace, select the **Electronic invoicing** tile.
2. On the **Electronic invoicing Features** page, verify that the **Egyptian electronic invoice (EG)** Electronic invoicing feature you created is selected.
3. On the **Versions** tab, verify the **Draft** version is selected.
4. On the **Setups** tab, in the grid, select **Sales invoice** feature setup.
5. Select **Edit**, and on the **Actions** tab in the **Actions** field group, select **Sign json document for Egyptian Tax Authority**.
6. In the **Parameters** field group, select the parameter, **Certificate name** and select the name of the digital certificate created to use with the Electronic invoicing feature.
7. In the **Actions** field group, select **Integrate with Egyptian ETA service**. Repeat this step for the two occurrences of this action.
8. In the **Parameters** field group, select **Web service URL** and **Login service URL** and, if necessary, review the URL parameters. Consult the Egyptian tax authority website to get the Testing and Production URL, using the link provided in the [Egyptian e-invoicing SDK](https://sdk.sit.invoicing.eta.gov.eg/faq/).
9. Select **Save** and close the page.
10. To deploy the Electronic invoicing feature to the Service environment, see [Get started with Electronic invoicing](e-invoicing-get-started.md).

## Country-specific configuration of the application setup for the Egyptian electronic invoice (EG) Electronic invoicing feature

Complete these steps before you deploy the Application setup to your Finance or Supply Chain Management Connected application.

This section complements the **Country-specific configuration of application setup** section in the topic [Get started with Electronic invoicing](e-invoicing-get-started.md).

1. In RCS, in the **Features** section of the **Globalization feature** workspace, select the **Electronic invoicing** tile.
2. In the **Electronic invoicing Features** page, verify that the **Egyptian electronic invoice (EG)** Electronic invoicing feature is selected.
3. On the **Versions** tab, verify that the **Draft** version is selected.
4. On the **Setups** tab, select **Application setup** and in the **Connected application** field, select the application where you want to deploy.
5. In the **Table name** field, verify that the customer invoice journal is selected.
6. Select **Response types**, and then select **New**.
7. In the **Response type** field, enter "Response" and in the **Description** field, enter "Description".
8. In the **Submission status** field, select **Pending**.
9. In the **Model mapping** field, select **Model mapping from response message**, with **(Preview) Response message import format**, and then select **Save**.
10. Select **New** and in the **Response type** field, enter "ResponseData" as a fixed value. In the **Description** field, enter "Description".
11. In the **Submission status** field, select **Pending**.
12. In the **Data entity name** field, select **Sales invoice headers V2**.
13. In the **Model mapping** field, select **Egypt response data import**, with **(Preview) Egypt response data import** and then select **Save**.
14. To deploy the application setup to the Finance or Supply Chain Management connected application, see [Get started with Electronic invoicing](e-invoicing-get-started.md).

## Privacy notice

Enabling the **Egyptian electronic invoice (EG)** feature may require sending limited data, including the organization tax registration ID. This data will be transmitted to third-party agencies authorized by the tax authority for the purpose of sending electronic invoices to this tax authority in the predefined format that's required for integration with the government's web service. An administrator can enable and disable the feature by navigating to **Organization administration** > **Setup** > **Electronic document parameters**. On the **Features** tab, select the row that contains the **Egyptian electronic invoice (EG)** feature, and then make the appropriate selection. Data imported from these external systems into this Dynamics 365 online service are subject to our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=512132). Consult the Privacy notice sections in country-specific feature documentation for more information.

## Additional resources

- [Electronic invoicing overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](e-invoicing-get-started.md)
- [Customer electronic invoices in Egypt](emea-egy-e-invoices.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
