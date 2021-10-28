---
# required metadata

title: Service-to service-authentication
description: This describes how to import and export product ratings and reviews in Microsoft Dynamics 365 Commerce.A way to call into Dynamics 365 Commerce Ratings and Reviews service API securely.
author: gvrmohanreddy
ms.date: 10/26/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2017-06-20
---

# Service-to-service authentication

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

Dynamics 365 Commerce offers [Ratings and Reviews](ratings-reviews-overview.md) as an omni-channel solution. Ratings and Reviews solution allows to access the service API's from outside of Dynamics 365 Commerce, such as importing reviews from your external system into Dynamics 365 or exporting review from Dynamics 365 using Power Automate. This article explains how to configure service-to-service authentication to securely calling into the Ratings and Reviews service API's. 

## Configure service-to-service (S2S) authentication

To configure service-to-service authentication in Commerce site builder, follow these steps.

1. Go to **Home \> Reviews \> Settings**.
1. Find the card with the title Service-to-Service (S2S) Authentication and select Manage.

![ALT_1](media/Ratings-reviews-settings-service-to-service-authentication.png)

![ALT_2](https://user-images.githubusercontent.com/42852473/137647263-63711900-2b90-4f9f-b788-58335b2b65e2.png)

After selecting Manage, a flyout panel will appear on the right side of the screen, for S2S App Entries with the following options.

1. Add a new S2S App Registration
1. Edit an existing S2S App Registration (pencil icon)
1. Remove an existing S2S App Registration (trashcan icon)

 ### Add a new app registration

Before you add a new app registration, you must first create an application using the [Azure Portal](https://portal.azure.com). To register an app on Azure Active Directory and enable authentication, follow the steps in [Use Azure Active Directory with a custom connector in Power Automate](/connectors/custom-connectors/azure-active-directory-authentication) . 

Collect the following IDs from the azure portal to be used in the next steps.
- Client Application ID
- Client directory (tenant) ID.

To add an app registration, follow these steps in Commerce site builder.

1. Select Add a new S2S App Registration
1. Enter the following required items in the form displayed, using values from your Azure application registration.
    - Name: The name for your application, for example "Fabrikam App".
    - Client App ID: The application ID, for example “00000000-0000-0000-0000-000000000000”
    - Directory (Tenant) ID: The directory ID, for example “00000000-0000-0000-0000-000000000000”
1. Select Submit. You should now see the name of your application appear in the list.
1. Close the S2S App Entries panel.
1. Select Save to save your changes.
 
![ALT_3](media/Ratings-reviews-settings-S2S-APP-entry.png)
 
### Edit an existing app registration

To edit an existing app registration, follow these steps.

1. Select the pencil icon next to the entry you wish to edit.
1. Update Name, Client App ID, Directory (Tenant) ID.
1. Select Submit.
1. Close the S2S App Entries panel.
1. Select Save to save your changes.

![ALT_4](https://user-images.githubusercontent.com/42852473/137647292-e60dc766-471a-406f-975c-4cba8d806ea2.png)

### Remove an existing app registration

To remove an existing app registration, follow these steps.

1. Select the trashcan icon next to the entry you wish to remove.
1.  The entry will be removed from the list.
1.  Close the S2S App Entries panel.
1. Select Save to save your changes.

![ALT_5](https://user-images.githubusercontent.com/42852473/137647294-ff54425c-18c0-429a-a7bf-cde31f47b5b1.png)
