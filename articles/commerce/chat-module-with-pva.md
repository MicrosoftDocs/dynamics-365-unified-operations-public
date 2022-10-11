---
# required metadata

title: Commerce Chat for online shoppers with Microsoft Power Virtual Agents
description: This article describes the commerce chat feature for online shoppers that integrates Microsoft Dynamics 365 Commerce with Microsoft Power Virtual Agents.
author: gvrmohanreddy
ms.date: 10/11/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2022-09-07

---

# Dynamics 365 Commerce & Microsoft Power Virtual Agents 

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes the commerce chat feature for online shoppers that integrates Microsoft Dynamics 365 Commerce with Microsoft Power Virtual Agents.

Commerce Chat empowers Dynamics 365 e-Commerce customers to use Power Virtual Agents chatbot capabilities to address customer queries.

> [!NOTE] 
> To understand differences between Omnichannel for Customer Service and Power Virtual Agents, see [Commerce chat modules overview](/commerce-chat-modules-overview.md).

Commerce Chat with Power Virtual Agent feature enables businesses to

- Increase personalized engagement with their consumers and better retention.
- Increase customer service with integration of self-service chatbots
- Increase overall customer satisfaction thus increase in sales.
 
This feature provides **Commerce Chat with Power Virtual Agents** module part of the e-Commerce module library.

## Prerequisites for Power Virtual Agents

As a prerequisite, you must create a Power Virtual Agents chatbot for web and obtain some of the parameters to configure the Commerce chat experience. For instructions, see [Create a power virtual agent bot](/power-virtual-agents/authoring-first-bot).

After you configure the chatbot, copy the **Bot ID** and **Tenant ID** values. For information on how to copy these values, see [Retrieve your Power Virtual Agents bot parameters](/power-virtual-agents/publication-connect-bot-to-custom-application#retrieve-your-power-virtual-agents-bot-parameters) .

## Configure your e-commerce site 

Starting from Dynamics 365 Commerce 10.0.30 release, a new module called **Commerce Chat with Power Virtual Agents** is added to module library. 

One recommended way to implement the chat experience for your e-commerce site is to add the  **Commerce Chat with Power Virtual Agents** module to the shared header fragment that is used on your e-commerce site pages.

To add the chat module to your site's header fragment in Commerce site builder, follow these steps.

1. In site builder for your site, go to **Fragments**.
1. Select **New**.
1. In the **Select a fragment** dialog box, select the **Commerce Chat with Power Virtual Agents** module, enter a name for the fragment, and then select **OK**.
1. In the outline view, select the **Msdyn365 pva chat connector** slot.
1. In the **properties** pane on the right, follow these steps:
    1. In the Bot framework webchat CDN URL field, leave the default value (for example, `https://cdn.botframework.com/botframework-webchat/latest/webchat.js`).
    1. In the PVA directline token generate URL field, leave the default value (for example, `https://powerva.microsoft.com/api/botmanagement/v1/directline/directlinetoken`).
    1. In the PVA bot ID field, the PVA bot id value that you obtained from the **prerequisites for Power Virtual Agents** step above.
    1. In the PVA tenant ID field, enter the data-org-url value that you obtained from the **prerequisites for Power Virtual Agents** step above.
1. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish** to publish it.
1. Go to **Fragments**, and open the header fragment for your site.
1. In the **Default container** slot, select the ellipsis (**...**), and then select **Add fragment**.
1. In the **Select modules** dialog box, select the chat fragment that you created earlier, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish** to publish it.

## Proactive chat parameters

For a complete list of proactive chat configuration parameters, see [Proactive chat parameters](/chat-modules-proactive-chat-properties.md).

<!--![Dynamics 365 Commerce Site Builder - Commerce Chat with PVA](media/Commerce-chat-with-pva-creating-new-fragment.png)-->

> [!NOTE] 
> Currently, Power Virtual Agents doesn't support Azure Active Directory business-to-consumer (B2C) authentication. Only anonymous Retail Cloud Scale Unit (RCSU) calls (for example, for store hours) get product availability or calling any other anonymous API's are supported. Calling authenticated API's via Power Virtual Agents chatbot will require explicit sign-in. 
