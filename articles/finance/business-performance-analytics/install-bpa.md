# required metadata

title: Installing Business performance analytics
description: Steps to install Business performance analytics
author: jinniew
ms.date: 04/22/2023
ms.topic: article
ms.prod: 
ms.technology: 
---
# Installing Business performance analytics

Using the app source link, which would directly navigate to the Business performance analytics offering. The administrator who has completed the configuration steps should login. 

> [!NOTE]
> For gated public preview, Microsoft will share the App link to you separately via email.  

	1.  Click on Get it Now, this should auto-redirect to Power Platform Admin Center. 
	2.  Post-redirection, Select the Dataverse environment to install on. 
	3.  Once T&C (terms and conditions) are accepted, click on the install and the app installation should begin on the environment selected. 
	4.  This installation should take close to 1 hour to complete. Check the status of app installation and on successful completion it should be reflected as Installed in PPAC. 
	5.  Post App Installation is successful, ensure the following service principal is provisioned. 

The following Azure AD apps are registered in Azure AD. 
| Application            | App ID                               |
| ---------------------- | ------------------------------------ |
| far-dataverse-pipeline | 0e3659ee-3f34-4d0f-be21-d11f7141572f |

To verify the application is registered in Azure AD, check the All Applications list. For more details, see [View enterprise applications](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/view-applications-portal). If the application isn't registered in Azure AD, contact support. 
