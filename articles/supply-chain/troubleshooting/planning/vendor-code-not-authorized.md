---
# required metadata

title: How to resolve - Vendor code %1 is not authorized for %2 on %3.
description: How to resolve - Vendor code %1 is not authorized for %2 on %3.
author: SmithaNataraj
manager: tfehr
ms.date: 3/24/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqTransPO_ReqTransPoMarkFirm
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: niwang@microsoft.com

---

# How to resolve - Vendor code %1 is not authorized for %2 on %3.

Error code: SYP4881415

When an item line is added to a purchase order, there display a warning or error message "Vendor code %1 is not authorized for %2 on %3."

## Symptoms
When an item line is added to a purchase order, there display a warning or error message "Vendor code %1 is not authorized for %2 on %3."

## Cause
This is because "Approved vendor check method" is either set as "Warning only" or "Not allowed" for the item.

## Resolution
1. Go to Product information management > Products > Released products, find the item
2. Go to Released product details > Purchase tab
3. Find field "Approved vendor check method" under field group "APPROVED VENDOR" field group, and set expected value

Or
1. Go to Product information management > Products > Released products, find the item
2. Go to upper button groups  > Purchase, click "Setup" under "Approved vendor" button groups
3. Create a new record to add vendor that is approved for the item



