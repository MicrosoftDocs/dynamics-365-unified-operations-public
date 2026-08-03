---
title: Positive pay overview
description: Learn about positive pay, which is used to generate an electronic list of checks that can be presented to a bank.
author: twheeloc
ms.author: twheeloc
ms.topic: overview
ms.date: 07/28/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: BankPositivePaySummary
ms.dyn365.ops.version: AX 7.0.1
ms.assetid: 1e3a39d3-f9b3-4073-9730-c96a607243e2
---

# Positive pay overview

[!include [banner](../includes/banner.md)]

This article provides information about positive pay, which is used to generate an electronic list of checks that you can present to a bank.

Use positive pay to generate an electronic list of checks that you present to a bank. Positive pay files can help banks prevent check fraud. Set up positive pay to generate an electronic list of checks every time that you print checks. Then, when you present a check to the bank, the bank compares the check with the list of checks that you previously submitted. If the check matches a check in the list, the bank clears it. If the check doesn't match a check in the list, the bank holds it for review.

Positive pay is also known as SafePay.

Positive pay files can contain sensitive information about payees and check amounts. Therefore, make sure that you use appropriate security measures from the time that the files are generated until they are received by the bank. Positive pay files are downloaded according to the download instructions for the web browser.

Positive pay files can contain sensitive information about payees and check amounts. Therefore, make sure that you use appropriate security measures from the time that the files are generated until the bank receives them. You download positive pay files according to the download instructions for the web browser.

For each bank account that you want to generate positive pay information for, you must assign the positive pay format. After you generate payments, you can generate a positive pay file for a single legal entity and a single bank account. Alternatively, you can generate positive pay files for multiple legal entities and bank accounts at the same time.

Create positive pay files by using data entities. Before you generate a positive pay file, set up the transformation formats for the XML that translates the data into a format that the bank can consume.

If you must change a positive pay file, you can recall it. Then, for each check in the positive pay file, the field that indicates whether that check has been included in a positive pay file is reset.

For more information, see [Set up and generate positive pay files](set-up-generate-positive-pay-files.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
