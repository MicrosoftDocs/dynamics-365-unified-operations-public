---
title: Customer account rename data maintenance
description: This article describes how to sync customer records that weren't updated during the rename process.
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

# Customer account rename data maintenance

On a customer record, the **Rename** function is used to rename the unique record of a customer. It updates all references from the old name to a new name that's entered. This function can fail for many reasons that are related to the table structure and the amount of data.

The **Customer account rename data maintenance** feature continues to process out-of-sync records (that is, records that have the old name). Therefore, all records are updated to the new name.

## Update customer records that weren't renamed

To update a customer record that wasn't successfully renamed, follow these steps.

1. In the **Feature management** workspace, select **All**.
1. Search for **Customer account rename data maintenance**.
1. Select the record.
1. Select **Enable Now**.
1. Go to **Credit and collections** \> **Inquiries and reports** \> **Data maintenance** \> **Customer account rename data maintenance**.
1. The page shows all records that haven't been updated. Select a record to continue the rename process.
