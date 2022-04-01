---
# required metadata
title: Set up and generate positive pay files by using Electronic reporting
description: This topic explains how to set up positive pay by using Electronic reporting.
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
ms.custom: 88433
ms.assetid: 73f3dcf6-040a-44ad-9512-7b3e0d17a571
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Set up positive pay files by using Electronic reporting

Set up positive pay to generate an electronic list of checks that is provided to the bank. Then, when a check is presented to the bank, the bank compares it with the list of checks. If the check matches a check in the list, the bank clears it. If the check doesn't match a check in the list, the bank holds it for review.

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

1. Go to **Cash and bank management \> Banks accounts \> Bank accounts**.
2. Open the bank account.
3. On the **General** FastTab, set the **Positive pay format** field to the format that was created earlier.
4. Set the **Positive pay start date** field to the current date.

## Generate a positive pay file

1. Go to **Cash and bank management \> Bank Accounts \> Bank Accounts**.
2. Open a bank account that positive pay is set up for.
3. Select **Manage payments \> Positive pay \> Positive pay file**.
4. Set the **Cut-off date** field. Checks that were generated before this date will be included.

The resulting XML file will be downloaded.
