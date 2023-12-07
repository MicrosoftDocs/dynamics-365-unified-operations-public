---
title: Notification and registration for the NemHandelsRegistret in Denmark 
description: This article describes how to handle notification and registration with the NemHandelsRegistret in Denmark.
author: mrolecki
ms.date: 12/05/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: kfend
ms.search.validFrom: 2023-12-30
ms.dyn365.ops.version: Version 1611
ms.custom: 264824
ms.search.form: nemhandel, NemHandelsRegistret, notification, registration, denmark
---

# Notification and registration for the NemHandelsRegistret in Denmark

According to the Danish bookkeeping act, as of January 2024, all standard systems must notify users that they can register with the NemHandelsRegistret. They must also provide information about the registration functionality.

In addition, if the company isn't registered with the NemHandelsRegistret, a notification appears at the top of page and provides registration instructions.

## Notification about option to register

When you create a new legal entity with Denmark chosen as **Country/region**, a notification of the option to register in the Danish NemHandelsRegisteret (NHR) appears.   

You can complete the registration process directly from the notification, by selecting either the **Register in NemHandel** link or the **Review NemHandel’s registration guide** link. Both links direct you to the external Nemhandel content.

Existing users receive notification in a form of feature callout whenever you reach the Default Dashboard in a Danish legal entity, until you confirm you became familiar with the notification.

## Notification about not being registered

If the company isn't registered with the NemHandelsRegistret, you receive the following notification: "Your company is not registered in NemHandelsRegistret.". You can complete the registration process directly from the notification, by selecting the **Register in NemHandel** link. The link directs you to the external NemHandel's content.

If the company is already registered, valid Central Business Register (CVR) number and European Article Number (EAN) are entered in the **Registration IDs** for your **Legal entity**, the notification doesn't appear.

> [!NOTE]
> A notification appears on the **Legal entities** page for all the users having access to this page. Registration is confirmed based on the company's CVR number from the **Registration IDs** of the **Legal entity** through the API call to NemHandel.

## Registration with the NemHandelsRegistret 

To start registration, select the **Register in NemHandel** link in the notification. Before the external system calls are made, or before you open the NemHandelsRegistret registration form, you must confirm your consent.

After you complete the registration with the NemHandelsRegistret, and both Central Business Register (CVR) number and European Article Number (EAN) are entered, the existing notification disappears. 

> [!IMPORTANT]
> Entered Central Business Register (CVR) number and European Article Number (EAN) are used in electronic invoices.

## See also

[Registration IDs](https://review.learn.microsoft.com/en-us/dynamics365/finance/localizations/europe/emea-registration-ids?branch=pr-en-us-17322)  
[EAN Location Number](https://review.learn.microsoft.com/en-us/dynamics365/finance/localizations/europe/ean-number?branch=pr-en-us-17322)

