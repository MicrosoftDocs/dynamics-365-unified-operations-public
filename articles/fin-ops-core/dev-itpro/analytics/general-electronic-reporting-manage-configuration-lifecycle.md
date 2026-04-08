---
title: Manage the Electronic reporting (ER) configuration lifecycle
description: Learn how to manage the lifecycle of Electronic reporting (ER) configurations for Dynamics 365 Finance, including a table of various concepts.
author: kfend
ms.author: filatovm
ms.topic: how-to
ms.date: 04/08/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: ERDataModelDesigner, ERMappedFormatDesigner, ERModelMappingDesigner, ERModelMappingTable, ERSolutionImport, ERSolutionTable, ERVendorTable, ERWorkspace
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 35ad19ea-185d-4fce-b9cb-f94584b14f75
---

# Manage the Electronic reporting (ER) configuration lifecycle

[!include [banner](../includes/banner.md)]

This article describes how to manage the lifecycle of [Electronic reporting](general-electronic-reporting.md) (ER) [configurations](general-electronic-reporting.md#Configuration) for Dynamics 365 Finance.

## Overview

Electronic reporting (ER) is an engine that supports statutory required and country/region-specific electronic documents. In general, ER assumes an ability to perform the following tasks for a single electronic document. For more details, see [Electronic reporting (ER) overview](general-electronic-reporting.md).

- Design a template for an electronic document:

  - Identify the required sources of data that you can present in the document:

    - Underlying data, such as data tables, data entities, and classes.
    - Process-specific properties, such as execution date and time, and time zone.
    - User input parameters, specified by the end user at run time.

  - Define the required document elements and their topology to specify a final document format.
  - Configure the desired flow of data from selected data sources to defined document elements (via data source bindings to document format components), and specify process control logic.

- Make a template available so that you can use it in other instances:

  - Transform a document template that you created into an ER configuration, and export the configuration from the current application instance as an XML package that you can store either locally or in Lifecycle Services (LCS).
  - Transform an ER configuration into an application document template.
  - Import an XML package that you store either locally or in LCS into the current instance.

- Customize the template of an electronic document:

  - Bring a template from LCS into the current instance as an ER configuration.
  - Design a custom version of an ER configuration, and keep a reference to the base version.

- Integrate a template with a particular business process, so that it's available in the application:

  - Configure settings so that the application starts to use an ER configuration, by referring to that configuration in a process-related parameter. For example, refer to the ER configuration in a specific Accounts payable payment method to generate an electronic payment message for processing invoices.

- Use a template in a specific business process:

  - Run an ER configuration in a specific business process. For example, to generate an electronic payment message for processing invoices when a payment method that references the ER configuration is selected.

## Concepts

The following roles and related activities are associated with the ER configuration lifecycle.

| Role                                       | Activities                                                      | Description |
|--------------------------------------------|-----------------------------------------------------------------|-------------|
| Electronic reporting functional consultant | Create and manage ER components (models and formats).           | A business person who designs ER domain–specific data models, designs the required templates for electronic documents, and binds them accordingly. |
| Electronic reporting developer             | Create and manage data model mappings.                          | A specialist who selects the required Finance data sources and binds them to ER domain–specific data models. |
| Accounting supervisor                      | Configure process-related settings that reference ER artifacts. | For example, an **Accounting supervisor** role that allows the settings of an ER configuration to be used in a particular Accounts payable payment method to generate an electronic payment message for processing invoices. |
| Accounts payable payments clerk            | Use ER artifacts in a specific business process.                | For example, an **Accounts payable payments clerk** role that allows electronic payment messages to be generated for processing invoices, based on the ER format that is configured for a specific payment method. |

## ER configuration development lifecycle

For the following ER-related reasons, design ER configurations in the development environment, as a separate instance of finance and operations:

- Users in either the **Electronic reporting developer** role or the **Electronic reporting functional consultant** role can edit configurations and run them for testing purposes. This scenario can cause calls to methods of classes and tables that might harm business data and the performance of the instance.
- Calls to methods of classes and tables as ER data sources of ER configurations aren't restricted by entry points and logged company content. Therefore, users in either the **Electronic reporting developer** role or the **Electronic reporting functional consultant** role can access business-sensitive data.

You can [upload](#data-persistence-consideration) ER configurations that you design in the development environment to the test environment for configuration evaluation (proper process integration, correctness of results, and performance) and quality assurance, such as correctness of role-driven access rights and segregation of duties. Use the features that enable ER configuration interchange for this purpose. Proven ER configurations can be uploaded to LCS to share them with service subscribers, or they can be [imported](#data-persistence-consideration) to the production environment for internal use.

:::image type="content" source="./media/ger-configuration-lifecycle.png" alt-text="Screenshot of the ER configuration lifecycle.":::

## Data persistence consideration

You can individually [import](tasks/er-import-configuration-lifecycle-services.md) different versions of an ER [configuration](general-electronic-reporting.md#Configuration) to your Finance instance. When you import a new version of an ER configuration, the system controls the content of the draft version of this configuration:

- If the imported version is lower than the highest version of this configuration in the current Finance instance, the content of the draft version of this configuration remains unchanged.
- If the imported version is higher than any other version of this configuration in the current Finance instance, the content of the imported version is copied to the draft version of this configuration so you can continue editing the last completed version.

If the configuration belongs to the configuration [provider](general-electronic-reporting.md#Provider) that you currently activate, you can view the draft version of this configuration on the **Versions** FastTab of the **Configurations** page (**Organization administration** > **Electronic reporting** > **Configurations**). You can select the draft version of the configuration and [modify](er-quick-start2-customize-report.md#ConfigureDerivedFormat) its content by using the relevant ER designer. When you edit the draft version of an ER configuration, its content no longer matches the content of the highest version of this configuration in the current Finance instance. To prevent the loss of your changes, the system displays an error that the import can't continue because the version of this configuration is higher than the highest version of this configuration in the current Finance instance. When this error occurs, for example with the format configuration **X**, the **Format 'X' version is not completed** error is displayed.

To undo the changes that you introduced in the draft version, select the highest completed or shared version of your ER configuration in Finance on the **Versions** FastTab, and then select the **Get this version** option. The content of the selected version is copied to the draft version.

## Applicability consideration

When you design a new version of an ER configuration, you can define its [dependency](tasks/er-define-dependency-er-configurations-from-other-components-july-2017.md) on other software components. This step is a prerequisite for controlling the download of this configuration's version from an ER repository or an external XML file, and for any further use of the version. When you try to import a new version of an ER configuration, the system uses the configured prerequisites to control whether the version can be imported.

In some cases, you might require that the system ignore the configured prerequisites when you import new versions of ER configurations. To have the system ignore the prerequisites during import, follow these steps:

1. Go to **Organization administration** \> **Electronic reporting** \> **Configurations**.
1. On the **Configurations** page, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
1. Set the **Skip product updates and version prerequisite check during import** option to **Yes**.

    > [!NOTE]
    > This parameter is user-specific and company-specific.

## Dependencies on other components

You can configure ER configurations as [dependent](er-download-configurations-global-repo.md#import-filtered-configurations) on other configurations. For example, you can [import](er-download-configurations-global-repo.md) an ER [data model](er-overview-components.md#data-model-component) configuration from the Global repository into your [Microsoft Regulatory Configuration Services (RCS)](../../../finance/localizations/rcs-overview.md) or Dynamics 365 Finance instance. Then, you can create a new ER [format](er-overview-components.md#format-component) configuration that is [derived](er-quick-start2-customize-report.md#DeriveProvidedFormat) from the imported ER data model configuration. The derived ER format configuration depends on the base ER data model configuration.

:::image type="content" source="./media/ger-configuration-lifecycle-img1.png" alt-text="Screenshot of the derived ER format configuration on the Configurations page.":::

When you finish designing the format, change the status of your initial version of the ER format configuration from **Draft** to **Completed**. Then, share the completed version of the ER format configuration by [publishing](../../../finance/localizations/rcs-global-repo-upload.md) it to the Global repository. Next, you can access the Global repository from any RCS or Finance cloud instance. You can then import any ER configuration version that is applicable to the application from the Global repository into that application.

:::image type="content" source="./media/ger-configuration-lifecycle-img2.png" alt-text="Screenshot of the published ER format configuration on the Configuration repository page.":::

Based on the configuration dependency, when you select the ER format configuration in the Global repository to import it into a newly deployed RCS or Finance instance, the base ER data model configuration is automatically found in the Global repository and imported together with the selected ER format configuration as the base configuration.

You can also export your ER format configuration version out of your current RCS or Finance instance, and store it locally as an XML file.

:::image type="content" source="./media/ger-configuration-lifecycle-img3.png" alt-text="Screenshot of exporting an ER format configuration version as XML on the Configuration page.":::

In versions of Finance **before version 10.0.29**, when you try to import the ER format configuration version from that XML file or from any repository other than the Global repository into a newly deployed RCS or Finance instance that doesn't yet contain any ER configurations, the following exception is thrown to inform you that a base configuration can't be obtained:

> Unresolved references left<br>
Reference of the object '\<imported configuration name\>' to the object 'Base' (\<globally unique identifier of the missed base configuration\>,\<version of the missed base configuration\>) can't be established

:::image type="content" source="./media/ger-configuration-lifecycle-img4.gif" alt-text="Screenshot of importing the ER format configuration version on the Configuration repository page.":::

In version **10.0.29 and later**, when you try to do the same configuration import, if a base configuration can't be found in the current application instance or in the source repository that you're currently using (if applicable), the ER framework automatically tries to find the name of the missing base configuration in the Global repository cache. It then presents the name and globally unique identifier (GUID) of the missing base configuration in the text of the exception that is thrown.

> Unresolved references left<br>
Reference of the object '\<imported configuration name\>' to the object 'Base' (\<name of the missed base configuration\> \<globally unique identifier of the missed base configuration\>,\<version of the missed base configuration\>) can't be established

:::image type="content" source="./media/ger-configuration-lifecycle-img5.png" alt-text="Screenshot of the exception on the Configuration repository page when the base configuration can't be found.":::

You can use the provided name to find the base configuration and then manually import it.

> [!NOTE]
> This new option works only when at least one user already signs in to the Global repository by using the [Configuration repositories](er-download-configurations-global-repo.md#open-configurations-repository) page or one of the Global repository [lookup](er-extended-format-lookup.md) fields in the current Finance instance, and when the Global repository content is cached.

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Define the dependency of ER configurations on other components](tasks/er-define-dependency-er-configurations-from-other-components-july-2017.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
