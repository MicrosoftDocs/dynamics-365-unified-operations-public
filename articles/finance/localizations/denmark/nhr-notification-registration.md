---
title: Notification and registration for the NemHandelsRegistret in Denmark
description: This article describes how to handle notification and registration with the NemHandelsRegistret (NHR) in Denmark.
author: mrolecki
ms.date: 12/07/2023
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

[!include [banner](../../includes/banner.md)]

According to the Danish bookkeeping act, as of January 2024, all standard systems must notify users that they can register with the NemHandelsRegistret (NHR). The system must also provide information about the registration functionality.

In addition, if the company isn't registered with the NHR, a notification appears at the top of the page and provides registration instructions.

## Notification about the option to register

When you create a new legal entity that's located in Denmark, a notification to register in the NHR appears. You can complete the registration process directly from the notification by selecting either the **Register in NemHandel** link or the **Review NemHandel's registration guide** link. Both links take you to the external NemHandel content.

Existing users receive a notification in the form of a feature callout whenever they open the default dashboard in a Danish legal entity. This notification continues to appear until it's confirmed.

## Notification about not being registered

If the company isn't registered with the NHR, you receive the following notification: "Your company is not registered in NemHandelsRegistret." You can complete the registration process directly from the notification by selecting the **Register in NemHandel** link. This link takes you to the external NemHandel content.

If the company is already registered, a valid Central Business Register (CVR) number and European Article Number (EAN) are entered in the registration IDs for your legal entity, and the notification doesn't appear.

> [!NOTE]
> A notification appears on the **Legal entities** page for all the users who have access to this page. Through an API call to NemHandel, registration is confirmed based on the company's CVR number from the registration IDs for the legal entity.

## Registration with the NHR

To begin registration, select the **Register in NemHandel** link in the notification. Before the external system calls are made, or before you open the NHR registration form, confirm your consent.

After you complete the registration with the NHR, and both the CVR number and EAN are entered, the existing notification disappears.

> [!IMPORTANT]
> The CVR number and EAN that you entered are used in electronic invoices.

## See also

[Registration IDs](../europe/emea-registration-ids.md)  
[European article numbering (EAN) location numbers](../europe/ean-number.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
