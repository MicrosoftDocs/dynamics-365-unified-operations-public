---
# required metadata

title: Use the Asset management mobile workspace

description: This topic provides information about the Asset management mobile workspace.
author: johanhoffmann 
ms.date: 01/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
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
ms.dyn365.ops.version: 10.0.5
ms.search.validFrom: 2019-08-31

---

# Use the Asset management mobile workspace

[!include [banner](../../includes/banner.md)]

This topic provides information about the **Asset management** mobile workspace. This workspace lets users view and create maintenance requests and work orders. Users can also view the assigned work order jobs in a calendar or list view. Assets and functional locations can also be viewed and searched for.

## Overview

Asset Management is an advanced module for managing assets and work order jobs in Dynamics 365 Supply Chain Management. The **Asset management** mobile workspace lets users quickly view assigned work order jobs on the mobile device of their choice. Users can also create and manage maintenance requests, update lifecycle state, and view asset and functional location details by using their mobile device.

Specifically, the **Asset management** mobile workspace lets users perform these tasks:

- Create, view, and edit maintenance requests, take a photo or attach an existing image to the maintenance request, change the maintenance request lifecycle state. 
- Create, view, and edit work orders, take a photo or attach an existing image to the work order, change the work order lifecycle state, view work order jobs.
- View assigned work order jobs in a calendar view.
- Create, view, and edit work order job, update asset counters, view maintenance checklist, view and edit work order job notes, view the tools required for the work order job.
- View or search for a specific asset or functional location.

## Prerequisites

Before you can use the **Asset management** mobile workspace, your admin must set up the required user and worker accounts, and publish the workspace. For more information, see [Set up the Asset management mobile workspace](set-up-asset-management-mobile.md).

## Download and install the mobile app

Download and install the Dynamics 365 for Unified Operations mobile app:

