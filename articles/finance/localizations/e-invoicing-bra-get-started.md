---
# required metadata

title: Get started with the Electronic invoicing add-on for Brazil
description: This topic provides information that will help you get started with the Electronic invoicing add-on for Brazil in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
author: gionoder
manager: AnnBe
ms.date: 09/04/2020
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

# Get started with the Electronic invoicing add-on for Brazil 

[!include [banner](../includes/banner.md)]


This topic provides information that will help you get started with the
Electronic invoicing add-on for Brazil. It guides you through the
configuration steps that are country-dependent in Regulatory
Configuration Services (RCS), complementing the steps described in [Get
started with the Electronic invoicing
add-on](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/finance/localizations/e-invoicing-get-started.md).

## Country specific configuration for Brazilian NF-e (BR) Electronic invoicing feature

The configuration of Brazilian NF-e (BR) Electronic invoicing feature
requires specific steps to be accomplished. Some of parameters from the
configurations are published with default values, so they need to be
reviewed and updated to better fit to your business operation.

### Prerequisite

Before you complete the procedures in this topic, you must have created
a Brazilian NF-e (BR) Electronic invoicing feature under your
organization, as described in the section **Create an Electronic
invoicing feature under your organization provider** from [Get started
with the Electronic invoicing
add-on](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/finance/localizations/e-invoicing-get-started.md).

1.  In RCS, in the **Features** section of the **Globalization feature**
    workspace, select the **Electronic invoicing add-on** tile.

2.  In the **Electronic invoicing add-on Features** page, verify if the
 **Brazilian NF-e (BR)** Electronic invoicing feature you have
    created is selected.

3.  On the **Versions** tab, verify the **Draft** version is selected.

4.  On the **Setups** tab, in the grid, select **Submit** Feature setup.

5.  Select **Edit.**

6.  Select **Actions** tab, in the **Actions** field group, select
 **(Preview) Sign xml document** action.

7.  In the **Parameters** field group, select **Certificate name**
    parameter.

8.  In the **Value** field, enter the name of certificate associated to
    your Key vault parameter.

9.  Select **Actions** tab, in the **Actions** field group, select
 **(Preview) Call Brazilian SEFAZ service** action.

10. In the **Parameters** field group, select **URL address** parameter.

11. In the **Value** field, if necessary, review and update the URL of
    the web services published by the SEFAZ documentation for your
    state.

12. Select **Save.**

13. Select **Applicability rules** tab, in the **Setup of applicability
    rule** field group, and if necessary, review and update the
 **State** field criteria for the same state which the URL of the web
    services is referred to.

14. Select **Save.**

15. Close the page.

16. Return to [Get started with the Electronic invoicing
    add-on](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/finance/localizations/e-invoicing-get-started.md)
    for configuration of the application setup.

## Country specific configuration of Application setup for Brazilian NF-e (BR) Electronic invoicing feature

The configuration of the Application setup for Brazilian NF-e (BR)
Electronic invoicing feature requires specific steps to be accomplished.
You must accomplish those steps before you deploy your Electronic
invoicing feature to your Electronic invoicing add-on service
environment.

### Prerequisite

Before you complete the procedures in this topic, you must have created
a Brazilian NF-e (BR) Electronic invoicing feature and you must have
initiated the configuration of application setup for Brazilian NF-e (BR)
Electronic invoicing feature, as described in the section **Configure
the application setup** from [Get started with the Electronic invoicing
add-on](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/finance/localizations/e-invoicing-get-started.md).

1.  In RCS, in the **Features** section of the **Globalization feature**
    workspace, select the **Electronic invoicing add-on** tile.

2.  In the **Electronic invoicing add-on Features** page, verify if the
 **Brazilian NF-e (BR)** Electronic invoicing feature is selected.

3.  On the **Versions** tab, verify that the **Draft** version is
    selected.

4.  On the **Setups** tab, select **Application setup**.

5.  In the **Connected application** field, select the application to
    where you want to deploy.

6.  On **Table name**, verify if Fiscal document header is selected.

7.  Select **Response types** and select **New**.

8.  In the **Response type** field, enter "Response" as fixed value. In
    the **Description** field, enter Description.

9.  In the **Submission status** field, select Pending.

10. In the **Model mapping** field, select **Model mapping from response
    message**, with **(Preview) Response message import format.**

11. Select **Save**.

12. Select **New**.

13. In the **Response type** field, enter "ResponseData" as fixed value.
    In the **Description** field, enter Description.

14. In the **Submission status** field, select Pending.

15. In the **Model mapping** field, select **Response data import**,
    with **(Preview) NF-e response data import format (BR).**

16. Select **Save**.

17. Return to in [Get started with the Electronic invoicing
    add-on](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/finance/localizations/e-invoicing-get-started.md)
    for deployment of the Electronic invoicing feature.

## Country specific configuration for Brazilian NFS-e ABRASF Curitiba (BR) Electronic invoicing feature

The configuration of Brazilian NFS-e ABRASF Curitiba (BR) Electronic
invoicing feature requires specific steps to be accomplished. Some of
parameters from the configurations are published with default values, so
they need to be reviewed and updated to better fit to your business
operation.

### Prerequisite

Before you complete the procedures in this topic, you must have created
a Brazilian NFS-e ABRASF Curitiba (BR) Electronic invoicing feature
under your organization, as described in the section **Configure
Electronic invoicing feature** from [Get started with the Electronic
invoicing
add-on](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/finance/localizations/e-invoicing-get-started.md).

1.  In RCS, in the **Features** section of the **Globalization feature**
    workspace, select the **Electronic invoicing add-on** tile.

