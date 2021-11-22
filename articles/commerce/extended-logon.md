---
# required metadata

title: Set up extended logon functionality for MPOS and Cloud POS
description: This topic covers your options for setting up extended logon for Cloud POS and Retail Modern POS (MPOS).
author: boycezhu
ms.date: 09/07/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailFunctionalityProfile
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 92353
ms.assetid: 7473e237-fbc8-41d5-8ba0-920242747488
ms.search.region: global
ms.search.industry: Retail
ms.author: boycez
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Set up extended logon functionality for MPOS and Cloud POS

[!include [banner](includes/banner.md)]

This topic covers your options for setting up extended logon for Cloud POS and Retail Modern POS (MPOS).

## Setting up extended logon

You can find the setup for bar code masks at **Retail and Commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Functionality profiles**. The **Functions** FastTab includes the following options that are related to extended logon.

### Staff bar code logon

When the **Staff bar code logon** option is enabled, workers who have an extended logon assigned to their point of sale (POS) credentials can log on by using a bar code.

### Staff bar code logon requires password

When the **Staff bar code logon requires password** option is enabled, the staff bar code logon selects only the worker who is assigned to the extended logon that is presented. Workers must still enter their password when this option is enabled.

### Staff card logon

When the **Staff card logon** option is enabled, workers who have an extended logon assigned to their POS credentials can log on by using a magnetic stripe.

### Staff card logon requires password

When the **Staff card logon requires password** option is enabled, the staff card logon selects only the worker who is assigned to the extended logon that is presented. Workers must still enter their password when this option is enabled.

## Assigning an extended logon

By default, only managers can assign extended logon to workers. To assign extended logon, go to **Extended log on** in POS. Then search for a worker by entering the worker's operator ID in the search field. Select the worker, and then click **Assign**. On the next page, swipe or scan the extended logon to assign to the worker. If the swipe or scan is successfully read, the **OK** button becomes available. Click **OK** to save the extended logon for that worker.

## Deleting an extended logon

To delete the extended logon that is assigned to a worker, search for the worker by using the **Extended log on** operation. Select the worker, and then click **Unassign**. All extended logon credentials that are associated with that worker are removed.

## Extending extended logon

Extended logon only allows five significant characters to be the unique identifier out-of-the-box. For example, if you configure two cards with the IDs “1234567” and “1234578”, they'll both be considered to be “12345”. You could build an extension to support more characters. For detailed instructions, check [Extending the Extended Logon functionality for MPOS and Cloud POS](https://cloudblogs.microsoft.com/dynamics365/no-audience/2018/12/14/extending-the-extended-logon-functionality-for-mpos-and-cloud-pos/).

The logon service can be extended to support additional extended logon devices, such as palm scanners. For more information, see the POS extensibility documentation.

## Using extended logon

When extended logon is configured, and a worker has been assigned a bar code or magnetic stripe, the worker just has to swipe or scan the worker's card while the POS logon page is displayed. If a password is also required before logon can proceed, the worker is prompted to enter the worker's password.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
