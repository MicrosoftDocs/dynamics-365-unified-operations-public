---
# required metadata

title: Human Resources app in Teams
description: This topic introduces the Microsoft Dynamics 365 Human Resources app in Microsoft Teams.
author: andreabichsel
manager: AnnBe
ms.date: 05/04/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
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
ms.search.validFrom: 2020-05-04
ms.dyn365.ops.version: Human Resources

---

# Human Resources app in Teams

[!include [banner](includes/preview-feature.md)]

The Microsoft Dynamics 365 Human Resources app in Microsoft Teams lets employees quickly request time off and view their time-off balance information in Microsoft Teams. Employees can interact with a bot to request information. The **Time off** tab provides more detailed information.

![Human Resources Teams leaves app bot](./media/hr-admin-teams-leave-app-bot.png)

![Human Resources Teams leave app Time off tab](./media/hr-teams-leave-app-timeoff-tab.png)

## Install and setup

You can find the Human Resources app in the Teams store. For information about installing the Teams app, see [Manage leave requests in Teams](hr-teams-leave-app.md).

For information about managing app permissions in Teams, see [Manage app permission policies in Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-app-permission-policies).

## Known issues

| Issue | Status |
| --- | --- |
| The balance is incorrect when submitting time off for a future date. | Forecasting isn't yet available. The balance displays for the current date. |
| When reducing the number of hours taken in an existing request, the **Remaining balance** goes down instead of up. | We'll address this known issue in the future. The display is incorrect, but the correct amounts are adjusted upon submission. |
| The date picker isn't accessible in dark mode. | We'll add dark mode support in the future. |
| Two **Upcoming time off** cards display for the same dates. | The cards represent individual submissions. We'll continue to take feedback and make adjustments. |
| Unable to cancel an **In review** request. | This functionality isn't currently supported and will be added in a future release. |

## Privacy information

The Human Resources app in Teams uses the Language Understanding Intelligent Service (LUIS) in Azure Cognitive Services. The app also uses Microsoft’s Azure Bot Service. The following links provide more information about these services and privacy.

| For more information about | See |
| --- | --- |
| LUIS| [Language Understanding (LUIS)](https://www.luis.ai/home) |
| User privacy with LUIS | [Export and delete your customer data in Language Understanding (LUIS) in Cognitive Services](https://docs.microsoft.com/azure/cognitive-services/luis/luis-user-privacy) |
| Data storage in LUIS | [Data storage and removal in Language Understanding (LUIS) Cognitive Services](https://docs.microsoft.com/azure/cognitive-services/luis/luis-concept-data-storage) | 
| Azure Bot Service | [Azure Bot Service]() | 
| Azure Cognitive Services | [Cognitive Services](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)<br>[Language Understanding](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/) |
| Azure Cognitive Services privacy | [Azure Cognitive Services](https://azure.microsoft.com/support/legal/cognitive-services-compliance-and-privacy/) |
| Microsoft privacy | [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement) |
| Teams privacy	| [For IT professionals: Privacy and security in Microsoft Teams](https://www.microsoft.com/microsoft-365/blog/2020/04/06/it-professionals-privacy-security-microsoft-teams/) |

The LUIS service can only access user queries and isn't designed to be connected to the user’s Dynamics data or account. However, a user of the Human Resources bot could voluntarily enter a query containing personal or other data, and that query content could be sent to LUIS and the Azure Bot Service.

To manage admin settings for apps in Microsoft Teams, go to the Microsoft 365 admin center and open **Settings > Services & add-ins**, and then select **Microsoft Teams**. If you're signed in as an Office 365 admin, you can access these controls in the [Office 365 admin portal](https://admin.microsoft.com/adminportal/home#/Settings/ServicesAndAddIns). You can also uninstall from the admin portal.

## Additional resources

[Manage leave requests in Teams](hr-teams-leave-app.md)

