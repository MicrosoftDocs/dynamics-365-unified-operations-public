---
# required metadata

title: Collections coordinator summary
description: This topic shows how AI-generated text, Collections coordinator summary, displays on the Collections coordinator workspace. 
author: JodiChristiansen
ms.date: 06/04/2023
ms.topic: article
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

> [Note] Some or all of the functionality noted in this article is available as part of a preview release. The content and the functionality are subject to change. 

## Overview
Enable the Collections coordinator summary feature to see an AI-generated summary of a customer’s account and revenue and use AI-generated reminder emails. This feature is powered by Azure Open AI’s large language model and has been specifically developed to reduce the time it takes to review collections details for your customers. The goal of this capability is to provide you with customer account information to help you make better decisions about your customers while increasing your efficiency by drafting a reminder email that can be edited and then sent to your customer

## Version requirements
Collections coordinator summary requires the latest hotfix on Dynamics 365 Finance version 10.0.34 and later. 

## Configure Collections coordinator summary
This article describes how to configure Collections coordinator summary.

Collections coordinator summary is currently supported in the USA. It is only available to users configured to use English-United States in Dynamics 365 Finance. The AI-generated text displays on the Collections coordinator workspace.
To complete the following procedures and successfully configure the Collections coordinator summary, you must have the following privileges:
 - The **System Administrator** and **System Customizer** roles in Power Platform admin center
 - The **System administrator** role in Microsoft Dynamics 365 Finance
 - The **Organization Admin** role to create environments in Microsoft Dynamics Lifecycle Services. Additionally, the **Project owner** or **Environment manager** role must be assigned to the user in the **Project security** role field in Lifecycle Services.

## Required configurations in Power Platform Admin Center
1.	In Power Platform Admin Center, select the Microsoft Power Platform environment to install the application into. 
2.	Select Resources and then Dynamics 365 installed apps. 
3.	Find the **Finance and Operations Virtual entity**, the status should say Update available. Select the ... and choose Update. Accept the terms of service and then select Update. 
4.	You can check the status of the update. During the update the status is **Installing**. On completion, the status will change to **Installed**

## Install the Dataverse app Copilot in Microsoft Dynamics 365 Finance
1. In Partner Center find the **Copilot in Microsoft Dynamics 365 Finance** solution. 
2. Accept the terms and conditions and then select Install. This will start the installation of **Copilot in Microsoft Dynamics 365 Finance** in the selected environment.
3.Go to the environment page for the select environment, click **Dynamics 365 apps** to check the status of the installation. During installation the status is **Installing**. On completion, the status will change to **Installed**.

## Dataverse consent for user impersonation
Explicit consent must be greanted for Finance and Operations to impersonate Dataverse users. 

1. In Power Platform admin center select the Microsoft Power Platform environment where the above application was installed.
2. Select **Settings** in the top action pane.
3. Expand **Product** and then select **Features**. 
4. Find the **Finance and Operations in Dataverse**
5. Set **Enable Finance and Operations User Impersonation in Dataverse** to **On**.  

> [Note] For more information see Managed feature settings - Power Platform.

## Enable Collections coordinator summary in Dynamics 365 Finance
Collections coordinator summary is enabled through **Feature management**. In the Feature management workspace, on the **All** tab, enter **(Preview) Collections coordinator summary**. Select the “view terms” link to learn more about the AI terms. Select **Enable**. 

> [Note] The **(Preview) Collections coordinator workspace** must also be enabled for this functionality to work because it displays on this workspace.

## Summary text
The AI-generated content appears below the data points on the Collections coordinator workspace as soon as a customer is selected in the Customer account field. Azure OpenAI is used to generate the results based on data in Dynamics 365 Finance and the provided prompts. All calculations are done through Dynamics 365 Finance code. The summary is based on the amounts for a customer’s payment history for the past year, outstanding debt amount and revenue year-to-date.

## Create reminder email
Select **Create reminder email** to have an AI-generated email drafated in the format of a reminder letter. When selected, A dialog box displays the message “A reminder email will be created with AI. Make sure AI-generated content is complete, accurate, and appropriate before using. Do you want to create the email?” Select **No** to close the dialog and return to the workspace. Select **Yes** to open your default email service with an email draft.  Azure OpenAI services incorporates robust filters and safeguards to help prevent the generation of offensive, destructive or abusive content and will not be created using this feature.

> [Note] The email is created using AI and Dynamics 365 Finance data and is a suggestion. It is your responsibility to review and edit the suggested content to make sure it’s accurate and appropriate before sending your email.  

## Collections coordinator summary: Frequently asked questions
What is Collections coordinator summary?
 - Collections coordinator summary is AI-generated text that displays on the Collections coordinator workspace and generates a reminder letter using AI-generated text. This feature uses customer data such as aged balances, overdue invoices, and payment history as input. The output is a summary of overdue amounts, overdue balances and payment history displayed on the workspace. The second form of output is an email that is generated by AI in the format of a collection letter. 

What can Collections coordinator summary do?
 - This feature is powered by Azure Open AIs large language model using the customer name and Finance data as input. The summary provides the collections coordinator with information on the payment history and revenue. The email provides an email that can be sent to the customer to remind them of an overdue balance. 

What are the Collections coordinator summary intended uses? 
 - The intended uses are summarizing Dynamics 365 Finance data and creating a draft email based on the summary in a reminder letter format. 

How was Collections coordinator summary evaluated? What metrics are used to measure performance? 
 - The AI-generated summary was evaluated based on the existing Dynamics 365 Finance data. All calculations are performed in Dynamics 365 Finance, not through Azure OpenAI. All emails were based on Dynamics 365 Finance data and verified against the data in the testing process. 

What are the limitations of Collections coordinator summary? How can users minimize the impact of Collections coordinator summary’s limitations when using the system? 
 - If the same customer exists in multiple legal entities in Dynamics 365 Finance, the data on the workspace is only returned based on the legal entity that the Collections coordinator is using. It may not give you the full picture of the customer account across all entities. 
 
What operational factors and settings allow for effective and responsible use of Collections coordinator summary. 
 - All processing of data is configured using the prompt inside Dynamics 365 Finance and cannot be changed or modified. All data that is AI-generated comes from the customer data inside Dynamics 365 Finance. There is no text that can be entered by the end user and processed through Azure OpenAI. Only the customer name and Finance data, found directly in Finance, are processed through Azure OpenAI and returned as a summary or used to generate a draft email. 




