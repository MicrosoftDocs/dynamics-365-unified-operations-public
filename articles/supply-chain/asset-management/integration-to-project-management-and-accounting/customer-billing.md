---
# required metadata

title: Bill for maintenance on customer-owned assets
description: This topic explains how you can create, process, and bill maintenance work done on assets owned by your customers.
author: johanhoffmann
manager: tfehr
ms.date: 01/28/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: EntAssetWorkOrderProjCostInfoPart 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2021-01-28
ms.dyn365.ops.version: 10.0.17
---

# Bill for maintenance on customer-owned assets

[!include [banner](../includes/banner.md)]

The *Work order billing* feature lets can create, process, and bill maintenance work done on assets owned by your customers. With this feature, you can:

- Connect customers to the assets they own.
- When you create a work order, you can choose a customer and view the assets that customer owns.
- Set up a parent project for each customer.
- Register hours, items, expenses, and fees against the work order and afterwards create an invoice proposal for the customer.

In addition:

- The project contract from a customer's parent project is automatically copied to the relevant work order project.
- Asset Management can now use the *fee* project transaction type both on work order forecasts and work order journals.

## Turn on the customer billing feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Project management and accounting*
- **Feature name:** *Work order billing*

## Example scenario

To gain an understanding for how this feature works, work through the following example scenario:

### Step 1: Create a new project contract for the customer

Do the following:

1. Navigate to **Project management and accounting \> Projects \> Project contracts**
2. Create **New**
3. Fill out the following information in the record
    - Funding type: Customer
    - Funding source: Pelican Wholesales
    - Name: Pelican Wholesales
4. Select **OK**

### Step 2: Create a new parent project for the customer

This parent project will be used when work orders for the customer are created.

Do the following:

1. Navigate to **Project management and accounting \> Projects \> All projects**
2. Create a new project &quot;New&quot;
3. Add following information to the record
    - Project type: Time and material
    - Project name: Pelican Wholesales Work orders
    - Project group: TM
    - Project contract ID: Pelican Wholesales (the contract you created in step 1)
    - Start date: Todays date
    - Select **Create project**

### Step 3: Create new work order type in Asset Management

Do the following:

1. Navigate to **Asset management \> Setup \> Work order \> Work order types**
2. Create **New**
3. Add following information to the record
    - Work order type: Service
    - Name: Service work orders
    - Work order lifecycle state: Standard

### Step 4: Link the customer account to the parent project

Now link the customer account to the parent project in Asset management's project setup. Do the following:

  1. Navigate to **Asset management \> Setup \> Work orders \> Project setup \> Parent project**
  2. Select **Add** to create a new line
  3. Fill out the following information in the record:
    1. Customer account: US-013 (Pelican Wholesales)
    2. Project ID: Pelican Wholesales Work orders (the project you created in step 2)

### Step 5: Link the project group and type to the work order project

Do the following:

1. Navigate to **Asset management \> Setup \> Work orders \> Project setup \> Project group**
2. Select **Add** to create a new line
3. Fill out the following information in the record:
    - Work order type: Service (the work order type you created in step 3)
    - Project group: TM

> [!NOTE]
> The project contract on the work order project is always inherited from the parent project_

### Step 6: Link an asset to the customer ID

Do the following:

1. Navigate to **Asset management \> Assets \> Active assets**
2. Filter on asset: VE-102 in filter field
3. Navigate to Customer Tab
4. Add following information to the Customer section
    - Customer account: US-013 (Pelican Wholesales)

### Step 7: Create a new work order on the asset

Do the following:

1. Navigate to **Asset management \> Work orders \> Active work orders**
2. Create **New**
3. Fill out the following information in the record:
    - Work order type: Service
    - Customer account: US-013 (Pelican Wholesales)
    - Asset: VE-102
    - _Note: Asset look-up will only show assets linked to the customer_
    - Description: Repair Truck
    - Maintenance job type: Repair
    - Trade: Mechanic
    - Service level: 4
    - Select **OK**.

### Step 8: Check the work order and start working on it

Do the following:

1. Check that the parent project is the *Pelican wholesales Work order* project
2. In the work order navigate to Work order \> Lifecycle state \> Update work order state
    - Choose the state *In progress*
    - Select **OK**.

### Step 9: Post the hours spend on the work order and create a new invoice proposal

Do the following:

1. Navigate to **Project** \> **Journals** to register your time spend on the work order
    1. Navigate to the **Hours** section and **Add line**
    2. Edit **Hours** to 4
    3. Select **Post journals**
2. Navigate to **Invoicing** \> **New invoice proposal**
3. Add following information to the record
    1. Select the line that you want to invoice
    2. Select **OK**.
