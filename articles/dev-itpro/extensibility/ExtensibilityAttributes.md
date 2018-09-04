---
# required metadata

title: Attributes making methods extensible
description: This article describes attributes making methods extensible.
author: mfp
manager: AnnBe
ms.date: 09/09/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 


# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfp
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Attributes making methods extensible

This topic describes the various attributes used to control extensibility capability for methods.

Default attributes based on access modifiers:

|Hookable |	Wrappable |	Replaceable |
|---------|----------|-----------|
| Private |	Not-supported |	Not-supported |	Not-supported |
| Protected |	Yes |	Yes |	No |
| Public | Yes |	Yes |	No |
