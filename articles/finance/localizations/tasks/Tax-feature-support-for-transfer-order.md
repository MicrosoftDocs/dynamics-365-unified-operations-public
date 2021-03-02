---
# required metadata

title: Tax feature support for transfer order
description: This topic explains the new tax feature support for transfer orders using the tax calculation service.
author: kliang
manager: tfehr
ms.date: 03/02/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.18

---

# Tax feature support for transfer order

[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

This topic provides information about tax calculation and posting integration in transfer orders. This functionality provides the possibility to set up tax calculation and posting in transfer orders for stock transfers, which are considered intra-community supply and intra-community acquisition under the EU VAT regulation.

There are three main steps to configure and use this functionality:

1. RCS setup: Set up the tax feature, tax codes, and tax codes applicability for tax code determination in transfer orders.
2. Finance setup: Enable the **Tax in transfer order** feature, set up the tax service parameters for inventory, and set up core tax parameters.
3. Inventory setup: Set up the inventory configuration for transfer order transactions.


## Set up RCS for tax and transfer order transactions

Complete the following steps to set up the tax involved in a transfer order. In this procedure, the transfer order is from Netherlands to Belgium. 

1.  On the **Tax features** page, on the **Versions** tab, select the draft feature version, and then select **Edit**.

    [![Edit tax feature](../media/image1.png)](/media/image1.png)

2.  On the  **Tax features setup** page, on the **Tax codes** tab, select **Add** to create new tax codes. For example, NL-exempt, BE-RC+21, and BE-RC-21.

    - When a transfer order is shipped from a Netherlands warehouse, the Netherlands VAT exempted tax code is applied.

       [![Create tax code](../media/image2.png)](./media/image2.png)

    - When a transfer order is received at a Belgium warehouse, the reverse charge mechanism is applied.

       [![Setup reverse charge tax code 1](../media/image3.png)](./media/image3.png)

       [![Setup reverse charge tax code 2](../media/image4.png)](./media/image4.png)

3.  Create and edit the tax codes applicability.

    1. Select **Manage columns** and then select the columns to build the applicability table.
    
       > [!NOTE]
       > Select **Business process** and **Tax directions** and add them to the table. Both columns are essential to the tax in transfer orders functionality.
    
    2. Add applicability rules. The **Tax codes**, **Tax group**, and **Item tax group** fields shouldn't be blank.
       
        1. In the **Business process** field, select "Inventory" to make the rule applicable for a transfer order.
        2. In the **Tax direction** field, select "Output" to make the rule applicable for **Ship transfer order**.
        3. In the **Tax direction** field, select "Input" to make the rule applicable for **Receive transfer order**.

           [![Apply applicability rules](../media/image5.png)](./media/image5.png)

4.  Verify that "Multiple VAT ID configurations" has been set up. 
5.  Complete and publish the new tax feature version.

    [![Change status](../media/image6.png)](../media/image6.png)


## Set up Finance for transfer order transactions

Complete the steps in this section to enable and set up taxes for transfer orders.

1. In Finance, go to **Workspaces** > **Feature management**. 
2. In the list, locate and enable the feature, **Tax in transfer order**.

   > [!NOTE]
   > The **Tax in transfer order** feature is fully dependent on the tax service and can only enabled after you have installed the tax service.

   [![Enable feature](../media/image7.png)](./media/image7.png)

3.  Enable tax service and select the **Inventory** business process.

    > [!IMPORTANT]
    > These steps must be completed for each legal entity in Finance that you want to enable the tax service and tax in transfer order for.

    1. Go to **Tax** > **Setup** > **Tax configuration** > **Tax service setup**.
    2. In the **Business process** field, select **Inventory**.
    3. Repeat steps 1 and 2 for each legal entity in your Finance environment that you want to enable the tax service and tax in transfer order for. 

       [![Setup business process](../media/image8.png)](./media/image8.png)

4. Verify that the reverse charge mechanism is set up.

    - Go to **General ledger** > **Setup** > **Parameters** and on the **Reverse charge** tab, verify that **Enable reverse charge** is set to **Yes**.

      [![Enable reverse charge](../media/image9.png)](./media/image9.png)

5. Verify that the related tax codes, tax groups, item tax groups, and VAT registration numbers have been set up in Finance according to the tax service guidance.
6. Set up a ledger account in **Ledger posting groups** for "Interim transit". This step is only required when the tax applied to a transfer order isn't applicable for a tax exempted or reverse charge mechanism.

    1. Go to **Tax** > **Setup** > **Sales tax** > **Ledger posting groups**.
    2. In the **Interim transit** field, select a ledger account.

       [![Setup Interim transit account](../media/image10.png)](./media/image10.png)

## Set up basic inventory for transfer order transactions

Complete the following steps to set up basic inventory to enable transfer order transactions.

1. Create ship-from and ship-to sites for your warehouses in different countries and add the primary address for each Site.

   1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Sites**.
   2. Select **New**, and create the site which will later be assigned to a warehouse.
   3. Repeat step 2 for all of the sites that you need to create.

   > [!NOTE]
   > Create a site called **Transit** and assign to the **Transit warehouse** in the next steps, so that tax related inventory vouchers can be posted in transfer order "ship" and "receive" transactions. The address of the transit site is irrelevant to tax calculation and can be left blank.
   >
   >[![Setup Sites](../media/image11.png)](./media/image11.png)

2.  Create ship-from, transit, and ship-to warehouses. If there is address information maintained in the warehouse, it will override the site address in tax calculation.

    1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Warehouses**.
    2. Select **New**, create a warehouse and assign it to the corresponding site.
    3. Repeat step 2 to create a warehouse for each site as needed.
    
        [![Setup warehouses](../media/image12.png)](./media/image12.png)
    
    > [!NOTE]
    > For a ship-from warehouse, a transit warehouse must be assigned under the parameter **Transit warehouse** for transfer order transactions.
    >
    > [![transit warehouse](../media/image13.png)](./media/image13.png)

3.  Verify that the inventory posting configuration is set up for transfer order transactions.

    1. Go to **Inventory management** > **Setup** > **Posting** > **Posting**.
    2. On the **Inventory** tab, verify that **Inventory issue** and **Inventory receipt** have a ledger account set up.
    
       [![Setup inventory issue](../media/image14.png)](./media/image14.png)
    
    3. Verify that **Inter-unit payable** has a ledger account set up.
    
       [![Setup inter-unit payable](../media/image15.png)](./media/image15.png)
    
    4. Verify that **Inter-unit receivable** has a ledger account set up.
    
       [![Setup inter-unit receivable](../media/image16.png)](./media/image16.png)


