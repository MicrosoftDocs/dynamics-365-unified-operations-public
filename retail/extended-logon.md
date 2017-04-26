---
# required metadata

title: Set up extended logon functionality for Cloud POS and MPOS
description: This topic covers your options for setting up extended logon for Cloud POS and Retail Modern POS (MPOS).
author: josaw1
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 41
ms.search.scope: AX 7.0.0, Operations, Core, Retail
# ms.tgt_pltfrm: 
ms.custom: 92353
ms.assetid: 7473e237-fbc8-41d5-8ba0-920242747488
ms.search.region: global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Set up extended logon functionality for Cloud POS and MPOS

[!include[banner](includes/banner.md)]


This topic covers your options for setting up extended logon for Cloud POS and Retail Modern POS (MPOS).

Setting up extended logon
=========================

You can find the setup for bar code masks at **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Functionality profiles**. The **Functions** FastTab includes the following options that are related to extended logon.

### Staff bar code logon

When the **Staff bar code logon** option is enabled, workers who have an extended logon assigned to their point of sale (POS) credentials can log on by using a bar code.

### Staff bar code logon requires password

When the **Staff bar code logon requires password** option is enabled, the staff bar code logon selects only the worker who is assigned to the extended logon that is presented. Workers must still enter their password when this option is enabled.

### Staff card logon

When the **Staff card logon** option is enabled, workers who have an extended logon assigned to their POS credentials can log on by using a magnetic stripe.

### Staff card logon requires password

When the **Staff card logon requires password** option is enabled, the staff card logon selects only the worker who is assigned to the extended logon that is presented. Workers must still enter their password when this option is enabled.

Assigning an extended logon
===========================

By default, only managers can assign extended logon to workers. To assign extended logon, go to **Extended log on** in POS. Then search for a worker by entering his or her operator ID in the search field. Select the worker, and then click **Assign**. On the next page, swipe or scan the extended logon to assign to the worker. If the swipe or scan is successfully read, the **OK** button becomes available. Click **OK** to save the extended logon for that worker.

Deleting an extended logon
==========================

To delete the extended logon that is assigned to a worker, search for the worker by using the **Extended log on** operation. Select the worker, and then click **Unassign**. All extended logon credentials that are associated with that worker are removed.

Extending extended logon
========================

The logon service can be extended to support additional extended logon devices, such as palm scanners. For more information, see the POS extensibility documentation.

Using extended logon
====================

When extended logon is configured, and a worker has been assigned a bar code or magnetic stripe, the worker just has to swipe or scan his or her card while the POS logon page is displayed. If a password is also required before logon can proceed, the worker is prompted to enter his or her password.



