---
title: Error when the Report as finished journal is posted
description: When you post the Report as finished journal, you receive an error message that states that the ordered quantity ordered can't be reduced.
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

# Error when the Report as finished journal is posted

KB number: 4612891

## Symptoms

When you post the **Report as finished** journal, an error occurs, and you receive the following error message:

> Quantity ordered cannot be reduced because there are not enough open inventory transactions with the ordered status. The items are Purchased, Received or Registered.

This error occurs only when the **Error quantity** field is set on the first line of the **Report as finished** journal, and the **Good quantity** field is set on the last line. If the **Error quantity** field is set on the last line, no error occurs.

## Resolution

To prevent this error, open the **Production control parameters** page, and then, on the **General** tab, set the **Increase remain qty with error qty** option to *Yes*.
