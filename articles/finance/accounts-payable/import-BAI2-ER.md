---
title: Set up advanced bank reconciliation import by using Electronic reporting
description: Learn about how to use Electronic reporting to set up the advanced bank reconciliation import process, including a step-by-step process.
author: twheeloc
ms.author: shpandey
ms.topic: how-to
ms.date: 04/01/2026
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

The Advanced bank reconciliation feature lets you import electronic bank statements and automatically reconcile them with bank transactions in Microsoft Dynamics 365 Finance. This article explains how to set up the import functionality for your bank statements. The setup for bank statement import varies, depending on the format of your electronic bank statement. Microsoft Dynamics 365 Finance supports three bank statement formats: ISO20022, MT940, and BAI2.

## Set up the Electronic reporting configuration

1. Go to **Workspaces** > **Electronic reporting**.
1. On the tile for the **Microsoft** configuration provider, select **Repositories**.
1. Select **Dataverse**, and then select **Open**. For more details, see [Import Electronic reporting (ER) configurations from Dataverse](../../finance/localizations/global/workspace/gsw-import-er-config-dataverse.md).
1. If you need to establish a connection to the repository, select the blue link in the dialog box.
1. In the configuration list, find **Advanced bank reconciliation statement model > ABR BAI2 format**. MT940 and ISO20022/camt053 formats are also available.
1. Select the **ABR BAI2 format**.
1. On the **Versions** FastTab, select the latest version, and then select **Import**.

## Set up the bank statement format

1. Go to **Cash and bank management** > **Setup** > **Advanced bank reconciliation setup** > **Bank statement format**.
1. Select **New**.
1. Set the **Statement format** and **Name** fields.
1. Select the **Generic electronic import format** checkbox.
1. Set the **Import format configuration** field to the **BAI2** format.

## Set up the bank account

1. Go to **Cash and bank management > Bank accounts > Bank accounts**.
1. Open the bank account.
1. On the **Reconciliation** FastTab, set the **Advanced bank reconciliation** option to **Yes**.
1. Set the **Statement format** field to the **BAI2** format that you created earlier.

## Import the bank statement

1. Go to **Cash and bank management > Bank statement reconciliation > Bank statements**.
1. At the top of the **Bank statements** page, select **Import statement**.
1. Set the **Bank account** field to the bank account in the statement.
1. Set the **Statement format** field to the **BAI2** format that you created earlier.
1. Select **Browse**, and select the **BAI** file.
1. Select **Upload**.
1. Select **OK** to import the selected file.

## Examples of bank statement formats and technical layouts

The following table shows examples of the advanced bank reconciliation import file technical layout definitions and three related bank statement example files: [Import file examples](//download.microsoft.com/download/8/e/c/8ec8d2d0-eb8c-41fb-ad8c-f01a4d670a44/Dynamics365FinanceAdvancedBankStatementLayouts.xlsx)  

| Technical layout definition                             | Bank statement example file          |
|---------------------------------------------------------|--------------------------------------|
| DynamicsAXMT940Layout | [MT940StatementExample](//download.microsoft.com/download/2/d/c/2dcc4e55-ddc8-4a74-b79c-250fae201c3c/mt940StatementExample.txt)     |
| DynamicsAXISO20022Layout | [ISO20022StatementExample](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdownload.microsoft.com%2Fdownload%2F1%2F5%2F5%2F155d84ed-c250-48f3-b0b1-c5a431e7855b%2FISO20022-MultipleStatements.xml&data=04%7C01%7CRobert.Schlomann%40microsoft.com%7C30d0c233cb6546547d0a08d8f4965edc%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637528273956712775%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=3VzvLZK%2BO8PjuI7XVdC6rD2j3nUJfteo7zFp%2B1s9BwM%3D&reserved=0)             |
| DynamicsAXBAI2Layout    | [BAI2StatementExample](//download.microsoft.com/download/1/1/6/11693f57-bfc1-4993-a274-5fb978be70fa/BAI2StatementExample.txt)     |
