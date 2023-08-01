---
# required metadata

title: Collections coordinator summary
description: This article describes how the Collections coordinator summary feature shows AI-generated text in the Collections coordinator workspace.
author: JodiChristiansen
ms.date: 06/27/2023
ms.topic: conceptual
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2023-06-05
ms.dyn365.ops.version: 10.0.24

---
# Collections coordinator summary

> [!NOTE]
> Some or all of the functionality that's mentioned in this article is available as part of a preview release. The content and the functionality are subject to change.

Enable the **Collections coordinator summary** feature to get an AI-generated summary of a customer's account and revenue in the **Collections coordinator** workspace, and to send AI-generated reminder emails. This feature is powered by Microsoft Azure OpenAI's large language model and is designed to reduce the time that you must spend reviewing collections details for your customers.

This feature has three purposes:

- Provide customer account information.
- Help you make better decisions about your customers.
- Increase efficiency by drafting reminder emails that you can edit and then send to your customers.

## Prerequisites

### Version requirements

Collections coordinator summary requires the latest hotfix on Dynamics 365 Finance version 10.0.34 (10.0.1591.107) and version 10.0.35 (10.0.1627.70) or later.

### Location and language requirements

Collections coordinator summary is currently supported only in the United States. It's available only to users who are configured to use United States English as their language in Finance.

### Role requirements

To complete the configuration procedures in the next section, you must have the following roles:

- The **System administrator** and **System customizer** roles in Power Platform admin center.
- The **System administrator** role in Finance.
- The **Organization Admin** role, so that you can create environments in Microsoft Dynamics Lifecycle Services. Additionally, the **Project owner** or **Environment manager** role must be assigned to you in the **Project security** role field in Lifecycle Services.

## Configure Collections coordinator summary

Follow the procedures in this section to configure Collections coordinator summary.

### Configure Power Platform admin center

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. On the left menu, select **Resources** \> **Dynamics 365 installed apps**.
1. Select **Resources** \> **Dynamics 365 installed apps**.
1. Find **Finance and Operations Virtual entity**. The status should be **Update available**.
1. Select the ellipsis button (**&hellip;**), and then select **Update** on the menu.
1. Accept the terms of service, and then select **Update**.
1. You can check the status of the update. While the update is occurring, the status is **Installing**. After the update is completed, the status is changed to **Installed**.

### Install Copilot

1. In Partner Center, go to the [Copilot in Microsoft Dynamics 365 Finance](https://appsource.microsoft.com/product/dynamics-365/mscrm.d365-financeai-preview?flightCodes=9b882e82e59c4f35a1b0a5368d42ea92) solution.
1. Accept the terms and conditions, and then select **Install**. The Copilot solution is installed in the selected environment.
1. Go to the environment page for the selected environment.
1. Select **Dynamics 365 apps** to check the status of the installation. While the installation is occurring, the status is **Installing**. After the installation is completed, the status is changed to **Installed**.

### Grant Dataverse consent for user impersonation

You must grant explicit consent for Dynamics 365 finance and operations apps to impersonate Dataverse users.

1. In Power Platform admin center, select the Microsoft Power Platform environment where you installed the Copilot solution.
1. Select **Settings** at the top of the page.
1. Expand **Product**, and select **Features**.
1. Find **Finance and Operations in Dataverse**.
1. Set the **Enable finance and operations user impersonation in Dataverse** option to **On**.

> [!NOTE]
> For more information, see [Managed feature settings](/power-platform/admin/settings-features).

### Assign roles to Dataverse users

Users in Dataverse must be assigned the **Finance and Operations AI** role and the **AIB** role.

1. In Power Platform admin center, select the Microsoft Power Platform environment where you installed the Copilot solution.
1. Select **Settings** at the top of the page.
1. Expand **Users and Permissions**, and select **Security roles**.
1. Find the **Finance and Operations AI** role.
1. Use the ellipsis button (**&hellip;**) to add new members to the role.
1. Find the **AIB** role.
1. Use the ellipsis button (**&hellip;**) to add new members to the role.

> [!NOTE]
> For more information, see [Security roles and privileges](/power-platform/admin/security-roles-privileges?wt.mc_id=ppac_inproduct_settings).

### Enable SQL change tracking in Lifecycle Services

1. In Lifecycle Services, find your environment and select Full details.
2. Select the Maintain and then **Enable maintenance mode**.
3. Login to Finance and Operations
4. Go to System administration > Setup > License configuration
5. On the Configuration keys tab, mark **SQL row version change tracking (Preview)**
6. Save changes.
7. In Lifecycle Services, select Maintain and then **Exit Maintenance mode**. 

### Enable Collections coordinator summary

1. In Finance, open the **Feature management** workspace.
1. On the **All** tab, search for and select **(Preview) Collections coordinator summary**.
1. Select **Learn more** to learn more about the AI terms.
1. Select **Enable**.

> [!IMPORTANT]
> The **(Preview) Collections coordinator workspace** feature must also be enabled. This feature makes the **Collections coordinator workspace** available. For more information, see [Collection coordinator workspace](collectionsworkspace.md).
 
## View summary text

As soon as a customer is selected in the **Customer account** field in the **Collections coordinator** workspace, the AI-generated content appears below the data points. Azure OpenAI is used to generate the results, based on data in Finance and the provided prompts. All calculations are done in Finance. The summary is based on the amounts for the selected customer's payment history for the past year, outstanding debt amount, and year-to-date revenue.

## Generate a reminder email

To have AI generate a draft email in the form of a reminder letter, select **Create reminder email**. You receive the following message:

> A reminder email will be created with AI. Make sure AI-generated content is complete, accurate, and appropriate before using. Do you want to create the email?

To return to the **Collections coordinator** workspace without generating an email, select **No**. To generate and open a draft email in your default email service, select **Yes**. Azure OpenAI services incorporates robust filters and safeguards to help prevent offensive, destructive, or abusive content from being created by using this feature.

> [!NOTE]
> The email is generated by using AI and Finance data, and the content is a suggestion. It's your responsibility to review and edit the suggested content to ensure that it's complete, accurate, and appropriate before you send the email.

For additional information, see [Collections coordinator summary: FAQ](collections-coordinator-summary-faq.md).
 
