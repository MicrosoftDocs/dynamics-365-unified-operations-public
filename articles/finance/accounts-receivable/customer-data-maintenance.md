---
title: Customer account rename data maintenance
description: This article describes how to synchronize customer records that didm't finish during the rename process
author: JodiChristiansen
ms.author: twheeloc
ms.topic: article
ms.date: 04/26/2024
ms.custom: 
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom:
ms.search.form: 
ms.dyn365.ops.version: 
---

# Customer data maintenance

On a customer record, the **Rename** function is used to rename the unique record of a customer. This updates all references from an old name to the new name entered. This action can fail for a number of reasons related to table structure and the amount of data. 

The **Customer account rename data maintenance** feature allows out of sync records (the ones with the old account) to continue processing so all records are updated to the new name. 

## Customer account rename data maintenance

To update a customer name, follow these steps:
1. In the **Feature management** workspace, select **All**.
2. Search for **Customer account rename data maintenance**.
3. Select the record.
4. Select **Enable Now**.
5. Go to **Credit and collections > Inquiries and reports > Data maintenance > Customer account rename data maintenance**.
6. Any records that haven't been updated are displayed.
7. Select the record to contine the rename process. 
