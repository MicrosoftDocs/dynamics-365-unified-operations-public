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

The main steps to configure and use this functionality are:

-   RCS setup: Set up tax feature, tax codes and tax codes applicability for tax code determination in transfer order.

-   Finance setup: Enable feature "tax in transfer order", Set up tax service parameters for inventory (for example, transfer order), set up core tax parameters (for example, reverse charge).

-   Inventory setup: Follow generic process to set up the inventory configuration for transfer order transactions.



## Microsoft Dynamics Regulatory Service setup

Following is an example setup for the tax involved in a transfer order from Netherlands to Belgium. 

1.  Create and edit **Tax Feature**, select the draft feature version, click **Edit.**

[![Edit tax feature](../media/image1.png)](/media/image1.png)

2.  Create **Tax codes** (for example, NL-exempt, BE-RC+21, BE-RC-21).

    a.  When shipping a transfer order from a Netherlands warehouse, it shall apply a Netherlands VAT exempted tax code.

[![Create tax code](../media/image2.png)](./media/image2.png)

b.  When receiving a transfer order at a Belgium warehouse, it shall apply reverse charge mechanism.

[![Setup reverse charge tax code 1](../media/image3.png)](./media/image3.png)

[![Setup reverse charge tax code 2](../media/image4.png)](./media/image4.png)

3.  Create and edit Tax codes applicability.

    1. Click Manage columns and select columns to build the applicability table.
    
       > [!NOTE]
       > Select "Business process" and "Tax Directions" into the table. Both columns are essential to tax in transfer order functionality.
    
    2. Add applicability rules (Tax codes, Tax Group, and Item Tax Group shall not be blank).
    
       > [!NOTE]
       > - Set Business Process = "Inventory" to make the rule applicable in Transfer order.
       > - Set Tax Direction = "Output" to make the rule applicable when "Ship Transfer order".
       > - Set Tax Direction = "Input" to make the rule applicable when "Receive Transfer order".

[![Apply applicability rules](../media/image5.png)](./media/image5.png)

4.  Make sure "Multiple VAT ID configurations" has been properly configured. 
5.  Complete and Publish the new tax feature version.

[![Change status](./media/image6.png)](../media/image6.png)



## Microsoft Dynamics 365 Finance setup

After you complete the setups in section "Microsoft Dynamics Regulatory Configuration Service setup" and published version of tax feature, you can continue the setups in this section in Dynamics 365 Finance.

1. Enable feature "Tax in transfer order" in Feature Management.

   > [!NOTE]
   > Feature "Tax in transfer order" is fully dependent on tax service. It can be only enabled after you have installed tax service.

[![Enable feature](../media/image7.png)](./media/image7.png)



The following setup is by legal entity. You need to configure it for each legal entity, which you want to enable tax service and tax in transfer order in Dynamics 365 Finance.

2.  Enable tax service and select "Inventory" in Business process.

    a.  Go to module Tax, path Setup - Tax configuration - Tax service setup.

    b.  Tick "Inventory" in the parameter "Business process"

[![Setup business process](../media/image8.png)](./media/image8.png)

3.  Ensure reverse charge mechanism has been properly set up.

    a.  Switch on "Enable reverse charge" under General ledger parameters.

[![Enable reverse charge](../media/image9.png)](./media/image9.png)

4.  Ensure related tax codes, tax groups, item tax groups and VAT registration numbers have been set up in Dynamics 365 Finance according to tax service guidance.

5.  **\[Optional\]** Setup a ledger account in Ledger posting groups for "Interim transit" (it's only required in case the tax applied to transfer order is not applicable for tax exempted or reverse charge mechanism)

    a.  Go to module Tax, path Setup - Sales tax - Ledger posting groups.

    b.  Add a ledger account in parameter "Interim transit".

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

2.  Create ship-from, transit, and ship-to warehouses. If there is address infromation maintained in the warehouse, it will override the site address in tax calculation.

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


