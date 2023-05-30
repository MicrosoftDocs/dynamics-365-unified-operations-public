---
# required metadata
title: Set up and generate positive pay files by using Electronic reporting
description: This article explains how to set up positive pay by using Electronic reporting.
author: panolte
ms.date: 03/20/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BankPositivePayFormat
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 73f3dcf6-040a-44ad-9512-7b3e0d17a571
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Set up positive pay files by using Electronic reporting

This article explains how to set up positive pay and generate positive pay files by using Electronic reporting.

> [!NOTE] 
> Before using the **Generate bank positive pay file** function, you will need to refresh the entity list first.
> Go to **Data management > Import / Export > Framework parameters** 
> **Entity settings** FastTab, select **Refresh entity list**.


Set up positive pay to generate an electronic list of checks that is provided to the bank. When a check is presented to the bank, the bank compares it with the list of checks. If the check matches a check in the list, the bank clears it. If the check doesn't match a check in the list, the bank holds it for review.

## Security for positive pay files
Positive pay files can contain sensitive information about payees and check amounts. Therefore, make sure that you use appropriate security measures from the time that the files are generated until they are received by the bank. Positive pay files are downloaded to the location that is specified by your web browser. Because positive pay files can contain sensitive information, it's important that only authorized users have access to generate and view this information in Microsoft Dynamics 365 Finance. Use the following table to help you determine the privileges that are required.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Task</th>
<th>Privilege</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Generate positive pay files from the <strong>Bank accounts</strong> list page or the <strong>Bank accounts</strong> page.</td>
<td><ul>
<li><strong>Maintain bank positive pay information</strong> (BankPositivePayProcess)</li>
<li><strong>BankPositivePayExportEntityView</strong> (BankPositivePayExportEntityView)</li>
</ul></td>
</tr>
<tr class="even">
<td>Generate positive pay files for multiple legal entities and bank accounts from the <strong>Generate a positive pay file</strong> page.</td>
<td><ul>
<li><strong>Maintain bank positive pay information</strong> (BankPositivePayProcess)</li>
<li><strong>BankPositivePayExportEntityView</strong> (BankPositivePayExportEntityView)</li>
</ul></td>
</tr>
<tr class="odd">
<td>View positive pay files on the <strong>Positive pay file summary</strong> page.</td>
<td><strong>View bank positive pay information for multiple legal entities</strong> (BankPositivePayView)</td>
</tr>
<tr class="even">
<td>Confirm a bank positive pay file on the <strong>Positive pay file summary</strong> page.</td>
<td><strong>Confirm positive payment file</strong> (BankPositivePayConfirm)</td>
</tr>
<tr class="odd">
<td>Recall a bank positive pay file on the <strong>Positive pay file summary</strong> page.</td>
<td><strong>Recall positive pay file</strong> (BankPositivePayRecall)</td>
</tr>
</tbody>
</table>

## Set up the Electronic reporting configuration

1. Go to **Workspaces \> Electronic reporting**.
2. On the tile for the **Microsoft** configuration provider, select **Repositories**.
3. Select **Global**, and then select **Open**.
4. If a connection to the repository must be established, select the blue link in the dialog box.
5. In the configuration list, find and select **Positive pay model \> Positive pay format**.
6. On the **Versions** FastTab, select the latest version, and then select **Import**.

## Set up a positive pay format

1. Go to **Cash and bank management \> Setup \> Positive pay formats**.
2. Select **New**.
3. Set the **Payment format** and **Description** fields.
4. Select the **Generic electronic export format** checkbox.
5. Set the **Export format configuration** field to **Positive pay format**.

## Assign a positive pay format to a bank account
For each bank account that you want to generate positive pay information for, you must assign the positive pay format that you specified in the previous section. On the Bank accounts page, select the positive pay format that corresponds to the bank account. In the **Positive pay start date** field, enter the first date to generate positive pay files. 

>[!Important]
> Enter a date in the **Positive pay start date** field field. If left blank, the first positive pay file that is generated will include all checks that have been created for this bank account.

1. Go to **Cash and bank management \> Banks accounts \> Bank accounts**.
2. Open the bank account.
3. On the **General** FastTab, set the **Positive pay format** field to the format that was created earlier.
4. Set the **Positive pay start date** field to the current date.

## Assign a number sequence for positive pay files
Each positive pay file must have a unique number. On the **Cash and bank management parameters** page, create a number sequence for positive pay files on the **Number sequences** tab.

## Generate a positive pay file for a single bank account
You can generate a positive pay file for a single legal entity and a single bank account. For information about how to generate positive pay files for multiple legal entities and bank accounts at the same time, see the next section. To generate a positive pay file for a single legal entity and a single bank account, open the **Generate a positive pay file** dialog box from the **Bank accounts** page. In the **Cut-off date** field, enter the last check date to include in the positive pay file. All checks that haven’t been included in a positive pay file by the end of this check date are included in the file.

1. Go to **Cash and bank management \> Bank Accounts \> Bank Accounts**.
2. Open a bank account that positive pay is set up for.
3. Select **Manage payments \> Positive pay \> Positive pay file**.
4. Set the **Cut-off date** field. Checks that were generated before this date will be included.

## Generate a positive pay file for multiple bank accounts
To generate a positive pay file for multiple bank accounts, use the **Positive pay file** periodic task. Select the positive pay format for the file, and specify whether to generate the file for all legal entities or for a selected legal entity. You can also generate the positive pay file for all bank accounts that use the specified positive pay format or for a selected bank account. In the **Cut-off date** field, enter the last check date to include in the positive pay file. All checks that haven’t been included in a positive pay file by the end of this check date are included in the file.

## View the results of positive pay file generation
After the positive pay file is generated, you can view the results on the **Positive pay file summary** page. To view the details of the individual checks, go to the **Positive pay file details** page.

## Confirm a positive pay file
After the checks that are listed in a positive pay file have been paid, you receive a confirmation number from your bank. You can then confirm the positive pay file. On the **Positive pay file summary** page, select a positive pay file that has a status of **Created**, and then select the **Enter confirmation** action. When you confirm a positive pay file, the confirmation number that you received from the bank is recorded.

## Recall a positive pay file
If you must change a positive pay file, you can recall it. On the **Positive pay file summary** page, select a positive pay file that has a status of **Created**, and then select the **Recall** action. For each check in the positive pay file, the field that indicates whether that check has been included in a positive pay file is reset. You can then create a new positive pay file that includes the check that was recalled.


The resulting XML file will be downloaded.
