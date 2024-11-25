---
title: Configure the layout of a printed invoice for Latin America
description: Learn how to configure the LATAM invoice layout format when printing a document, including prerequisites and an outline on setting up invoice layout printing.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 10/09/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Configure the layout of a printed invoice for Latin America

[!include[banner](../../includes/banner.md)]

This article explains how to set up the basic configuration for the Latin American (LATAM) invoice layout when you print invoices.

## Prerequisites

Before you complete the tasks in this article, the following prerequisites must be met:

- The legal entity must have an address in a country/region that's within the LATAM localization.
- The country/region-specific LATAM feature and the general feature must be enabled.
- You must download the following Electronic reporting (ER) configurations from the Global repository:

    - Invoice model
    - Invoice Model LATAM
    - FiscalDocumentsReport
    - Country/region-specific ER configurations, such as **FiscalDocumentReport(CL)**

    For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- You must run the following two commands as an administrator from a PowerShell console.

    ```powershell
    cd C:\AOSService\PackagesLocalDirectory\Plugins\AxReportVmRoleStartupTask
    ```

    ```powershell
    ./DeployAllReportsToSsrs.ps1 -Module ApplicationSuite -PackageInstallLocation "C:\AosService\PackagesLocalDirectory"
    ```

## Set up invoice layout printing

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
2. Select the country/region-specific ER configuration.
3. Configure the application-specific parameters so that they include the tax codes that the report will use to filter each transaction.
4. Go to **Accounts receivable** \> **Setup** \> **Forms** \> **Form Setup**.
5. In the **General** section, select **Print management** to indicate to the launcher which format will be run. 
6. Depending on the invoice that you want to print, select one of the options in the list, and select a value in the **Destination Name** field.

    > [!NOTE]
    > To run a free text invoice format, enable the **Use RDP-based model mapping for the Free text invoice report** feature in the **Feature management** workspace.

7. To create a destination name, select the button next to the **Destination Name** field, create a record that has a name and format, and then enable the file option.
8. In the **Report format** field, select the layout format to use.
9. To configure project invoice formats, go to **Project management and accounting** \> **Setup** \> **Forms** \> **Forms setup**, and repeat steps 5 through 8.
10. Go to the invoice journals or project invoice journal inquiry, and select a journal in the **Invoice** section. Then, on the Action Pane, select **Document** \> **View** \> **Use print management** to download the invoice layout report.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
