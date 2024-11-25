---
title: Workflow history summary - Transparency FAQ
description: This article answers some frequently asked questions about the Workflow history summary feature in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
author: JodiChristiansen
ms.author: jchrist
ms.topic: faq
ms.custom: 
  - bap-template
ms.date: 6/15/2023
ms.reviewer: twheeloc
ms.collection: bap-ai-copilot
---

# Workflow history summary: Transparency FAQ

This article answers some frequently asked questions about the Workflow history summary feature in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.

## What is Workflow history summary?

Workflow history summary is a feature in Dynamics 365 Finance that is powered by Azure OpenAI Service's large language model. It shows AI-generated summary text on the existing **Workflow history** page for all workflow document types.

## What can Workflow history summary do?

The summary uses existing workflow history information in a customer's Dynamics 365 Finance or Dynamics 365 Supply Chain Management.

## What is Workflow history summary's intended use?

Workflow approvers use this feature to view a summary of the workflow on the **Workflow history** page. This summary helps improve efficiency by bringing the most important information to the top of the page in a concise form. Recent workflow history consists of the workflow's most recent approve or reject request change records or resubmit records.

## How was Workflow history summary evaluated? What metrics are used to measure performance?

The AI-generated summary was evaluated based on the existing workflow history of the same document type by using the submitter, submitted date, current status, approvers, due date, and comments. The summary is shown first, and then the most recent workflow actions are shown.

## What are the limitations of Workflow history summary? How can users minimize the impact of those limitations when they use the system?

- The summary is based on the current workflow history that the user is viewing. Only the most recent actions are shown. They are arranged in chronological order by session date. 
- This Copilot feature was validated for [these languages](https://go.microsoft.com/fwlink/?linkid=2270154). Although it can be used in other languages, it might not work as intended. Language quality might vary, based on the user's interactions or system settings, and might therefore affect accuracy and the user experience.

## What operational factors and settings allow for effective and responsible use of Workflow history summary?

System users can't change the processing of the workflow history data (the submitter, approval list, workflow actions, due dates, and comments). Dynamics 365 Finance performs this processing by using Azure OpenAI's large language model. Comments that are entered during the approval process aren't processed.

The system administrator can turn this feature off or on in Feature management by using the **Workflow history summary** feature.

The AI-generated text and draft email options are optional and can be turned off or on in Feature management by using the **Collections coordinator summary** feature.

## See also

- [Workflow history summary](../organization-administration/workflow-history-summary.md)
