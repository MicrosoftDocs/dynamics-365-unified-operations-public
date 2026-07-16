---
title: Set up advanced bank reconciliation import by using Electronic reporting
description: Learn about how to use Electronic reporting to set up the advanced bank reconciliation import process, including a step-by-step process.
author: mukumarm
ms.author: mukumarm
ms.topic: how-to
ms.date: 07/08/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: BankStatementFormat
ms.dyn365.ops.version: AX 10.0.25
ms.assetid: 73f3dcf6-040a-44ad-9512-7b3e0d17a571
---

# Set up advanced bank reconciliation import by using Electronic reporting

[!include [banner](../includes/banner.md)]

The Advanced bank reconciliation feature lets you import electronic bank statements and automatically reconcile them with bank transactions in Dynamics 365 Finance. This article explains how to configure the bank statement import process by using Electronic Reporting (ER). The setup varies depending on the format of the bank statement file that your bank provides. Dynamics 365 Finance supports the following bank statement formats for Advanced Bank Reconciliation:

      -  ISO 20022 CAMT.053
      -  MT940
      -  BAI2

## Set up the Electronic reporting configuration

Before you can import and reconcile bank statements, you must import the Electronic Reporting (ER) configuration that corresponds to the bank statement format provided by your bank. The imported ER configuration is used to interpret and process bank statement files during the Advanced Bank Reconciliation import process.

1. Go to **Workspaces** > **Electronic reporting**.
1. On the tile for the **Microsoft** configuration provider, select **Repositories**.
1. Select **Dataverse**, and then select **Open**. For more details, see [Import Electronic reporting (ER) configurations from Dataverse](../../finance/localizations/global/workspace/gsw-import-er-config-dataverse.md).
1. If you need to establish a connection to the repository, select the blue link in the dialog box.
1. In the configuration list, locate **Advanced bank reconciliation statement model** and select the format that matches the electronic bank statement received from your bank.
      - **ABR BAI2 format**
      - **ABR MT940 format**
      - **ABR ISO20022/camt053 format**
1. Select the required format.
1. On the **Versions** FastTab, select the latest available version, and then select **Import**.
1. After the import is completed, verify that the configuration appears on the **Configurations** page and that no validation errors are reported.

## Set up the bank statement format

Before you can import and reconcile electronic bank statements, create a bank statement format and associate it with the appropriate Electronic Reporting (ER) configuration that matches the file format provided by your bank, such as BAI2, MT940, or ISO 20022 CAMT.053. This configuration enables Advanced Bank Reconciliation to correctly interpret and process imported bank statement files.

1. Go to **Cash and bank management** > **Setup** > **Advanced bank reconciliation setup** > **Bank statement format**.
1. Select **New**.
1. Set the **Statement format** and **Name** fields. Enter values that identify the bank statement format.
1. Select the **Generic electronic import format** checkbox.
1. In the **Import format configuration** field, select the Electronic Reporting (ER) configuration that matches the bank statement format that you import:  
    - **ABR BAI2 format** for BAI2 statement files.
    - **ABR MT940 format** for MT940 statement files.
    - **ABR ISO20022/camt053 format** for ISO 20022 CAMT.053 statement files.
1. Save the record.

## Set up the bank account

Before you import bank statements, ensure that Advanced bank reconciliation is enabled for the bank account that you use during the reconciliation process.

1. Go to **Cash and bank management** > **Bank accounts** > **Bank accounts**.
1. Open the bank account.
1. On the **Reconciliation** FastTab, set the **Advanced bank reconciliation** option to **Yes**.
1. In the **Statement format** field, select the Electronic Reporting (ER) format that matches your bank statement file:
    - **ABR BAI2 format** for BAI2 statement files.
    - **ABR MT940 format** for MT940 statement files.
    - **ABR ISO20022/camt053 format** for ISO 20022 CAMT.053 statement files.
1. Save the bank account.

> [!IMPORTANT]
> The statement format that you select on the bank account must match the format of the bank statement file that you import. If the selected format doesn't match the file format, statement import can fail.

For more details about the Advanced bank reconciliation setup process, see [Advanced bank reconciliation setup process](../../finance/cash-bank-management/configure-advanced-bank-reconciliation.md).  

## Import the bank statement

Import a bank statement file to create a bank statement record that you can match and reconcile against bank transactions in **Dynamics 365 Finance**.

1. Go to **Cash and bank management** > **Bank statement reconciliation** > **Bank statements**.
1. Select **Import statement**.
1. In the **Bank account** field, select the bank account that the statement belongs to.
1. In the **Statement format** field, select the bank statement format that's associated with the appropriate Electronic Reporting (ER) configuration.
1. Select **Browse**, and then select the bank statement file.
1. Select **Upload**.
1. Select **OK** to import the statement.

## Examples of bank statement formats and technical layouts

The following table shows examples of the advanced bank reconciliation import file technical layout definitions and three related bank statement example files: [Import file examples](//download.microsoft.com/download/8/e/c/8ec8d2d0-eb8c-41fb-ad8c-f01a4d670a44/Dynamics365FinanceAdvancedBankStatementLayouts.xlsx)  

| Technical layout definition                             | Bank statement example file          |
|---------------------------------------------------------|--------------------------------------|
| DynamicsAXMT940Layout | [MT940StatementExample](//download.microsoft.com/download/2/d/c/2dcc4e55-ddc8-4a74-b79c-250fae201c3c/mt940StatementExample.txt)     |
| DynamicsAXISO20022Layout | [ISO20022StatementExample](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdownload.microsoft.com%2Fdownload%2F1%2F5%2F5%2F155d84ed-c250-48f3-b0b1-c5a431e7855b%2FISO20022-MultipleStatements.xml&data=04%7C01%7CRobert.Schlomann%40microsoft.com%7C30d0c233cb6546547d0a08d8f4965edc%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637528273956712775%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=3VzvLZK%2BO8PjuI7XVdC6rD2j3nUJfteo7zFp%2B1s9BwM%3D&reserved=0)             |
| DynamicsAXBAI2Layout    | [BAI2StatementExample](//download.microsoft.com/download/1/1/6/11693f57-bfc1-4993-a274-5fb978be70fa/BAI2StatementExample.txt)     |
