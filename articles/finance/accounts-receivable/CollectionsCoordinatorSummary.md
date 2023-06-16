---
# required metadata

title: Collections coordinator summary
description: This topic shows how AI-generated text, Collections coordinator summary, displays on the Collections coordinator workspace. 
author: JodiChristiansen
ms.date: 06/04/2023
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

>[!Note] 
>Some or all of the functionality noted in this article is available as part of a preview release. The content and the functionality are subject to change. 

## Overview
Enable the **Collections coordinator summary** feature to get an AI-generated summary of a customer’s account and revenue and use AI-generated reminder emails. This feature is powered by Azure OpenAI’s large language model and has been developed to reduce the time it takes to review collections details for your customers. The goals of this capability are to: 
 - provide customer account information 
 - help make better decisions about your customers 
 - increase efficiency by drafting a reminder email that can be edited and then sent to your customer

## Version requirements
Collections coordinator summary requires the latest hotfix on Dynamics 365 Finance version 10.0.34 and later. 

## Configure Collections coordinator summary
This article describes how to configure **Collections coordinator summary**.

**Collections coordinator summary** is currently supported in the United States. It is only available to users configured to use English-United States in Dynamics 365 Finance. The AI-generated text displays on the **Collections coordinator** workspace.
To complete the following procedures and successfully configure the **Collections coordinator summary**, you must have the following privileges:
 - The **System administrator** and **System customizer** roles in Power Platform admin center
 - The **System administrator** role in Microsoft Dynamics 365 Finance
 - The **Organization Admin** role to create environments in Microsoft Dynamics Lifecycle Services. Additionally, the **Project owner** or **Environment manager** role must be assigned to the user in the **Project security** role field in Lifecycle Services.

## Configure Power Platform admin center
1.	In the Power Platform admin center, select the Microsoft Power Platform environment to install the application. 
2.	Select **Resources** > **Dynamics 365 installed apps**. 
3.	Find **Finance and Operations Virtual entity**. The status should be **Update available**. Select the **...** and **Update**. 
4.	Accept the terms of service and then select **Update**. 
5.	You can check the status of the update. During the update, the status is **Installing**. On completion, the status will change to **Installed**

## Install Copilot 
1. In Partner Center, find the **Copilot in Microsoft Dynamics 365 Finance** solution. 
2. Accept the terms and conditions and select **Install**. The **Copilot in Microsoft Dynamics 365 Finance** will be installed in the selected environment.
3. Go to the environment page for the selected environment. 
4. Select **Dynamics 365 apps** to check the status of the installation. The status is **Installing** and after completion, the status is **Installed**.

## Dataverse consent for user impersonation
Explicit consent must be granted for Dynamics 365 finance and operations to impersonate Dataverse users. 

1. In Power Platform admin center, select the Microsoft Power Platform environment where the above application was installed.
2. Select **Settings** in the top action pane.
3. Expand **Product** and select **Features**. 
4. Find **Finance and Operations in Dataverse**.
5. Set **Enable finance and operations user impersonation in Dataverse** to **On**.  

>[!Note] 
>For more information, see [Managed feature settings](/power-platform/admin/settings-features.md) .

## Dataverse role assignment
Users in Dataverse need to be assigned to the AIB role.

1.	In Power Platform admin center, select the Microsoft Power Platform environment where the above application was installed.
2.	Select **Settings** in the top action pane.
3.	Expand **Users and Permissions**.
4.	Select **Security roles**. 
5.	Find the AIB role
6.	Use the **...** menu to add new members to this role.

>[!Note] 
>For more information, see [Security roles and privileges](/power-platform/admin/security-roles-privileges?wt.mc_id=ppac_inproduct_settings).

## Enable Collections coordinator summary 
To enable the **Collections coordinator summary**, go to:
1. Go to **Feature management** workspace, on the **All** tab. 
2. Enter **(Preview) Collections coordinator summary**. 
3. Select **Learn more** to learn more about the AI terms. 
4. Select **Enable**. 

>[!Note] 
>The **(Preview) Collections coordinator workspace** must also be enabled for this functionality to display this workspace.

## Summary text
The AI-generated content appears below the data points on the **Collections coordinator** workspace as soon as a customer is selected in the **Customer account** field. Azure OpenAI is used to generate the results based on data in Dynamics 365 Finance and the provided prompts. All calculations are done in Dynamics 365 finance. The summary is based on the amounts for a customer’s payment history for the past year, outstanding debt amount and revenue year-to-date.

## Create reminder email
Select **Create reminder email** to have an AI-generated email drafted in the format of a reminder letter. When selected, a dialog box displays the message **"A reminder email will be created with AI. Make sure AI-generated content is complete, accurate, and appropriate before using. Do you want to create the email?”**. Select **No** to close the dialog and return to the workspace. Select **Yes** to open your default email service with an email draft. Azure OpenAI services incorporates robust filters and safeguards to help prevent the generation of offensive, destructive or abusive content and will not be created using this feature.

>[!Note] 
>The email is created using AI and Dynamics 365 Finance data and is a suggestion. It is your responsibility to review and edit the suggested content to make sure it’s complete, accurate and appropriate before sending your email.  






