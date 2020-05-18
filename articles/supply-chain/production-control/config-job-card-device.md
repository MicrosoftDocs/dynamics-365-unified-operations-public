---
# required metadata

title: Configure job card for devices
description: XXXX
author: johanhoffmann
manager: tfehr
ms.date: 05/29/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: XXXX
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: johanho
ms.search.validFrom: 2020-05-29
ms.dyn365.ops.version: Release 10.0.12
---
<!-- KFM: In above meta data, add: 

description: Add description based on intro
ms.search.form: Add the form name for context help; I think that's (other?): JmgRegistrationSetupTouch

 -->


# Configure job card for devices

<!-- KFM: Add a short intro. What is a job card device, what does it do? What will we do in this topic? -->

## Enable new features in feature management

A few of the settings described in this topic must be enabled on your system before they will be available to you. Use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to enable any or all of the following features as required:

### Generate license plate

To make this feature available, enable the following features in feature management (in order):

1. *License plate for reporting as finished added to the Job Card Device*
1. *Enable automatic generation of license plate number when reporting as finished in the job card device*

### Print label

To make this feature available, enable the following features in feature management (in order):

1. *License plate for reporting as finished added to the Job Card Device*
1. *Print label from Job Card Device*

### Allow locking of touch screen

To make this feature available, enable the following features in feature management (in order):

1. 
1. 

## Manage and configure your devices

To configure your job card devices, go to **Production control > Setup > Manufacturing execution > Configure job card for devices**. The **Configure job card for devices** page opens, which shows a list of existing devices. From here, you can do the following:

- Select any device listed in the left column to view and edit the configuration settings for that device
- Select **New** on the Action Pane to add a new device to the list. Then enter a name in the **Configuration** field to identify the new device. The value you enter here must be unique among all devices, and you won't be able to edit it later.

See the following sections for details about each of the settings and FastTabs provided here.

## General settings

The **General** FastTab lets you configure each of the various options available for the job card device. The following settings are available here:

- **Report quantity at clock-out** - 
- **Lock employee** - 
- **Barcode scanner** - 
- **Use the actual time of registration** - 
- **Single worker** - 
- **Allow workers to set personal filters** - 
- **Allow locking the touchscreen** - 
- **Production unit** - 
- **Resource group** - 
- **Resource** - 
- **Generate license plate** - 
- **Print label** - 

## Assigned users

Use the **Assigned users** FastTab to ... <!-- KFM: Describe this, why we have it, and what we can do here -->

## Additional resources

[Report production orders as finished](report-production-orders-as-finished.md)
