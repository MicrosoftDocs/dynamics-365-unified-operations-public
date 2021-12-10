---
# required metadata

title: Configure a Dynamics 365 Commerce evaluation environment
description: This topic explains how to configure a Microsoft Dynamics 365 Commerce evaluation environment after it's provisioned.
author: psimolin
ms.date: 12/10/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: psimolin
ms.search.validFrom: 2019-12-10
ms.dyn365.ops.version: Release 10.0.5
---

# Configure a Dynamics 365 Commerce evaluation environment

[!include [banner](includes/banner.md)]

This topic explains how to configure a Microsoft Dynamics 365 Commerce evaluation environment after it's provisioned.

Complete the procedures in this topic only after your Commerce evaluation environment has been provisioned. For information about how to provision your Commerce evaluation environment, see [Provision a Commerce evaluation environment](provisioning-guide.md).

After your Commerce evaluation environment has been provisioned end to end, additional post-provisioning configuration steps must be completed before you can start to evaluate the environment. To complete these steps, you must use Microsoft Dynamics Lifecycle Services (LCS) and Dynamics 365 Commerce.

## Before you start

1. Sign in to the [LCS portal](https://lcs.dynamics.com).
1. Go to your project.
1. On the top menu, select **Cloud-hosted environments**.
1. Select your environment in the list.
1. In the environment information on the right, select **Log on to environment**. You will be sent to Commerce headquarters.
1. Make sure that the **USRT** legal entity is selected in the upper-right corner.
2. Go to **Commerce parameters > Configuration parameters** and make sure there's an entry for **ProductSearch.UseAzureSearch** set to **true**. If this entry is missing, you can add this entry and run **Channel Database > Full Sync** for the Commerce Scale unit associated with your eCommerce website.

During post-provisioning activities in Commerce headquarters, make sure that the **USRT** legal entity is always selected.

## Configure the point of sale

### Associate a worker with your identity

To associate a worker with your identity, follow these steps in Commerce headquarters.

1. Use the menu on the left to go to **Modules \> Retail and commerce \> Employees \> Workers**.
1. In the list, find and select the following record: **000713 - Andrew Collette**.
1. On the Action Pane, select **Commerce**.
1. Select **Associate existing identity**.
1. In the **Email** field to the right of **Search using email**, enter your email address.
1. Select **Search**.
1. Select the record that has your name.
1. Select **OK**.
1. Select **Save**.

### Activate Cloud POS

To activate Cloud POS, follow these steps in LCS.

1. On the top menu, select **Cloud-hosted environments**.
1. Select your environment in the list.
1. In the environment information on the right, select **Log on to Cloud Point of Sale**.
1. Select **Next** to open the **Before you start** dialog box.
1. Leave the **Server URL** field as it is. Select **Next**.
1. Sign in by using your Microsoft Azure Active Directory (Azure AD) account.
1. Under **Store name**, select **San Francisco**, and then select **Next**.
1. Under **Register and device**, select **SANFRAN-1**.
1. Select **Activate**. You're signed out and taken to the POS sign-in page.
1. You can now sign in to the Cloud POS experience by using operator ID **000713** and password **123**.

## Set up your site in Commerce

To start to set up your evaluation site in Commerce, follow these steps.

1. Sign in to site builder by using the URL that you made a note of when you initialized e-Commerce during provisioning (see [Initialize e-Commerce](provisioning-guide.md#initialize-e-commerce)).
1. Select the **Fabrikam** site to open the site setup dialog box.
1. Select the domain that you entered when you initialized e-Commerce.
1. Select **Fabrikam extended online store** as the default channel. (Make sure that you select the **extended** online store.)
1. Select **en-us** as the default language.
1. Leave the value of the **Path** field as it is.
1. Select **OK**. The list of pages on the site appears.

## Enable jobs

To enable jobs in Commerce, follow these steps.

1. Sign in to the environment (HQ).
1. Use the menu on the left to go to **Retail and commerce \> Inquiries and reports \> Batch jobs**.

    The remaining steps of this procedure must be completed for each of the following jobs:

    * Process retail order email notification
    * Product availability
    * P-0001
    * Synchronize orders job

1. Use the Quick Filter to search for the job by name.
1. If the status of the job is **Executing**, follow these steps:

    1. Select the record.
    1. On the Action Pane, on **Batch job** tab, select **Change status**.
    1. Select **Canceling**, and then select **OK**.

1. If the status of the job is **Withheld**, follow these steps:

    1. Select the record.
    1. On the Action Pane, on **Batch job** tab, select **Change status**.
    1. Select **Waiting**, and then select **OK**.

Optionally, you can also set the recurrence interval to one (1) minute for the following jobs:

* Process retail order email notification job
* P-0001 job
* Synchronize orders job

### Run full data synchronization

To run full data synchronization in Commerce, follow these steps in Commerce headquarters.

1. Use the menu on the left to go to **Modules \> Retail and commerce \> Headquarters setup \> Commerce scheduler \> Channel database**.
1. Select the channel that is named **scXXXXXXXXX**.
1. On the Action Pane, select **Full data sync**.
1. Enter **9999** as the distribution schedule.
1. Select **OK**.
1. Select **OK**.

### Test credit card information to do test purchases

To perform test transactions on the site, you can use the following test credit card information:

- **Card number:** 4111-1111-1111-1111
- **Expiration date:** 10/30
- **Card verification value (CVV) code:** 737

> [!IMPORTANT]
> Never, under any circumstances, try to use actual credit card information on the test site.

## Next steps

After the provisioning and configuration steps are completed, you can start to use your evaluation environment. Use the Commerce site builder URL to go to the authoring experience. Use the Commerce site URL to go to the retail customer site experience.

To configure optional features for your Commerce evaluation environment, see [Configure optional features for a Commerce evaluation environment](cpe-optional-features.md).

> [!NOTE]
> Commerce evaluation environments come with a preloaded Azure Active Directory (Azure AD) business-to-consumer (B2C) tenant for demonstration purposes. Configuring your own Azure AD B2C tenant is not required for evaluation environments. However, if you are configuring the evaluation environment to use your own Azure AD B2C tenant, please make sure to add ``https://login.commerce.dynamics.com/_msdyn365/authresp`` as a reply URL in the Azure AD B2C application via the Azure Portal.

## Additional resources

[Dynamics 365 Commerce evaluation environment overview](cpe-overview.md)

[Provision a Dynamics 365 Commerce evaluation environment](provisioning-guide.md)

[Configure optional features for a Dynamics 365 Commerce evaluation environment](cpe-optional-features.md)

[Configure BOPIS in a Dynamics 365 Commerce evaluation environment](cpe-bopis.md)

[Dynamics 365 Commerce evaluation environment FAQ](cpe-faq.md)

[Microsoft Lifecycle Services (LCS)](/dynamics365/unified-operations/dev-itpro/lifecycle-services/lcs-user-guide)

[Retail Cloud Scale Unit (RCSU)](/business-applications-release-notes/october18/dynamics365-retail/retail-cloud-scale-unit)

[Microsoft Azure portal](https://azure.microsoft.com/features/azure-portal)

[Dynamics 365 Commerce website](https://aka.ms/Dynamics365CommerceWebsite)

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
