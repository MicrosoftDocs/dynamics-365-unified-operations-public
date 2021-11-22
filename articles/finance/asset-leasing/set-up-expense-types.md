---
# required metadata

title: Set up expense types
description: This topic explains how to set up expense types in Asset leasing.
author: moaamer
ms.date: 04/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetLeaseExpenseTypeTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2019-10-28
ms.dyn365.ops.version: 10.0.14

---

# Set up expense types

[!include [banner](../includes/banner.md)]

This topic explains how to set up expense types in Asset leasing. Costs that aren't represented by the payment schedule are known as *expense costs*. Examples of these costs include property taxes, common area maintenance costs, and insurance expenses.

## Add an administrative expense type

1. Go to **Asset leasing \> Setup \> Expense types**.
2. Select **New**.
3. In the appropriate fields, enter the new expense type and a description.

## Assign accounts to administrative costs

Next, you should associate accounts with the expense types. These accounts will be debited when expense schedule entries are posted. The offset account is specified on the **Executory costs payment schedule** lines on each lease.

1. Go to **Asset leasing \> Setup \> Asset leasing parameters**.
2. On the **Accounts** tab, on the **Executory costs** FastTab, in the **Expense type** field, select the expense type.
3. Select **Add**.
4. In the **Book type** field, select the book type to link to the administrative costs.

    > [!NOTE]
    > Multiple book types can be linked to the same expense account.

5. In the **Account code** field, specify which leases the book should be applied to:

    - **All** – Apply the book to all leases.
    - **Group** – Apply the book to a specific group of leases.
    - **Table** – Apply the book to specific leases.

6. If you selected **Group** or **Table** in the **Account code** field, select an account number or group number in the **Account/Group number** field.
7. In the appropriate fields, select the finance lease main account and the operating lease main account.

When you've completed these steps, you can add expenses through the **Executory costs payment schedule** lines on the **Lease details** page of a selected lease. Alternatively, you can add expenses when you create a new lease.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
