---
title: Can't change the effective date for an approved vendor
description: The Approved vendor list by product entity doesn't allow the effective date to be changed
author: kamaybac
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: PurchTable, PurchTablePart
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.13
---

# Can't change the effective date for an approved vendor


## Symptoms

A product has an approved vendor that has, for example, an effective date of January 11, 2018 (*01/11/2018*), and an expiration date of *Never*. If you try to change the effective date to January 10, 2018 (*01/10/2018*), or January 12, 2018 (*01/12/2018*), you receive the following error:

> Cannot create a record in Approved supplier list (PdsApproveVendorList). The 'Expiration' value needs to be greater than or equal to the 'Effective' value.

## Resolution

You can only extend the period that the vendor is approved for. The following rules apply:

- To change the effective date so that it's earlier than any of the existing records (periods) for the item vendor, the expiration date of the new period must be before all the expiration dates in the existing records.
- To change the expiration date so that it's later than any of the existing periods, the effective date must be after the latest expiration date in any existing record.
- To reduce the overall period that the vendor is approved for, you must delete or modify existing records. Alternatively, you can use the **truncate** switch during import. This switch deletes all existing records in the table for approved vendors by item.

For the example scenario that is described in the issue description, where a record has an effective date of *01/11/2018* and an expiration date of *Never*, you can import a new record that has an effective date of *01/10/2018* and an expiration date of *Never*. However, you can't reduce the period so that the effective date is updated to *01/12/2018* via data management. You must make this change through the UI.
