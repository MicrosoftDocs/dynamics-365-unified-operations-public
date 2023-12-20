---
title: European article numbering (EAN) location numbers
description: This article provides information about European article numbering (EAN) location numbers.
author: kfend
ms.date: 12/07/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: kfend
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 264824
ms.search.form: E
---

# European article numbering (EAN) location numbers

[!include [banner](../../includes/banner.md)]

A European article numbering (EAN) location number is an electronic address that you use when you send or receive an electronic invoice. It uniquely identifies a buyer's billing address. EAN location numbers can be used in countries/regions outside Europe and are sometimes referred to as Global Location Numbers (GLNs).

## EAN location numbers in Microsoft Dynamics 365 Finance

Departments, directorates, agencies, and other organizations in Denmark have EAN location numbers that uniquely identify a customer's billing address. An EAN location number can be defined as one category and type of registration ID. It's then used for a legal entity, customer, vendor, or any other party that supports registration IDs.

An EAN location number has a fixed length of 13 digits. This number must be processed in its entirety. Here's an example of an EAN location number:

5790987654321

EAN location numbers start with a three-digit prefix that's allocated by EAN International. For Denmark, the first three digits are **579**. The EAN location number ends with a check digit that's calculated based on the first 12 digits.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
