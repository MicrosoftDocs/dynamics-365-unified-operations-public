---
title: Packing station doesn't display product notes
description: Packing station doesn't display product notes
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: WHSPack
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Packing station doesn't display product notes

KB Number: 4614615

## Issue description

Packing notes aren't displayed on the packing form when the packing instructions attachment is added either to a product master or to a product variant.

## Resolution

This is the expected behavior.

The current logic for displaying packing notes on the packing form requires the notes to be associated with the shipments.
