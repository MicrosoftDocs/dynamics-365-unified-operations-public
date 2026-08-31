---
title: Review Electronic reporting (ER) validation history
description: Learn how to review the persistent validation history for Electronic reporting (ER) configurations, including results by configuration and version.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 04/08/2026
ms.custom: 
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 
ms.search.form: ERModelMappingDesigner, EROperationDesigner
ms.dyn365.ops.version: 10.0.49
ms.assetid: 
---

# Review Electronic reporting (ER) validation history

[!INCLUDE [banner](../includes/banner.md)]

This article describes how to review the validation history for Electronic reporting (ER) configurations.
Validation history lets you return to previous validation runs to confirm which configuration versions were validated, when they were validated, and what errors or warnings were reported.

## Overview

When you validate ER configurations, the system retains the results in a persistent validation history.
Instead of re-running validation to confirm a configuration's state, you can open the history at any time and review the outcome of earlier runs.

The history is organized by configuration and by version, so you can review the individual errors and warnings that were reported for that run.
Because the history is persistent and shared, you and other users in the environment see the same results.

Validation history is part of the enhanced validation management feature that's introduced in version 10.0.49.
For information about turning on the feature and running validation, see [Validate ER format and model mapping to prevent runtime issues](er-components-inspections.md).

## Prerequisites

- Turn on the **Enhanced validation management for Electronic Reporting configurations** feature in **Feature management**.
- Complete at least one validation run so that there are results to review.

## Open the validation history

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On the Action Pane, select **Validation** > **Validation history**.

The **Validation history** opens and lists the validation runs that are completed in the current environment.

## Review validation runs

The **History** tab shows every validation run that completed in the current environment. Each row provides the following information.

| Column | Description |
| --- | --- |
| **Completed** | The date and time when the validation run finished. |
| **Created by** | The user who started the validation run. |
| **Mode** | How the run was performed - **Interactive** or **Batch**. |
| **Batch job** | The ID of the batch job, when the run was performed in batch mode. |
| **Configurations checked** | The number of configurations that the run validated. |
| **Passed** | The number of configurations that passed validation. |
| **Warnings** | The number of configurations that reported warnings. |
| **Failed** | The number of configurations that failed validation. |

To review a run, select its row in the **History** grid. The configurations that the run checked appear in the lower **Configurations** grid.

## Review the configurations that were checked

When you select a run on the **History** tab, the **Configurations** grid lists the configurations that the run validated. Each row provides the following information.

| Column | Description |
| --- | --- |
| **Configuration** | The name of the validated ER configuration. |
| **Version** | The configuration version that the run validated. |
| **Status** | The status of the version, such as **Draft** or **Completed**. |
| **Configuration type** | The component type - for example, **Format**, **Model mapping**, or **Data model**. |
| **Result** | The validation result for the version, such as **Valid**. |
| **Messages** | The number of validation messages that the run reported for the version. |

## Show message details

To review the individual errors and warnings that a validation run reported, select **Show message details**.
You can use this action in both the **History** grid and the **Configurations** grid. You can review messages for an entire run or for a single configuration version.

## Delete validation runs

To remove a validation run from the history, select the run in the **History** grid, and then select **Delete**.

Because the system tracks validation for each configuration version, both users and system processes can identify which versions are already validated in the current environment.
This information helps you avoid redundant validation runs and focus on the versions that still need attention.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
