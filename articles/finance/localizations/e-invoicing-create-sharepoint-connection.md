---
# required metadata

title: Configure SharePoint connection
description: This topic provides description of the process of installation Electronic invoicing Add-in in LCS.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

# Configure SharePoint connection

[!include [banner](../includes/banner.md)]

Electronic invoicing service can read files from SharePoint folders, and upload files to it.
To make sure Electronic invoicing can access SharePoint site, you should provide credentials to the Electronic invoicing service. To make sure the credentials are stored securely, you should provide them not directly, but store in Azure Key Vault, and provide Key Vault secret instead.

## Grant an access to SharePoint folder
1. Create an App registration in the tenant where RCS is installed to:
    
    a. Go to Azure portal (https://portal.azure.com/)
    
    b. Navigate to **App registrations**
		
    c. Select **New registration**, enter a name (i.e. "SharePoint App for Electronic Invoicing") and complete registration
		
    d. Select the created **App Registration**
		
    e. Go to **Authentication** tab and enable **Allow public client flows** setting
		
    f. Go to **Certificates & secrets** tab and create a new client secret by selecting **New client secret** button
		  
      - Do not use one App Registration for different services
      
      - Follow Password policy recommendations (https://docs.microsoft.com/en-us/microsoft-365/admin/misc/password-policy-recommendations?view=o365-worldwide)
			
      - Setup rotation of the passwords (create new client secret for the App Registration and update the Key Vault, then delete the old secret)
		
    g. Copy value of the created secret
    
2. Save ***App Registration secret*** and ***Application (client) ID*** as two new secrets in Azure Key vault used in your Electronic Invoicing environments setup
3. Add secrets created in step 2 to the Key Vault parameters in RCS Electronic Invoicing environments setup
4. Grant access to SharePoint in Azure portal (this step should be performed by the Tenant administrator):
		
   a. Select the created **App Registration**
    
   b. Go to **API permissions** tab and select **Add a permission** button
		
   c. Select **Microsoft graph (Application permissions)** > **Sites.Selected**
		
   d. Press **Grant admin consent for …**
		
   e. Make sure permissions are granted by reviewing the status:
		![Configured permissions page.](media/configured-permissions.jpg)

    
   f. Go to Graph Explorer - Microsoft Graph and log in
		
   g. In **Sample queries** section find **SharePoint Sites** > get SharePoint site based on relative path of the site
		
   h. Fill in _{host-name}_ and _{server-relative-path}_ parameters. i.e. _{host-name}_ = `<domain>.sharepoint.com`, _{server-relative-path}_ = `sites/<siteName>`

	> [!NOTE]
	> For the Default website live {server-relative-path} parameter empty.

   i. Select **Run query** and save the result.
   
   j. Configure a query:
   
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
		
   k. In **Modify permissions** tab, select **Open the permissions panel** > select **Sites** > **Sites.FullControl.All** > **Consent**
   
   l. Select **Run query**
		
Now, Electronic invoicing service will have an access to your SharePoint.
