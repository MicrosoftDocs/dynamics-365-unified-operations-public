---
# required metadata

title: Positive pay overview
description: This article provides information about positive pay, which is used to generate an electronic list of checks that can be presented to a bank. 
author: angelad116
ms.date: 10/24/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BankPositivePaySummary
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: thweeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 1e3a39d3-f9b3-4073-9730-c96a607243e2
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Positive pay overview

[!include [banner](../includes/banner.md)]

This article provides information about positive pay, which is used to generate an electronic list of checks that can be presented to a bank. 

Positive pay is used to generate an electronic list of checks that can be presented to a bank. Positive pay files can help banks prevent check fraud. You set up positive pay to generate an electronic list of checks every time that checks are printed. Then, when a check is presented to the bank, the bank compares the check with the list of checks that you previously submitted. If the check matches a check in the list, the bank clears it. If the check doesn't match a check in the list, the bank holds it for review.

Positive pay is also known as SafePay. 

Positive pay files can contain sensitive information about payees and check amounts. Therefore, make sure that you use appropriate security measures from the time that the files are generated until they are received by the bank. Positive pay files are downloaded according to the download instructions for the web browser. 

Positive pay files are created by using data entities. Before you generate a positive pay file, you must set up the transformation formats for the XML that translates the data into a format that the bank can consume. 

For each bank account that you want to generate positive pay information for, you must assign the positive pay format. After you generate payments, you can generate a positive pay file for a single legal entity and a single bank account. Alternatively, you can generate positive pay files for multiple legal entities and bank accounts at the same time. 

After the checks that are listed in a positive pay file have been paid, you receive a confirmation number from your bank. You can then confirm the positive pay file in the system. 

If you must change a positive pay file, you can recall it. Then, for each check in the positive pay file, the field that indicates whether that check has been included in a positive pay file is reset.

For more information, see [Set up and generate positive pay files](set-up-generate-positive-pay-files.md).





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