- [For Android phones](https://go.microsoft.com/fwlink/?linkid=850662)
- [For iPhones](https://go.microsoft.com/fwlink/?linkid=850663)

## Sign in to the mobile app

1. Start the app on your mobile device.

1. Enter your Dynamics 365 URL.

1. The first time that you sign in, you're prompted for your user name and password. Enter your credentials.

1. After you sign in, the available workspaces for your company are shown. Note that if your system administrator publishes a new workspace later, you'll have to refresh the list of mobile workspaces.

    ![Select a workspace.](media/am-mobile-01.png "Select a workspace")

## View assigned work order jobs in calendar view

1. On your mobile device, open the **Asset management** workspace.

1. Select **My work order jobs calendar**.

1. Select the date you want to view work order jobs for. In the list, you'll see the asset ID and functional location ID for each work order job.

1. Select a work order job in the list to see job details: Asset and functional location details as well as other navigation links to view **Attachments**, **Checklists**, **Tools**, **Asset counters**, **Notes**, **Journals**.

    ![View assigned work order jobs in calendar view.](media/am-mobile-02.png "View assigned work order jobs in calendar view")

## Create a work order job

1. On your mobile device, open the **Asset management** workspace.

1. Select **All maintenance work orders**.

1. Select the work order you want to create a new work order job for.

1. Select the **Add line** button.

1. Select the **Asset** you want to create a work order job for.

1. Select **Maintenance job type**, **Maintenance job type variant** and **Trade**.

1. Select **Done**.

    ![The Add line screen.](media/am-mobile-03.png "The Add line screen")


## Add attachment to a work order job

1. On your mobile device, open the **Asset management** workspace.

1. Select **All maintenance work orders**.

1. Select the work order > work order job you want to add an attachment to.
    - Alternatively, you can also select **My work order jobs calendar** or **My work order jobs list** on the home page to navigate to the **Work order job details** page.

1. Select **Attachments** on the **Work order job details** page.

1. You'll see existing attachments on the work order job. Select **Add attachment**.

1. Enter **Name** and **Notes** for the attachment.

1. Select **Choose image** to select a photo from the mobile gallery, or **Take photo** to take a photo.

1. Select **Done**.

    ![View and add attachments for a work order job.](media/am-mobile-04.png "View and add attachments for a work order job")

## View maintenance checklist on a work order job

1. On your mobile device, open the **Asset management** workspace.

1. Select **All maintenance work orders**.

1. Select the work order > work order job you want to view checklists for.
    - Alternatively, you can also select **My work order jobs calendar** or **My work order jobs list** on the home page to navigate to the **work order job details** page.

1. Select **Checklists** on the **Work order job details** page.

1. You'll see a list of checklist lines related to the work order job. Select a checklist line to view **Instructions** and add **Notes**.

1. Select the back button (**<**) to return to the previous page.

    ![Maintenance checklist and line details.](media/am-mobile-05.png "Maintenance checklist and line details")

## View and update asset counters on a work order job

1. On your mobile device, open the **Asset management** workspace.

1. Select **All maintenance work orders**.

1. Select the work order > work order job you want to view asset counters for.
    - Alternatively, you can also select **My work order jobs calendar** or **My work order jobs list** on the home page to navigate to the **work order job details** page.

1. Select **Asset counters** on the **Work order job details** page.

1. You see a list of asset counters related to the work order job. Select the pencil icon on an asset counter line to update the counter value.

1. Enter a new counter value, and select **Done**.

    ![View and update asset counters.](media/am-mobile-06.png "View and update asset counters")

## Register consumption on a work order job

1. On your mobile device, open the **Asset management** workspace.

1. Select **All maintenance work orders**.

1. Select the work order > work order job you want to add consumption registrations for.
    - Alternatively, you can also select **My work order jobs calendar** or **My work order jobs list** on the home page to navigate to the **work order job details** page.

1. Select **Journals** on the **Work order job details** page.

1. Select **Add hours** to create work hour registrations.
    1. Select the **Category** from the lookup.
    1. In the **Hours** field, enter the number of work hours spent on the work order job.
    1. Select the appropriate **Line property**.
    1. Select **Done**.

1. Select **Add items** to create item registrations.
    1. Select the **Item number** from the lookup.
    1. Select the **Site** from the lookup.
    1. Enter the **Quantity** of items consumed.
    1. Select **Done**.

1. Select **Add expense** to create expense registrations.
    1. Select the **Category** from the lookup.
    1. Enter the quantity for the expense registration.
    1. Select the **Sales currency** from the lookup.
    1. Enter the **Cost price** for the expense registration.
    1. Select **Done**.

    ![Update a work order journal.](media/am-mobile-07.png "Update a work order journal")

## Update lifecycle state on a work order

1. On your mobile device, open the **Asset management** workspace.

1. Select **All maintenance work orders**.

1. Select the work order you want to update lifecycle state for.

1. Select the **Update state** button at the bottom of the screen.

1. Select a new lifecycle state from the list.

1. Select **Done**.

    ![Update lifecycle state on a work order.](media/am-mobile-08.png "Update lifecycle state on a work order")

## Create a maintenance request

1. On your mobile device, open the **Asset management** workspace.

1. Select **All maintenance requests**.

1. Select **Actions** at the bottom of the screen, and select **Create maintenance request**.

1. If number sequence is enabled for maintenance requests in **Asset management**, the **Maintenance request** field is hidden because it is automatically filled out. If the **Maintenance request** field is visible, enter a maintenance request ID.

1. Select a **Maintenance request type**.

1. Enter a **Description** for the maintenance request.

1. Select the **Asset** you want to create the request for.

1. Select the **Service level** for the maintenance request.

1. Select **Done**.

    ![Create a maintenance request.](media/am-mobile-09.png "Create a maintenance request")

## Add attachment to a maintenance request

1. On your mobile device, open the **Asset management** workspace.

1. Select **All maintenance requests**.

1. Select the maintenance request you want to add an attachment to.

1. Select **Attachments** at the bottom of the screen.

1. Select **Add attachments**.

1. Enter **Name** and **Notes** for the attachment.

1. Select **Choose image** to select a photo from the mobile gallery or **Take photo** to take a photo.

1. Select **Done**.

    ![Add an attachment to a maintenance request.](media/am-mobile-10.png "Add an attachment to a maintenance request")


[!INCLUDE[footer-include](../../includes/footer-banner.md)]