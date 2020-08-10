---
# required metadata

title: Confirm payment schedules in batch
description:  This topic walks through an example of the dual reporting capabilities in Asset leasing for both IFRS and statutory reporting. 
author: moaamer
manager: Ann Beebe
ms.date: 08/07/2020
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
ms.search.validFrom: 2020-08-07
ms.dyn365.ops.version: 10.0.14
---

# Dual reporting

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic walks through an example of the dual reporting capabilities in Asset leasing for both IFRS and statutory reporting. For purposes of this example, familiarity with posting layers in Dynamics is required.

## Fact Pattern

The lease below will be account for under both Italian statutory reporting under a cash-basis method and IFRS reporting methods. The company must establish three books in order to account for both Italian statutory requirements and IFRS 16 requirements -- a book for IFRS 16, a book for statutory requirements, and a book to automatically reverse the statutory postings. The book setup details are explained as follows.

This first book is to comply with the IFRS 16 accounting standard. All entries posted in this book will post to a custom layer.


