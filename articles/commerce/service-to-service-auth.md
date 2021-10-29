---
# required metadata

title: Configure Service-to-Service authentication
description: This topic describes how to configure Service-to-Service authentication in Microsoft Dynamics 365 Commerce to securely call ratings and reviews service APIs.
author: gvrmohanreddy
ms.date: 10/26/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2017-06-20
---

# Service-to-ervice authentication

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes how to configure Service-to-Service (S2S) authentication in Microsoft Dynamics 365 Commerce to securely call ratings and reviews service APIs.

Dynamics 365 Commerce offers [ratings and reviews](ratings-reviews-overview.md) as an omni-channel solution that allows access to service APIs from outside of Commerce to perform tasks such as importing ratings and reviews from your external system into Commerce or exporting ratings and reviews from Commerce. To securely call ratings and reviews service APIs , you must configure S2S authentication. 

## Configure service-to-service authentication

To configure service-to-service authentication in Commerce site builder, follow these steps.

1. Go to **Home \> Reviews \> Settings**.
1. Find the card with the title Service-to-Service (S2S) Authentication and select Manage.

![ALT_1](media/Ratings-reviews-settings-service-to-service-authentication.png)

After selecting Manage, a flyout panel will appear on the right side of the screen, for S2S App Entries with the following options.

1. Add a new S2S App Registration
1. Edit an existing S2S App Registration (pencil icon)
1. Remove an existing S2S App Registration (trashcan icon)

## Add a new app registration

Before you add a new app registration, you must first create an application using the [Azure Portal](https://portal.azure.com). To register an app on Azure Active Directory and enable authentication, follow the steps in [Use Azure Active Directory with a custom connector in Power Automate](/connectors/custom-connectors/azure-active-directory-authentication) . 

Collect the following IDs from the azure portal to be used in the next steps.
- Client Application ID
- Client directory (tenant) ID.

To add an app registration, follow these steps in Commerce site builder.

1. Select **Add a new S2S App Registration**.
1. Enter the following required items in the form displayed, using values from your Azure application registration.
    - **Name**: The name for your application, for example "Fabrikam App".
    - **Client App ID**: The application ID, for example “00000000-0000-0000-0000-000000000000”
    - **Directory (Tenant) ID**: The directory ID, for example “00000000-0000-0000-0000-000000000000”
1. Select **Submit**. You should now see the name of your application appear in the list.
1. Close the S2S App Entries panel.
1. Select **Save** to save your changes.
 
![ALT_3](media/Ratings-reviews-settings-S2S-APP-entry.png)
 
## Edit an existing app registration

To edit an existing app registration in Commerce site builder, follow these steps.

1. Select the pencil symbol next to the entry you want to edit.
1. Update values for **Name**, **Client App ID**, and **Directory (Tenant) ID** as needed.
1. Select **Submit**.
1. Close the **S2S App Entries** pane.
1. Select **Save**.

## Remove an existing app registration

To remove an existing app registration in Commerce site builder, follow these steps.

1. Select the trashcan symbol next to the entry you wish to remove. The entry will be removed from the list.
1. Close the **S2S App Entries** pane.
1. Select **Save**.

![ALT_5](https://user-images.githubusercontent.com/42852473/137647294-ff54425c-18c0-429a-a7bf-cde31f47b5b1.png)
