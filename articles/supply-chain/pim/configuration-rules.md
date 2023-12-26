---
# required metadata

title: Configuration rules
description: This article provides general information about configuration rules. Configuration rules define relationships between items in a bill of materials (BOM) for products that use the dimension-based configuration technology.
author: t-benebo
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BOMConfigRule
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: e4c6622d-1e2d-4a4d-8047-c553a25d4f87
ms.search.region: Global
# ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configuration rules

[!include [banner](../includes/banner.md)]

This article provides general information about configuration rules. Configuration rules define relationships between items in a bill of materials (BOM) for products that use the dimension-based configuration technology.

Configuration rules are available when you define dimension-based configuration models. Configuration rules are used to either enforce or prohibit specific item combinations in a bill of materials (BOM). After a BOM has been created and the relevant items have been assigned to their respective configuration groups, one or more configuration rules can be defined. If two items belong together, the **Select** operator is used to ensure inclusion. If two items are mutually exclusive, the **Deselect** operator is used to ensure exclusion.  

**Note:** This information applies only to product masters that use the dimension-based configuration technology.  

Existing configurations aren't affected by subsequent changes to the configuration rules. However, it's important that you set the rules before you define a new configuration, and that you check the rules if you think they have been changed.  

**Note:** For the **Select** method, the derived configuration group, item number, and configuration are automatically selected. For the **Deselect** method, the derived configuration group, item number, and configuration can't be selected.

## Additional resources

[Dimension-based product configuration overview](dimension-based-product-configuration.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]