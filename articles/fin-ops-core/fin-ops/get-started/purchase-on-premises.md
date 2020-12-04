---
# required metadata

title: Buy Finance + Operations (on-premises)
description: This topic explains how to purchase and deploy Microsoft Dynamics 365 Finance + Operations (on-premises).
author: maertenm 
manager: AnnBe
ms.date: 09/12/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
#ms.search.scope:  Operations 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: sericks
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Platform update 8 
---

# Buy Finance + Operations (on-premises)

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Finance + Operations (on-premises) offers a variety of license types to best suit the needs of your organization. To better understand how Finance + Operations (on-premises) is licensed, please work with your partner, who can access the [Licensing guide](https://mbs.microsoft.com/Files/public/365/DynamicsOperationsOnPremEnterprise.pdf) on PartnerSource. When you are ready to purchase licenses for your organization, work with your partner to follow the steps outlined in this topic.

> [!IMPORTANT]
> On-premises environments are not supported on any public cloud infrastructure, including Azure.

## Purchase client access licenses

To run on-premises environments, you must obtain the proper number of client access licenses (CALs) for your organization per the licensing guide. The CAL purchased for an individual user determines the functionality that the user has the rights to use. User CALs can be purchased from the [Microsoft Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx).

## Purchase server licenses

A server license is required for every server running Finance + Operations (on-premises). After purchasing your server licenses, work with your partner to download a license file from the [PartnerSource Business Center](https://businesscenter.mbs.microsoft.com/). Keep this license file handy, as the details it contains will be used when setting up your Lifecycle Services (LCS) project.

Partners can download a customer's Finance + Operations (on-premises) license file from the PartnerSource Business Center using these steps:

1. Log on to the [PartnerSource Business Center](https://businesscenter.mbs.microsoft.com/).
2. Enter the customer name or account number in the **Find A Customer** field, and then click **Search**.
3. Click the company name of the customer. This opens the **Customer Summary** page.
4. Under **Registered Products**, click **Registration Keys**.
5. Select **version 07** in the **Request and Display License Keys For Version** field.
6. Click **Display License Keys**.
7. On the **Request License Keys** page, select **Download Current License/Registration Key**.
8. Click **Save As** in the **File Download** dialog box, select the folder where you want to download the license file to in the **Save As** dialog box, and then click **Save**.

> [!NOTE]
> If you cannot see registration keys in PartnerSource Business Center, you will need to ensure that your PartnerSource Business Center Profile has **Can See Registration Keys** set to **Yes**.

## Get started with Lifecycle Services (LCS)

To purchase Finance + Operations (on-premises) you must have a Microsoft Online Services ID. The Microsoft Online Services ID is used to provision an LCS project that contains the necessary artifacts for on-premises environments. LCS is the service where on-premises environments will be provisioned, Business Process Model created/uploaded, hotfixes are made available, support cases are entered and managed, license key serial number activation submitted, etc.

The Microsoft Online Services ID is required to provision and register Finance + Operations (on-premises) into entity-owned hardware and environment. See the Provisioning guide (linked to below) to complete the provisioning and registration process. If a Microsoft Online Services ID already exists, the process must be completed by the Global Administrator. If creating a Microsoft Online Services ID for the first time, the person initiating the process will be the Global Administrator.

If you have an existing Microsoft Online Services trial or paid subscription, you already have a Microsoft Online Services ID that was created at the time of sign-up. When you click a link below, choose to sign in with this account if you want to use this same Azure Active Directory (AAD) tenant for the on-premises environment.

Access to the Provisioning guide can be found here:

- [Provisioning guide on CustomerSource](https://go.microsoft.com/fwlink/?linkid=852080)
- [Provisioning guide on PartnerSource](https://mbs.microsoft.com/partnersource/global/deployment/documentation/user-guides/D365Ops_OnPremEEProvisionGuide)

After you have logged into LCS, a project will be automatically provisioned for you. The LCS project will allow you to deploy an on-premises environment. For more details on getting started with your LCS project, see [Set up on-premises projects in Lifecycle Services (LCS)](../../dev-itpro/lifecycle-services/lbd-create-lcs-on-prem-project.md).
