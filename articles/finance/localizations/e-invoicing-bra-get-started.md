---
title: Get started with Electronic invoicing for Brazil
description: This article provides information that will help you get started with Electronic invoicing for Brazil in Finance and Supply Chain Management.
author: gionoder
ms.date: 03/29/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: gionoder
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12
ms.collection: get-started
ms.assetid: 
ms.search.form: 
---

# Get started with Electronic invoicing for Brazil 

[!include [banner](../includes/banner.md)]

This article provides information that will help you get started with Electronic invoicing for Brazil. The article guides you through the configuration steps that are country/region-dependent in Regulatory Configuration Services (RCS), and complement the steps described in the article, [Get started with Electronic invoicing](e-invoicing-get-started.md).

## Country/region-specific configuration for Brazilian NF-e (BR) Electronic invoicing feature

Some of the parameters from the **Brazilian NF-e (BR) Electronic invoicing feature** are published with default values. Review the values and if necessary, update the values to better reflect your business operation before you deploy the Electronic invoicing feature to the Service environment.

This section complements the **Country/region-specific configuration for Electronic invoicing feature** section in the article, [Get started with Electronic invoicing](e-invoicing-get-started.md).

1. In RCS, in the **Features** section of the **Globalization feature** workspace, select the **Electronic invoicing** tile.
2. On the **Electronic invoicing Features** page, verify that the **Brazilian NF-e (BR)** Electronic invoicing feature you created is selected.
3. On the **Versions** tab, verify that the **Draft** version is selected.
4. On the **Setups** tab, in the grid, select **Submit** and then select **Edit.**
5. On the **Actions** tab, in the **Actions** field group, select **(Preview) Sign xml document** action.
6. In the **Parameters** field group, select **Certificate name**, and in the **Value** field, enter the name of certificate associated to your Key vault parameter.
7. On the **Actions** tab, in the **Actions** field group, select **(Preview) Call Brazilian SEFAZ service** action.
8. In the **Parameters** field group, select **URL address** parameter.
9. In the **Value** field, if necessary, review and update the URL of the web services published by the SEFAZ documentation for your state and then select **Save.**
10. On the **Applicability rules** tab, in the **Setup of applicability rule** field group, review and update the **State** field criteria as necessary for the same state, which the URL of the web services is referred to.
11. Select **Save** and close the page.
12. To deploy the Electronic invoicing feature to the Service environment, see [Get started with Electronic invoicing](e-invoicing-get-started.md).

## Country/region-specific configuration of application setup for Brazilian NF-e (BR) Electronic invoicing feature

Complete these steps before you deploy the application setup to your Finance or Supply Chain Management connected application.

This section complements the **Country/region-specific configuration of Application setup** section in the article, [Get started with Electronic invoicing](e-invoicing-get-started.md).

1. In RCS, in the **Features** section of the **Globalization feature** workspace, select the **Electronic invoicing** tile.
2. On the **Electronic invoicing Features** page, verify that the **Brazilian NF-e (BR)** Electronic invoicing feature is selected.
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
13. To deploy the application setup to the Finance or Supply Chain connected application, see [Get started with Electronic invoicing](e-invoicing-get-started.md).

## Country/region-specific configuration for Brazilian NFS-e ABRASF Curitiba (BR) Electronic invoicing feature

Some of the parameters from the **Brazilian NFS-e ABRASF Curitiba (BR) Electronic invoicing feature** are published with default values. Review and, if necessary, update the values to better fit your business operation needs before you deploy the Electronic invoicing feature to the Service environment.

This section complements the **Country-specific configuration for Electronic invoicing feature** section in the article, [Get started with Electronic invoicing](e-invoicing-get-started.md).

1. In RCS, in the **Features** section of the **Globalization feature** workspace, select the **Electronic invoicing** tile.
2. On the **Electronic invoicing Features** page, verify that the **Brazilian NFS-e ABRASF Curitiba (BR)** Electronic invoicing feature you created is selected.
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
18. To deploy the Electronic invoicing feature to the Service environment, see [Get started with Electronic invoicing](e-invoicing-get-started.md).

## Country/region-specific configuration of application setup for Brazilian NFS-e ABRASF Curitiba (BR) Electronic invoicing feature

Complete these steps before you deploy the application setup to your Finance or Supply Chain Management connected application.

This section complements the **Country/region-specific configuration of application setup** section in the article, [Get started with Electronic invoicing](e-invoicing-get-started.md).

1. In RCS, in the **Features** section of the **Globalization feature** workspace, select the **Electronic invoicing** tile.
2. On the **Electronic invoicing Features** page, verify that the **Brazilian NFS-e ABRASF Curitiba (BR)** Electronic invoicing feature is selected.
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
17. To deploy the application setup to the Finance or Supply Chain connected application, see [Get started with Electronic invoicing](e-invoicing-get-started.md).

## Privacy notice
Enabling the **NF-e Federal - Brazilian electronic invoice (BR)** and the **NFS-e - Brazilian service (city) electronic invoice** features may require sending limited data, including the organization tax registration ID. This data is transmitted to third-party agencies authorized by the tax authority for the purpose of sending electronic invoices to this tax authority in the predefined format required for integration with the government’s web service. As an administrator, you can enable or turn off the **NF-e Federal - Brazilian electronic invoice (BR)** and the **NFS-e - Brazilian service (city) electronic invoice** features. The following steps show how to do this: 

1. Go to **Organization administration** > **Setup** > **Electronic document parameters**. 
2. On the **Features** tab, select the row that contains the **NF-e Federal - Brazilian electronic invoice (BR)** or the **NFS-e - Brazilian service (city) electronic invoice** feature, and select the feature. Data imported from these external systems into this Dynamics 365 online service are subject to our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=512132). Consult the Privacy notice sections in country/region-specific feature documentation for more information.

## Additional resources

- [Electronic invoicing overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](e-invoicing-get-started.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
