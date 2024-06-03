---
# required metadata

title: Workflow history summary  
description: This topic describes the copilot capabilities on the Workflow history page.
author: JodiChristiansen
ms.date: 06/03/2024
ms.topic: article


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
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24


---
# Workflow history summary

This article describes how to enable the optional Summary by Copilot on any **Workflow history** page in Microsoft Dynamics 365 Finance and Microsoft Dynamics 365 Supply Chain Management. 

## Turn on Copilot support for the Workflow history page

The feature **Workflow history summary** is enabled by default in 10.0.39 in Microsoft Dynamics 365 Finance. 

> [!NOTE]
>  As of version 10.0.40, and in the proactive updates (PQUs) for version 10.0.39, the feature **Workflow history summary** is set to On by default in Feature management.

Workflow history can be used either with or without its AI-powered Copilot functionality. To use the Copilot functionality in workflow history the **Copilot in Microsoft Dynamics 365 Finance** app must be installed on your Dataverse environment. For more information, see [Enable Copilot in Microsoft Dynamics 365 Finance](need link/).  

Use this feature to get an AI-generated summary of the workflow history that you are viewing on the workflow history page. The submitter, submission date, current status, approval/rejection/request change actions, due dates and comments are summarized for you. This feature is powered by Microsoft Azure OpenAI’s large language model and is designed to reduce the time that you spend searching the workflow history for the most important details so you can approve documents quickly and efficiently.  

For additional information, see [Transparency FAQ: Workflow history summary](Need link/).  

This feature has two purposes: 
- Provide a concise workflow history summary
- Help you make quicker decisions when approving workflow documents.

## Country/region and language availability 

This copilot feature was validated for [these languages](https://go.microsoft.com/fwlink/?linkid=2270154/). While it can be used in other languages, it may not function as intended. Language quality may vary based on the user’s interaction or system settings, which may impact accuracy and the user experience. 

## Version requirements 

Workflow history summary requires the latest Product quality update (PQU) on Dynamics 365 Finance version 10.0.39 and 10.0.40.

## Role requirements 

The user must be able to view workflow history in Dynamics 365 Finance or Dynamics 365 Supply Chain Management to use this feature. 

## Summary by Copilot 

In any **Workflow history** page, if the workflow has been submitted, the Summary by copilot displays at the top. The submitter, submitted date, current status and comments display on the first line. Then the most recent workflow actions display on the next lines. Workflow actions include approvals, delegations, rejections and change requests. The workflow action dates and user who performed the action are shown along with comments if they are entered. The comments may be summarized if they exceed the space allocated for comments.  
