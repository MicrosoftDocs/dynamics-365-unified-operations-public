---
# required metadata

title: Configure a SharePoint connection
description: This topic explains how to configure a connection so that Electronic invoicing can access a Microsoft SharePoint site.
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

# Configure a SharePoint connection

[!include [banner](../includes/banner.md)]

The Electronic invoicing service can read files from Microsoft SharePoint folders and upload files to SharePoint. To ensure that Electronic invoicing can access a specific SharePoint site, you must provide the site credentials to the Electronic invoicing service. Additionally, to ensure that the credentials are securely stored, don't provide them directly. Instead, store them in an Azure key vault, and provide an Azure Key Vault secret.

## Grant access to a SharePoint folder

1. Create an app registration in the tenant where Regulatory Configuration Service (RCS) is installed.

    1. Sign in to the [Azure portal](https://portal.azure.com/).
    2. Go to **App registrations**.
    3. Select **New registration**.
    4. Enter a name, such as **SharePoint App for Electronic Invoicing**, and complete the registration
    5. Select the new app registration.
    6. On the **Authentication** tab, enable the **Allow public client flows** option.
    4. On the **Certificates & secrets** tab, select **New client secret** to create a client secret.
    5. Copy the value of the secret that was created.

    Follow these guidelines:

    - Don't use the same app registration for different services.
    - Follow the [password policy recommendations](/microsoft-365/admin/misc/password-policy-recommendations?view=o365-worldwide).
    - Set up rotation of passwords. During rotation, create a new client secret for the app registration, update the key vault, and then delete the old secret.

2. Save the **App Registration secret** and **Application (client) ID** values as two new secrets in the key vault in the setup of your Electronic invoicing environment.
3. Add the secrets that you created to the Key Vault parameters in the setup of your Electronic invoicing environment in RCS.
4. In the Azure portal, grant access to SharePoint. This step should be completed by the tenant administrator.

    1. Select the app registration that you created.
    2. On the **API permissions** tab, select **Add a permission**.
    3. Select **Microsoft graph (Application permissions)** \> **Sites.Selected**.
    4. Select **Grant admin consent for \<user&nbsp;name\>**.
    5. Review the **Status** field to make sure that permissions are granted.

        ![Permissions granted on the API permissions tab.](media/configured-permissions.jpg)

    6. Open [Graph Explorer - Microsoft Graph](https://developer.microsoft.com/graph/graph-explorer), and sign in.
    7. In the left pane, on the **Sample queries** tab, under **SharePoint Sites**, select **get SharePoint site based on relative path of the site**.
    8. Fill in the **\{host-name\}** and **\{server-relative-path\}** parameters. For example, fill in `<domain>.sharepoint.com` for **\{host-name\}** and `sites/<siteName>` for **\{server-relative-path\}**.

        > [!NOTE]
        > For the default website, leave the **\{server-relative-path\}** parameter blank.

    9. Select **Run query**, and save the result.
    10. Configure the following query.

        `POST https://graph.microsoft.com/v1.0/sites/{site-id}/permissions`

        In this query, **\{site-id\}** is the value of the **id** node from the previous query response.

        Here is the request body.

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

        In this request body, **\{app-id\}** is the **Application (client) ID** value, and **\{app-name\}** is the **Application name** value.

        ![POST query.](media/app-id-query.jpg)

    11. On the **Modify permissions** tab, select **Open the permissions panel**, and then select **Sites** \> **Sites.FullControl.All** \> **Consent**.
    12. Select **Run query**.

The Electronic invoicing service now has access to your SharePoint site.
