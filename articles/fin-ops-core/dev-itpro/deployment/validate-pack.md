---
# required metadata

title: Validate a package in Lifecycle Services
description: This article explains how to validate a package in Microsoft Dynamics Lifecycle Services before you apply it to a self-service cloud environment.
author: kumarnaresh
ms.date: 07/08/2023
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

# Validate a package in Lifecycle Services

[!include [banner](../includes/banner.md)]

This article explains how to validate a package in Microsoft Dynamics Lifecycle Services before you apply it to a self-service cloud environment.

## Overview 
A new **Validate packages** feature has been introduced in Lifecycle Services. This feature lets customers validate an environment package before they schedule it or apply it to an environment. The validation involves no downtime.

>[!NOTE]
>No changes are made to the environment during this validation. 

## Prerequisites

- This functionality applies only to self-service environments.
- The package that will be validated must meet some requirements. For more information, see [Apply updates to cloud environments](apply-deployable-package-system.md#prerequisite-steps).

## Validate a package

1. In Lifecycle Services, select **Maintain** and then **Validate Packages**.
2. Follow one of these steps, depending on the type of environment:

    - In a sandbox environment, select the deployable package to validate.
    - In a production environment, select the sandbox environment that the update has been applied to, and then select the specific environment update to validate. The environment update doesn't have to be a **Release Candidate** to be validated.

3. Select **Yes** and then **Proceed**.

After the validation has begun, the environment homepage will show updated service action information. The environment status will be **Validating Package**. The environment will be available during this environment state.

After the validation is completed, details can be found on the **Environment history** page. If the validation fails, a rollback isn't required. The **Action state** will be **Failed** on the **History** page.

### Troubleshoot errors

This validation can be used to detect typical failures that occur during the pre-servicing phase of a deployment. For more information, see [Pre-servicing and post-servicing](../lifecycle-services/pre-post-servicing.md#common-failures).

### Releases
This feature is in preview and available only in LCS Sandbox environments in the following regions:
 - United States
 - Switzerland
 - France
 - South Africa


