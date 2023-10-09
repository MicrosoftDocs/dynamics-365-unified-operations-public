---
title: Configure the layout of a printed invoice for Latin America
description: This article how to configure the LATAM invoice layout format when printing a document. 
author: Fhernandez0088
ms.date: 10/09/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Configure the layout of a printed invoice for Latin America

[!include[banner](../../includes/banner.md)]

This article explains how to set up the basic configuration for the Latin American invoice layout when you print invoices.

## Prerequisites
Before you complete the tasks in this article, the following prerequisites must be met.

- The legal entity must have an address in a country/region that's within the LATAM localization.
- The country/region-specific LATAM feature and the general feature must be enabled.
- You must download the following Electronic reporting (ER) configurations from the Global repository:

  - Invoice model
  - Invoice Model LATAM
  - FiscalDocumentsReport
  - Country specific ER configurations. For example, FiscalDocumentReport(CL). To learn more, see [Download ER Configuration](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
- Execute the following two commands from a PowerShell console as an administrator:

  - cd C:\AOSService\PackagesLocalDirectory\Plugins\AxReportVmRoleStartupTask
  - ./DeployAllReportsToSsrs.ps1 -Module ApplicationSuite -PackageInstallLocation "C:\AosService\PackagesLocalDirectory"

## Set up invoice layout printing
1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
2. Select the country-specific ER configuration.
3. Configure the application specific parameters to include the tax codes that the report will use to filter each transaction.
4. Go to **Accounts receivable** > **Setup** > **Forms** > **Form Setup**.
5. In the **General** section, select **Print management** to indicate to the launcher which format will be executed. 
6. Depending on the invoice you want to print, select one of the options from the list, and in the **Destination Name** field, select a value.

   > [!NOTE]
   > To execute a free text invoice format, enable the **Use RDP-based model mapping for the Free text invoice report** feature in the **Feature management** workspace.

7. To create a **Destination Name**, select the button next to the field and create a new record with a name and format, and then enable the file option.
8. In the **Report format** field, select the layout format to use.
9. To configure project invoice formats, go to **Project management and accounting** > **Setup** > **Forms** > **Forms setup** and repeat steps 5 - 8.
10. Navigate to the invoice journals or project invoice journal inquiry and select a journal from the Invoice section. On the Action Pane select **Document** > **View** > **Use print management** to download the invoice layout report.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]



