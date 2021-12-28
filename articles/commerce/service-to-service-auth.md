---
# required metadata

title: Configure Service-to-Service authentication
description: This topic describes how to configure Service-to-Service authentication in Microsoft Dynamics 365 Commerce to securely call ratings and reviews service APIs.
author: gvrmohanreddy
ms.date: 12/28/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2017-06-20
---

# Configure Service-to-Service authentication

[!include [banner](includes/banner.md)]

This topic describes how to configure Service-to-Service (S2S) authentication in Microsoft Dynamics 365 Commerce to securely call ratings and reviews service APIs.

Dynamics 365 Commerce offers [ratings and reviews](ratings-reviews-overview.md) as an omni-channel solution that allows access to service APIs from outside of Commerce to perform tasks such as importing ratings and reviews from your external system into Commerce or exporting ratings and reviews from Commerce. To enable Commerce to securely call ratings and reviews service APIs, you must first configure S2S authentication by following the procedures below. 

## Add a new app registration

Before you add a new app registration, you must first create an application using the [Azure Portal](https://portal.azure.com). To register an app on Azure Active Directory and enable authentication, follow the steps in [Use Azure Active Directory with a custom connector in Power Automate](/connectors/custom-connectors/azure-active-directory-authentication) . 

Collect the following IDs from the Azure portal to be used in the following steps.
- Client application ID
- Client directory (tenant) ID.

To add a new app registration in Commerce site builder, follow these steps.

1. Go to **Home \> Reviews \> Settings**.
1. Under **Service-to-Service (S2S) Authentication**, select **Manage**.

    ![Service-to-Service (S2S) Authentication section in site builder](media/Ratings-reviews-settings-service-to-service-authentication.png)

1. In the **S2S App Entries** flyout pane that appears on the right, select **Add a new S2S App Registration**.
1. In the **Add S2S App Entry** dialog box, enter the following required items using values from your Azure application registration.
    - **Name**: The name for your application, for example "Fabrikam App".
    - **Client App ID**: The application ID, for example “00000000-0000-0000-0000-000000000000”
    - **Directory (Tenant) ID**: The directory ID, for example “00000000-0000-0000-0000-000000000000”
1. Select **Submit**. You should now see the name of your application appear in the list on the **S2S App Entries** pane.
1. Close the **S2S App Entries** pane.
1. Select **Save**.
 
![The Add S2S App Entry dialog box in site builder](media/Ratings-reviews-settings-S2S-APP-entry.png)

## Edit an existing app registration

To edit an existing app registration in Commerce site builder, follow these steps.

1. Go to **Home \> Reviews \> Settings**.
1. Under **Service-to-Service (S2S) Authentication**, select **Manage**.
1. In the **S2S App Entries** flyout pane, select the pencil symbol next to the entry you want to edit.
1. Update values for **Name**, **Client App ID**, and **Directory (Tenant) ID** as needed.
1. Select **Submit**.
1. Close the **S2S App Entries** pane.
1. Select **Save**.

## Remove an existing app registration

To remove an existing app registration in Commerce site builder, follow these steps.

1. Go to **Home \> Reviews \> Settings**.
1. Under **Service-to-Service (S2S) Authentication**, select **Manage**.
1. In the **S2S App Entries** flyout pane, select the trashcan symbol next to the entry you wish to remove. The entry will be removed from the list.
1. Close the **S2S App Entries** pane.
1. Select **Save**.

## Additional resources

[Ratings and reviews overview](ratings-reviews-overview.md)

[Manage ratings and reviews](manage-reviews.md)

[Configure ratings and reviews](configure-ratings-reviews.md)

[Import and export ratings and reviews](import-export-reviews.md)

[Ratings and reviews FAQ](ratings-reviews-faq.md) 

