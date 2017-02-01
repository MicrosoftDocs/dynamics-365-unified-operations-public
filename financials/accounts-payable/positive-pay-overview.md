---
# required metadata

title: Positive pay overview | Microsoft Docs
description: This article provides information about positive pay, which is used to generate an electronic list of checks that can be presented to a bank. 
author: twheeloc
manager: AnnBe
ms.date: 2016-05-23 15:48:40
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 101
ms.suite: Released- Dynamics AX application 7.0.1
# ms.tgt_pltfrm: 
ms.custom: 88463
ms.assetid: b8366a14-c3d8-433e-bf85-57542669617f
ms.region: Global
# ms.industry: 
ms.author: abruer

---

# Positive pay overview

This article provides information about positive pay, which is used to generate an electronic list of checks that can be presented to a bank. 

Positive pay is used to generate an electronic list of checks that can be presented to a bank. Positive pay files can help banks prevent check fraud. You set up positive pay to generate an electronic list of checks every time that checks are printed. Then, when a check is presented to the bank, the bank compares the check with the list of checks that you previously submitted. If the check matches a check in the list, the bank clears it. If the check doesn't match a check in the list, the bank holds it for review. Positive pay is also known as SafePay. Positive pay files can contain sensitive information about payees and check amounts. Therefore, make sure that you use appropriate security measures from the time that the files are generated until they are received by the bank. Positive pay files are downloaded according to the download instructions for the web browser. Positive pay files are created by using data entities. Before you generate a positive pay file, you must set up the transformation formats for the XML that translates the data into a format that the bank can consume. For each bank account that you want to generate positive pay information for, you must assign the positive pay format. After you generate payments, you can generate a positive pay file for a single legal entity and a single bank account. Alternatively, you can generate positive pay files for multiple legal entities and bank accounts at the same time. After the checks that are listed in a positive pay file have been paid, you receive a confirmation number from your bank. You can then confirm the positive pay file in Microsoft Dynamics 365 for Operations. If you must change a positive pay file, you can recall it. Then, for each check in the positive pay file, the field that indicates whether that check has been included in a positive pay file is reset.

See also
--------

[Set up and generate positive pay files](https://docs.microsoft.com/en-us/dynamics365/operations/financials/accounts-payable/set-up-and-generate-positive-pay-files)

