---
# required metadata

title: Employee self service workspace summary - Transparance FAQ
description: This article answers some frequently asked questions about the Employee self service workspace summary.
author: jcart
ms.date: 06/11/2024
ms.topic: overview
ms.reviewer: twheeloc
# optional metadata

ms.search.form: HRMParameters, EssWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.collection: bap-ai-copilot
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 2cfb061a-a616-4bf9-9d98-9cde00039eec
ms.search.region: Global
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 2020-03-19
ms.dyn365.ops.version: Human Resource

# Employee self service workspace summary: Responsible AI FAQ
 This article answers some frequently asked questions about the Employee self service workspace summary.
 
## What is Employee self service workspace summary?
 Employee self service workspace summary is a feature of Dynamics 365 Finance that is powered by Azure Open AI's large language model. It shows AI-generated summary text on the **Employee self service page**. 
 The summary info is displayed at the top of the Employee self service page when the user opens it.

## What can Employee self service workspace summary do?
It uses employee leave balances and time off requests as inputs. These data come from customer’s Dynamics 365 Finance environment only.
It gives a summary of current time off balances and also informs the user of time off that may be subject to forfeiture if not used.

## What is the Employee self service workspace summary’s intended use?
The intended use is for the users having access to Employee self service workspace form to quickly get a summary of the time off. It can reduce the time spent on switching between pages to determine time off 
balances and what time off could be lost to improve operational efficiency.

## How was Employee self service workspace summary evaluated? What metrics are used to measure performance?
The AI-generated summary was evaluated based on the existing transaction data, (i.e. leave balances, time off requests, and leave plan configuration). All calculations are done in Finance, not through Azure OpenAI. They were verified against the same data during the testing process.

## What are the limitations of Employee self service workspace summary? How can users minimize the impact of Employee self service workspace summary’s limitations when using the system?
The summary provides a comprehensive view of the employees time off balances. Included is the expected amount to lose, which is calculated using the balance, approved and not yet approved time off as well as the
expected accruals between now and when the balance expires. This will save time for the user to understand how much time off they are at risk of forfeiting.
This Copilot feature was validated for [these languages](https://go.microsoft.com/fwlink/?linkid=2270154). While it can be used in other languages, it may not function as intended. Language quality may vary based
on the user’s interaction or system settings which may impact accuracy and the user experience.

## What operational factors and settings allow for effective and responsible use of Employee self service workspace summary?
Processing of the employee time off can't be changed by the end users. This processing is performed by Dynamics 365 Finance using Azure Open AI's large language model.
This feature can be turned off or on by the administrator in **Feature management** using the **Employee self service workspace summary**.
