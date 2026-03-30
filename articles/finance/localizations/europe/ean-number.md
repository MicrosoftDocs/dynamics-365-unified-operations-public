---
title: European article numbering (EAN) location numbers
description: Learn about European article numbering (EAN) location numbers, including an outline on EAN location numbers in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: overview
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.custom: 
  - bap-template
---

# European article numbering (EAN) location numbers

[!include [banner](../../includes/banner.md)]

A European article numbering (EAN) location number is an electronic address that you use when you send or receive an electronic invoice. It uniquely identifies a buyer's billing address. EAN location numbers can be used in countries/regions outside Europe and are sometimes referred to as Global Location Numbers (GLNs).

## EAN location numbers in Microsoft Dynamics 365 Finance

Departments, directorates, agencies, and other organizations in Denmark have EAN location numbers that uniquely identify a customer's billing address. You can define an EAN location number as one category and type of registration ID. Use it for a legal entity, customer, vendor, or any other party that supports registration IDs.

An EAN location number has a fixed length of 13 digits. You must process this number in its entirety. Here's an example of an EAN location number:

5790987654321

EAN location numbers start with a three-digit prefix that's allocated by EAN International. For Denmark, the first three digits are **579**. The EAN location number ends with a check digit that's calculated based on the first 12 digits.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
