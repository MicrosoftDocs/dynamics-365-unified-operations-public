---
title: Release a dimension-based product master
description: This procedure shows how to release a product master, which will be used for the dimension-based configurations. 
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: EcoResProductListPage, EcoResProductRelease   
ms.topic: how-to
ms.date: 11/10/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Release a dimension-based product master

[!include [banner](../../includes/banner.md)]

This procedure shows how to release a product master, which will be used for the dimension-based configurations. It is a prerequisite that you have created a product master with the dimension-based configuration technology.

This is the second procedure [of an eight-procedure sequence](../dimension-based-product-configuration.md#sequence) that explains how to build combinations for dimension-based configuration. You should do all eight procedures, in order, because each new procedure builds on data created by the previous procedures. To work through this sequence by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed, and you must select the *USMF* legal entity before you begin.

1. Go to **Product information management \> Products \> Product masters**.
    * Filter the **Configuration technology** column so that only the dimension-based configuration is displayed. For example, you can filter the column by typing *Dimension*.
2. In the list, mark the selected row.
3. Select **Release products**.
4. Select **Next**.
    * For products that are crated with the dimension-based configuration technology, the product variants must be created in the company where the bill of materials will be created.  
5. Select **Next**.
6. In the list, find and select the desired record.
    * Select the company *USMF* for this procedure.  
7. Select **Next**.
8. Select **Finish**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]