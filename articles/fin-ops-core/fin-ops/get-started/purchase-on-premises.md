---
# required metadata

title: Buy Finance + Operations (on-premises)
description: This article explains how to purchase and deploy Microsoft Dynamics 365 Finance + Operations (on-premises).
author: faix 
ms.date: 01/13/2023
ms.topic: article
ms.prod: dynamics-365
ms.service:
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: osfaixat
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: Platform update 8 
search.app:
  - financeandoperationsonprem-docs
---

# Buy Finance + Operations (on-premises)

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Finance + Operations (on-premises) offers various license types to best suit the needs of your organization. To better understand how Finance + Operations (on-premises) is licensed, work with your partner, who can access the [Licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544). When you're ready to purchase licenses for your organization, work with your partner to follow the steps that are outlined in this article.

> [!IMPORTANT]
> On-premises environments are not supported on any public cloud infrastructure, including Azure. However, they are supported to run on [Microsoft Azure Stack HCI](https://azure.microsoft.com/products/azure-stack/hci/) and [Microsoft Azure Stack Hub](https://azure.microsoft.com/products/azure-stack/hub/).

## Purchase a Dynamics 365 cloud subscription license

Thanks to the Dual Use Rights that are mentioned in the [Licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544), a Dynamics 365 cloud subscription license can be used to deploy Finance + Operations (on-premises).

For information about how to purchase a subscription, see [Buy and manage a subscription](./before-you-buy.md#step-three-buy-and-manage-a-subscription). After you have a subscription, follow these steps to create your on-premises implementation project.

### Get started with Lifecycle Services 

When you purchase a subscription, it's assigned to your Microsoft Online Services ID. The Microsoft Online Services ID is required to provision and register Microsoft Dynamics 365 applications. The Microsoft Online Services ID is used to provision a Microsoft Dynamics Lifecycle Services project that contains the necessary artifacts for on-premises environments. Lifecycle Services is the service where on-premises environments will be provisioned, Business process models will be created and uploaded, hotfixes will be made available, support cases will be entered and managed, subscriptions will be validated, and so on.

If you have an existing Microsoft Online Services trial or paid subscription, you already have a Microsoft Online Services ID that was created at the time of sign-up. When you sign in to [Lifecycle Services](https://lcs.dynamics.com), select to use this account for sign-in if you want to use the same Azure Active Directory (Azure AD) tenant for the on-premises environment.

After you've signed in to Lifecycle Services, a cloud project is automatically provisioned for you. However, you'll need an on-premises project. Therefore, you'll have to raise a support case, so that an on-premises project can be generated for you. The Lifecycle Services project will let you deploy an on-premises environment. For more information about how to get started with your Lifecycle Services project, see [Set up on-premises projects in Lifecycle Services](../../dev-itpro/lifecycle-services/lbd-create-lcs-on-prem-project.md).

## Purchase a Dynamics 365 Finance + Operations (on-premises) license

### Purchase client access licenses

To run on-premises environments, you must obtain the proper number of client access licenses (CALs) for your organization per the licensing guide. The CAL purchased for an individual user determines the functionality that the user has the rights to use. User CALs can be purchased from the [Microsoft Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx).

### Purchase server licenses

A server license is required for every server that runs Finance + Operations (on-premises). After you purchase your server licenses, work with your partner to download a license file from the [PartnerSource Business Center](https://businesscenter.mbs.microsoft.com/). Keep this license file handy, because you will use the details that it contains when you set up your Lifecycle Services project.

Partners can download a customer's Finance + Operations (on-premises) license file from the PartnerSource Business Center using these steps:

1. Sign in to the [PartnerSource Business Center](https://businesscenter.mbs.microsoft.com/).
2. Enter the customer name or account number in the **Find A Customer** field, and then click **Search**.
3. Click the company name of the customer. This opens the **Customer Summary** page.
4. Under **Registered Products**, click **Registration Keys**.
5. Select **version 07** in the **Request and Display License Keys For Version** field.
6. Click **Display License Keys**.
7. On the **Request License Keys** page, select **Download Current License/Registration Key**.
8. Click **Save As** in the **File Download** dialog box, select the folder where you want to download the license file to in the **Save As** dialog box, and then click **Save**.

> [!NOTE]
> If you can't see registration keys in PartnerSource Business Center, make sure that **Can See Registration Keys** is set to **Yes** in your PartnerSource Business Center profile.

### Get started with Lifecycle Services

To purchase Finance + Operations (on-premises), you must have a Microsoft Online Services ID. The Microsoft Online Services ID is used to provision a Lifecycle Services project that contains the necessary artifacts for on-premises environments. Lifecycle Services is the service where on-premises environments will be provisioned, Business process models will be created and uploaded, hotfixes will be made available, support cases will be entered and managed, license key serial number activation will be submitted, and so on.

The Microsoft Online Services ID is required to provision and register Finance + Operations (on-premises) into entity-owned hardware and environment. See the Provisioning guide (linked to below) to complete the provisioning and registration process. If a Microsoft Online Services ID already exists, the process must be completed by the Global Administrator. If creating a Microsoft Online Services ID for the first time, the person initiating the process will be the Global Administrator.

If you have an existing Microsoft Online Services trial or paid subscription, you already have a Microsoft Online Services ID that was created at the time of sign-up. Choose to sign in with this account if you want to use this same Azure Active Directory (AAD) tenant for the on-premises environment. For details, see the [Provisioning guide](https://mbs2.microsoft.com/fileexchange/?fileID=7ddd6ddf-aa22-402a-baa1-5405ce0b1076).

After you've signed in to Lifecycle Services, a project will automatically be provisioned for you. The Lifecycle Services project will let you deploy an on-premises environment. For more information about how to get started with your Lifecycle Services project, see [Set up on-premises projects in Lifecycle Services](../../dev-itpro/lifecycle-services/lbd-create-lcs-on-prem-project.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
