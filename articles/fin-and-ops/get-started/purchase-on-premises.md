---
# required metadata

title: Buy Dynamics 365 for Finance and Operations, Enterprise edition (on-premises)
description: This topic explains how to purchase and deploy Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (on-premises).
author: maertenm 
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope:  Operations, Platform 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: maertenm
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Platform update 8 
---

# Buy Dynamics 365 for Finance and Operations, Enterprise edition (on-premises)

[!include[banner](../includes/banner.md)]

Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (on-premises) offers a variety of license types to best suit the needs of your organization. To better understand how Finance and Operations (on-premises) is licensed, please work with your partner, who can access the [Licensing guide](https://go.microsoft.com/fwlink/?linkid=852079) on PartnerSource. When you are ready to purchase licenses for your organization, work with your partner to follow the steps outlined in this topic.

> [!NOTE]
> Dynamics 365 for Operations (on-premises) is currently being renamed. You will see Dynamics 365 for Operations (on-premises) referenced throughout communications and licensing guides. The in-product name that you will see when deploying the product is Dynamics 365 for Finance and Operations, Enterprise edition. Both of these names refer to the same product.

Purchase client access licenses
-------------------

To run Finance and Operations (on-premises) you must obtain the proper number of client access licenses (CALs) for your organization per the licensing guide. The CAL purchased for an individual user determines the functionality that the user has the rights to use. User CALs can be purchased from the [Microsoft Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx).

Purchase server licenses
--------------------------

A server license is required for every server running Finance and Operations (on-premises). After purchasing your server licenses, work with your partner to download a license file from the [PartnerSource Business Center](https://businesscenter.mbs.microsoft.com/). Keep this license file handy, as the details it contains will be used when setting up your Lifecycle Services (LCS) project.

Partners can download a customer's Finance and Operations (on-premises) license file from the PartnerSource Business Center using these steps:

1.  Log on to the [PartnerSource Business Center](https://businesscenter.mbs.microsoft.com/).

3.  Enter the customer name or account number in the **Find A Customer** field, and then click **Search**.

4.  Click the company name of the customer. This opens the **Customer Summary** page.

5.  Under **Registered Products**, click **Registration Keys**.

6.  Select **version 07** in the **Request and Display License Keys For Version** field.

7.  Click **Display License Keys**.

8.  On the **Request License Keys** page, select **Download Current License/Registration Key**.

9.  Click **Save As** in the **File Download** dialog box, select the folder where you want to download the license file to in the **Save As** dialog box, and then click **Save**.

**Note**: If you cannot see registration keys in PartnerSource Business Center, you will need to ensure that your PartnerSource Business Center Profile has **Can See Registration Keys** set to **Yes**.

Get started with Lifecycle Services (LCS)
---------------------------------------

To purchase Finance and Operations (on-premises) you must have a Microsoft Online Services ID. The Microsoft Online Services ID is used to provision an LCS project that contains the necessary artifacts for Finance and Operations (on-premises). LCS is the service where on-premises environments will be provisioned, Business Process Model created/uploaded, hotfixes are made available, support cases are entered and managed, license key serial number activation submitted, etc.

The Microsoft Online Services ID is required to provision and register Finance and Operations (on-premises) into entity-owned hardware and environment. See the Provisioning guide (linked to below) to complete the provisioning and registration process. If a Microsoft Online Services ID already exists, the process must be completed by the Global Administrator. If creating a Microsoft Online Services ID for the first time, the person initiating the process will be the Global Administrator.

If you have an existing Microsoft Online Services trial or paid subscription, you already have a Microsoft Online Services ID that was created at the time of sign-up. When you click a link below, choose to sign in with this account if you want to use this same Azure Active Directory (AAD) tenant for the on-premises deployment.

Access to the Provisioning guide can be found here:

- [Provisioning guide on CustomerSource](https://go.microsoft.com/fwlink/?linkid=852080)

- [Provisioning guide on PartnerSource](https://go.microsoft.com/fwlink/?linkid=852081)

After you have logged into LCS, a project will be automatically provisioned for you. The LCS project will allow you to deploy Finance and Operations (on-premises). For more details on getting started with your LCS project, see [Create an on-premises project in Lifecycle Services](../../dev-itpro/lifecycle-services/lbd-create-lcs-on-prem-project.md).