2.  In the **Electronic invoicing add-on Features** page, verify if the
 **Brazilian NFS-e ABRASF Curitiba (BR)** Electronic invoicing
    feature you have created is selected.

3.  On the **Versions** tab, verify the **Draft** version is selected.

4.  On the **Setups** tab, in the grid, select **Submit** Feature setup.

5.  Select **Edit.**

6.  Select **Actions** tab, in the **Actions** field group, select the
    first occurrence of **(Preview) Sign xml document** action.

7.  In the **Parameters** field group, select **Certificate name**
    parameter.

8.  In the **Value** field, enter the name of certificate associated to
    your Key vault parameter.

9.  in the **Actions** field group, select the second occurrence of **(Preview) Sign
    xml document** action.

10. In the **Parameters** field group, select **Certificate name**
    parameter.

11. In the **Value** field, enter the name of certificate associated to
    your Key vault parameter.

12. Select **Actions** tab, in the **Actions** field group, select
 **(Preview) Call Brazilian SEFAZ service** action.

13. In the **Parameters** field group, select **URL address** parameter.

14. In the **Value** field, if necessary, review and update the URL of
    the web services published by the tax department for the city of
    Curitiba.

15. Select **Save.**

16. On the **Setups** tab, in the grid, select **Inquire** Feature
    setup.

17. Select **Edit.**

18. Select **Actions** tab, in the **Actions** field group, select
 **(Preview) Call Brazilian SEFAZ service** action.

19. In the **Parameters** field group, select **URL address** parameter.

20. In the **Value** field, if necessary, review and update the URL of
    the web services published by the tax department for the city of
    Curitiba.

21. Select **Save.**

22. Close the page.

23. Return to [Get started with the Electronic invoicing
    add-on](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/finance/localizations/e-invoicing-get-started.md)
    for configuration of the application setup.

## Country specific configuration of Application setup for Brazilian NFS-e ABRASF Curitiba (BR) Electronic invoicing feature

The configuration of the Application setup for Brazilian NFS-e ABRASF
Curitiba (BR) Electronic invoicing feature requires specific steps to be
accomplished. You must accomplish those steps before you deploy your
Electronic invoicing feature to your Electronic invoicing add-on service
environment.

### Prerequisite

Before you complete the procedures in this topic, you must have created
a Brazilian NFS-e ABRASF Curitiba (BR) Electronic invoicing feature and
you must have initiated the configuration of application setup for
Brazilian NFS-e ABRASF Curitiba (BR) Electronic invoicing feature, as
described in the section **Configure the application setup** from [Get
started with the Electronic invoicing
add-on](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/finance/localizations/e-invoicing-get-started.md).

1.  In RCS, in the **Features** section of the **Globalization feature**
    workspace, select the **Electronic invoicing add-on** tile.

2.  In the **Electronic invoicing add-on Features** page, verify if the
 **Brazilian NFS-e ABRASF Curitiba (BR)** Electronic invoicing
    feature is selected.

3.  On the **Versions** tab, verify that the **Draft** version is
    selected.

4.  On the **Setups** tab, select **Application setup**.

5.  In the **Connected application** field, select the application to
    where you want to deploy.

6.  On **Table name**, verify if Fiscal document header is selected.

7.  Select **Response types** and select **New**.

8.  In the **Response type** field, enter "ABRASFCuritibaSubmitResponse"
    as fixed value. In the **Description** field, enter Description.

9.  In the **Submission status** field, select Pending.

10. In the **Model mapping** field, select **Response message import**,
    with **(Preview) NFS-e ABRASF Curitiba response message import
    (BR).**

11. Select **Save**.

12. Select **New**.

13. In the **Response type** field, enter
    "ABRASFCuritibaSubmitResponseData" as fixed value. In the
 **Description** field, enter Description.

14. In the **Submission status** field, select Pending.

15. In the **Model mapping** field, select **Response data import**,
    with **(Preview) NFS-e ABRASF response data import format (BR).**

16. Select **Save**.

17. Select **New**.

18. In the **Response type** field, enter
    "ABRASFCuritibaInquireResponse" as fixed value. In the
 **Description** field, enter Description.

19. In the **Submission status** field, select Pending.

20. In the **Model mapping** field, select **Response message import**,
    with **(Preview) NFS-e ABRASF Curitiba response message import
    (BR).**

21. Select **Save**.

22. Return to in [Get started with the Electronic invoicing
    add-on](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/finance/localizations/e-invoicing-get-started.md)
    for deployment of the Electronic invoicing feature.

## Privacy notice
Enabling the BR-00053 (NF-e Federal) and the BR-00095 (NFS-e - Brazilian service (city) electronic invoice) features may require sending limited data, which includes the organization tax registration ID. This will be transmitted to third-party agencies authorized by the tax authority for purposes of sending electronic invoices to this tax authority in the predefined format required for integration with the government’s web service. An administrator can enable and disable the BR-00053 (NF-e Federal) and the BR-00095 (NFS-e - Brazilian service electronic invoice) features by navigating to **Organization administration \> Setup \> Electronic document parameters**. Select the **Features** tab, select the row containing the BR-00053 or BR-00095 features, and then make the appropriate selection. Data imported from these external systems into this Dynamics 365 online service are subject to our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=512132). Please consult the Privacy notice sections in country-specific feature documentation for more information.


## Additional resources

- [Electronic invoicing add-on overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing add-on service administration](e-invoicing-get-started-service-administration.md)
- [Get started with the Electronic invoicing add-on](e-invoicing-get-started.md)

