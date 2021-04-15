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
<!-- KFM: This topic is not clear. Please clarify or remove. -->
# Marking between transfer order receipt and batch order is not working correctly when using "Firm and consolidate"

KB Number: 4612127

## Issue description
<!-- KFM: In what way does it work incorrectly? -->
Marking between Transfer order receipt and batch order is not working correctly when using "Firm and consolidate".

## Resolution
<!-- KFM: More detail is needed. Where are these settings? Which setting needs to be changed on Master planning parameters? -->

Setting "no" for marking in explosion view has no effect only on the firming of that particular order. When firming and consolidate is done, that action has no effect. To change update marking behavior for firming go to Master planning parameters > Standard update.
