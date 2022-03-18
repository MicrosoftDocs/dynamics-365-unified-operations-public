---
# required metadata

title: Set up and use extended logon
description: This topic describes how to set up and use the extended logon capability of the Microsoft Dynamics 365 Commerce point of sale (POS) application.
author: boycez
ms.date: 03/18/2022
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

# Set up and use extended logon capability

[!include [banner](includes/banner.md)]

This topic describes how to set up and use the extended logon capability of the Microsoft Dynamics 365 Commerce point of sale (POS) application.

Cloud POS (CPOS) and Modern POS (CPOS) provide extended logon capability for retail store workers to sign in to the POS application by scanning a barcode or swiping a card with a magnetic stripe reader (MSR).

## Set up extended logon

To set up extended logon for POS registers in a retail store, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. 
2. In the left navigation pane, select the functionality profile that is associated with the retail store.
3. On the **Functions** FastTab under **Additional logon authentication options**, set the following options to **Yes** or **No** as appropriate. 
    - **Staff bar code logon**. Set this option to **Yes** if you want your workers to sign in to POS by scanning a barcode. 
    - **Staff bar code logon requires password**. Set this option to **Yes** if you want your workers to enter a password when they sign in to POS by scanning a barcode.
    - **Staff card logon**. Set this option to **Yes** if you want your workers to sign in to POS by swiping a card.
    - **Staff card logon requires password**. Set this option to **Yes** if you want your workers to enter a password when they sign in to POS by swiping a card.

The barcode or card is associated with credentials that can be assigned to a worker, and credentials must have at least six characters. The string containing the first five characters must be unique and is considered a *credential ID* that is used to look up a worker. The rest of the characters are used for security verification. For example, if you have two cards with the credentials "12345DGYDEYTDW" and "12345EWUTBDAJH", they both have the same credential ID "12345" and can't both be successfully assigned to workers.

## Assign extended logon

By default, only managers can assign extended logon to workers. To assign extended logon, go to **Extended log on** in POS. Then search for a worker by entering the worker's operator ID in the search field. Select the worker, and then click **Assign**. On the next page, swipe or scan the extended logon to assign to the worker. If the swipe or scan is successfully read, the **OK** button becomes available. Click **OK** to save the extended logon for that worker.

## Delete extended logon

To delete the extended logon that is assigned to a worker, search for the worker by using the **Extended log on** operation. Select the worker, and then click **Unassign**. All extended logon credentials that are associated with that worker are removed.

## Use extended logon

When extended logon is configured, and a worker has been assigned a bar code or magnetic stripe, the worker just has to swipe or scan the worker's card while the POS logon page is displayed. If a password is also required before logon can proceed, the worker is prompted to enter the worker's password.

## Extend extended logon

The out-of-the-box implementation of the extended logon capability has a minimal length requirement of six characters for a credential where the first five characters (the credential ID) must be unique. It was originally intended to be a sample that developers could customize to fit the specific needs of a particular implementation, for example supporting more characters or using different security verification rules. For detailed instructions about how to build extensions for extended logons, see [Extending the extended logon functionality for MPOS and Cloud POS](https://cloudblogs.microsoft.com/dynamics365/no-audience/2018/12/14/extending-the-extended-logon-functionality-for-mpos-and-cloud-pos/).

The logon service can also be extended to support additional extended logon devices, such as palm scanners. For more information, see the POS extensibility documentation.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
