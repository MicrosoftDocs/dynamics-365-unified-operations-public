---
# required metadata
title: [Ratings and Review Configuration - Service to service authentication]
description: [A way to call into Dynamics 365 Commerce Ratings and Reviews service API securely.]
author: [gvrmohanreddy]
manager: jeffbl
ms.date: 08/27/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 
# optional metadata
# ms.search.form:  
#ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2021-10-17
ms.dyn365.ops.version: 10.0.24
---

#Overview

Dynamics 365 Commerce offers *[Ratings and Reviews]( https://docs.microsoft.com/en-us/dynamics365/commerce/ratings-reviews-overview)* as an omni-channel solution. Ratings and Reviews solution allows to access the service API's from outside of Dynamics 365 Commerce, such as importing reviews from your external system into Dynamics 365 or exporting review from Dynamics 365 using Power Automate. This article explains how to configure service-to-service authentication to securely calling into the Ratings and Reviews service API's. 

##Configure Service-to-Service (S2S) Authentication

To configure service-to-service authentication in Commerce site builder, follow these steps.
	1. Go to Home > Reviews > Settings.
	2. Find the card with the title Service-to-Service (S2S) Authentication and select Manage.

![Dynamics 365 Commerce - Ratings and Review settings](media/Ratings-reviews-settings-service-to-service-authentication.png)
![image](https://user-images.githubusercontent.com/42852473/137647263-63711900-2b90-4f9f-b788-58335b2b65e2.png)

After selecting Manage, a flyout panel will appear on the right side of the screen, for S2S App Entries with the following options.
	1. Add a new S2S App Registration
	2. Edit an existing S2S App Registration (pencil icon)
	3. Remove an existing S2S App Registration (trashcan icon)



 ###Adding a new app registration

First create an application using [Azure Portal](https://portal.azure.com), by following the steps *[Use Azure Active Directory with a custom connector in Power Automate](https://docs.microsoft.com/en-us/connectors/custom-connectors/azure-active-directory-authentication)* to register an app on Azure Active Directory and enable authentication. 

Collect the following IDs from the azure portal to be used in the next steps.
	• Client Application ID
	• Client directory (tenant) ID.

To add an app registration, follow these steps in Commerce site builder.
	1. Select Add a new S2S App Registration
	2. Enter the following required items in the form displayed, using values from your Azure application registration.
		○ Name: The name for your application, for example "Fabrikam App".
		○ Client App ID: The application ID, for example “00000000-0000-0000-0000-000000000000”
		○ Directory (Tenant) ID: The directory ID, for example “00000000-0000-0000-0000-000000000000”
	3. Select Submit. You should now see the name of your application appear in the list.
	4. Close the S2S App Entries panel.
	5. Select Save to save your changes.
 
![Dynamics 365 Commerce - Ratings and Review settings](media/Ratings-reviews-settings-S2S-APP-entry.png)
 
###Editing an existing app registration

To edit an existing app registration, follow these steps.
	1. Select the pencil icon next to the entry you wish to edit.
	2. Update Name, Client App ID, Directory (Tenant) ID.
	3. Select Submit.
	4. Close the S2S App Entries panel.
	5. Select Save to save your changes.
![image](https://user-images.githubusercontent.com/42852473/137647292-e60dc766-471a-406f-975c-4cba8d806ea2.png)

###Removing an existing app registration
To remove an existing app registration, follow these steps.
	1. Select the trashcan icon next to the entry you wish to remove.
	2. The entry will be removed from the list.
	3. Close the S2S App Entries panel.
Select Save to save your changes.![image](https://user-images.githubusercontent.com/42852473/137647294-ff54425c-18c0-429a-a7bf-cde31f47b5b1.png)
