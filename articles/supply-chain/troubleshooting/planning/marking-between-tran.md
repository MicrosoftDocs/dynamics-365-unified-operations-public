---
title: Marking between Transfer order receipt and batch order is not working correctly when using "Firm and consolidate"
description: Marking between Transfer order receipt and batch order is not working correctly when using "Firm and consolidate"
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ReqTransPo,PmfBulkPlanConsolidate
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: angarmas
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Marking between Transfer order receipt and batch order is not working correctly when using "Firm and consolidate"

KB Number: 4612127

## Issue description

Marking between Transfer order receipt and batch order is not working correctly when using "Firm and consolidate"

## Resolution

Setting "no" for marking in explosion view has no effect only on the firming that particular order. When firming and consolidate is done that action has no effect. To change update marking behavior for firming go to Master planning parameters > Standard update.
