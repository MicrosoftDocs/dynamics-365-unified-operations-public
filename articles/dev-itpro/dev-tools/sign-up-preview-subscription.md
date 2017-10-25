---
# required metadata

title: Sign up for a preview subscription
description: This topic explains how to subscribe to the preview/partner offer and deploy an environment.
author: RobinARH
manager: AnnBe
ms.date: 10/11/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations, 
# ms.tgt_pltfrm: 
ms.custom: 13211
ms.assetid: bd976311-f6e3-418b-a6c6-49bb568de130
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Sign up for a preview subscription

[!include[banner](../includes/banner.md)]

This topic explains how to subscribe to the preview/partner offer and deploy an environment. The subscription that you create gives you a Microsoft Online Services test tenant and a Microsoft Dynamics Lifecycle Services (LCS) project where you can deploy an environment. This topic will also help you set up additional users in your Microsoft Online Services tenant and gain experience with service administration capabilities. Here are the skills that you will learn:

- Subscribe, and create a new Microsoft Online test tenant.
- Navigate to LCS projects.
- Use various features of LCS.
- Add users to Microsoft Azure Active Directory (Azure AD) and the client.
- View resources in your subscription email.

## Key terms
- **Microsoft Online Services tenant** – A tenant is the group of all subscriptions and users for your organization. The tenant is created at the same time as your first subscription in Microsoft Online Services.
- **Subscription** – A subscription gives you an online cloud environment and experience. It also lets you see how customizations that you develop can be deployed to the cloud.
- **Microsoft Azure Active Directory** – The cloud environment includes Azure AD. Azure AD helps you manage users, groups, security roles, and licenses for online applications, much as you manage them for on-premise environments.
- **Users** – Users of the services that your organization has subscribed to are managed in Azure AD. Any users in your tenant can be added and assigned to security roles.
- **Developers and administrators** – Developers and administrators are users who also have access to LCS that lets them manage projects and environments. These users are also end users.
- **Organizational account** – Users receive Azure AD credentials. These credentials are separate from other desktop or corporate credentials. The Azure AD credentials are used to sign in to Microsoft Office 365 and other Microsoft cloud services. Users sign in by using their organizational account.

    > [!IMPORTANT]
    > For this release, we ask that you not use any existing credentials that are associated with other online services, such as Office 365 or Microsoft Dynamics CRM Online.

- **Microsoft account** – Microsoft accounts were formerly known as Passport accounts or Windows Live ID accounts. Currently, Microsoft accounts can't be used with Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, Microsoft Dynamics 365 for Retail, or other Microsoft Online Services. However, Microsoft accounts are still required for Microsoft Connect and other Microsoft Business Solutions sites, such as CustomerSource, PartnerSource, Information Source, and Microsoft Dynamics Community. You will continue to use your Microsoft account to access these services.
- **Microsoft Office 365 admin center** – Office 365 admin center is the subscription management portal that Office 365 provides for administrators. Office 365 admin center is used to provide management functions for users and subscriptions.
- **Environments** – You can deploy as many single instances of a virtual machine (VM) as you require. We call these instances *environments*.

## Prerequisites
1. You've received an email that invites you to participate in the preview.
2. If your company has an organizational account with Microsoft Online Services, and you're signed in, you must sign out before you continue. Alternatively, you can use **InPrivate Browsing** mode.
3. If you aren't sure whether you're signed in, delete your browser cookies, and then close your browser before you continue.

## Subscribe
> [!IMPORTANT]
> Only one person (tenant administrator) in an organization must perform this task. If you aren't the person who is subscribing to this release, wait until your organization has been signed up and you've received your user credentials. Then continue with the procedure.

