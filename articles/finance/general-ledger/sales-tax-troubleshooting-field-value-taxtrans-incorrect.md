---
# required metadata

title: Incorrect field value in TaxTrans
description: This topic provides information about troubleshooting an incorrect field values in TaxTrans.
author: bijian
manager: beya
ms.date: 04/13/2021
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

# Incorrect field value in TaxTrans

[!include [banner](../includes/banner.md)]

When you discover that a field value in a **TaxTrans** is incorrect, you can use the sections in this topic to try and resolve the issue.

## Prerequisites
The following prerequisites must be met before you complete the steps in this topic.

Because **TaxTrans**, **TaxUncommitted**, and **TmpTaxWorkTrans** are similar data sets in different forms:

  - **TaxTrans** is the final posted tax transaction result persisted in the database
  - **TaxUncommitted** is the intermediate calculated tax result persisted in the database (if applicable), which will be used later in posting
  - **TmpTaxWorkTrans** is the temporary calculated tax result in the in-memory table (Table Type = InMemory)

IF you find the root cause of the incorrect **TaxTrans** column, you also find the root cause of an incorrect **TaxUncommitted** or **TmpTaxWorkTrans**, because the three columns are copied from each other.

Generally, during tax calculation, **TmpTaxWorkTrans** is generated, and then, if applicable, **TaxUncommitted** is generated. During tax posting, **TaxTrans** is generated.


## Add break points

1. Add extensions and break points in *insert()* and *update()* in the extensions as shown below.

     - **TaxTrans**

        ```x++
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

     - **TaxUncommitted**

        ```x++
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

     - **TmpTaxWorkTrans**

        ```x++
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

2. Alternatively, you can add break points directly when **TaxUncommitted** is not involved.

     - *TaxTrans.insert()*, *TaxTrans.update()*
     - *TmpTaxWorkTrans.insert()*, *TmpTaxWorkTrans.update()*

## Reproduce and debug

Because the breakpoints are set, every data persistency change is visible during debugging. To find the root cause of an incorrect column of **TaxTrans**, **TaxUncommitted**, or **TmpTaxWorkTrans**, review and note the following:

1. The last breakpoint where the column is correct.
2. The first breakpoint where the column is incorrect.
3. What happens inbetween those two points.

## Determine whether customization exists
If you've completed the steps in the previous sections but have found no issue, determine whether customization exists. If no customization exists, create a Microsoft service request for further support.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

