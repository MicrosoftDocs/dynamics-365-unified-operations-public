---
# required metadata

title: Compound interval functionality
description: This topic describes how to choose between compounding levels of monthly, quarterly, semiannual, or annual.
author: moaamer
manager: Ann Beebe
ms.date: 08/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-08-06
ms.dyn365.ops.version: 10.0.14
---

# Compound interval functionality

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes how to choose between compounding levels of monthly, quarterly, semiannual, or annual. The compounding interval functionality is used to determine the number of compounding periods per year in a lease's payment schedule. The following examples illustrate how a lease's payment schedule would appear using each of the 4 different interval choices.

The user is unable to select a compounding interval that is less frequent than the lease's payment frequency. For example, there cannot be a quarterly compounding interval with a monthly payment frequency, or an annual compounding interval with a semiannual payment frequency. If the user attempts this, a warning will be thrown.
Note: These 4 examples showcase compounding intervals with matching payment frequencies.

Setup for all 4 leases:
