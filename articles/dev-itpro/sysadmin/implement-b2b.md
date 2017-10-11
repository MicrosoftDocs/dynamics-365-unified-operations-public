 dis---
# required metadata

title: B2B functionality in Dynamics 365 for Finance and Operations, Enterprise edition
description: This article provides information about implementing the business-to-business transaction functionality in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: sarvanisathish
manager: AnnBe
ms.date: 10/06/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2017-10-06
ms.dyn365.ops.version: Platform update 12

---

# Export B2B users to AAD automatically in Dynamics 365 for Finance and Operations, Enterprise edition
With Platform Update 12, you are now able to export B2B users automatically to AAD. In the past the B2B users were first exported manually to a .csv file. Then the AAD tenant administrator had to pick up this file and add the user to AAD manually in the AAD portal. Below are the steps to use the automated export functionality.

## Pre-requisites
In order to enable the automatic export feature a one time setup and configuration must be exercised. The one time setup and configuration includes 
1. Setting up an B2B invitation service application in Azure Active Directory
2. Configure the B2B invitation service settings in Dynamics 365 for Finance and Operations, Enterprise edition

### Setup B2B invitation service application in Azure Active Directory
The tenant administator of your AAD tenant will need to complete the following steps.

1. Log on to the [Azure portal](https://portal.azure.com) as the tenant administrator. 
2. Click on **Azure Active Directory -> Properties**
3. Copy the **Directory ID** (this is the tenant id) and save it. You will need this later.
4. Now go to **App registrations -> New application registration**
5. In the New application registration blade enter the below details and click Create.
  1. **Name** of the application. e.g. B2B admin application.
  2. Web app /API for **ApplicationType**
  3. **Sign-on URL** of your Dynamics 365 for Finance and Operations, Enterprise edition application
6. In the **App registrations** blade, navigate to the newly created application and navigate to **Settings -> Required permissions -> Add**
7. In the **Add API access** blade go to 
  1. **Select an API** and select **Microsoft Graph**
  2. **Select permissions** and select the below permissions and click on **Done**
    -APPLICATION PERMISSIONS 
    Read and write directory data
    Read and write all users' full profiles
    -DELEGATED PERMISSIONS 
    Sign in and read user profile
8. In the **Required permissions** blade, navigate to the **Grant permissions** tab and click on **Yes** to assign the permissions.
9. In the **Settings -> Keys** blade, 
  1. Enter a name of the key in **Description** field
  2. Set the Expiration duration in **Expires** field
10. Saving the Key will display the **Value**. 

[!WARNING]

Ensure you copy the Key **Value** on save. This value will not be available when you leave the blade







  
  
  

[!include[banner](../includes/banner.md)]
