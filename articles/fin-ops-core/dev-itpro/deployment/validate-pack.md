---
# required metadata

title: Validate a package in Lifecycle Services (LCS)
description: This article explains how to validate a package in Lifecycle Services (LCS) before applying it to a self-service cloud environment.
author: 
ms.date: 05/08/2023
ms.topic: how-to
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: ms.custom: 107013
ms.assetid: 341a229f-d9c3-4678-b353-d08d5b2c1caf
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Validate a package in Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]

This article explains how to validate a package in Lifecycle Services (LCS) before applying it to a cloud environment.

## Validate packages

A new service action - Validate Packages, has been introduced in Microsoft Dynamics Lifecycle Services to validate an environment update/deployable package before scheduling/applying in their environments, 
without taking any downtime.

### Prerequisites
 - This is applicable only to self-service environments
 - The package to be validated should meet the prerequisite mentioned here - Apply updates to cloud environments - Finance & Operations | Dynamics 365 | Microsoft Learn

### Steps to trigger Validate Packages service action
1. Click on the newly introduced ‘Maintain’ drop down option ‘Validate Packages’.
2. In case of Sandbox environments, choose the deployable package to be validated.  
In the case of Production environments, choose the Sandbox environment in which the update has been applied and then choose the specific Environment Update to be validated. The Environment Update need not be 
marked as a Release Candidate to be validated using this service action.
3. Click ‘Yes’/’Proceed’ in the confirmation boxes.
4.	Once the action is started successfully, the environment homepage will be reloaded with the ongoing service action information as below. The status of the environment would be ‘Validating Package’. The 
environment does not go down during this environment state.
5. Once the action completes, action details can be found in the environment history page. As no update happens during this service action, rollback is not needed in case of failures. In such cases, action 
state will be displayed as ‘failed’ in the history page.

### Troubleshoot

Common failures that occur during pre-servicing phase of a deployment, can be caught using this service action. For more information on the errors and how can those be troubleshooted, see Pre-servicing and 
post-servicing.
