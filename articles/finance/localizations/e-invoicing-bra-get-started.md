---
# required metadata

title: Get started with the Electronic invoicing add-in for Brazil
description: This topic provides information that will help you get started with the Electronic invoicing add-in for Brazil in Finance and Supply Chain Management.
author: gionoder
manager: AnnBe
ms.date: 03/12/2021
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
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Get started with the Electronic invoicing add-in for Brazil 

[!include [banner](../includes/banner.md)]

This topic provides information that will help you get started with the Electronic invoicing add-in for Brazil. The topic guides you through the configuration steps that are country-dependent in Regulatory Configuration Services (RCS), and complement the steps described in the topic, [Get started with the Electronic invoicing add-in](e-invoicing-get-started.md).

## Country-specific configuration for Brazilian NF-e (BR) Electronic invoicing feature

Configuring the Brazilian NF-e (BR) Electronic invoicing feature requires that specific steps be completed. Some of the parameters from the configurations are published with default values, so they must be reviewed and updated to better fit your business operation.

### Prerequisites

Before you complete the procedure in this section, you must have created a Brazilian NF-e (BR) Electronic invoicing feature for your organization, as described in the **Create an Electronic invoicing feature under your organization provider** section of the topic, [Get started with the Electronic invoicing add-in](e-invoicing-get-started.md).

1. In RCS, in the **Features** section of the **Globalization feature** workspace, select the **Electronic invoicing add-in** tile.
2. On the **Electronic invoicing add-in Features** page, verify that the **Brazilian NF-e (BR)** Electronic invoicing feature you created is selected.
3. On the **Versions** tab, verify that the **Draft** version is selected.
4. On the **Setups** tab, in the grid, select **Submit** and then select **Edit.**
5. On the **Actions** tab, in the **Actions** field group, select **(Preview) Sign xml document** action.
6. In the **Parameters** field group, select **Certificate name**, and in the **Value** field, enter the name of certificate associated to your Key vault parameter.
7. On the **Actions** tab, in the **Actions** field group, select **(Preview) Call Brazilian SEFAZ service** action.
8. In the **Parameters** field group, select **URL address** parameter.
9. In the **Value** field, if necessary, review and update the URL of the web services published by the SEFAZ documentation for your state and then select **Save.**
10. On the **Applicability rules** tab, in the **Setup of applicability rule** field group, review and update the **State** field criteria as necessary for the same state which the URL of the web services is referred to.
11. Select **Save** and close the page.
12. To deploy the Electronic invoicing feature, see [Get started with the Electronic invoicing add-in](e-invoicing-get-started.md).

## Country-specific configuration of Application setup for Brazilian NF-e (BR) Electronic invoicing feature

Configuring the Application setup for Brazilian NF-e (BR) Electronic invoicing feature requires that specific steps be completed. Complete these steps before you deploy the Application setup to your Finance or Supply Chain Connected application.

This section complements the **Configure the application setup** section in the topic, [Get started with the Electronic invoicing add-in](e-invoicing-get-started.md).

1. In RCS, in the **Features** section of the **Globalization feature** workspace, select the **Electronic invoicing add-in** tile.
2. On the **Electronic invoicing add-in Features** page, verify that the **Brazilian NF-e (BR)** Electronic invoicing feature is selected.
3. On the **Versions** tab, verify that the **Draft** version is selected.
4. On the **Setups** tab, select **Application setup** and in the **Connected application** field, select the application to where you want to deploy.
5. In the **Table name** field, verify if **Fiscal document header** is selected.
6. Select **Response types**, and then select **New**.
7. In the **Response type** field, enter "Response" as a fixed value, and in the **Description** field, enter "Description".
8. In the **Submission status** field, select **Pending**.
9. In the **Model mapping** field, select **Model mapping from response  message** with **(Preview) Response message import format**, and then select **Save**.
10. Select **New** and in the **Response type** field, enter "ResponseData" as a fixed value and in the **Description** field, enter "Description".
11. In the **Submission status** field, select **Pending**.
12. In the **Model mapping** field, select **Response data import** with **(Preview) NF-e response data import format (BR)**, and then select **Save**.
13. To deploy the Application setup for the Electronic invoicing feature, see [Get started with the Electronic invoicing add-in](e-invoicing-get-started.md).

## Country-specific configuration for Brazilian NFS-e ABRASF Curitiba (BR) Electronic invoicing feature

Configuring the Brazilian NFS-e ABRASF Curitiba (BR) Electronic invoicing feature requires that specific steps be completed. Some of the parameters from the configurations are published with default values, so they must be reviewed and updated to better fit your business operation.

### Prerequisites

Before you complete the procedure in this section, you must have created a Brazilian NFS-e ABRASF Curitiba (BR) Electronic invoicing feature in your organization, as described in the **Create an Electronic invoicing feature under your organization provider** section of the topic, [Get started with the Electronic invoicing add-in](e-invoicing-get-started.md).

