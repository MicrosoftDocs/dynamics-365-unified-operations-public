---
# required metadata

title: Set up advanced bank reconciliation import by using Electronic reporting
description: This topic explains how to use Electronic reporting to set up the advanced bank reconciliation import process for BAI2 statements.
author: panolte
ms.date: 03/30/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BankStatementFormat
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 88433
ms.assetid: 73f3dcf6-040a-44ad-9512-7b3e0d17a571
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 10.0.25

---
# Set up advanced bank reconciliation import by using Electronic reporting

[!include [banner](../includes/banner.md)]

The Advanced bank reconciliation feature lets you import electronic bank statements and automatically reconcile them with bank transactions in Microsoft Dynamics 365 Finance. This topic explains how to set up the import functionality for your BAI2 bank statements.

## Set up the Electronic reporting configuration

1. Go to **Workspaces \> Electronic reporting**.
2. On the tile for the **Microsoft** configuration provider, select **Repositories**.
3. Select **Global**, and then select **Open**.
4. If a connection to the repository must be established, select the blue link in the dialog box.
5. In the configuration list, find **Bank statement model \> Bank statement model of BAI2**.
6. Select the **BAI2** format.
7. On the **Versions** FastTab, select the latest version, and then select **Import**.

## Set up the bank statement format

1. Go to **Cash and bank management \> Setup \> Advanced bank reconciliation setup \> Bank statement format**.
2. Select **New**.
3. Set the **Statement format** and **Name** fields.
4. Select the **Generic electronic import format** checkbox.
5. Set the **Import format configuration** field to the **BAI2** format.

## Set up the bank account

1. Go to **Cash and bank management \> Bank accounts \> Bank accounts**.
2. Open the bank account.
3. On the **Reconciliation** FastTab, set the **Advanced bank reconciliation** option to **Yes**.
4. Set the **Statement format** field to the **BAI2** format that was created earlier.

## Import the bank statement

1. Go to **Cash and bank management \> Bank statement reconciliation \> Bank statements**.
2. At the top of the **Bank statements** page, select **Import statement**.
3. Set the **Bank account** field to the bank account in the statement.
4. Set the **Statement format** field to the **BAI2** format that was created earlier.
5. Select **Browse**, and select the **BAI** file.
6. Select **Upload**.
7. Select **OK** to import the selected file.
