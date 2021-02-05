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

[!include [banner](../../includes/banner.md)]

The *Work order billing* feature lets you create, process, and bill maintenance work done on assets owned by your customers. With this feature, you can:

- Connect customers to the assets they own.
- Choose a customer and view the assets that customer owns when you create a work order.
- Set up a parent project for each customer.
- Register hours, items, expenses, and fees against the work order and afterwards create an invoice proposal for the customer.

In addition:

- The project contract from a customer's parent project is automatically copied to the relevant work order project.
- Asset Management can now use the *fee* project transaction type both on work order forecasts and work order journals.

## Turn on the customer billing feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module** - *Project management and accounting*
- **Feature name** - *Work order billing*

## Example scenario

To gain an understanding for how this feature works, work through the following example scenario.

To work through this scenario using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) is installed. You must select the **USMF** legal entity before you begin.

You can also use this scenario as guidance for using this feature as you work on a production system. However, in that case, you must substitute your own values, and you might be missing some types of required records that the standard demo data provides.

### Step 1: Create a new project contract for the customer

Do the following:

1. Go to **Project management and accounting \> Projects \> Project contracts**
1. Select **New** on the Action Pane.
1. The **New project contract** dialog box opens. Make the following settings:
    - **Name** - *Pelican Wholesales*
    - **Funding type** - *Customer*
    - **Funding source** - *US-013* (Pelican Wholesales)
1. Select **OK**.

### Step 2: Create a new parent project for the customer

This parent project will be used when work orders for the customer are created. Do the following:

1. Go to **Project management and accounting \> Projects \> All projects**
1. Select **New** on the Action Pane.
1. The **New project** dialog box opens. Make the following settings:
    - **Project type** - *Time and material*
    - **Project name** - *Pelican Wholesales work orders*
    - **Project group** - *TM*
    - **Project contract ID** - *Pelican Wholesales* (the contract you created previously)
    - **Start date** - (Select today's date)
1. Select **Create project**.
1. The new project opens. Take note of the **Project ID**. You'll need it later.

### Step 3: Create new work order type in Asset Management

Do the following:

1. Go to **Asset management \> Setup \> Work order \> Work order types**
1. Select **New** on the Action Pane.
1. A new record is added to the list. Make the following settings for it:
    - **Work order type** - *Service*
    - **Name** - *Service work orders*
    - **Work order lifecycle state** - *Standard*

### Step 4: Link the customer account to the parent project

Now link the customer account to the parent project in Asset management's project setup by doing the following:

1. Go to **Asset management \> Setup \> Work orders \> Project setup**
1. Open the **Parent project** tab.
1. Select **Add** on the toolbar to create a new line.
1. Make the following settings for the new line:
    - **Customer account** - *US-013* (Pelican Wholesales)
    - **Project ID** -  (Enter the project ID you noted earlier when you created the project named *Pelican Wholesales Work orders*)

### Step 5: Link the project group and type to the work order project

Do the following:

1. You should still be on the **Project setup** page (**Asset management \> Setup \> Work orders \> Project setup**).
1. Open the **Project group** tab.
1. Select **Add** on the toolbar to create a new line.
1. Make the following settings for the new line:
    - **Work order type** - *Service* (the work order type you created earlier)
    - **Project group** - *TM*

> [!NOTE]
> The project contract on the work order project is always inherited from the parent project

### Step 6: Link an asset to the customer ID

Do the following:

1. Go to **Asset management \> Assets \> Active assets**
1. In the **Filter** field, enter *VE-102* and choose to filter by **Asset**.
1. Select the found asset to open its settings.
1. Expand the **Customer** FastTab and make the following setting:
    - **Customer account** - *US-013* (Pelican Wholesales)

The **Name** field will automatically update to show *Pelican Wholesales* after you enter the customer account number.

### Step 7: Create a new work order on the asset

Do the following:

1. Go to **Asset management \> Work orders \> Active work orders**
1. Select **New** on the Action Pane.
1. The **Create work order** dialog box opens. Make the following settings:
    - **Work order type** - *Service*
    - **Description** - Repair Truck
    - **Customer account** - *US-013* (Pelican Wholesales)
    - **Asset** - *VE-102* (the lookup only shows assets linked to the selected customer account)
    - **Maintenance job type** - *Repair*
    - **Trade** - *Mechanic*
    - **Service level** - *4*
1. Select **OK**.

### Step 8: Check the work order and start working on it

Do the following:

1. Continue working on the work order you created in the previous section.
1. Check that the parent project is the *Pelican wholesales Work order* project by doing the following:
    1. Select a line form the **Work order maintenance jobs** section.
    1. Expand the **Line details** FastTab.
    1. Inspect the **Project ID** value. It should show a hyphenated number, which uses the form *\<Parent-Project-ID\>-\<Project-ID\>*. The number is a link, so you can get more information by selecting it, which opens a page where you can read the parent project and project names.
1. On the Action Pane, open the **Work order** tab and, from the **Lifecycle state** group, select **Update work order state**.
1. The **Update work order state** dialog box opens. In the **Select** column, mark the check box for the row where **Lifecycle state** is *In progress*.
1. Select **OK**.
1. The **Lifecycle state: InProgress** dialog box opens. Select **OK**.

### Step 9: Post the hours spent on the work order and create a new invoice proposal

Do the following:

1. Continue working on the work order you had open in the previous section.
1. On the Action Pane, open the **Work order** tab and, from the **Project** group, select **Journals**.
1. The **Work order journals** page opens. Here, you can register the time you spent on the work order.
1. On the **Hours** FastTab, select **Add line** from the toolbar. Then make the following setting for the new line:
    - **Hours** - *4*
1. On the Action Pane, select **Post journals**.
1. Close the **Work order journals** page to return to the work order.
1. On the Action Pane, open the **Invoicing** tab and select **New invoice proposal**.
1. The **Create invoice proposal** dialog box opens. In the **Project transactions** section, mark the **Select** check box for each line  you want to invoice.
1. Select **OK** to close the dialog box and view the new invoice proposal.
