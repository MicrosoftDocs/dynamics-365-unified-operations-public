---
# required metadata

title: Set up expense types
description: This topic lists the steps for setting up expense types in Asset leasing.
author: moaamer
manager: Ann Beebe
ms.date: 08/14/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TaxTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2019-08-14
ms.dyn365.ops.version: 10.0.6

---

# Set up expense types (Preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic lists the steps for setting up expense types in Asset leasing. Costs that aren't represented by the payment schedule are called expense costs. Examples of these costs can include property taxes, common area maintenance costs and insurance expenses. 

1. To add an administrative expense type, go to **Asset leasing > Setup > Expense types**.
2. Click **New** and create the expense type followed by the description in the respective fields.

## Assign accounts to administrative costs 
  Next, accounts should be associated to the expense types. These accounts will be debited when posting expense schedule entries. The offset account is specified on the **Executory costs payment schedule** lines on each lease.

1.	Navigate to **Asset leasing > Setup > Asset leasing parameters**.
2.	Select **Accounts** and open the **Executory costs** FastTab.
3.	Select the **Expense type** and click **Add**.
4.	Select the book type to be tied to the administrative costs from the **Book type** drop-down.

  > [!Note]
  > Multiple book types can be linked to the same expense account.

5. Use the **Account code** drop-down to specify which leases the book should be applied to. To apply the book at all leases, select **All**. To apply the book to a specific group of leases, select **Group**. To apply the book to specific leases, select **Table**. If you select **Group** or **Table**, an you must select an account or group number from the **Account/Group number** drop-down.
6. Select the respective finance lease main account and operating lease main account from the appropriate drop-downs.

When you've finished the preceding steps, you can add expenses through the **Executory costs payment schedule** lines on the **Lease details** page of a selected lease, or when you create a new lease.

