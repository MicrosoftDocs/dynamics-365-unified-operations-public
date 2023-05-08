---
# required metadata

title: Validate a package in Lifecycle Services (LCS)
description: This article explains how to validate a package in Lifecycle Services (LCS) before applying it to a self-service cloud environment.
author: kumarnaresh
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
ms.author: kumarnaresh
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Validate a package in Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]

This article explains how to validate a package in Lifecycle Services (LCS) before applying it to a self-service cloud environment.

## Validate packages

A new feature **Validate packages** has been introduced in Microsoft Dynamics Lifecycle Services. This allows customers to validate an environment package before scheduling or applying it in an environment 
without downtime.

### Prerequisites
 - This is feature applies to self-service environments.
 - The package to be validated needs to meet the prerequisites. For more information, see [Apply updates to cloud environments](apply-deployable-package-system.md#prerequisite-steps).

### Validate a package
1. In LCS, click **Maintain** and **Validate Packages**.
2. In a Sandbox environment, select the deployable package to be validated.  
In a Production environment, select the Sandbox environment that the update has been applied and select the specific environment update to be validated. The environment update doesn't need to be a **Release Candidate** to be validated.
3. Click **Yes** and then **Proceed**.
4.	After the action has started, the environment homepage will display updated service action information. The environment status will be **Validating Package**. The environment will be available during this environment state.
5. After the validation is complete, details can be found on the **Environment history** page. If the validation fails, a rollback isn't needed. The **Action state** will be **Failed** on the **History** page.

### Troubleshoot

Common failures that occur during pre-servicing phase of a deployment, can be detected using this service. For more information, see [Pre-servicing and post-servicing](/lifecycle-services/pre-post-servicing.md#common-failures).
