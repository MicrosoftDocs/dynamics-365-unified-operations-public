---
# required metadata

title: Set up dimension control for settlements 
description: This topic provides information about dimension control for settlements in Russia. 
author: ShylaThompson
manager: AnnBe
ms.date: 10/28/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Set up dimension control for settlements 

[!include [banner](../includes/banner.md)]

## Set up accounts payable parameters for dimensions control for settlements 

Use this procedure to set up dimension control for settlements using the **Accounts payable parameters** page.

1.  Click **Accounts payable** \> **Setup** \> **Accounts payable parameters**.

2.  Click the **Settlement** tab.

3.  In the **Settlement by dimension** field, select one of the following options to control settlement transactions:
    
      - **No** – Transactions are not controlled by dimensions during settlement.
    
      - **Auto** – Transactions are controlled by dimensions during automatic settlement.
    
      - **Manual** – Transactions are controlled by dimensions during manual settlement.
    
      - **Always** – Transactions are controlled by dimensions during automatic and manual settlement.

4.  Click the **Advance holders** tab.

5.  In the **Settlement by dimension** field, select one of the following options to control settlement transactions for an advance holder. The advance holder can be a customer or a vendor.
    
      - **No** – Transactions are not controlled by dimensions during settlement.
    
      - **Auto** – Transactions are controlled by dimensions during automatic settlement.
    
      - **Manual** – Transactions are controlled by dimensions during manual settlement.
    
      - **Always** – Transactions are controlled by dimensions during automatic and manual settlement.

## Set up vendor posting profiles for dimensions control for settlements 

Use this procedure to set up vendor posting profiles for settlement dimension control using the **Vendor posting profiles** page. For required groups or for a vendor, you must specify a dimension set for dimension control. You must also allow empty values at settlement control for the posting profile.

1.  Click **Accounts payable** \> **Setup** \> **Vendor posting profiles**.

2.  Press CTRL+N to create a new vendor posting profile, and then enter the required details.

3.  Click the **Table restrictions** FastTab.

4.  In the **Allow empty dimension value** field, select the condition under which settlements can be processed if dimension values are not specified. The following options are available:
    
      - **No** – Do not allow transaction settlement, whether the dimension values are specified or not.
    
      - **Auto** – Allow automatic transaction settlement, whether the dimension values are specified or not.
    
      - **Manual** – Allow manual transaction settlement, whether the dimension values are specified or not.
    
      - **Always** – Allow transaction settlement, whether the dimension values are specified or not.
    
    > [!NOTE]
    > This parameter lets you ignore the setting of dimensions when individual transactions are created.


5.  Click the **Setup** FastTab.

6.  In the **Set** field, select the dimension set for settlement control. The specified dimension set indicates that dimension control is activated.


## Set up accounts receivable parameters for dimensions control for settlements 

Use this procedure to set up dimensions control for settlements using the **Accounts receivable parameters** page.

1.  Click **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.

2.  Click the **Settlement** tab.

3.  In the **Settlement by dimension** field, select one of the following options to control settlement transactions for a customer:
    
      - **No** – Transactions are not controlled by dimensions during settlement.
    
      - **Auto** – Transactions are controlled by dimensions during automatic settlement.
    
      - **Manual** – Transactions are controlled by dimensions during manual settlement.
    
      - **Always** – Transactions are controlled by dimensions during automatic and manual settlement.


## Set up customer posting profiles for dimensions control for settlements 

Use this procedure to set up customer posting profiles for settlement dimension control using the **Customer posting profiles** page. For required groups or for a customer, you must specify a dimension set for dimension control. You must also include empty values at settlement control for the posting profile.

1.  Click **Accounts receivable** \> **Setup** \> **Customer posting profiles**.

2.  Press CTRL+N to create a new customer posting profile, and then enter the required details. 

3.  Click the **Table restrictions** FastTab.

4.  In the **Allow empty dimension value** field, select the condition under which customer transaction settlements can be processed if dimension values are not specified. The following options are available:
    
      - **No** – Transactions are not settled, whether the dimension values are specified or not.
    
      - **Auto** - Automatic transactions are settled, whether the dimension values are specified or not.
    
      - **Manual** – Manual transactions are settled, whether the dimension values are specified or not.
    
      - **Always** – All transactions are settled, whether the dimension values are specified or not.
    

    > [!NOTE]
    > This parameter lets you ignore the setting of dimensions when individual transactions are created.



5.  Click the **Setup** FastTab.

6.  In the **Set** field, select the dimension set for settlement control.
    

    > [!NOTE]
    > The specified dimension set indicates that dimension control is activated.



## Set up a dimension set for dimensions control for settlements 

Dimension control for settlements helps you accurately manage and analyze accounting with vendors, customers, and advance holders by financial dimension. When you register vendor or customer operations, such as debts and payments, or advance holder operations, such as advance reports and payments, you can specify financial dimensions during settlement. Because you are still specifying dimensions during settlement, you do not generate correct balances for a specific vendor or customer by financial dimension. Dimension control allows you to stop the settlement of invoices and payments that do not have specified dimensions. Dimension control also allows you to verify that the financial dimensions match when you settle vendor, customer, or advanced holder operations.

Use this procedure to set up a dimension set for dimension control for settlements by using the **Financial dimension sets** page.

1.  Click **General ledger** \> **Chart of accounts** \> **Dimensions** \> **Financial dimension sets**.

2.  Press CTRL+N to create a dimension set.

3.  Enter the required details. 
