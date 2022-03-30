---
# required metadata
title: Set up and generate positive pay files using Electronic reporting.
description: This topic explains how to set up positive pay using Electronic reporting. 
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

# Set up positive pay files using Electronic reporting

Set up positive pay to generate an electronic list of checks that is provided to the bank. Then, when a check is presented to the bank, the bank compares it with the 
list of checks. If the check matches a check in the list, the bank clears it. If the check doesn't match a check in the list, the bank holds it for review.


## Set up the **Electronic reporting** configuration
1. Go to **Workspaces > Electronic reporting**.
2. On the **Microsoft configuration provider** tile, click **Repositories**.
3. Select **Global** and click **Open**.
4. Connect to the repository if needed by clicking the blue link in the dialog.
5. In the configuration list, find and select **Positive pay model > Positive pay format**.
6. On the **Versions** FastTab, select the latest version and click **Import**.

## Set up Positive pay format
1. Go to **Cash and Bank Management > Setup > Positive pay formats**.
2. Click **New**.
3. Set the **Payment format** and **Description**.
4. Select the **Generic electronic export format** checkbox.
5. Set **Export format configuration** to **Positive pay format**.

## Set up Bank Account
1. Go to **Cash and Bank Management > Banks accounts > Bank accounts**.
2. Open the bank account.
3. On the **General** FastTab, set **Positive pay format** to the format created earlier.
4. Set the **Positive pay start date** to today’s date.

## Generate positive pay file
1. Go to **Cash and Bank Management > Bank Accounts > Bank Accounts**.
2. Open a bank account that has Positive pay set up.
3. Click **Manage payments > Positive pay > Positive pay file**.
4. Set the **Cut-off date**. Checks that were generated prior to this date will be included.
5. The resulting XML file will be downloaded. 
