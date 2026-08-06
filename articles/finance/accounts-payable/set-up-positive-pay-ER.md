---
title: Set up and generate positive pay files by using Electronic reporting
description: Learn about how to set up positive pay by using Electronic reporting, including outlines on security for positive pay files.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 07/28/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: BankPositivePayFormat
ms.dyn365.ops.version: AX 7.0.1
ms.assetid: 73f3dcf6-040a-44ad-9512-7b3e0d17a571
---

# Set up positive pay files by using Electronic reporting

This article explains how to set up positive pay and generate positive pay files by using Electronic reporting.

> [!NOTE]
> Before using the **Generate bank positive pay file** function, refresh the entity list first.
> Go to **Data management > Import / Export > Framework parameters**
> **Entity settings** FastTab, select **Refresh entity list**.

Set up positive pay to generate an electronic list of checks that you provide to the bank. When you present a check to the bank, the bank compares it with the list of checks. If the check matches a check in the list, the bank clears it. If the check doesn't match a check in the list, the bank holds it for review.

## Security for positive pay files

Positive pay files can contain sensitive information about payees and check amounts. Therefore, use appropriate security measures from the time you generate the files until the bank receives them. Your web browser downloads positive pay files to the location you specify. Because positive pay files can contain sensitive information, it's important that only authorized users can generate and view this information in Microsoft Dynamics 365 Finance. Use the following table to help you determine the required privileges.

| Task | Privilege |
|------|-----------|
| Generate positive pay files from the **Bank accounts** list page or the **Bank accounts** page. | <ul><li>**Maintain bank positive pay information** (BankPositivePayProcess)</li><li>**BankPositivePayExportEntityView** (BankPositivePayExportEntityView)</li></ul> |
| Generate positive pay files for multiple legal entities and bank accounts from the **Generate a positive pay file** page. | <ul><li>**Maintain bank positive pay information** (BankPositivePayProcess)</li><li>**BankPositivePayExportEntityView** (BankPositivePayExportEntityView)</li></ul> |
| View positive pay files on the **Positive pay file summary** page. | **View bank positive pay information for multiple legal entities** (BankPositivePayView) |
| Confirm a bank positive pay file on the **Positive pay file summary** page. | **Confirm positive payment file** (BankPositivePayConfirm) |
| Recall a bank positive pay file on the **Positive pay file summary** page. | **Recall positive pay file** (BankPositivePayRecall) |

## Set up the Electronic reporting configuration

1. Go to **Workspaces > Electronic reporting**.
1. On the tile for the **Microsoft** configuration provider, select **Repositories**.
1. Select **Global**, and then select **Open**.
1. If you need to connect to the repository, select the blue link in the dialog box.
1. In the configuration list, find and select **Positive pay model > Positive pay format**.
1. On the **Versions** FastTab, select the latest version, and then select **Import**.

## Set up a positive pay format

1. Go to **Cash and bank management > Setup > Positive pay formats**.
1. Select **New**.
1. Set the **Payment format** and **Description** fields.
1. Select the **Generic electronic export format** checkbox.
1. Set the **Export format configuration** field to **Positive pay format**.

## Assign a positive pay format to a bank account

For each bank account that you want to generate positive pay information for, assign the positive pay format that you specified in the previous section. On the **Bank accounts** page, select the positive pay format that corresponds to the bank account. In the **Positive pay start date** field, enter the first date to generate positive pay files.

> [!IMPORTANT]
> Enter a date in the **Positive pay start date** field. If you leave this field blank, the first positive pay file that is generated includes all checks that are created for this bank account.

1. Go to **Cash and bank management > Banks accounts > Bank accounts**.
1. Open the bank account.
1. On the **General** FastTab, set the **Positive pay format** field to the format that you created earlier.
1. Set the **Positive pay start date** field to the current date.

## Assign a number sequence for positive pay files

Each positive pay file must have a unique number. On the **Cash and bank management parameters** page, create a number sequence for positive pay files on the **Number sequences** tab.

## Generate a positive pay file for a single bank account

You can generate a positive pay file for a single legal entity and a single bank account. For information about how to generate positive pay files for multiple legal entities and bank accounts at the same time, see the next section. To generate a positive pay file for a single legal entity and a single bank account, open the **Generate a positive pay file** dialog box from the **Bank accounts** page. In the **Cut-off date** field, enter the last check date to include in the positive pay file. The file includes all checks that aren't included in a positive pay file by the end of this check date.

1. Go to **Cash and bank management > Bank Accounts > Bank Accounts**.
1. Open a bank account that you set up for positive pay.
1. Select **Manage payments > Positive pay > Positive pay file**.
1. Set the **Cut-off date** field. The file includes checks that you generated before this date.

## Generate a positive pay file for multiple bank accounts

To generate a positive pay file for multiple bank accounts, use the **Positive pay file** periodic task. Select the positive pay format for the file, and specify whether to generate the file for all legal entities or for a selected legal entity. You can also generate the positive pay file for all bank accounts that use the specified positive pay format or for a selected bank account. In the **Cut-off date** field, enter the last check date to include in the positive pay file. The file includes all checks that aren't included in a positive pay file by the end of this check date.

## View the results of positive pay file generation

After the system generates the positive pay file, you can view the results on the **Positive pay file summary** page. To view the details of the individual checks, go to the **Positive pay file details** page.

## Confirm a positive pay file

After you pay the checks that are listed in a positive pay file, you receive a confirmation number from your bank. You can then confirm the positive pay file. On the **Positive pay file summary** page, select a positive pay file that has a status of **Created**, and then select the **Enter confirmation** action. When you confirm a positive pay file, the confirmation number that you received from the bank is recorded.

## Recall a positive pay file

If you need to change a positive pay file, you can recall it. On **Positive pay file summary**, select a positive pay file with the **Created** status, and then select **Recall**. For each check in the positive pay file, the field that indicates whether the check is included in a positive pay file is reset. You can then create a new positive pay file that includes the check you recalled.

The XML file is downloaded.
