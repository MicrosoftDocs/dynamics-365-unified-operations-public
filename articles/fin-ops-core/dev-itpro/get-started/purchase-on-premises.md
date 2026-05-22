---
title: Buy Finance + Operations (on-premises)
description: Learn about how to purchase and deploy Microsoft Dynamics 365 Finance + Operations (on-premises), with an outline on purchasing Dynamics 365 cloud subscription licenses.
author: faix
ms.author: osfaixat
ms.topic: how-to
ms.date: 03/26/2026
ms.custom:
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2017-06-30
ms.search.form:
ms.dyn365.ops.version: Platform update 8 
search.app:
  - financeandoperationsonprem-docs
ms.service: dynamics-365-op
---

# Buy Finance + Operations (on-premises)

[!include [banner](../../../finance/includes/banner.md)]

Microsoft Dynamics 365 Finance + Operations (on-premises) offers various license types to best suit the needs of your organization. To better understand how Finance + Operations (on-premises) is licensed, work with your partner, who can access the [Licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544). When you're ready to purchase licenses for your organization, work with your partner to follow the steps that are outlined in this article.

> [!IMPORTANT]
> On-premises environments aren't supported on any public cloud infrastructure, including Azure. However, they support running on [Microsoft Azure Stack HCI](https://azure.microsoft.com/products/azure-stack/hci/) and [Microsoft Azure Stack Hub](https://azure.microsoft.com/products/azure-stack/hub/).

## Purchase a Dynamics 365 cloud subscription license

Thanks to the dual use rights that are mentioned in the [Licensing guide](https://go.microsoft.com/fwlink/?LinkId=866544), you can use a Dynamics 365 cloud subscription license to deploy Finance + Operations (on-premises).

For information about how to purchase a subscription, see [Buy and manage a subscription](../../fin-ops/get-started/before-you-buy.md#step-three-buy-and-manage-a-subscription). After you have a subscription, follow these steps to create your on-premises implementation project.

### Get started with Lifecycle Services

When you purchase a subscription, you assign it to your Microsoft Online Services ID. You need the Microsoft Online Services ID to provision and register Microsoft Dynamics 365 applications. Use the Microsoft Online Services ID to provision a Microsoft Dynamics Lifecycle Services project that contains the necessary artifacts for on-premises environments. Lifecycle Services is the service where you provision on-premises environments, create and upload business process models, make hotfixes available, enter and manage support cases, validate subscriptions, and so on.

Before you can create your Lifecycle Services project and begin creating on-premises environments, follow the [Provisioning guide](https://mbs2.microsoft.com/fileexchange/?fileID=7ddd6ddf-aa22-402a-baa1-5405ce0b1076) to obtain an on-premises license.

If you have an existing Microsoft Online Services trial or paid subscription, you already have a Microsoft Online Services ID that you created at the time of sign-up. When you sign in to [Lifecycle Services](https://lcs.dynamics.com), select to use this account for sign-in if you want to use the same Microsoft Entra tenant for the on-premises environment.

After you sign in to Lifecycle Services, a cloud project is automatically provisioned for you. However, you need an on-premises project. To create a new on-premises project, follow the [Start a new Lifecycle Services project guide](/dynamics365/project-operations/environment/create-lcs-project) and select the **On-premises implementation** project type. The Lifecycle Services project lets you deploy an on-premises environment. For more information about how to get started with your Lifecycle Services project, see [Set up on-premises projects in Lifecycle Services](../lifecycle-services/lbd-create-lcs-on-prem-project.md).

## Purchase a Dynamics 365 Finance + Operations (on-premises) license

### Purchase client access licenses

To run on-premises environments, you must obtain the proper number of client access licenses (CALs) for your organization per the licensing guide. The CAL you purchase for an individual user determines the functionality that the user has the rights to use. You can purchase user CALs from the [Microsoft Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx).

### Purchase server licenses

You need a server license for every server that runs Finance + Operations (on-premises). After you purchase your server licenses, work with your partner to download a license file from the [PartnerSource Business Center](https://businesscenter.mbs.microsoft.com/). Keep this license file handy, because you use the details that it contains when you set up your Lifecycle Services project.

Partners can download a customer's Finance + Operations (on-premises) license file from the PartnerSource Business Center by using these steps:

1. Sign in to the [PartnerSource Business Center](https://businesscenter.mbs.microsoft.com/).
1. Enter the customer name or account number in the **Find A Customer** field, and then select **Search**.
1. Select the company name of the customer. The **Customer Summary** page opens.
1. Under **Registered Products**, select **Registration Keys**.
1. Select **version 07** in the **Request and Display License Keys For Version** field.
1. Select **Display License Keys**.
1. On the **Request License Keys** page, select **Download Current License/Registration Key**.
1. Select **Save As** in the **File Download** dialog box, select the folder where you want to download the license file to in the **Save As** dialog box, and then select **Save**.

> [!NOTE]
> If you can't see registration keys in PartnerSource Business Center, make sure that **Can See Registration Keys** is set to **Yes** in your PartnerSource Business Center profile.

### Get started with Lifecycle Services

To purchase Finance + Operations (on-premises), you must have a Microsoft Online Services ID. Use the Microsoft Online Services ID to provision a Lifecycle Services project that contains the necessary artifacts for on-premises environments. In Lifecycle Services, you can provision on-premises environments, create and upload business process models, make hotfixes available, enter and manage support cases, submit license key serial number activations, and more.

You need a Microsoft Online Services ID to provision and register Finance + Operations (on-premises) into entity-owned hardware and environment. See the Provisioning guide to complete the provisioning and registration process. If a Microsoft Online Services ID already exists, the tenant administrator must complete the process. If you're creating a Microsoft Online Services ID for the first time, you're the tenant administrator.

If you have an existing Microsoft Online Services trial or paid subscription, you already have a Microsoft Online Services ID that you created at the time of sign-up. Choose to sign in with this account if you want to use this same Microsoft Entra ID tenant for the on-premises environment. For details, see the [Provisioning guide](https://mbs2.microsoft.com/fileexchange/?fileID=7ddd6ddf-aa22-402a-baa1-5405ce0b1076).

After you sign in to Lifecycle Services, a project is automatically provisioned for you. The Lifecycle Services project lets you deploy an on-premises environment. For more information about how to get started with your Lifecycle Services project, see [Set up on-premises projects in Lifecycle Services](../lifecycle-services/lbd-create-lcs-on-prem-project.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
