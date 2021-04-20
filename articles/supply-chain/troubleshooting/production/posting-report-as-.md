---
title: Error on posting report as finished journal
description: On posting the report as finished journal, the following error is shown - "Quantity ordered cannot be reduced because there are not enough open inventory transactions with the ordered status"
author: johanhoffmann
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ProdTableListPage, ProdParameters
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Error on posting report as finished journal

KB Number: 4612891

## Symptoms

On posting the *Report as finished* journal, the following error is shown:

> Quantity ordered cannot be reduced because there are not enough open inventory transactions with the ordered status. The items are Purchased, Received or Registered.

This error only occurs when **Error quantity** is populated on the first journal line and **Good quantity** on the last journal line. If the **Error quantity** line is populated on last line in *Report as finished* journal, then there is no error.

## Resolution

To prevent this error, open the **General** tab of the **Production control parameters page** and set **Increase remain qty with error qty** to *Yes*.
