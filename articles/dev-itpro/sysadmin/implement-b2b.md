---
# required metadata

title: B2B functionality in Dynamics 365 for Finance and Operations, Enterprise edition
description: This article provides information about implementing the business-to-business transaction functionality in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: sarvanisathish
manager: AnnBe
ms.date: 10/11/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sarvanis
ms.search.validFrom: 2017-10-31
ms.dyn365.ops.version: Platform update 12

---

# Export B2B users to AAD automatically in Dynamics 365 for Finance and Operations, Enterprise edition
With Platform Update 12, you are now able to export B2B users automatically to AAD. In the past the B2B users were first exported manually to a .csv file. Then the AAD tenant administrator had to pick up this file and add the user to AAD manually in the AAD portal. 

In order to enable the automatic export feature a one time setup and configuration must be exercised. Once the onetime setup is completed, you may use the **Provision new user** workflow task to enable automatically export B2B users to AAD.

For more information about Azure AD B2B collaboration, see [What is Azure AD B2B collaboration?](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b)

The one-time set up and configuration means you'll need to: 
1. Set up a B2B invitation service application in Azure AD.
2. Configure the B2B invitation service settings in Finance and Operations.

### Set up a B2B invitation service application in Azure AD
The tenant administator of your Azure AD tenant will need to complete the following steps.

1. Log on to the [Azure portal](https://portal.azure.com) as the tenant administrator. 

2. Click **Azure Active Directory** > **Properties**.

3. Copy the **Directory ID** (this is the tenant ID) and save it. You will need this later.

4. Click **App registrations** > **New application registration**.

5. Enter the folliwng information, and then click **Create**.
    1. In the **Name** field, enter the name of the application. For example: **B2B admin application**.
    2. In the **Application type** field, select **Web app /API**.
    3. In the **Sign-on URL** field, enter the URL of Finance and Operations.
  
6. Click the **App registrations** tab, click the newly created application, copy the **Application ID**, and save it. You will need this later.

7. Click **All settings** > **Required permissions** > **Add**.

8. In the **Add API access** pane, do the following:
    1. Click the **Select an API** tab. Click **Microsoft Graph**, and then click **Select**.
    
    2. On the **Select permissions** tab, select the following application permissions:
      - **Read and write all users' full profiles**
      - **Read and write directory data**
    
    3. Select the following delegatded permission:
      - **Sign in and read user profile**
     
    4. Then click **Select** and **Done**.
    
9. In the **Required permissions** blade, click **Grant Permissions**, and then click **Yes** to assign the permissions.

10. Click **All settings** > **Keys**, and then do the following: 

  1. Enter a name of the key in the **Description** field.
  2. Set the expiration duration in the **Expires** field.
  
11. Click **Save**. Saving the key will display the **Value**. 

    > [!WARNING]
    > Be sure to copy the key **Value** after saving the key. This value will not be available when you leave the blade.

### Configure the B2B invitation service settings in Finance and Operations, Enterprise edition

1. Log in to the Dynamics 365 for Finance and Operations, Enterprise edition as administrator.

2. Navigate to **System administration -> Setup -> B2B Invitation Configuration** form and click **Edit**.

3. Select **Enabled**.

4. Verify **Tenant ID** is the same as the **Directory ID** copied from the above setup.

5. Enter the **Application ID** copied from the above step into **Client ID**.

6. Enter the Key **Value** copied from the above step into **Application Key**.

7. **Save** the settings.

Now you may start using the **Provision new users** workflow task in your workflows to export the B2B users to AAD automatically.





  
  
  

[!include[banner](../includes/banner.md)]
