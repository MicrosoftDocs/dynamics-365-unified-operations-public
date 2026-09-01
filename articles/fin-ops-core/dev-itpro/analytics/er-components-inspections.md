---
title: Validate ER format and model mapping to prevent runtime issues
description: Learn about how to inspect the configured Electronic reporting (ER) components to prevent runtime issues that might occur.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 07/17/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: ERSolutionTable, ERDataModelDesigner, ERModelMappingTable, ERModelMappingDesigner, EROperationDesigner
ms.dyn365.ops.version: Version 7.0.0
ms.assetid: 
---

# Validate ER format and model mapping to prevent runtime issues

[!INCLUDE [banner](../includes/banner.md)]

You can validate each configured [Electronic reporting (ER)](general-electronic-reporting.md) [format](er-overview-components.md#format-components-for-outgoing-electronic-documents) and [model mapping](er-overview-components.md#model-mapping-component) at design time. During this validation, a consistency check runs to help prevent runtime problems, such as execution errors and performance degradation. For every problem that the check finds, it provides the path of a problematic element. For some problems, an automatic fix is available.

By default, the validation automatically runs in the following cases for an ER configuration that contains the previously mentioned ER components:

- You [import](general-electronic-reporting.md) a new version of an ER configuration into your instance of Microsoft Dynamics 365 Finance.
- You change the status of the editable ER configuration from **Draft** to **Completed**.
- You [rebase](general-electronic-reporting.md#upgrading-a-format-by-selecting-a-new-version-of-base-format-rebase) an editable ER configuration by applying a new base version.

Starting in version 10.0.49, enhanced validation management lets you [validate multiple completed configuration versions](#validate-multiple-configurations) in a single operation, run that validation in the background as a batch job, and review the results later through a persistent [validation history](er-review-validation-history.md). 

> [!NOTE]
> Enhanced validation management is a feature that you turn on in **Feature management**.
>
> 1. Go to **Workspaces** > **Feature management**.
> 1. In the list, find and select **Enhanced validation management for Electronic Reporting configurations**.
> 1. Select **Enable now**.

## Validate a single configuration version

To validate one version of a configuration, follow these steps:

1. Go to **Organization administration > Electronic reporting > Configurations**.
1. In the configurations tree in the left pane, select the desired ER configuration that contains the ER format or ER model mapping component.
1. On the **Versions** FastTab, select the version of the selected ER configuration.
1. On the **Versions** FastTab or on Action Pane (if **Enhanced validation management for Electronic Reporting configurations** feature is disabled), select **Validate**.

The system validates the selected version and reports any errors or warnings.

> [!NOTE]
> When the **Enhanced validation management for Electronic Reporting configurations** feature is disabled, the **Validate** button is available on Action Pane and validates the selected version of the selected configuration.
> 
> When the **Enhanced validation management for Electronic Reporting configurations** feature is enabled, the **Validate** button is available on the **Versions** FastTab and validates the selected version of the selected configuration.

## Validate multiple configurations

> [!NOTE]
> This function is available starting in version 10.0.49 when the **Enhanced validation management for Electronic Reporting configurations** feature is enabled.

When you turn on the feature, the Action Pane on the **Configuration repository** page includes a **Validation** menu that you can use to validate several configurations at once.

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On the Action Pane, select **Validation** > **Validate configurations**.
1. In the **Configuration validation** dialog box, select the completed configuration versions that you want to validate.
1. Choose how to run the validation:

    - To run validation immediately in interactive mode, start the validation and confirm when prompted. Interactive validation can take some time, depending on how many configurations you select.
    - To run validation in the background, schedule it as a batch job by using the **Batch** button. When the job is queued, a notification confirms that the ER configuration validation job is added to the batch queue.

> [!TIP]
> Run validation as a batch job when you select many configurations or large configurations, so that the work doesn't block your interactive session.

Only completed configuration versions are available for validation.

## Validate ER format in the Designer

1. Go to **Organization administration > Electronic reporting > Configurations**.
1. In the configurations tree in the left pane, select the desired ER configuration that contains the ER format component.
1. On the **Versions** FastTab, select the version of the selected ER configuration.
1. On the Action Pane, select **Designer**.
1. On the **Format designer** page, on the Action Pane, select **Validate**.

## Validate ER model mapping in the Designer

1. Go to **Organization administration > Electronic reporting > Configurations**.
1. In the configurations tree in the left pane, select the ER configuration that contains the ER model mapping component.
1. On the **Versions** FastTab, select the version of the selected ER configuration.
1. On the Action Pane, select **Designer**.
1. On the **Model to datasource mapping** page, on the Action Pane, select **Designer**.
1. On the **Model mapping designer** page, on the Action Pane, select **Validate**.

## Skip the validation when importing the configuration

To skip the validation when importing the configuration, follow these steps:

1. Go to **Organization administration > Electronic reporting > Configurations**.
1. On the **Configurations** page, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
1. Set the **Validate the configuration after importing** option to **No**.

## Skip the validation when you change or rebase the version's status

To skip the validation when you change or rebase the version's status, follow these steps:

1. Go to **Organization administration > Electronic reporting > Configurations**.
1. On the **Configurations** page, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
1. Set the **Skip validation at configuration's status change and rebase** option to **Yes**.

ER uses the following categories to group consistency check inspections:

- **Executability** – Inspections that detect critical issues that might occur at runtime. These issues are mostly at an **Error** level.
- **Performance** – Inspections that detect issues that might cause inefficient execution of configured ER components. These issues are mostly at a **Warning** level.
- **Data integrity** – Inspections that detect issues that might cause data loss or runtime issues. These issues are mostly at a **Warning** level.

## Additional resources

[ALLITEMS ER function](er-functions-list-allitems.md)

[ALLITEMSQUERY ER function](er-functions-list-allitemsquery.md)

[INT64VALUE ER function](er-functions-conversion-int64value.md)

[INTVALUE ER function](er-functions-conversion-intvalue.md)

[FILTER ER function](er-functions-list-filter.md)

[WHERE ER function](er-functions-list-where.md)

[Use JOIN data sources to get data from multiple application tables in ER model mappings](er-join-data-sources.md)

[Trace the execution of ER formats to troubleshoot performance issues](trace-execution-er-troubleshoot-perf.md)

[Business document management overview](er-business-document-management.md)

- [Suppress Word content controls in generated reports](er-design-configuration-word-suppress-controls.md)

- [Manage several derived mappings for a single model root](er-multiple-model-mappings.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
