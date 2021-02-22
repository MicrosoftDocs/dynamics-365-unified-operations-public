---
# required metadata

title: Get started with the Electronic invoicing add-on for Egypt
description: This topic provides information that will help you get started with the Electronic invoicing add-on for Egypt in Finance and Supply Chain Management.
author: gionoder
manager: AnnBe
ms.date: 02/10/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Get started with the Electronic invoicing add-on for Egypt

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic provides information that will help you get started with the Electronic invoicing add-on for Egypt. The topic guides you through the configuration steps that are country-dependent in Regulatory Configuration Services (RCS), and complement the steps described in [Get started with the Electronic invoicing add-on](e-invoicing-get-started.md).

## Country-specific configuration for Egyptian electronic invoice (EG) Electronic invoicing feature

To configure the Egyptian electronic invoice (EG) Electronic invoicing feature, there are some steps to complete. Some of the parameters from the configurations are published with default values, so they must be reviewed and updated to better fit your business operation.

### Prerequisites

Before you complete the procedure in this section, create an Egyptian electronic invoice (EG) Electronic invoicing feature for your organization, as described in the **Create an Electronic invoicing feature under your organization provider** section in the topic, [Get started with the Electronic invoicing add-on](e-invoicing-get-started.md).

1. In RCS, in the **Features** section of the **Globalization feature** workspace, select the **Electronic invoicing add-on** tile.
2. On the **Electronic invoicing add-on Features** page, verify that the **Egyptian electronic invoice (EG)** Electronic invoicing feature you created is selected.
3. On the **Versions** tab, verify the **Draft** version is selected.
4. On the **Setups** tab, in the grid, select **Sales invoice** Feature setup.
5. Select **Edit** and on the **Actions** tab, in the **Actions** field group, select **Sign json document for Egyptian Tax Authority**.
6. In the **Parameters** field group, select **Certificate name** parameter.
7. Select **Save** and close the page.
8. To configure the application setup, see [Get started with the Electronic invoicing add-on](e-invoicing-get-started.md).

## Country-specific configuration of the application setup for the Egyptian electronic invoice (EG) Electronic invoicing feature

The configuration of the Application setup for **Egyptian electronic invoice (EG)** Electronic invoicing feature requires that specific steps be accomplished. You must accomplish those steps before you deploy your Electronic invoicing feature to your Electronic invoicing add-on service environment.

### Prerequisites

Before you complete the procedure in this section, create and initiate a **Egyptian electronic invoice (EG)** Electronic invoicing feature to configure the application setup for **Egyptian electronic invoice (EG)** Electronic invoicing feature, as described in the **Configure the application setup** section in the topic, [Get started with the Electronic invoicing add-on](e-invoicing-get-started.md).

1. In RCS, in the **Features** section of the **Globalization feature** workspace, select the **Electronic invoicing add-on** tile.
2. In the **Electronic invoicing add-on Features** page, verify that the **Egyptian electronic invoice (EG)** Electronic invoicing feature is selected.
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
14. To deploy the Electronic invoicing feature, see [Get started with the Electronic invoicing add-on](e-invoicing-get-started.md).

## Privacy notice

Enabling the **EG-00008 (E-invoicing for Egypt)** feature may require sending limited data, including the organization tax registration ID. This data will be transmitted to third-party agencies authorized by the tax authority for the purpose of sending electronic invoices to this tax authority in the predefined format that's required for integration with the government's web service. An administrator can enable and disable the feature by navigating to **Organization administration** > **Setup** > **Electronic document parameters**. On the **Features** tab, select the row that contains the **EG-00008** feature, and then make the appropriate selection. Data imported from these external systems into this Dynamics 365 online service are subject to our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=512132). Consult the Privacy notice sections in country-specific feature documentation for more information.

## Additional resources

- [Electronic invoicing add-on overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing add-on service administration](e-invoicing-get-started-service-administration.md)
- [Get started with the Electronic invoicing add-on](e-invoicing-get-started.md)
- [Customer electronic invoices in Egypt](emea-egy-e-invoices.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]