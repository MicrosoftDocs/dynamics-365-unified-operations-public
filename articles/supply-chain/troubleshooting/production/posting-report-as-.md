---
title: Posting - Report as finished journal gives the error "Quantity ordered cannot be reduced because there are not enough open inventory transactions with the ordered status"
description: Posting - Report as finished journal gives the error "Quantity ordered cannot be reduced because there are not enough open inventory transactions with the ordered status"
author: SmithaNataraj
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

# Posting - Report as finished journal gives the error "Quantity ordered cannot be reduced because there are not enough open inventory transactions with the ordered status"

KB Number: 4612891

## Issue description

Posting - Report as finished journal gives the error "Quantity ordered cannot be reduced because there are not enough open inventory transactions with the ordered status. The items are Purchased, Received or Registered."

It happens only when "Error quantity" is populated on the first journal line and "Good quantity" on the last journal line. If the "Error quantity" line is populated on last line in RAF journal , then  there is no error. 

## Resolution

This issue can be resolved by setting the production parameter Increase remain qty with error qty to Yes in the Production control parameters form.
