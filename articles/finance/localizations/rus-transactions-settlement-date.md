---
# required metadata

title: Set up dimension control for settlements (Russia)
description: This topic explains how to set up dimension control for settlements in Russia.
author: ShylaThompson
ms.date: 10/28/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendParameters 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Set up dimension control for settlements (Russia)
[!include [banner](../includes/banner.md)]

Dimension control for settlements helps you accurately manage and analyze accounting with vendors, customers, and advance holders by financial dimension. When you register vendor or customer operations, such as debts and payments, or advance holder operations, such as advance reports and payments, you can specify financial dimensions during settlement. Because you're still specifying dimensions during settlement, you don't generate correct balances for a specific vendor or customer by financial dimension. Dimension control lets you stop the settlement of invoices and payments that don't have specified dimensions. Dimension control also lets you verify that the financial dimensions match when you settle vendor, customer, or advanced holder operations.

## Set up Accounts payable parameters for dimensions control for settlements
Use this procedure to set up dimension control for settlements on the **Accounts payable parameters** page.

1. Select **Accounts payable** \> **Setup** \> **Accounts payable parameters**.
2. On the **Settlement** tab, in the **Settlement by dimension** field, select one of the following options to control settlement transactions:

    - **No** – Transactions aren't controlled by dimensions during settlement.
    - **Auto** – Transactions are controlled by dimensions during automatic settlement.
    - **Manual** – Transactions are controlled by dimensions during manual settlement.
    - **Always** – Transactions are controlled by dimensions during both automatic settlement and manual settlement.

3. On the **Advance holders** tab, in the **Settlement by dimension** field, select one of the following options to control settlement transactions for an advance holder. The advance holder can be a customer or a vendor.

    - **No** – Transactions aren't controlled by dimensions during settlement.
    - **Auto** – Transactions are controlled by dimensions during automatic settlement.
    - **Manual** – Transactions are controlled by dimensions during manual settlement.
    - **Always** – Transactions are controlled by dimensions during both automatic settlement and manual settlement.

## Set up vendor posting profiles for dimensions control for settlements
Use this procedure to set up vendor posting profiles for settlement dimension control on the **Vendor posting profiles** page. For required groups or for a specific vendor, you must specify a dimension set for dimension control. You must also fill in the **Allow empty dimensions value** field for the posting profile.

1. Select **Accounts payable** \> **Setup** \> **Vendor posting profiles**.
2. Press Ctrl+N to create a vendor posting profile, and enter the required details.
3. On the **Table restrictions** FastTab, in the **Allow empty dimension value** field, select the condition under which transaction settlements can be processed if dimension values aren't specified. The following options are available:

    - **No** – Don't allow transaction settlement, regardless of whether the dimension values are specified.
    - **Auto** – Allow automatic transaction settlement, regardless of whether the dimension values are specified.
    - **Manual** – Allow manual transaction settlement, regardless of whether the dimension values are specified.
    - **Always** – Allow all transaction settlement, regardless of whether the dimension values are specified.

    > [!NOTE]
    > This field lets you ignore the settings of dimensions when individual transactions are created.

4. On the **Setup** FastTab, in the **Set** field, select the dimension set for settlement control. If the dimension set is selected, dimension control is activated.

## Set up Accounts receivable parameters for dimensions control for settlements
Use this procedure to set up dimension control for settlements on the **Accounts receivable parameters** page.

1. Select **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2. On the **Settlement** tab, in the **Settlement by dimension** field, select one of the following options to control settlement transactions for customers:

    - **No** – Transactions aren't controlled by dimensions during settlement.
    - **Auto** – Transactions are controlled by dimensions during automatic settlement.
    - **Manual** – Transactions are controlled by dimensions during manual settlement.
    - **Always** – Transactions are controlled by dimensions during both automatic settlement and manual settlement.

## Set up customer posting profiles for dimensions control for settlements
Use this procedure to set up customer posting profiles for settlement dimension control on the **Customer posting profiles** page. For required groups or for a specific customer, you must specify a dimension set for dimension control. You must also fill in the **Allow empty dimensions value** field for the posting profile.

1. Select **Accounts receivable** \> **Setup** \> **Customer posting profiles**.
2. Press Ctrl+N to create a customer posting profile, and enter the required details.
3. On the **Table restrictions** FastTab, in the **Allow empty dimension value** field, select the condition under which customer transaction settlements can be processed if dimension values aren't specified. The following options are available:

    - **No** – Don't allow transaction settlement, regardless of whether the dimension values are specified.
    - **Auto** – Allow automatic transaction settlement, regardless of whether the dimension values are specified.
    - **Manual** – Allow manual transaction settlement, regardless of whether the dimension values are specified.
    - **Always** – Allow all transaction settlement, regardless of whether the dimension values are specified.

    > [!NOTE]
    > This field lets you ignore the settings of dimensions when individual transactions are created.

4. On the **Setup** FastTab, in the **Set** field, select the dimension set for settlement control. If the dimension set is selected, dimension control is activated.

## Set up a dimension set for dimensions control for settlements
Use this procedure to set up a dimension set for dimension control for settlements on the **Financial dimension sets** page.

1. Select **General ledger** \> **Chart of accounts** \> **Dimensions** \> **Financial dimension sets**.
2. Press Ctrl+N to create a dimension set, and enter the required details.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]