1. In RCS, in the **Features** section of the **Globalization feature** workspace, select the **Electronic invoicing add-in** tile.
2. On the **Electronic invoicing add-in Features** page, verify that the **Brazilian NFS-e ABRASF Curitiba (BR)** Electronic invoicing feature you created is selected.
3. On the **Versions** tab, verify the **Draft** version is selected, and on the **Setups** tab, in the grid, select **Submit**.
4. Select **Edit** and on the **Actions** tab, in the **Actions** field group, select the first occurrence of **(Preview) Sign xml document**.
5. In the **Parameters** field group, select **Certificate name**.
6. In the **Value** field, enter the name of certificate associated to your Key vault parameter.
7. In the **Actions** field group, select the second occurrence of **(Preview) Signxml document**.
8. In the **Parameters** field group, select **Certificate name**.
9. In the **Value** field, enter the name of certificate associated to your Key vault parameter.
10. On the **Actions** tab, in the **Actions** field group, select **(Preview) Call Brazilian SEFAZ service** action.
11. In the **Parameters** field group, select **URL address** parameter.
12. In the **Value** field, if necessary, review and update the URL of the web services published by the tax department for the city of Curitiba and then select **Save.**
13. On the **Setups** tab, in the grid, select **Inquire** and then select **Edit.**
14. On the **Actions** tab, in the **Actions** field group, select **(Preview) Call Brazilian SEFAZ service** action.
15. In the **Parameters** field group, select **URL address** parameter.
16. In the **Value** field, if necessary, review and update the URL of the web services published by the tax department for the city of Curitiba.
17. Select **Save** and then close the page.
18. To deploy the Electronic invoicing feature, see [Get started with the Electronic invoicing add-in](e-invoicing-get-started.md).

## Country-specific configuration of Application setup for Brazilian NFS-e ABRASF Curitiba (BR) Electronic invoicing feature

Configuring the application setup for Brazilian NFS-e ABRASF Curitiba (BR) Electronic invoicing feature requires that specific steps be completed. Complete these steps before you deploy the Application setup to your Finance or Supply Chain Connected application.

This section complements the **Configure the application setup** section in the topic, [Get started with the Electronic invoicing add-in](e-invoicing-get-started.md).

1. In RCS, in the **Features** section of the **Globalization feature** workspace, select the **Electronic invoicing add-in** tile.
2. On the **Electronic invoicing add-in Features** page, verify that the **Brazilian NFS-e ABRASF Curitiba (BR)** Electronic invoicing feature is selected.
3. On the **Versions** tab, verify that the **Draft** version is selected, and on the **Setups** tab, select **Application setup**.
4. In the **Connected application** field, select the application where you want to deploy.
5. On **Table name** field, verify that the fiscal document header is selected.
6. Select **Response types** and select **New**.
7. In the **Response type** field, enter "ABRASFCuritibaSubmitResponse" as a fixed value, and in the **Description** field, enter "Description".
8. In the **Submission status** field, select **Pending**.
9. In the **Model mapping** field, select **Response message import**, with **(Preview) NFS-e ABRASF Curitiba response message import (BR)** and then select **Save**.
10. Select **New**, and in the **Response type** field, enter "ABRASFCuritibaSubmitResponseData", and in the **Description** field, enter "Description".
11. In the **Submission status** field, select **Pending**.
12. In the **Model mapping** field, select **Response data import**, with **(Preview) NFS-e ABRASF response data import format (BR)** and then select **Save**.
13. Select **New**, and in the **Response type** field, enter "ABRASFCuritibaInquireResponse", and in the **Description** field, enter "Description".
14. In the **Submission status** field, select **Pending**.
15. In the **Model mapping** field, select **Response message import**, with **(Preview) NFS-e ABRASF Curitiba response message import (BR).**
16. Select **Save** and close the page.
17. To deploy the Application setup for the Electronic invoicing feature, see [Get started with the Electronic invoicing add-in](e-invoicing-get-started.md).

## Privacy notice
Enabling the **NF-e Federal - Brazilian electronic invoice (BR)** and the **NFS-e - Brazilian service (city) electronic invoice** features may require sending limited data, including the organization tax registration ID. This data is transmitted to third-party agencies authorized by the tax authority for the purpose of sending electronic invoices to this tax authority in the predefined format required for integration with the government’s web service. As an administrator, you can enable or turn off the **NF-e Federal - Brazilian electronic invoice (BR)** and the **NFS-e - Brazilian service (city) electronic invoice** features. The following steps show how to do this: 

1. Go to **Organization administration** > **Setup** > **Electronic document parameters**. 
2. On the **Features** tab, select the row that contains the **NF-e Federal - Brazilian electronic invoice (BR)** or the **NFS-e - Brazilian service (city) electronic invoice** feature, and select the feature. Data imported from these external systems into this Dynamics 365 online service are subject to our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=512132). Consult the Privacy notice sections in country-specific feature documentation for more information.

## Additional resources

- [Electronic invoicing add-in overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing add-in service administration](e-invoicing-get-started-service-administration.md)
- [Get started with the Electronic invoicing add-in](e-invoicing-get-started.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
