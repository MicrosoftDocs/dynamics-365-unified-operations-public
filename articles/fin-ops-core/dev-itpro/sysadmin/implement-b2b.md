---
title: Export business-to-business (B2B) users to Microsoft Entra ID
description: Learn about implementing the business-to-business transaction functionality, including an overview on setting up invitation service applications.
author: paulliew
ms.author: paulliew
ms.topic: how-to
ms.date: 01/21/2026
ms.custom:
ms.reviewer: johnmichalak
audience: developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2017-10-31
ms.search.form: B2BInvitationConfiguration
ms.dyn365.ops.version: Platform update 12
---

# Export business-to-business (B2B) users to Microsoft Entra ID

[!include [banner](../includes/banner.md)]

You can automatically export business-to-business (B2B) users to Microsoft Entra ID.

Previously, you had to manually export B2B users to a .csv file. Then, the Microsoft Entra tenant administrator used this file to manually add the users to Microsoft Entra through the Azure portal.

To enable the automatic export feature, complete a one-time setup and configuration process. After you complete the process, you can use the **Provision Microsoft Entra B2B user** workflow task to automatically export B2B users to Microsoft Entra ID.

The one-time setup and configuration requires that you:

1. Set up a B2B invitation service application in Microsoft Entra ID.
1. Configure the B2B invitation service settings in finance and operations.

## Set up a B2B invitation service application in Microsoft Entra ID

The tenant administrator of your Microsoft Entra tenant needs to complete the following steps.

1. Sign in to the [Azure portal](https://portal.azure.com) as the tenant administrator.
1. Select **Microsoft Entra ID** > **Properties**.
1. Copy the **Directory ID** (this is the tenant ID) and save it. You need this value later.
1. Select **App registrations** > **New application registration**.
1. Enter the following information, and then select **Create**.
    1. In the **Name** field, enter the name of the application. For example: **B2B admin application**.
    1. In the **Application type** field, select **Web app /API**.
    1. In the **Sign-on URL** field, enter the URL for finance and operations.
1. Select the **App registrations** tab, select the newly created application, copy the **Application ID**, and save it. You need this value later.
1. Select **All settings** > **Required permissions** > **Add**.
1. In the **Add API access** pane, complete the following steps:
    1. Select the **Select an API** tab. Select **Microsoft Graph**, and then select **Select**.
    1. In the **Select permissions** tab, select the following **application permissions** and set them to **Yes**:
         - **Invite guest users to the organization**
         - **Read and write directory data**
         - **Read and write all users' full profiles**
    1. Select the following **delegated permissions** and set them to **Yes**:
         - **Invite guest users to the organization**
         - **Read and write directory data**
         - **Read and write all users' full profiles**
         - **Sign in and read user profile**
    1. Select **Select** and **Done**.
1. In the **Required permissions** blade, select **Grant Permissions**, and then select **Yes** to assign the permissions.
1. Select **All settings** > **Keys**, and then complete the following steps:
    1. Enter a name of the key in the **Description** field.
    1. Set the expiration duration in the **Expires** field.
1. Select **Save**. When you save the key, the **Value** is displayed.

    > [!WARNING]
    > Be sure to copy the key **Value** after saving the key. You can't access this value when you leave the blade.

### Configure the B2B invitation service settings

1. Sign in to finance and operations as administrator.
1. Go to the **B2B Invitation Configuration** page, and select **Edit**.
1. Select **Enabled**.
1. Verify that the **Tenant ID** matches the **Directory ID** (which you noted in step 3 of the previous procedure).
1. In the **Client ID** field, enter the **Application ID** (which you noted in step 6 of the previous procedure).
1. Enter the key **Value**, copied from the previous procedure, into the **Application Key** field.
1. **Save** the settings.

Now you can start using the **Provision Microsoft Entra B2B user** workflow task in your workflows to automatically export B2B users to Microsoft Entra ID.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