1. Finance and Operations and Retail are available only to existing Microsoft Dynamics 365 channel partners and customers who are currently enrolled in the Business Ready Enhancement Plan (BREP) service plan. Existing customers can find details about how to access trials on [CustomerSource](https://mbs.microsoft.com/customersource/global/AX/news-events/news/Microsoft_Dynamics_AX_Public_Preview). Partners can find the details on [PartnerSource](https://mbs.microsoft.com/partnersource/global/news-events/news/Microsoft_Dynamics_AX_Public_Preview).
2. On the **Account setup** page, in the **Country or region** field, select the country or region.
3. Follow the wizard and prompts to complete the sign-up, until you reach the last step.

    [![You're ready to go](./media/wizardprompt.png)](./media/wizardprompt.png)

## Start a new project in LCS
To use LCS to manage your environments, you must create a new project.

1. Go to <https://lcs.dynamics.com/Logon/Index>.
2. Select **Sign in**.
3. Sign in by using the account that you used to subscribe.
4. Select the plus sign (**+**) to create a new project.

    [![Create a project](./media/11-1024x473.jpg)](./media/11.jpg)

5. Select the project type.
6. Enter the project information, and then select **Create**.

    If you plan to evaluate Retail, be sure to select **Microsoft Dynamics 365 for Retail** in the **Product name** field.

    The new project for managing your instance is created.

    ![New project](./media/projectworkspace.jpg)

## Add users to LCS
You're already set up as a user of your LCS project. If you've also added other Office 365 users, you must add them to this project. Other administrators and developers will then be able to deploy their own environments. These LCS users are team members who will actively work on the implementation. Don't confuse them with end users. Start on the project page in LCS.

1. Scroll to the right, and then, in the **More tools** section, select the **Project users** tile.
2. In the upper left, select the plus sign (**+**) to add a new user.
3. In the **Email** field, enter the email address of the user that you're adding. This email address should be the Office 365 organization email address that you created earlier.
4. In the **Project role** field, select **Project Owner**.
5. Select **Invite**.
6. Repeat steps 2 through 5 for all users in your organization.

## Deploy environments
Environments should be deployed to an existing Azure subscription.

> [!NOTE]
> Each developer of an environment must deploy his or her own system to Azure. However, only the first project user must set up the Azure subscription for deployment.

You can create environments in two ways:

- Deploy to Microsoft cloud services (Azure).
- Download a local virtual hard disk (VHD).

Start on the project page in LCS.

1. In the **Environments** section, select the plus sign (**+**). The **Microsoft Azure setup** dialog box appears.
2. Enter your Azure subscription ID. You can find your Azure subscription ID in Azure Management Portal (<https://manage.windowsazure.com/>), under **Settings** in the lower left.
3. Select **Next**.
4. Download the Azure Management Certificate to a local folder on your computer, and then upload it to Azure Management Portal by going to **Settings** &gt; **Management Certificates**. This certificate will enable LCS to communicate with Azure on your behalf.
5. Return to LCS, and select **Next**.
6. Select the Azure region to deploy in. The **West US** region will have the fastest deployments, but it's important that you select a data center that is close to where you plan to use this system.
7. Select **Connect**.
8. In the list of available topologies, select the topology to deploy. You can select either the **Download** link to download the VHD or **Next** to deploy on Azure. Azure is the preferred path.
9. Enter the name of the environment.
10. Read the pricing and licensing terms, and then select the check box to indicate that you understand them.
11. Select **Next**.
12. Confirm the details, and then select **Deploy**.

    > [!NOTE]
    > Developers and administrators who will use their own environments must sign in and repeat these steps.
    
    After you deploy your environment, it's available in the **Environments** section.

    [![New environment in the Environments section](./media/pic7.jpg)](./media/pic7.jpg)

13. Select the environment to view details about the deployment status. The first deployment will require a few hours, but each subsequent deployment will be much faster.
14. When the deployment status changes to **Deployed**, select **Login** to connect to the client, or select the name of the VM to connect to the development machine by using Remote Desktop. After the deployment is completed, you can find the base URL and the information that you require to connect to the environment via Remote Desktop.

## Use the features of LCS
LCS is the starting point for performing online administrative activities. Here are some of these activities:

- Deploy VMs on Azure.
- Access materials.
- Access downloads of tools and resources.

### Explore the LCS project
1. Review the methodology, and complete the tasks and phases as you progress through the life cycle.

    [![Phases and tasks](./media/pic8.jpg)](./media/pic8.jpg)[](./media/methodologyreview.png)
    
    The phases and task information lets you view tools and resources that are available throughout your enterprise resource planning (ERP) experience.

2. Scroll to the right, and review the tiles.

    [![Tiles](./media/pic9.jpg)](./media/pic9.jpg)

    The available tiles include various tools and services in LCS. They also include the following additional tiles:

    - **My subscription** – The Office 365 subscription management portal is where you can view and work with your online subscriptions. By selecting **User and Groups** in the left navigation section of the page, you can also manage your online users.

        > [!NOTE]
        > To access the page, you must be a member of the **Global Administrator** role for your organization's Microsoft Online Services tenant.

    - **Feedback and bugs** – This tile opens the **General Feedback** page in Microsoft Connect. Use this page to record bugs, and to design change requests, feature requests, and suggestions.
    - **Office 365 users** – This tile opens the **Users and groups** page in Office 365 admin center. You can add, update, and remove users, reset passwords, and assign licenses for other services.

        > [!NOTE]
        > To access the page, you must be a member of the **Global Administrator** role for your organization's Microsoft Online Services tenant. The installing user is always a global administrator, but other users must be added to this role.

        [![Active users in Office 365 admin center](./media/activeusersadmin.png)](./media/activeusersadmin.png)
