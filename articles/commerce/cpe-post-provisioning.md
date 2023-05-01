---
title: Configure a Dynamics 365 Commerce sandbox environment
description: This article explains how to configure a Microsoft Dynamics 365 Commerce sandbox environment after it's provisioned.
author: josaw1
ms.date: 01/30/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application user
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2019-12-10
ms.dyn365.ops.version: Release 10.0.5
ms.custom: 
ms.assetid: 
---

# Configure a Dynamics 365 Commerce sandbox environment

[!include [banner](includes/banner.md)]

This article explains how to configure a Microsoft Dynamics 365 Commerce sandbox environment after it's provisioned.

Complete the procedures in this article only after your Commerce sandbox environment has been provisioned. For information about how to provision your Commerce sandbox environment, see [Provision a Commerce sandbox environment](provisioning-guide.md).

After your Commerce sandbox environment has been provisioned end to end, additional post-provisioning configuration steps must be completed before you can start to use the environment. To complete these steps, you must use Microsoft Dynamics Lifecycle Services (LCS) and Dynamics 365 Commerce.

## Before you start

1. Sign in to the [LCS portal](https://lcs.dynamics.com).
1. Go to your project.
1. Select your environment in the list.
1. In the environment information on the right, select **Log on to environment**. You will be sent to Commerce headquarters.
1. Make sure that the **USRT** legal entity is selected in the upper-right corner. This legal entity has been preconfigured in the demo data.
1. Go to **Commerce parameters \> Configuration parameters** and ensure that there's an entry for **ProductSearch.UseAzureSearch** and that the value is set to **true**. If this entry is missing, add it and set the value to **true**.
1. Go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Initialize Commerce scheduler**. On the **Initialize commerce scheduler** flyout menu, set the **Delete existing configuration** option to **Yes**, and then select **OK**.
1. For the store and e-commerce channels to work properly, they must be added to the Commerce Scale Unit. Go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Channel database**, and then in the left pane select the Commerce Scale Unit. On the **Retail channel** FastTab, add the **AW online store**, **AW Business online store**, and **Fabrikam extended online store** channels if you plan to use those e-commerce channels. Optionally, you can also add retail stores if you will be using point of sale (POS) (for example, **Seattle**, **San Francisco**, and/or **San Jose**).
1. To ensure that all changes are synchronized with the channel database, select **Channel Database \> Full data sync** for the Commerce Scale Unit.

During post-provisioning activities in Commerce headquarters, make sure that the **USRT** legal entity is always selected.

## Configure the point of sale

### Associate a worker with your identity

To associate a worker with your identity, follow these steps in Commerce headquarters.

1. Use the menu on the left to go to **Modules \> Retail and commerce \> Employees \> Workers**.
1. In the list, find and select the following record: **000713 - Andrew Collette**. This example user is associated with the San Francisco store that will be used in the next section.
1. On the Action Pane, select **Commerce**.
1. Select **Associate existing identity**.
1. In the **Email** field to the right of **Search using email**, enter your email address.
1. Select **Search**.
1. Select the record that has your name.
1. Select **OK**.
1. Select **Save**.

### Activate Store Commerce for web

To activate Store Commerce for web, follow these steps in LCS.

1. On the top menu, select **Cloud-hosted environments**.
1. Select your environment in the list.
1. In the environment information on the right, select **Log on to Cloud Point of Sale**.
1. Select **Next** to open the **Before you start** dialog box.
1. Leave the **Server URL** field as it is. Select **Next**.
1. Sign in by using your Microsoft Azure Active Directory (Azure AD) account.
1. Under **Store name**, select **San Francisco**, and then select **Next**.
1. Under **Register and device**, select **SANFRAN-1**.
1. Select **Activate**. You're signed out and taken to the POS sign-in page.
1. You can now sign in to Store Commerce for web by using operator ID **000713** and password **123**.

## Set up your e-commerce sites

There are three available e-commerce demo sites: Fabrikam, Adventure Works, and Adventure Works Business. Follow the steps below to configure each demo site.

1. Sign in to site builder by using the URL that you made a note of when you initialized e-Commerce during provisioning (see [Initialize e-Commerce](provisioning-guide.md#initialize-e-commerce)).
1. Select the site (**Fabrikam**, **Adventure Works**, or **Adventure Works Business**), to open the site setup dialog box.
1. Select the domain that you entered when you initialized Commerce.
1. In headquarters, select the preconfigured online store channel (**Fabrikam extended online store**, **AW online store**, or **AW Business online store**) that corresponds to the default channel.
1. Select **en-us** as the default language.
1. Configure the path fields. This can be left blank for a single site but will need to be configured if using the same domain name for multiple sites. For example, if the domain name is `https://www.constoso.com`, you can use a blank path for Fabrikam (`https://contoso.com`), and then use "aw" for Adventure Works (`https://contoso.com/aw`) and "awbusiness" for the Adventure Works business site (`https://contoso.com/awbusiness`).
1. Select **OK**. The list of pages on the site appears.
1. Optionally, repeat steps 2-7 to configure the other demo sites as needed.

## Enable jobs

To enable jobs in Commerce, follow these steps.

1. Sign in to the headquarters environment.
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

After the provisioning and configuration steps are completed, you can start to use your sandbox environment. Use the Commerce site builder URL to go to the authoring experience. Use the Commerce site URL to go to the retail customer site experience.

To configure optional features for your Commerce sandbox environment, see [Configure optional features for a Commerce sandbox environment](cpe-optional-features.md).

To enable e-commerce users to sign into the e-commerce site, additional configuration is required to enable site authentication via Azure Active Directory business-to-consumer (B2C). For instructions, see [Set up a B2C tenant in Commerce](set-up-b2c-tenant.md).

## Troubleshooting

### Site builder channel list is empty when configuring site

If site builder does not show any online store channels, in headquarters ensure that the channels have been added to the Commerce Scale Unit as described in the [Before you start](#before-you-start) section above. Also, run **Initialize commerce scheduler** with the **Delete existing configuration** value set to **Yes**.  Once these are steps are completed, on the **Channel database** page (**Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Channel database**), run the **9999** job on the Commerce Scale Unit.

### Color swatches are not rendering on the category page, but are rendering on the product details page (PDP) page

Follow these steps to ensure that the color and size swatches are set to be refinable.

1. In headquarters, go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**.
1. In the left pane, select the online store channel, and then select **Set attribute metadata**.
1. Set the **Show attribute on channel** option to **Yes**, set the **Can be refined** option to **Yes**, and then select **Save**. 
1. Return to the online store channel page, and then select **Publish channel updates**.
1. Go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Channel database** and run the **9999** job on the Commerce Scale Unit.

### Business features don't appear to be turned on for the AdventureWorks business site

In headquarters, ensure that the online store channel is configured with the **Customer type** set to **B2B**. If the **Customer type** is set to **B2C**, a new channel must be created since the existing channel can't be edited. 

Demo data shipped in Commerce version 10.0.26 and earlier had a bug where the **AW Business online store** channel was misconfigured. The workaround is to create a new channel with the same settings and configurations except for **Customer type**, which should be set to **B2B**.

## Additional resources

[Provision a Dynamics 365 Commerce sandbox environment](provisioning-guide.md)

[Configure optional features for a Dynamics 365 Commerce sandbox environment](cpe-optional-features.md)

[Configure BOPIS in a Dynamics 365 Commerce sandbox environment](cpe-bopis.md)

[Microsoft Lifecycle Services (LCS)](/dynamics365/unified-operations/dev-itpro/lifecycle-services/lcs-user-guide)

[Retail Cloud Scale Unit (RCSU)](/business-applications-release-notes/october18/dynamics365-retail/retail-cloud-scale-unit)

[Microsoft Azure portal](https://azure.microsoft.com/features/azure-portal)

[Dynamics 365 Commerce website](https://aka.ms/Dynamics365CommerceWebsite)

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
