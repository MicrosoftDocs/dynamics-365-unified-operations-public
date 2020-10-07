---
# required metadata

title: Troubleshoot "Dynamics 365 for Finance and Operations - Warehosing" mobile app connection issues
description: This topic describes how to resolve issues that you might encounter while trying to configure the warehouse mobile app connection to Dynamics.
author: ivanv-microsoft
manager: tfehr
ms.date: 09/13/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WMA
# ROBOTS: 
audience: Warehouse manager
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Warehousing
ms.author: ivanv
ms.search.validFrom: 2020-9-13
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot connection issues for *Dynamics 365 for Finance and Operations - Warehousing* application

This topic describes how to fix common issues that you might encounter while connecting the Warehouse mobile application with Dynamics 365 SCM application.

**Important**

If your issue is not listed below, please add a comment explaining the issue in detail here in this topic, or send a mail with this information to *dscmwarehousingand@microsoft.com*, so we can help you troubleshoot it, and append the below list

## Trust anchor for certification path not found

**Scope**

- OS version: Android 4.4.x devices (e.g., Zebra TC55). Not an issue on recent Android versions.
- Dynamics 365 location: Cloud / On Prem
- Connection mode: Client secret / Certificate

**Possible root cause**

Server SSL certificates updated by Microsoft so that one of the Intermediate certificates or Root certificate changes.
As a result, this certificate is not in the lst of trusted system certificates on the mobile device.

**Resolution**

- Contact Zebra / Google for an update of the system trusted CA certificates.
- Replace the device(s) with ones that are running a more recent version of Andriod (they get the trusted CAs updated automatically)

**Workaround**

Manually download the new root certificate as described below and install it onto the impacted devices. This certificate will show up under USER trusted certificates on the device.

TBD


## TO BE DONE
The line numbers for imported purchase order lines through data entity "Purchase order lines V2" are not defaulting to system line number increment specified in system parameters when adding auto-generated line numbers in DMF. When you create a PO and add lines manually through UI, it is correctly incrementing. However, when using DMF it is not.

**Resolution**
When importing the lines via the Data Management framework it will use the data management frameworks methods of assigning line numbers, when the line number is not already assigned in the imported entity. And that method is increments of 1.

**Workaround**
A way to do this could be to make sure that the desired line numbers are already given in the entity data when importing the purchase order line, then they will not be overwritten by the data management framework.
