---
# required metadata

title: Commerce Chat with Omnichannel for Customer Service module
description: This article describes the Commerce Chat with Omnichannel for Customer Service module in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 08/12/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2022-07-20
---

# Commerce Chat with Omnichannel for Customer Service module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes the Commerce Chat with Omnichannel for Customer Service module in Microsoft Dynamics 365 Commerce.

Starting with the Commerce version 10.0.29 release, a new *Commerce Chat with Omnichannel for Customer Service* module has been added to the Commerce module library. With this chat module, Dynamics 365 Commerce empowers e-commerce customers with the chat capabilities of Dynamics 365 Omnichannel for Customer Service. Omnichannel for Customer Service includes live agent support to help address customer queries, provide customer service, and facilitate sales for Commerce customers. 

The Commerce Chat feature enables retailers to:

- Increase personalized engagement with their customers that can result in improved customer retention.
- Augment customer service with integration of human agent and self-service chatbots.
- Garner agent experience with real-time customer profile, order, and purchasing data that drives operational improvements and engagement.
- Improve overall customer satisfaction which can lead to an increase in sales.
 
The following capabilities are available as part of the Commerce Chat feature:

 - Commerce Chat with Omnichannel for Customer Service
 - Addition of Commerce Call Center as an application tab to the agent experience in Dynamics 365 Omnichannel for Customer Service.

## Prerequisites for Omnichannel for Customer Service 

As a prerequisite, you must configure chat in the Omnichannel for Customer Service Administration module and obtain some of the parameters to configure the Commerce chat experience. For instructions, see [Configure a chat channel](/dynamics365/customer-service/set-up-chat-widget).

Once you've configured chat within the Omnichannel for Customer Service Administration module, you'll obtain a script similar to that in the example shown below.  

`<script id="Microsoft_Omnichannel_LCWidget" src="https://oc-cdn-ocprod.azureedge.net/livechatwidget/scripts/LiveChatBootstrapper.js" data-app-id="xxxx-xxx-4be7-bcd5-1d118ecffe1f" data-org-id="5a0e73c0-xxxx-xxxxx-xxx- 76df135f375d" data-org-url="https://xxsxxxxssdb348f-crm.omnichannelengagementhub.com"></script>`

Copy the script you obtained for later use because the script values are required to configure the chat module.

### Commerce Chat with Omnichannel for Customer Service mandatory fields

The Omnichannel for Customer Service Administration module script values listed in the following table are required to configure the Commerce Chat with Omnichannel for Customer Service module.

| Module property| Description  |
| ------------- |--------------|
| Script source | From the chat widget script source, locate **src** and use its value for this property. |
| Data application ID      | From the chat widget script source, locate **data-app-id** and use its value for this property. |
| Data organization ID      | From the chat widget script source, locate **data-org-id** and use its value for this property. |
| Data organization URL     | From the chat widget script source, locate **data-org-url** and use its value for this property. |

## Configure the Commerce chat experience for your e-commerce site 

One of the recommended approaches to implementing the chat experience for your e-commerce site is to add the chat module to the shared header fragment that is used on your e-commerce site pages. 

To add the chat module to your site's header fragment in Commerce site builder, follow these steps.

1. In site builder for your site, go to **Fragments**.
1. Select **+New**.
1. In the **Select a fragment** dialog box, select the **Commerce Chat with Omnichannel for Customer Service** module, enter a name for the fragment, and then select **OK**.
1. In the outline view, select the **Msdyn365 cs chat connector** slot. 
1. In the **Chat properties** properties pane on the right, do the following:
    1. For **Script source**, enter the script **src** value from the Omnichannel for Customer Service script you obtained above.
    1. For **Data application id**, enter the **data-app-id** value from the Omnichannel for Customer Service script you obtained above.
    1. For **Script source**, enter the **data-org-id** value from the Omnichannel for Customer Service script you obtained above.
    1. For **Script source**, enter the **data-org-url** value from the Omnichannel for Customer Service script you obtained above.
    ![Creating a Commerce Chat module fragment in Commerce site builder](media/Commerce-chat-creating-new-fragment.png)
1. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish** to publish it.
1. Go to **Fragments** and open the header fragment for your site. 
1. In the **Default container** slot, select the ellipsis (**...**), and then select **Add fragment**.
1. In the **Select modules** dialog box, select the chat fragment you created above, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish** to publish it.

## Add Commerce headquarters as an application tab for Omnichannel for Customer Service

Adding Commerce headquarters as an application tab for Omnichannel for Customer Service enables live agents using the Omnichannel for Customer Service agent experience user interface to easily access the Dynamics 365 Commerce Customer Service module with contextual information for the customer along with their sales orders information. It also enables customer service agents to place new orders, initiate returns, and verify order status information. 

### Create a new application tab that loads Commerce headquarters in an iFrame module 

To create a new application tab that loads Commerce headquarters in an iFrame module, follow these steps.

1. Go to the [Power Apps Maker Portal](https://make.powerapps.com). 
1. In the navigation pane on the left, select **Apps**.
1. In **Customer Service admin center**, go to **Agent experience \>  Workspaces**.
1. Select **Manage** for **Application tab templates**. 
1. Create a new application tab of type **Third-party website** by following the instructions at [Manage application tab templates](/dynamics365/app-profile-manager/application-tab-templates?tabs=customerserviceadmincenter).
1. Under **Parameters**,  for the **Value** field of the **url** parameter, enter the following URL, where `<YourOrganizationHeadquartersURL>` and `<LegalEntityname>` are replaced with the appropriate values. Omnichannel customer service reads **{AccountNumber}** from the chat context, so leave **{AccountNumber}** as is.

    `https://<YourOrganizationHeadquartersURL>/?mi=MCRCustomerService&cmp=<LegalEntityName>&embedded=true&customerId={AccountNumber}`

1. Leave the **Value** field of the **data** parameter empty.

![Dynamics 365 Omnichannel Customer Service - Application tab creation](media/OC-CS-Admin-Application-Tab-Parameters.png)

## Enable a new application tab for customer agents in Dynamics 365 Omnichannel for Customer Service

To enable a new application tab for customer agents in Dynamics 365 Omnichannel for Customer Service, follow these steps.
	
1. Go to the [Power Apps Maker Portal](https://make.powerapps.com).
1. In the **Customer Service admin center**, go to **Customer support \> Workstreams**.
1. Open the workstream you've created for your agents, and then under **Advanced settings**, select **Sessions default**. 
1. Under **Application Tabs**, select **Add Existing Application Tab**, and then add the new application tab you've created above. This step will ensure that when agent receives an incoming chat call from your e-commerce website, an application tab that loads Commerce headquarters will appear in an iFrame module.  

## Add context variables in Dynamics 365 Omnichannel for Customer Service

To add context variables in Dynamics 365 Omnichannel for Customer Service, follow these steps.

1. Go to the [Power Apps Maker Portal](https://make.powerapps.com).
1. In **Customer Service admin center**, go to **Customer support \>  Workstreams**.
1. Open the workstream you've created for your agents, and then under **Advanced settings**, go to the **Context variable** section. 
1. Select **Edit**, and then add **AccountNumber** as a context variable of type **text**. This variable will help Commerce headquarters load customer information with matching account numbers. 

> [!NOTE] 
> In addition to the **AccountNumber** context variable, if you want to read the emails and names of signed-in users from an e-commerce channel you can add **Email** and **Name** as context variables of type **text**. 





