---
title: Workflow history summary FAQ
description: This article answers some frequently asked questions about the Workflow history summary feature in Microsoft Dynamics 365 Finance.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.custom: faq
ms.date: 6/15/2023
ms.reviewer: twheeloc
---

# Workflow history summary: Transparency FAQ

This article answers some frequently asked questions about the Workflow history summary feature in Microsoft Dynamics 365 Finance.

## What is Workflow history summary?

Workflow history summary is a feature in Microsoft Dynamics 365 Finance powered by Azure OpenAI’s large language model. It shows AI-generated summary text in the Workflow history form for all workflow document types. This summary information is displayed on the existing workflow history page. 

## What can Workflow history summary do?

This summary uses existing workflow history information in a customer’s Dynamics 365 Finance or Dynamics 365 Supply Chain Management application.  

## What are Workflow history summary's intended use(s)?

A workflow approver will use this feature to view a summary of the workflow at the top of the workflow history page. This summary is more concise and brings the most important information to the top of the page to improve efficiency. Recent workflow history is the most recent approval or reject request change or resubmit records of the workflow.  

## How was Workflow history summary evaluated? What metrics are used to measure performance?

The AI-generated summary was evaluated based existing workflow history of the same document type using the submitter, submitted date, current status, approvers, due date, and comments. The summary is displayed first and then the most recent workflow actions are displayed.

## What are the limitations of Workflow history summary? How can users minimize the impact of Workflow history summary's limitations when they use the system?

- The summary is based on the current workflow history that the user is viewing. Only the most recent actions are displayed in chronological order starting with the session date.   
- This Copilot feature was validated for [these languages](https://go.microsoft.com/fwlink/?linkid=2270154/). While it can be used in other languages, it may not function as intended. Language quality may vary based on the user’s interaction or system settings which may impact accuracy and the user experience.   

## What operational factors and settings allow for effective and responsible use of Workflow history summary?

Processing of the workflow history data (i.e. submitter, approval list, workflow actions, due dates, and comments), cannot be changed by the end users. This processing is performed by Dynamics 365 Finance using Azure OpenAI's large language model. Comments entered during the approval process are not processed. 

This feature can be turned off or on by the system administrator in **Feature management** using the **Workflow history summary** feature.  

The AI-generated text and draft email options are optional and can be turned off or on in **Feature management** using the **Collections coordinatory summary**. 

## See also

- [Collections coordinator summary](../accounts-receivable/collectionscoordinatorsummary.md)
