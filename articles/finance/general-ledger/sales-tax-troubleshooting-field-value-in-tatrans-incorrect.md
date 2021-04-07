---
# required metadata

title: Field value in TaxTrans is incorrect
description:
author: bijian
manager: beya
ms.date: 02/04/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

#ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.1
---

# Field value in TaxTrans is incorrect

[!include [banner](../includes/banner.md)]

- A column in TaxTrans is incorrect.

## Prerequisites

- TaxTrans, TaxUncommitted, TmpTaxWorkTrans are similar data sets in different forms:

- - TaxTrans is the final posted tax transaction result persisted in the database;
  - TaxUncommitted is the intermediate calculated tax result persisted in the database (if applicable), which will be later used in posting;
  - TmpTaxWorkTrans is the temporary calculated tax result in the in-memory table (Table Type = InMemory).
  - To find the root cause of an incorrect column of TaxTrans, is to find the root cause of an incorrect column of TaxTrans, or TaxUncommitted, or TmpTaxWorkTrans, because the columns are copied from each other.

- Generally, during tax calculation, TmpTaxWorkTrans is generated, and then TaxUncommitted is generated (if applicable); during tax posting, TaxTrans is generated.



## Trouble shooting guide

- **Step 1: add break points**

  1. Add extensions, and add break points in insert() and update() in the extensions as follows:

     1. TaxTrans

        ```
        [ExtensionOf(tableStr(TaxTrans))]
        public final class TaxTrans_Extension
        {
            public void insert()
            {
                next insert();
            }
        
            public void update()
            {
                next update();
            }
        
        }
        ```

     2. TaxUncommitted

        ```
        [ExtensionOf(tableStr(TaxUncommitted))]
        public final class TaxUncommitted_Extension
        {
            public void insert()
            {
                next insert();
            }
        
            public void update()
            {
                next update();
            }
        
        }
        ```

     3. TmpTaxWorkTrans

        ```
        [ExtensionOf(tableStr(TmpTaxWorkTrans))]
        public final class TmpTaxWorkTrans_Extension
        {
            public void insert(boolean _ignoreCalculatedSalesTax)
            {
                next insert(_ignoreCalculatedSalesTax);
            }
        
            public void update(boolean _ignoreCalculatedSalesTax)
            {
                next update(_ignoreCalculatedSalesTax);
            }
        
        }
        
        ```

  2. alternatively, add break points directly when TaxUncommitted is not involved:

  3. 1. TaxTrans.insert(), TaxTrans.update()
     2. TmpTaxWorkTrans.insert(), TmpTaxWorkTrans.update()

- **Step 2:  reproduce and debug**

  1. Since the break points are set, every data persistency change is visible during debugging.

  2. To find the root cause of an incorrect column of TaxTrans, or TaxUncommitted, or TmpTaxWorkTrans:

  3. 1. the last break point where the column is correct;
     2. the first break point where the column is incorrect;
     3. what happens in between.

- **Step 3: If no issue is found in above steps, check whether customization exists. If not, create a service request to Microsoft for further support.**

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

