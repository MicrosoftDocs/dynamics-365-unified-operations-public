---
title: Maximum number of decimals for the stock keeping unit is 0
description: When you try to post an inventory transaction or an inventory reservation, you receive error "Maximum number of decimals for the stock keeping unit is 0".
author: sherry-zheng
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: 
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: chuzheng
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.16
---

# Maximum number of decimals for the stock keeping unit is 0


## Symptoms

When you try to post an inventory transaction or an inventory reservation, you receive the following error message:

> Maximum number of decimals for the stock keeping unit is 0.

This issue occurs when the inventory transaction quantity is specified as a decimal value that is below the level of precision that the field supports. For example, a quantity of *0.5* has been specified for an inventory transaction, but only integer quantities are supported. Therefore, the value should be *1* instead of *0.5*.

## Resolution

1. Run the following script on your SQL Server instance to round quantities in the inventory transactions. This script will correct values in the **inventTrans** table.

    ```sql
    update it set it.QTY = round(it.qty, decimalPrecisionValue) from inventtrans it where it.DATAAREAID='XXXX' and it.PARTITION=XXXXXX and it.qty <> round(it.qty, decimalPrecisionValue) and exists (select 'x' from INVENTTABLEMODULE a, unitofmeasure b where  a.unitid =b.SYMBOL and a.partition=it.partition and a.PARTITION=b.PARTITION and  MODULETYPE =0 and  b.DECIMALPRECISION=decimalPrecisionValue and a.DATAAREAID='XXXX' and a.ITEMID =it.ITEMID and it.DATAAREAID=a.DATAAREAID)
    ```

1. Run an on-hand consistency check where the **fix error** option is turned on. This check will correct values in the **inventSum** table.

> [!IMPORTANT]
> We strongly recommend that you carefully edit the script as required for your environment, test it in a test environment, and then check the resulting data before you run the script in a production environment.
