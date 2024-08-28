---
title: Workflow history summary
description: This topic describes the copilot capabilities on the Workflow history page.
author: JodiChristiansen
ms.date: 06/03/2024
ms.topic: article
ms.custom: 
  - bap-template
ms.collection: bap-ai-copilot
ms.reviewer: twheeloc
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24
---

# Workflow history summary

This article explains how to enable the optional **Summary by Copilot** field on any **Workflow history** page in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.

## Turn on Copilot support for the Workflow history page

The **Workflow history summary** feature is enabled by default in Dynamics 365 Finance version 10.0.39.

> [!NOTE]
> As of version 10.0.40, and in the proactive quality updates (PQUs) for version 10.0.39, the **Workflow history summary** feature is set to **On by default** in Feature management.

Workflow history can be used either with or without its AI-powered copilot functionality. To use the copilot functionality in workflow history, you must install the **Copilot in Microsoft Dynamics 365 Finance** app in your Dataverse environment. For more information, see [Copilot prerequisites](../../../finance/accounts-receivable/Enable-copilot-in-finance.md).

Use this feature to get an AI-generated summary of the workflow history that you're viewing on the **Workflow history** page. The submitter, submission date, current status, approval or rejection, request change actions, due dates, and comments are summarized for you. This feature is powered by Azure OpenAI Service's large language model. It's designed to reduce the time that you spend searching the workflow history for the most important details, so that you can approve documents quickly and efficiently.

For more information, see [Workflow history summary: Transparency FAQ](../copilot/workflow-history-summary-FAQ.md).

This feature has two purposes:

- Provide a concise workflow history summary.
- Help you make quicker decisions when you approve workflow documents.

## Country/region and language availability

For information about the languages that this Copilot feature was validated for, see [Explore Copilot features by geography and languages](https://go.microsoft.com/fwlink/?linkid=2270154). Although the feature can be used in other languages, it might not work as intended. Language quality might vary, based on the user's interactions or system settings, and might therefore affect accuracy and the user experience. 

## Version requirements

Workflow history summary requires the latest PQU on Dynamics 365 Finance versions 10.0.39 and 10.0.40.

## Role requirements

To use this feature, the user must be able to view workflow history in Dynamics 365 Finance or Dynamics 365 Supply Chain Management.

## Summary by Copilot

The **Summary by Copilot** field appears at the top of any **Workflow history** page if the workflow was submitted. The first line shows the submitter, submitted date, current status, and comments. The next lines show the most recent workflow actions. Workflow actions include approvals, delegations, rejections, and change requests. The workflow action dates and the user who performed each action are shown together with any comments that were entered. The comments might be summarized if they exceed the space that was allocated for comments.
