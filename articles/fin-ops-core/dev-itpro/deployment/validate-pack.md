---
title: Validate a package in Lifecycle Services
description: Learn how to validate a package in Microsoft Dynamics Lifecycle Services before you apply it to a self-service cloud environment.
author: kumarnaresh
ms.author: kumarnaresh
ms.topic: how-to
ms.date: 01/21/2024
ms.reviewer: twheeloc
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: 
ms.dyn365.ops.version: Platform update 1
---

# Validate a package in Lifecycle Services

[!include [banner](../includes/banner.md)]

This article explains how to validate a package in Microsoft Dynamics Lifecycle Services before you apply it to a self-service cloud environment.

## Overview 
A new **Validate packages** feature has been introduced in Lifecycle Services. This feature lets customers validate an environment package before they schedule it or apply it to an environment. The validation can detect issues such as:
 - Failure to create a new index due to duplicate values.
 - Failure to deploy an enum value because it already exists.

>[!NOTE]
>The validation involves no downtime and no changes are made to the environment. 

## Prerequisites

- This functionality applies only to self-service environments.
- The package that will be validated must meet some requirements. For more information, see [Apply updates to cloud environments](apply-deployable-package-system.md#prerequisite-steps).

## Validate a package

1. In Lifecycle Services, select **Maintain** and then **Validate package**.
2. Follow one of these steps, depending on the type of environment:

    - In a sandbox environment, select the deployable package to validate.
    - In a production environment, select the sandbox environment that the update has been applied to, and then select the specific environment update to validate. The environment update doesn't have to be a **Release candidate** to be validated.

3. Select **Validate** and then **Yes**.

After the validation has begun, the environment homepage will show updated service action information. The environment status will be **Validating package**. The environment will be available during this environment state.

After the validation is completed, details can be found on the **Environment history** page. If the validation fails, a rollback isn't required. The **Action state** will be **Failed** on the **History** page.

The validation can fail due to infrastructure issues that aren't considered as a validation failure. Users should check the logs in Lifecycle Services to confirm if the validation has failed.


### Troubleshoot errors

This validation can be used to detect typical failures that occur during the pre-servicing phase of a deployment. For more information, see [Pre-servicing and post-servicing](../lifecycle-services/pre-post-servicing.md#common-failures).

### Releases
This feature is available in both sandbox and production environments in all regions. 



