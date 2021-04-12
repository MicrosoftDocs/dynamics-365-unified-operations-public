---
title: Flushing principle not respected
description: Flushing principle not respected
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: PurchTable,ProdParameters
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Flushing principle not respected

KB Number: 4612725

## Issue description

When the Automatic BOM consumption parameter in Receive Purchase order section of the Automatic update tab is set to Flushing principle, all BOM lines are auto consumed when the PO is received, including those BOM lines set to Manual. BOM lines set to Manual should not be auto consumed by definition.

## Resolution

Please check the setting of Automatic BOM consumption in the production control parameters by site. In standard demo data it is set to Always which means that the flushing principles on the BOM lines will be disregarded and always flushed. Try set it to Flushing principle instead.
