---
title: Create a dimension-based product master
description: This procedure shows how to create a new product master with dimension-based configuration technology. 
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: EcoResProductListPage, EcoResProductCreate, EcoResProductMasterDraftFormPart
ms.topic: how-to
ms.date: 11/10/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Create a dimension-based product master

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a new product master with dimension-based configuration technology.

This is the first procedure [of an eight-procedure sequence](../dimension-based-product-configuration.md#sequence) that explains how to build combinations for dimension-based configuration. You should do all eight procedures, in order, because each new procedure builds on data created by the previous procedures. To work through this sequence by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed, and you must select the *USMF* legal entity before you begin.

1. Go to **Product information management \> Products \> Product masters**.
2. Select **New**.
3. In the **Product number** field, type a value.
    * Entering a product number is mandatory if no number sequence has been set up for the product number field.  
4. In the **Product name** field, type a value.
5. In the **Product dimension group** field, select the drop-down button to open the lookup.
6. In the list, find and select the desired record.
    * Select the configuration dimension for this procedure.  
7. In the list, select the link in the selected row.
8. In the **Configuration technology** field, select an option.
    * Select the dimension-based configuration technology.  
9. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]