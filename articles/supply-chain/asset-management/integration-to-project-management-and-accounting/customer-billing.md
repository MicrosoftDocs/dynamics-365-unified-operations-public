---
# required metadata

title: Bill for maintenance on customer-owned assets
description: This article explains how to create, process, and bill maintenance work that is done on assets that your customers own.
author: johanhoffmann
ms.date: 01/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ProjProjectContractsListPage, ProjInvoiceTable, ProjProjectsListPage, ProjTable, EntAssetWorkOrderType, EntAssetWorkOrderProjectSetup, EntAssetObjectTable, EntAssetWorkOrderTable
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

The *Work order billing* feature lets you create, process, and bill maintenance work that is done on assets that your customers own. This feature lets you perform the following tasks:

- Connect customers to the assets that they own.
- Select a customer and view the assets that customer owns when you create a work order.
- Set up a parent project for each customer.
- Register hours, items, expenses, and fees against the work order, and then create an invoice proposal for the customer later.

In addition, the feature provides the following functionality:

- The project contract from a customer's parent project is automatically copied to the relevant work order project.
- Asset management can now use the *fee* project transaction type on both work order forecasts and work order journals.

## Turn the work order billing feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.32, then admins can turn this functionality on or off by searching for the *Work order billing* feature in the [**Feature management** workspace](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Example scenario

To learn how this feature works, work through the following example scenario.

To work through this scenario by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. You must select the **USMF** legal entity before you begin.

You can also use this scenario as guidance for using the feature when you work on a production system. However, in that case, you must substitute your own values, and you might be missing some types of required records that the standard demo data provides.

### Step 1: Create a new project contract for the customer

1. Go to **Project management and accounting \> Projects \> Project contracts**.
1. On the Action Pane, select **New**.
1. In the **New project contract** dialog box, set the following values:

    - **Name:** *Pelican Wholesales*
    - **Funding type:** *Customer*
    - **Funding source:** *US-013* (*Pelican Wholesales*)

1. Select **OK**.

### Step 2: Create a new parent project for the customer

The parent project that you create here will be used when work orders for the customer are created.

1. Go to **Project management and accounting \> Projects \> All projects**.
1. On the Action Pane, select **New**.
1. In the **New project** dialog box, set the following values:

    - **Project type:** *Time and material*
    - **Project name:** *Pelican Wholesales work orders*
    - **Project group:** *TM*
    - **Project contract ID:** *Pelican Wholesales* (the contract that you created earlier)
    - **Start date:** Select today's date.

1. Select **Create project**.
1. The new project is opened. Make a note of the **Project ID** value. You will have to enter it later.

### Step 3: Create a new work order type in Asset management

1. Go to **Asset management \> Setup \> Work order \> Work order types**.
1. On the Action Pane, select **New**.
1. A new record is added to the list. Set the following values for it:

    - **Work order type:** *Service*
    - **Name:** *Service work orders*
    - **Work order lifecycle state:** *Standard*

### Step 4: Link the customer account to the parent project

You must now link the customer account to the parent project in the project setup in Asset management.

1. Go to **Asset management \> Setup \> Work orders \> Project setup**.
1. On the **Parent project** tab, select **Add** to add a line.
1. On the new line, set the following values:

    - **Customer account:** *US-013* (*Pelican Wholesales*)
    - **Project ID:** Enter the project ID that you made a note of earlier.

### Step 5: Link the project group and type to the work order project

You should still be on the **Project setup** page (**Asset management \> Setup \> Work orders \> Project setup**).

1. On the **Project group** tab, select **Add** to add a line.
1. On the new line, set the following values:

    - **Work order type:** *Service* (the work order type that you created earlier)
    - **Project group:** *TM*

> [!NOTE]
> The project contract on the work order project is always inherited from the parent project.

### Step 6: Link an asset to the customer ID

1. Go to **Asset management \> Assets \> Active assets**.
1. In the **Filter** field, enter *VE-102*, and select to filter by **Asset**.
1. Select the asset to open its settings.
1. On the **Customer** FastTab, set the **Customer account** field to *US-013* (*Pelican Wholesales*).

    The **Name** field is automatically updated to *Pelican Wholesales*.

### Step 7: Create a new work order on the asset

1. Go to **Asset management \> Work orders \> Active work orders**.
1. On the Action Pane, select **New**.
1. In the **Create work order** dialog box, set the following values:

    - **Work order type:** *Service*
    - **Description:** *Repair Truck*
    - **Customer account:** *US-013* (*Pelican Wholesales*)
    - **Asset:** *VE-102*

        > [!NOTE]
        > The lookup shows only assets that are linked to the selected customer account.

    - **Maintenance job type:** *Repair*
    - **Trade:** *Mechanic*
    - **Service level:** *4*

1. Select **OK**.

### Step 8: Review the work order and start to work on it

In this section, you will work on the work order that you created in the previous section.

1. Follow these steps to verify that the parent project is the *Pelican wholesales Work order* project:

    1. In the **Work order maintenance jobs** section, select a line.
    1. On the **Line details** FastTab, inspect the **Project ID** value. It should be a hyphenated number in the form *\<Parent-Project-ID\>-\<Project-ID\>*. This value is a link.
    1. Select the project ID link to open a page where you can view the parent project and project names.

1. On the Action Pane, on the **Work order** tab, in the **Lifecycle state** group, select **Update work order state**.
1. In the **Update work order state** dialog box, in the **Select** column, select the check box for the row where the **Lifecycle state** field is set to *In progress*.
1. Select **OK**.
1. In the **Lifecycle state: InProgress** dialog box, select **OK**.

### Step 9: Post the hours that were spent on the work order and create a new invoice proposal

In this section, you will continue to work on the work order that you worked on in the previous section.

1. On the Action Pane, on the **Work order** tab, in the **Project** group, select **Journals**.

    The **Work order journals** page appears. Here, you can register the time that you spent on the work order.

1. On the **Hours** FastTab, select **Add line**.
1. On the new, line, set the **Hours** field to *4*.
1. On the Action Pane, select **Post journals**.
1. Close the **Work order journals** page to return to the work order.
1. On the Action Pane, on the **Invoicing** tab, select **New invoice proposal**.
1. In the **Create invoice proposal** dialog box, in the **Project transactions** section, select the **Select** check box for every line  that you want to invoice.
1. Select **OK** to close the dialog box and view the new invoice proposal.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]