---
title: Configure the Electronic reporting (ER) framework
description: This article explains how to configure parameters of the Electronic reporting (ER) framework.
author: kfend
ms.date: 04/23/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: July 2017 update
ms.assetid: 3c1291de-230c-4e31-96c4-ba69a310690a
ms.search.form: ERSolutionTable, ERVendorTable, ERWorkspace, ERParameters, ERFormatDestinationTable
---

# Configure the Electronic reporting (ER) framework

[!include [banner](../includes/banner.md)]

This article explains how to set up the basic functionality for Electronic reporting (ER). It also describes the steps that you must complete before you can set up ER.

## Prerequisites for ER setup
Before you can set up ER, you must set up the required [document types](../../fin-ops/organization-administration/configure-document-management.md#configure-document-types) in Document management:

- A document type for Microsoft Office documents that are used as templates for ER reports.
- A document type that is used to store the output of ER reports in the jobs archive.
- A document type that is used to store the output of ER reports so that they can be viewed in other programs.
- A document type that is used to keep baselines of outputs of ER configurations.
- A document type that is used to handle files in the ER framework for all other purposes.

For each document type, the following attribute values can be selected.

| Attribute name | Attribute value                     |
|----------------|-------------------------------------|
| Class          | **Attach file**                     |
| Group          | **File**                            |
| Location       | **Azure storage** or **SharePoint** |

## Set up ER
Use the following procedure to set up the basic functionality of ER for all legal entities.

1. Open the **Electronic reporting** workspace page.
2. Click **Electronic reporting parameters**.

## Main parameters

On the **General** tab of the **Electronic reporting parameters** page, set the following ER parameters:

- **Enable design mode**

    - Set this option to **Yes** to enable embedded ER designers, so that users can create their own ER configurations.
    - Set this option to **No** to require that users access the functionality of ER designers by signing up for [Configuration service](/business-applications-release-notes/october18/dynamics365-finance-operations/regulatory-service-configuration).

- **Disable tracing of ER performance in data handling**

    - Set this option to **No** to allow Microsoft Telemetry to collect information about the average time that is required to process a single incoming or outgoing record as an ER configuration. This information is tracked as a specific health metric of the environment, and it will help Microsoft quickly identify and address issues that affect customers who use the ER framework.
    - Set this option to **Yes** to stop collecting telemetry information.

[![General tab of the Electronic reporting parameters page.](./media/er-configure-parameters-main.png)](./media/er-configure-parameters-main.png)

## <a name="ManageDocumentsParameters">Parameters to manage documents</a>

On the **Attachments** tab of the **Electronic reporting parameters** page, set the following ER parameters:

- **Configurations** – Select a document type to specify the storage of templates of ER formats. This document type is selected within the scope of a specific company. This document type will be used, regardless of the company that a user is signed in to while an ER format is being used.
- **Job archive** – Select a document type to specify the storage of generated documents that are attached to the records of the ER jobs [archive](er-destination-type-archive.md). This document type is selected as a company-specific document type. You must make sure that the selected document type is configured for every company that you plan to run ER formats for, and then store the results in the ER jobs archive.
- **Temporary** – Select a document type to specify the storage of generated documents that are used for other purposes. For example, documents might be generated for [preview](er-destination-type-screen.md) by other services. This document type is selected as a company-specific document type. You must make sure that the selected document type is configured for every company that you plan to run ER formats for, and then store the results in the ER jobs archive.
- **Baseline** – Select a document type to specify the storage of documents that are used as [baselines](er-trace-reports-compare-baseline.md) during the automated testing of ER configurations. This document type is selected as a company-specific document type. You must make sure that the selected document type is configured for every company that you plan to run ER formats for, and then store the results in the ER jobs archive.
- **Others** – Select a document type to specify the storage of generated documents that are used for all other purposes. This document type is selected as a company-specific document type. You must make sure that the selected document type is configured for every company that you plan to run ER formats for, and then store the results in the ER jobs archive.
- **Stop making backup copies of templates**

    - Set this option to **No** to automatically create a backup copy of any ER format configuration template and store the copy in the database storage.
    - Set this option to **Yes** to stop making backup copies of ER formation configuration templates.

    For more information, see [Backup storage of ER templates](er-backup-storage-templates.md).

[![Attachments tab of the Electronic reporting parameters page.](./media/er-configure-parameters-documents.png)](./media/er-configure-parameters-documents.png)

## LCS parameters

On the **LCS** tab of the **Electronic reporting parameters** page, define the number of parallel threads that should be used to load an ER configuration from repositories in Microsoft Dynamics Lifecycle Services (LCS), so that the configurations are loaded in the most efficient manner. The value can vary from **1** through **15**, depending on the available resources of the current program. Based on this setting and the number of other tasks and their priorities, the real number of threads will be defined automatically.

[![LCS tab of the Electronic reporting parameters page.](./media/er-configure-parameters-lcs.png)](./media/er-configure-parameters-lcs.png)

## RCS parameters

On the **RCS** tab of the **Electronic reporting parameters** page, sign up for [Configuration service](/business-applications-release-notes/october18/dynamics365-finance-operations/regulatory-service-configuration).

[![RCS tab of the Electronic reporting parameters page.](./media/er-configure-parameters-rcs.png)](./media/er-configure-parameters-rcs.png)

## Active ER configurations provider

On the **Configuration provider table** page, create ER provider records. Each provider can be [marked](tasks/er-configuration-provider-mark-it-active-2016-11.md) as **Active**. The active provider's name and internet address are stored in an ER configuration, as attributes of the configuration owner.

## Optional setup for ER
In addition to the basic functionality, ER has other functionality that you can set up.

- On the **Electronic reporting destination** page, define the ER output destinations for each file output of each ER format configuration. Use the [document types](../../fin-ops/organization-administration/configure-document-management.md#configure-document-types) of the Document management framework that you set up earlier. You can also use this page to set up the optional ER functionality for each legal entity. For more information, see [Electronic reporting (ER) destinations](electronic-reporting-destinations.md).
- When you add new Application Object Tree (AOT) artifacts or update existing AOT artifacts that are used as data sources (tables, views, or data entities) in ER, use the **Rebuild table references** menu item (**Organization administration** \> **Electronic reporting** \> **Rebuild table references**) to bring your AOT changes into the ER metadata.

## Frequently asked questions
**Question:** What is the optimal number of parallel threads to use to load an ER configuration from LCS?

**Answer:** To calculate the optimal number of parallel threads, use the following empirical formula: Cores ÷ 2 + 1(2). For example, if the program runs on a virtual machine (VM) that has two CPUs, and each CPU contains four cores, the optimal number is five or six parallel threads.

**Question:** I have added a custom table to the AOT. I created a new ER model mapping configuration for my ER data model. During the design of the model mapping, I tried to add a new data source type, **Table records**, that refers to my table. I could manually add my table name to the **Table** lookup, and the ER model mapping accepted it without errors or warnings. However, my table's name isn't included in the list of available choices that the **Table** lookup of this data source offers. How do I include the name of my table?

**Answer:** To include the name of your custom table in the **Table** lookup, use the **Rebuild table references** menu item as described in the "Optional setup for ER" section earlier in this article.

**Question:** Why can't I mark the Microsoft provider as **Active** in the **Electronic reporting** workspace in my production environment?

**Answer:** The Microsoft provider is used to mark ER configurations that have been designed and maintained by Microsoft. We expect that Microsoft will release new versions of the configurations in the future. We recommend that you not mark the Microsoft provider as **Active**. Otherwise, you can update the configurations. (For example, you can change the content and register new versions.) These updates will cause issues in the future, when Microsoft provides new versions of the configurations, and those new versions must be imported and adopted. Instead, register a new ER provider for your company, and use it for your ER configurations maintenance. To reuse a Microsoft configuration, select it as the base for your derived copy. To incorporate changes that are provided by Microsoft, rebase your configuration to a new version of the Microsoft configuration when it becomes available.

**Question:** I successfully ran an ER format in one company. However, when I ran the same ER format in another company and used the same settings, I received the following error message: "The provided document type is not a File type." Why?

**Answer:** Most likely, the second company doesn't contain document types that have been selected in the **Job archive**, **Temporary**, **Baseline**, and **Others** [ER parameters](#ManageDocumentsParameters). To fix this issue, configure these document types in the second company.

## <a name="AdditionalResources">Additional resources</a>

- [Electronic reporting (ER) overview](general-electronic-reporting.md)
- [Electronic reporting (ER) destinations](electronic-reporting-destinations.md)
- [Configuration service of Regulatory Services](/business-applications-release-notes/october18/dynamics365-finance-operations/regulatory-service-configuration)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
