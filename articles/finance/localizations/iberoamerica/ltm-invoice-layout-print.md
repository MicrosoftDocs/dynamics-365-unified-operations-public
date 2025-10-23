---
title: Configure the layout of a printed invoice for Latin America
description: Learn how to configure the LATAM invoice layout format when printing a document, including prerequisites and an outline on setting up invoice layout printing.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 10/09/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Configure the layout of a printed invoice for Latin America

This article explains how to set up the basic configuration for the Latin American (LATAM) invoice layout when printing invoices.

   > [!NOTE]
   > Layout is a graphical representation of the underlying XML structure of the electronic invoice.

## Prerequisites

Before you begin, ensure that the following prerequisites are met:

- The legal entity must have an address in a country/region within the LATAM localization.
- The country/region-specific LATAM feature and the general feature must be enabled.

- Download the specific report configurations from the Dataverse configuration repository:

| Element | Format name |
|---------|-------------|
| Model   | :::no-loc text="Invoice model LATAM"::: |
| Mapping | :::no-loc text="Invoice model mapping LATAM"::: |
| Format  | Country/region-specific ER configurations, such as :::no-loc text="**Fiscal Documents - Sales invoice (CL)**"::: |

- Learn more in [Import electronic reporting (ER) configurations from Dataverse]( gsw-import-er-config-dataverse.md).
- Configure the electronic reporting (ER) parameters. Learn more in [Configure the electronic reporting (ER) framework](electronic-reporting-er-configure-parameters.md).

- You must run the following two commands as an administrator from a PowerShell console.

    ```powershell
    cd C:\AOSService\PackagesLocalDirectory\Plugins\AxReportVmRoleStartupTask
    ```

    ```powershell
    ./DeployAllReportsToSsrs.ps1 -Module ApplicationSuite -PackageInstallLocation "C:\AosService\PackagesLocalDirectory"
    ```

## Configure SSRS Reports and Services references.

For printing layout you must configure the **SSRS Reports / Services references** following these steps:

1. Go to Organization administration **Setup > LATAM > SSRS Reports / Services references**.
1. Create a new record.
1. Complete the **Report/Service Id** and **Report/Service name** with code and description.
1. In **Settings** tab select **ER Configuration** for the **Report/Service type** field.
1. In **Parameter** section add the following line:
   1. **Name:** TaxApplicationId.
   1. **Value:** enter the **Tax application Id** that you created for the electronic invoice.

Learn more in [Configure SSRS Reports / Services references](#configure-ssrs-reports-and-services-references).

## Configure the Document Class

To configure document classes, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**
1. Select a **Document class** used in layout printing.
1. Complete the **Report/Service Id** field with the **SSRS Reports / Services references** record.

## Configure printing layout

To configure a printing layout, follow these steps:

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting** and select **Reporting configuration**.
1. On the left tree, select **Invoice model** \> **Invoice model LATAM**\> and select the **Fiscal Document** to be printed.
1. On the top menu, go to **Configurations** \> **Application specific parameters** \> **Setup**.
1. For each record in the **Lookups** section, in the **Conditions** section, select **Add** and complete with the desired **Lookup result** records.
   > [!NOTE]
   > To ensure the report shows transactions that meet the configured conditions, complete the Lookup result field as N/A with Blank and Not blank conditions.
1. Change the **State** field to **Completed**.
1. Go to **Accounts receivable** \> **Setup** \> **Forms** \> **Form Setup**.
1. In the **General** section, select **Print management**.
1. Select a record and complete the **Report format** field with the desired layout format from **Electronic Reporting**.
1. Click the arrow button next to the **Destination** field.
1. On the **Electronic reporting named destination** page click **New**.
1. Create a record and complete the **Name** field.
1. In the **File destination** section, click **New**.
1. Complete the **Name** and **File component name** fields.
1. Mark the **Convert to PDF** checkbox.
1. On the **Action Pane** go to **Settings**, select **File** and set **Enabled** to **Yes**.
1. Back on the **Print management setup** page, complete the **Destination** field.

   Learn more in [Configure print management record-specific ER destinations](#er-named-destinations).

1. To configure project invoice formats, go to **Project management and accounting** \> **Setup** \> **Forms** \> **Forms setup**, and repeat steps 7 through 16.
1. Go to the invoice journals or project invoice journal inquiry, and select a journal in the **Invoice** section. Then, on the Action Pane, select **Document** \> **View** \> **Use print management** to download the invoice layout report.

    > [!NOTE]
    > To run a free text invoice format, enable the **Use RDP-based model mapping for the Free text invoice report** feature in the **Feature management** workspace.
