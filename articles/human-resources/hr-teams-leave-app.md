---
# required metadata

title: Manage leave requests in Teams
description: This topic shows how to request time off in the Dynamics 365 Human Resources app in Microsoft Teams.
author: andreabichsel
manager: AnnBe
ms.date: 05/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: LeaveAbsenceWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-05-18
ms.dyn365.ops.version: Human Resources

---

# Manage leave requests in Teams

[!include [banner](includes/preview-feature.md)]

The Microsoft Dynamics 365 Human Resources app in Microsoft Teams lets you quickly request time off and view your time-off balance information right in Microsoft Teams. You can interact with a bot to request information. The **Time off** tab provides more detailed information.

## Install the app

You can find the Human Resources app in the Teams store.

1. In Microsoft Teams, select the ellipses.

   ![Human Resources Teams leave app ellipses](./media/hr-teams-leave-app-ellipses.png)
 
2. Search for Dynamics 365 Human Resources, and then select the **Human Resources** tile.

   ![Human Resources Teams leave app HR tile](./media/hr-teams-leave-app-human-resources-tile.png)

3. Select the **Add** button to install the app.

   ![Human Resources Teams leave app install](./media/hr-teams-leave-app-in-store.png)

If the app doesn't automatically sign you in, select the **Settings** tab to sign in.

![Human Resources Teams leave app Settings tab](./media/hr-teams-leave-app-settings-tab.png)

> [!NOTE]
> If you don’t see a sign-in dialog box, check your browser settings to allow pop-ups. 

If you have access to more than one instance of Human Resources, you can select which environment you want to connect to in the **Settings** tab.

> [!WARNING]
> The app doesn't currently support the System Administrator security role, and will display an error message if you sign in with a System Administrator account. To sign in with a different account, on the **Settings** tab, select the **Switch accounts** button, and then sign in with a user account that doesn’t have System Administrator privileges.
 
## Use the bot

After the app installs, a welcome message appears, letting you know the types of actions the bot can take on your behalf.

![Human Resources Teams leave app bot welcome message](./media/hr-teams-leave-app-bot.png)
 
> [!NOTE]
> When first interacting with the bot, you might need to sign in. If you don’t see a sign-in dialog box, check your browser settings to allow pop-ups.

You can ask the bot to:

- Show time-off balance information for each leave type you're enrolled in.

   ![Human Resources Teams leave app show balances](./media/hr-teams-leave-app-bot-balances.png)
 
- Show additional details about a specific leave type.

   ![Human Resources Teams leave app show details](./media/hr-teams-leave-app-bot-details.png)

- Start a leave request for you.

   ![Human Resources Teams leave app request leave](./media/hr-teams-leave-app-bot-request.png)
 
After you start a leave request, you can adjust the days right within the card, or you can select **Edit details** to add additional information to your request.

![Human Resources Teams leave app edit request](./media/hr-teams-leave-app-bot-edit.png)
 
When you're done entering information, type **Submit** to submit it for approval. You can also type **Save as draft** to come back to it later.

![Human Resources Teams leave app submit request](./media/hr-teams-leave-app-bot-submit.png)

## Manage your leave in Teams

The **Time off** tab allows you to view:

- Balance information for each leave type you're enrolled in

- Upcoming leave requests

- Time-off requests

- Draft leave requests

![Human Resources Teams leave app Time off tab](./media/hr-teams-leave-app-timeoff-tab.png)
 
### Create a new request

1. To create a new leave request, select **New request**.

   ![Human Resources Teams leave app New request](./media/hr-teams-leave-app-timeoff-tab-new.png)

2. Enter the day or days you want to take off, and then select **Add**.

   ![Human Resources Teams leave app add time off](./media/hr-teams-leave-app-timeoff-tab-add.png)

3. If applicable, enter a reason code. Also enter any comments and add any attachments.

4. When you're done entering information, type **Submit** to submit it for approval. You can also type **Save as draft** to come back to it later.

### Manage draft requests

1. Select the **Drafts** tab.

   ![Human Resources Teams leave app Drafts tab](./media/hr-teams-leave-app-drafts-tab.png)

2. Select the pencil to edit the request, or select the trash can to delete the request.

3. Make any necessary changes. When you're done entering information, type **Submit** to submit it for approval. You can also select **Save as draft** to come back to it later.

   ![Human Resources Teams leave app edit draft](./media/hr-teams-leave-app-drafts-edit.png)
   
## Privacy notice

With the Dynamics 365 Human Resources bot in Microsoft Teams, the user’s text inputs are analyzed for understanding the underlying query/intent. The user’s input such as “Search account Contoso” is routed to one of Microsoft’s Cognitive Service called Language Understanding Intelligent Service (LUIS). Read more about LUIS [here](https://www.luis.ai/). The LUIS service disambiguates or understands the intent of user input (in this case, the intent is to find information) and the target entity (in this case, the intended entity is an account named Contoso). This information is then passed on to Microsoft’s [Azure bot framework](https://azure.microsoft.com/services/bot-service/) which interacts with data from Dynamics 365 Human Resources and retrieves the desired information for the user query. 

By installing and allowing access to use of the bot, you agree to allow the LUIS service and Azure bot framework to process the intent behind the input,  which results in an enhanced conversational user experience. The LUIS service and Azure bot framework may have varying levels of compliance compared to Dynamics 365 Human Resources. While the LUIS service has access to only the user queries and is not designed to be connected to the user’s Dynamics 365 Human Resources data or account, a user of the Dynamics 365 Human Resources bot could voluntarily enter a query containing Customer Data, Personal Data, or other data and such query content could get sent to the LUIS service and the Azure bot framework. 

The content of user’s queries and messages is retained in LUIS system for a maximum of 30 days, is encrypted at rest, and is not used for training or service improvement. Read more about Cognitive Services [here](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/). 

To manage admin settings for apps in Microsoft Teams, go to the [Microsoft Teams admin center](https://admin.teams.microsoft.com/). 

## See also

[Download and install Microsoft Teams](https://support.office.com/article/download-and-install-microsoft-teams-422bf3aa-9ae8-46f1-83a2-e65720e1a34d)</br>
[Microsoft Teams help center](https://support.office.com/teams)</br>
[Human Resources app in Teams](hr-admin-teams-leave-app.md)
