---
# required metadata

title: Configure SharePoint connection
description: This topic provides information about how to install the Electronic invoicing Add-in in Lifecycle services.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Configure SharePoint connection

[!include [banner](../includes/banner.md)]

The Electronic invoicing service can read files from SharePoint folders, and upload files to SharePoint.
To make sure Electronic invoicing can access a specific SharePoint site, provide the site credentials to the Electronic invoicing service. To make sure the credentials are stored securely, don't provide them directly. Instead, store them in the Azure Key Vault, and provide a Key Vault secret instead.

## Grant access to a SharePoint folder
1. Create an App registration in the tenant where the Regulatory configuraion service (RCS) is installed.
    
    1. In the [Azure portal](https://portal.azure.com/), go to **App registrations**.
    2. Select **New registration**, enter a name, such as **SharePoint App for Electronic Invoicing**, and then complete the registration
    3. Select the app registration you created and on the **Authentication** tab, enable **Allow public client flows**.
    4. On the **Certificates & secrets** tab, create a new client secret by selecting **New client secret**.
		  
      - Don't use one App registration for different services.
      - Follow the [Password policy recommendations](/microsoft-365/admin/misc/password-policy-recommendations?view=o365-worldwide)		
      - Set up a rotation of the passwords. Create a new client secret for the App registration and update the Key Vault. Then delete the old secret.
		
    5. Copy the value of the created secret.
    
2. Save the **App Registration secret** and **Application (client) ID** as two new secrets in the Azure Key Vault in your Electronic Invoicing environment setup.
3. Add the secrets you created to the Key Vault parameters in the RCS Electronic Invoicing environment setup.
4. Grant access to SharePoint in the Azure portal. This step should be performed by the Tenant administrator.
		
   1. Select the created App registration and on the **API permissions** tab, select **Add a permission**.
   2. Select **Microsoft graph (Application permissions)** > **Sites.Selected**.
   3. Select **Grant admin consent for …**.
   4. Make sure permissions are granted by reviewing the status.
      
      ![Configured permissions page.](media/configured-permissions.jpg)

    
   5. Log in to **Graph Explorer - Microsoft Graph**.
   6. In the **Sample queries** section, locate **SharePoint Sites** and get the SharePoint site information based on relative path of the site.
   7. Fill in _{host-name}_ and _{server-relative-path}_ parameters. i.e. _{host-name}_ = `<domain>.sharepoint.com`, _{server-relative-path}_ = `sites/<siteName>`
      
      > [!NOTE]
      > For the default website live {server-relative-path} parameter empty.

   8. Select **Run query** and save the result.
   9. Configure the following query:
   
   `POST https://graph.microsoft.com/v1.0/sites/{site-id}/permissions` where *{site-id}* is the value of id node from the previous query response.
   
   Request body:
	
   ```json
   {
      "roles": [
          "read",
          "write"
      ],
      "grantedToIdentities": [
          {
              "application": {
                  "id": "{app-id}",
                  "displayName": "{app-name}"
              }
          }
      ]
   }
   ```

   where _{app-id}_ is the ***Application (client) ID*** from p.2, _{app-name}_ is the ***Application name***
		
   ![Configure SharePoint query.](media/app-id-query.jpg)
		
   10. On the **Modify permissions** tab, select **Open the permissions panel** >  **Sites** > **Sites.FullControl.All** > **Consent**.
   11. Select **Run query**
		
The Electronic invoicing service now has access to your SharePoint.
