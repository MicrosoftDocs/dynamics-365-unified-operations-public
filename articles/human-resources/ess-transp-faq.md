---
# required metadata

title: Employee self service leave summary - Transparancy FAQ
description: This article answers some frequently asked questions about the Employee self service leave summary feature.
author: jcart
ms.date: 06/18/2024
ms.topic: overview
ms.reviewer: twheeloc
# optional metadata

ms.search.form: HRMParameters, EssWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.collection: bap-ai-copilot
# ms.tgt_pltfrm: 
ms.assetid: 2cfb061a-a616-4bf9-9d98-9cde00039eec
ms.search.region: Global
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 2020-03-19
ms.dyn365.ops.version: Human Resource
---

# Employee self service leave summary: Transparency FAQ

This article answers some frequently asked questions about the **Employee self service leave summary** feature.

## What is Employee self service leave summary?

Employee self service leave summary is a feature of Microsoft Dynamics 365 Human Resources that is powered by Azure OpenAI Service's large language model. It shows AI-generated summary text at the top of the **Employee self service** page when a user opens it.

## What can Employee self service leave summary do?

Employee self service leave summary gives a summary of current time-off balances and also informs the user about time off that might be subject to forfeiture if it isn't used. It uses employee leave balances and time-off requests as inputs. This data comes from the customer's Dynamics 365 Human Resources environment only.

## What is Employee self service leave summary's intended use?

The intended use is for users to access the **Employee self service** page to quickly get a summary of their time off. The feature helps improve operational efficiency by reducing the time that users must spend switching between pages to determine their time-off balance and the amount of time off that they could lose.

## How was Employee self service leave summary evaluated? What metrics are used to measure performance?

The AI-generated summary was evaluated based on the existing transaction data (leave balances, time-off requests, and leave plan configuration). All calculations are done in Dynamics 365 Finance, not through Azure OpenAI. They were verified against the same data during the testing process.

## What are the limitations of Employee self service leave summary? How can users minimize the impact of those limitations when they use the system?

The summary provides a comprehensive view of the employee's time-off balances. Information includes the expected amount to lose, which is calculated by using the balance, approved and not yet approved time off, and the expected accruals between now and when the balance expires. This information helps the user quickly learn how much time off they are at risk of forfeiting.

This Copilot feature was validated for [these languages](https://go.microsoft.com/fwlink/?linkid=2270154). Although it can be used in other languages, it might not work as intended. Language quality might vary, based on the user's interactions or system settings, and might therefore affect accuracy and the user experience.

## What operational factors and settings allow for effective and responsible use of Employee self service leave summary?

System users can't change the processing of employee time off. Dynamics 365 Human Resources performs this processing by using Azure Open AI's large language model.

The system administrator can turn this feature off or on in **Feature management** using the **Employee self service leave summary** feature.
