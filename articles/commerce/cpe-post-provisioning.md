---
# required metadata

title: Configure a Commerce preview environment
description: This topic describes how to configure a Microsoft Dynamics 365 Commerce preview environment after provisioning.
author: psimolin
manager: annbe
ms.date: 12/02/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: psimolin
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
---

# Configure a Commerce preview environment

This topic describes how to configure a Microsoft Dynamics 365 Commerce preview environment after provisioning.

## Post-provisioning steps
At this stage, the environment has been provisioned end-to-end, but there are still configuration steps that need to be taken care of before you can start evaluating the environment.
### Before starting
1. From the top menu, select **Cloud-hosted environments**.
1. Select your environment from the list.
1. Click **Full details** from the environment info on the right.
1. Click **Login** to open a menu, choose **Log on to environment**.

Make sure that **USRT** legal entity is selected (top right corner).

### Configure POS
##### Associate worker with your identity
1. Using the menu on the left, go to **Modules > Retail > Employees > Workers**.
1. In the list, find and select record **000713 - Andrew Collette**.
1. On the Action Pane, click **Retail**.
1. Click **Associate existing identity**.
1. In the **Email** field (to the right of **Search using email**), type your email address.
1. Click **Search**.
1. Select the record with your name.
1. Click **OK**.
1. Click **Save**.
##### Activate Cloud POS
1. Log in to the LCS portal.
1. Navigate to your project.
1. From the top menu, select **Cloud-hosted environments**.
1. Select your environment from the list.
1. Click **Full details** from the environment info on the right.
1. Click **Login** to open a menu, choose **Log on to Cloud Point of Sale**, POS should load up.
1. Click **Next**.
1. Log in with your AAD account.
1. Under **Store name**, choose **San Francisco**.
1. Click **Next**.
1. Under **Register and device**, choose **SANFRAN-1**.
1. Click **Activate**.
1. You should be logged out and end up in the POS login screen.
1. You can now log in to the Cloud POS experience using Operator ID **000713** and password **123**.
### Site setup
1. Log in to the **site management tool** using the URL you noted earlier.
1. Click on the **Fabrikam** site to open the site setup dialog.
1. For domain, select the domain you entered earlier when initializing the e-Commerce.
1. For default channel, select **Fabrikam extended online store**. *Note: Make sure you select the **extended** online store*
1. For default language, select **en-us**.
1. Leave **Path** as it is.
1. Click **OK**.
1. You will be sent to the list of pages on the site.
### Enable jobs
1. Log in to the environment (HQ).
1. Using the menu on the left, go to **Retail > Inquiries and reports > Batch jobs**.
1. Perform the following steps for each of the jobs in the list below:
	* **Process retail order email notification**.
	* **Product availability**.
	* **P-0001**.
	* **Synchronize orders job**.
1. Use the Quick Filter to search for the job using its name (listed above).
1. If the Status of the job is **Withhold**, perform the following steps:
	1. Select the record.
	1. From the action pane, open **Batch job**-ribbon and click **Change status**.
	1. Select **Waiting** and Click **OK**.
### Run full data sync
1. Using the menu on the left, go to **Modules > Retail > Headquarters setup > Retail scheduler > Channel database**.
1. **Default** channel is selected from the list on the left. *Select the other available channel (named **scXXXXXXXXX**)*.
1. Click **Full data sync** from the action pane.
1. Enter **9999** as the distribution schedule.
1. Click **OK**.
1. Click **OK**.
### After these steps you are ready to start evaluating your preview environment!
Use the **e-Commerce site management tool** URL to navigate to the C1 authoring experience and the **e-Commerce site** URL to navigate to the C2 site experience.

## Additional resources
### How to find your AAD Tenant Id
AAD Tenant Id is a GUID and looks like this example: **72f988bf-86f1-41af-91ab-2d7cd011db47**
##### From Azure Portal
1. Log in to the Azure portal: https://portal.azure.com/
1. Make sure that you have the correct directory selected.
1. Click **Azure Active Directory** from the menu on the left.
1. Choose **Properties** under **Manage**.
1. AAD Tenant Id is shown under **Directory ID**.
##### From OpenID Connect metadata
Create **OpenID URL** by replacing **\{YOUR_DOMAIN\}** with your domain, e.g. microsoft.com: https://login.microsoftonline.com/{YOUR_DOMAIN}/.well-known/openid-configuration would become https://login.microsoftonline.com/microsoft.com/.well-known/openid-configuration

1. Navigate to the **OpenID URL** with your domain in it.
1. AAD Tenant Id can be seen in multiple property values.
1. Locate **authorization_endpoint** and extract the GUID right after **login.microsoftonline.com/**.
### How to find the ID of your AAD security group
AAD security group ID is a GUID and looks like this example: **436ea7f5-ee6c-40c1-9f08-825c5811066a**

This step assumes that the user is a member of the group they are attempting to locate ID for.
1. Navigate to the Graph Explorer: https://developer.microsoft.com/en-us/graph/graph-explorer#
1. Click **Sign In with Microsoft** and sign in using your credentials.
1. After signing in, click **show more samples** from the left.
1. Enable **Groups** from the right pane.
1. Close the right pane.
1. Click **all groups I belong to**.
1. Locate your group from the **Response Preview** text box.
1. Security group ID is noted under property **id**.
### Test credit card information to perform test purchases
In order to perform test transactions on the site, you can use this test credit card information:

Card number: 4111-1111-1111-1111, Expiration: 10/20, CVV: 737

*Note: You should not attempt to use actual credit card information on the test site under any circumstances!*
### Useful links
* [LCS (Lifecycle services)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/lifecycle-services/lcs-user-guide)
* [RCSU (Retail Cloud Scale Unit)](https://docs.microsoft.com/en-us/business-applications-release-notes/october18/dynamics365-retail/retail-cloud-scale-unit)
* [Microsoft Azure portal](https://azure.microsoft.com/en-us/features/azure-portal)
* [Dynamics 365 Commerce website](https://aka.ms/Dynamics365CommerceWebsite)
* [Dynamics 365 Retail](../retail/index.md)
### Microsoft Dynamics 365 Commerce Preview support
If you experience issues while performing the provisioning steps, please visit the [Microsoft Dynamics 365 Commerce Preview Yammer group](https://aka.ms/Dynamics365CommercePreviewYammer) for assistance. 

If you are having issues accessing the Yammer group, you can also reach us via email at **Dynamics365Commerce@microsoft.com**. This email address is not actively monitored so expect a delay in response.

## Next steps

## Additional resources

[Commerce preview environment overview] (cpe-overview.md)
[Provision a Commerce preview environment](provisioning-guide.md)
[Configure Commerce preview environment optional features](cpe-optional-features.md)
[Commerce preview environment FAQ](cpe-faq.md)
