---
# required metadata

title: Upgrade analysis 
description: This article explains how to use Upgrade analysis in Lifecycle Services (LCS). Upgrade analysis helps you plan full-version, minor-version, and in-place upgrades to Microsoft Dynamics AX 2012.
author: RobinARH
manager: AnnBe
ms.date: 2015-10-29 19 - 01 - 28
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 11394
ms.assetid: 86375ca9-6c2a-47a8-badc-b713b186b4e8
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.dyn365.ops.intro: 
ms.dyn365.ops.version: 2012

---

# Upgrade analysis (AX 2012)

This article explains how to use Upgrade analysis in Lifecycle Services (LCS). Upgrade analysis helps you plan full-version, minor-version, and in-place upgrades to Microsoft Dynamics AX 2012.

In Microsoft Dynamics Lifecycle Services (LCS), Upgrade analysis helps users plan a full-version upgrade to Microsoft Dynamics AX 2012 from Microsoft Dynamics AX 4.0 or Microsoft Dynamics AX 2009, or a minor-version or in-place upgrade from one version of AX 2012 to another. The following chart shows how the service works for both full-version upgrades and in-place upgrades. ![Upgrade analysis service options](./media/lcsupgradeanalysisservice.png) Upgrade analysis uses a Rapid Data Collector (RDC) tool to analyze information about the existing environment. This information can help you estimate the scale of the upgrade project. For more information about full-version upgrade, see [Scenario: Upgrade AX 4.0 or AX 2009 to AX 2012 (all versions)](http://technet.microsoft.com/library/ccf303bb-5d58-4e22-b802-986e61720488(AX.60).aspx).

## Collect and upload files for analysis (Fullversion upgrade: AX 4.0 or AX 2009)
To use Upgrade analysis, you must install the RDC tool, and then upload the RDC files and AOD files. The RDC tool collects metadata about the production environment, such as the number of records in tables. **Important:** The RDC tool should be run in a copy of the production environment where no upgrade scripts have been loaded.

### Install the RDC tool

1.  [Go to LCS](https://lcs.dynamics.com), and sign in.
2.  Open a project, and then click the **Upgrade analysis** tile.
3.  Click **Add**.
4.  On the **Upgrade analysis create job** page, in the source-to-target upgrade list, click **Download**.
5.  Download the RapidDataCollector.msi file, and then run it on an AX 4.0 or AX 2009 client to install and run the Rapid Data Collector service. The service creates a zip file that contains RDC files.
6.  Enter a name for the job, identify the version and build of Microsoft Dynamics AX that you're upgrading from, and then click **Create**.

### Upload and analyze files

You can upload the RDC files and AOD files in any order.

1.  On the **Upgrade analysis file upload** page, click **+ (Add files)**.
2.  Select the type of file to upload (**Rapid Data Collector** or **AOD**).
3.  Enter the file location, and then click **Upload**.
4.  After you upload all the files to analyze, click **Analyze**. When the analysis process is completed, the status appears as **Complete**.
5.  For information about the reports that are available, see the "Download the report" section.

## Collect and upload files for analysis (Inplace upgrade: AX 2012)
For in-place upgrades, you must upload a model store that you have exported as a zip file. Before you begin, follow the steps in the [Before you begin](http://technet.microsoft.com/library/eb8193f4-0318-427f-bcc9-2919f47afb8f(AX.60).aspx#Prerequisites) section of the [Scenario: Perform in-place upgrade to AX 2012 R2 or AX 2012 R3](http://technet.microsoft.com/library/eb8193f4-0318-427f-bcc9-2919f47afb8f(AX.60).aspx) topic.

### Export and zip your model store

1.  Use Microsoft Windows PowerShell or the AxUtil command-line utility to export the model store from the system that you plan to upgrade. For details, see [How to: Export and Import a Model Store](http://msdn.microsoft.com/library/754c52af-4025-4495-979c-f99d8c5b7d89(AX.60).aspx).
2.  Use Microsoft Windows or another system to zip (compress) the file.

### Upload and analyze files

1.  Sign in to LCS, open a project, and then click the **Upgrade analysis** tile.
2.  Click **Add**.
3.  On the **Upgrade analysis create job** page, enter a name for the job, identify the version and build of AX 2012 that you're upgrading from, and then click **Create**.
4.  On the **Upgrade analysis file upload** page, click **+ (Add files)**.
5.  Browse to the zipped model store, and then click **Upload**. After the file is uploaded, the site lists the file name and size.
6.  Click **Analyze Code** to start the analysis process. If no virtual machine is available when you start the process, the status appears as **Process pending**. **Note:** The analysis process takes 2 to 5 hours, depending on the size of the model store. You can close the website and sign in again later to check on the progress of the analysis. The progress is updated every 15 minutes.
7.  When the analysis process is completes, the status appears as **Complete**.
8.  For information about the reports that are available, see the "Download the report" section.

## Download the report
Upgrade analysis creates two reports: an overview report, which is an HTML file, and a detailed report, which is a Microsoft Excel file that you can download and review.

-   To view the overview report, click **View**.
-   To download the detailed report, click the Excel icon.

The following table describes the Excel worksheets that the detailed report provides.

| Worksheet                                    | Description                                                                                      | Input for                         |
|----------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------|
| Upgrade summary                              | A list of key reports, and the number of objects that are affected by the upgrade in each module |                                   |
| Global tables                                | A list of tables that don't have **DataAreaId** values                                           | Data upgrade, Code upgrade        |
| Customization Statistics                     | A list of all customizations                                                                     | Code upgrade                      |
| Customization View                           | The number of customized tables and classes                                                      | Data upgrade                      |
| Modified Objects                             | A list of modified objects                                                                       | Code upgrade                      |
| Modified Object Details                      | A list of what is modified in each object                                                        | Code upgrade                      |
| Domain information                           | A list of companies, domains, and related users                                                  | Security upgrade                  |
| Table statistics                             | A list of table sizes, properties, and counts of rows and columns                                | Data upgrade, Minimizing downtime |
| Parameters                                   | A list of parameter values                                                                       | Data upgrade, Code upgrade        |
| Tables without DataAreaId                    | A list of any tables that don't have **DataAreaId** values                                       | Data upgrade                      |
| SysUtilElementsLog (AX Object Usage Summary) | A list of usage patterns for **MSDAX** objects                                                   | Code upgrade                      |



See also
--------

[Upgrading to a new version of Microsoft Dynamics AX](https://msdn.microsoft.com/en-us/library/aa588216.aspx)

[Scenario: Perform in-place upgrade to AX 2012 R2 or AX 2012 R3](https://technet.microsoft.com/en-us/library/jj733502.aspx)

