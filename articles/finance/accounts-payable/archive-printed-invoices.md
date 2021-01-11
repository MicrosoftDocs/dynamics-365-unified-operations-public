---
# required metadata

title: Archive printed customer invoices with hash numbers
description: This topic explains how to configure archiving of printed customer invoices with hash numbers.  
author: Ilya Kondratenko
manager: AnnBe
ms.date: 01/11/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2021-03-05
ms.dyn365.ops.version: 10.0.18

---

# Archive printed customer invoices with hash numbers

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

In some countries, there is a legal requirement to store culculated hash numbers together with printed outputs of some documents.
This topic explains how to configure archiving of printed customer invoices with hash numbers.

## Prerequisites

- The primary address of the legal entity must be in Italy.
- Italian sales tax books and sections are configured in the system. For more information, see [Italian sales tax books](emea-ita-fiscal-books.md).
- In the Feature management workspace, turn on the **(Italy) Unified posting date control** feature. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Configure posting date control
Complete the following steps to configure posting date control.

1. Go to **Tax** > **Setup** > **Sales tax** > **Italian sales tax book sections**. 
2. In the **Skip posting date control** column, select whether posting date control is required for a selected sales tax book section.

![Posting date control](media/emea-ita-post-date-control.jpg)

 - If the field isn't enabled, which is the default option, the system doesn't allow posting of new invoices with dates earlier than the date of the latest posted invoice.  
 - If the field is enabled, the system allows posting with any date.

