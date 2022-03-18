---
# required metadata

title: Tax thresholds for India FAQ
description: This topic provides information about tax thresholds for India.
author: EricWangChen
ms.date: 01/08/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
# ms.suite: 
# ms.tgt_pltfrm: 
ms.search.region: India
# # ms.search.industry: 
ms.author: wangchen
ms.dyn365.ops.version: 7.3
ms.search.validFrom: 2017-12-31

---

# Tax thresholds for India FAQ

[!include [banner](../includes/banner.md)]

You can set up and apply threshold limits to calculate direct taxes on customer and vendor transactions. Perform the following tasks to set up and use threshold limits:

1.  Set up threshold limits by creating threshold definitions, and then design threshold segments to set up a threshold hierarchy.
2.  Assign thresholds to a withholding tax code, and set up tax values to apply to the final level of each threshold segment in the threshold hierarchy.
3.  Set up a withholding tax group that contains the withholding tax code to which you assigned the threshold and the threshold values.
4.  Create and post transactions that use the withholding tax group for the withholding tax code to which you assigned the threshold and threshold values. Direct taxes are calculated on transactions based on the threshold segments that you set up in the withholding tax codes and withholding tax groups that apply to the transactions.

## What are the different types of threshold limits?

You can apply the following types of threshold limits on transactions:

-   **Cumulative threshold** – The maximum limit of a cumulative transaction value, beyond which direct tax on the transaction value is applied. For example, you set up a cumulative threshold limit of 100,000, and a tax percentage of 10 percent for vendor account 1001. You create three transactions for the vendor that have values of 35,000, 55,000, and 60,000. The total value for all transactions for vendor account 1001 is 150,000 (which exceeds the threshold limit of 100,000). Direct taxes of 10 percent are calculated and applied on the total value for all transactions. The Total taxable amount = 150,000 and the Tax amount = 15,000.

-   **Transaction threshold** – The maximum limit of an individual transaction value, beyond which direct tax on the transaction value is applied. For example, you set up a transaction threshold limit of 30,000, and a tax percentage of 10 percent for vendor account 1001. You create three transactions for the vendor that have values of 25,000, 35,000, and 15,000. The transaction value 35,000 exceeds the threshold limit of 30,000. Direct taxes of 10 percent are calculated and applied only on the transaction that exceeds the transaction threshold limit. The Total taxable amount = 35,000 and the Tax amount = 3,500.

-   **Transaction line threshold** – The maximum limit of a transaction line value, beyond which direct tax on the transaction line value is applied. For example, you set up a transaction line threshold limit of 10,000, and a tax percentage of 10 percent for vendor account 1001. You create a transaction for the vendor that has transaction line values of 5,000, 25,000, and 15,000. The transaction line values 25,000 and 15,000 exceed the threshold limit of 10,000. Direct taxes of 10 percent are calculated and applied only on the transaction lines that exceed the transaction threshold limit. The Total taxable amount = 40,000 and the Tax amount = 4,000.

If the system previously calculated direct taxes by using thresholds for a transaction line or a transaction, thresholds and direct taxes are not applied to that transaction line or transaction again. The transaction line or transaction is excluded from threshold and direct tax calculations.

## Where can I use the threshold limits?
You can use threshold limits to apply taxes, tax concessions, or tax exemptions to customer and vendor transactions.

## What are the methods that I can use to define the threshold hierarchy structure?

You can design a hierarchy structure for a threshold in the following ways:

-   **Single threshold hierarchy** – This structure contains a single threshold segment. For example, you can set up a threshold by specifying the minimum value of 20,000, and then set up the direct tax percentage of 10 percent when you assign the threshold to an entity. The system calculates 10 percent direct tax on any transaction that exceeds a value of 20,000.

-   **Progressive threshold hierarchy** – This structure contains multiple threshold segments. You can specify multiple segments in a single level or in multiple levels. You can specify tax rates for each segment when you assign the threshold to an entity. For example, you can create a threshold hierarchy structure with the following segments.

    | Segment       | Minimum value | Maximum value | Tax rate   |
    |---------------|---------------|---------------|------------|
    | Segment one   | 0             | 1,00,000      | 5 percent  |
    | Segment two   | 1,00,000      | 5,00,000      | 10 percent |
    | Segment three | 5,00,000      | -             | 15 percent |

## When do I assign the tax rates to the hierarchy segments of a threshold?
You can specify tax rates that apply to the final levels of the various hierarchy segments of the threshold in the **Threshold designer** page. You need to do this after you set up a withholding tax code to use the threshold in the **Withholding tax codes** page and after which you set up an entity to use a threshold in the **Threshold references** page.

## Which PAN status should I select when I specify threshold values for a customer?
For the Permanent Account Number (PAN), if the threshold applies to a customer, a customer group, or all customers, you must select **Not applicable** in the **PAN Status** field in the **Threshold designer** page for each threshold value that you specify.

## When I create a withholding tax code that uses a threshold, what should I select in the Value field in the Withholding tax values page?
When you create a withholding tax code that uses a threshold, leave the **Value** field on the **Withholding tax values** page blank, because you specify the tax values for the final levels of each threshold segment on the **Threshold designer** page.

## Don't see your question here?

Comment on this topic to let us know what question you were expecting to get answered here.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
