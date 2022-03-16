---
# required metadata

title: Extended logon
description: This topic describes how to set up and use extended logon capability in POS application.
author: boycez
ms.date: 03/16/2022
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

# Extended logon

[!include [banner](includes/banner.md)]

Cloud POS (CPOS) and Modern POS (CPOS) provide extended logon capability for retail store workers to log in POS application by scanning a barcode or swipping a card with a magnetic stripe reader (MSR). This topic describes how to set up and use this capability.

## Setting up extended logon

To set up extended logon for POS registers in a retail store, in Commerce headquarters, find the functionality profile that is associated with the retail store, in the **Functions** FastTab, set **Additional logon authentication options** appriopriately. 

- **Staff bar code logon**. Use this option if you want your workers to log in POS by scanning barcode. 
- **Staff bar code logon requires password**. Use this option if you want your workers to log in POS by scanning barcode, plus entering their password.
- **Staff card logon**. Use this option if you want your workers to log in POS by swiping a card.
- **Staff card logon requires password**. Use this option if you want your workers to log in POS by swiping a card, plus entering their password.

The barcode or card is associated with a credential that could be assigned to a worker. Out of the box, a credential must have at least **six** characters. The first **five** characters combined is considered **credential ID**, used to lookup worker, and must be unique. The rest characters are used for security verification. For example, if you have two cards with IDs "12345DGYDEYTDW" and "12345EWUTBDAJH", they have the same credential ID "12345", therefore one of them cannot be successfully assigned to a worker if the other is already assigned.

## Assigning extended logon

By default, only managers can assign extended logon to workers. To assign extended logon, go to **Extended log on** in POS. Then search for a worker by entering the worker's operator ID in the search field. Select the worker, and then click **Assign**. On the next page, swipe or scan the extended logon to assign to the worker. If the swipe or scan is successfully read, the **OK** button becomes available. Click **OK** to save the extended logon for that worker.

## Deleting extended logon

To delete the extended logon that is assigned to a worker, search for the worker by using the **Extended log on** operation. Select the worker, and then click **Unassign**. All extended logon credentials that are associated with that worker are removed.

## Using extended logon

When extended logon is configured, and a worker has been assigned a bar code or magnetic stripe, the worker just has to swipe or scan the worker's card while the POS logon page is displayed. If a password is also required before logon can proceed, the worker is prompted to enter the worker's password.

## Extending extended logon

As described earlier, the out-of-the-box implementation of extended logon has minimal length requirement on credential (six characters minimal) and hard-coded logic on credential ID (first five characters to be unique). It was originally intended to be a sample upon which developers could customize to fit the specific needs of a particular implementation. For example, support more characters, or leverage different security verification rule. For detailed instructions about how to build extensions on extended logon, please check [Extending the Extended Logon functionality for MPOS and Cloud POS](https://cloudblogs.microsoft.com/dynamics365/no-audience/2018/12/14/extending-the-extended-logon-functionality-for-mpos-and-cloud-pos/).

The logon service can also be extended to support additional extended logon devices, such as palm scanners. For more information, see the POS extensibility documentation.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
