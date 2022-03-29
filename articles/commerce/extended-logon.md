---
# required metadata

title: Set up and use the extended logon capability
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

# Set up and use the extended logon capability

[!include [banner](includes/banner.md)]

This topic describes how to set up and use the extended logon capability of the Microsoft Dynamics 365 Commerce point of sale (POS) application.

Cloud POS (CPOS) and Modern POS (MPOS) provide an extended logon capability that lets retail store workers sign in to the POS application by scanning a bar code or swiping a card by using a magnetic stripe reader (MSR).

## Set up extended logon

To set up extended logon for POS registers in a retail store, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. 
2. In the left navigation pane, select the functionality profile that is associated with the retail store.
3. On the **Functions** FastTab, under **Additional logon authentication options**, set the following options to **Yes** or **No** as appropriate:

    - **Staff bar code logon** – Set this option to **Yes** if you want your workers to sign in to POS by scanning a bar code. 
    - **Staff bar code logon requires password** – Set this option to **Yes** if you want your workers to enter a password when they sign in to POS by scanning a bar code.
    - **Staff card logon** – Set this option to **Yes** if you want your workers to sign in to POS by swiping a card.
    - **Staff card logon requires password** – Set this option to **Yes** if you want your workers to enter a password when they sign in to POS by swiping a card.

The bar code or card is associated with credentials that can be assigned to a worker. The credentials must have at least six characters. The string that contains the first five characters must be unique and is considered a *credential ID* that is used to look up a worker. The remaining characters are used for security verification. For example, you have two cards, one of which has the credentials 12345DGYDEYTDW, and one of which has the credentials 12345EWUTBDAJH. Because these two cards have the same credential ID, 12345, they can't both be successfully assigned to workers.

## Assign extended logon

By default, only managers can assign extended logon to workers. To assign extended logon, go to **Extended log on** in POS. Then search for a worker by entering the worker's operator ID in the search field. Select the worker, and then click **Assign**. On the next page, swipe or scan the extended logon to assign to the worker. If the swipe or scan is successfully read, the **OK** button becomes available. Click **OK** to save the extended logon for that worker.

## Delete extended logon

To delete the extended logon that is assigned to a worker, search for the worker by using the **Extended log on** operation. Select the worker, and then click **Unassign**. All extended logon credentials that are associated with that worker are removed.

## Use extended logon

After extended logon is configured, and a bar code or magnetic stripe is assigned to a worker, the worker just has to swipe or scan their card while the POS logon page is shown. If a password is also required before logon can continue, the worker is prompted to enter their password.

## Extend extended logon

The out-of-box implementation of the extended logon capability requires that credentials have a minimum length of six characters, and that the first five characters (the credential ID) be unique. It was originally intended as a sample that developers could customize to meet the requirements of a specific implementation. (For example, it could be customized to support more characters or use different security verification rules.) For detailed information about how to build extensions for extended logon, see [Extending the extended logon functionality for MPOS and Cloud POS](https://cloudblogs.microsoft.com/dynamics365/no-audience/2018/12/14/extending-the-extended-logon-functionality-for-mpos-and-cloud-pos/).

The logon service can also be extended to support additional extended logon devices, such as palm scanners. For more information, see the [POS extensibility documentation](dev-itpro/pos-extension/pos-extension-overview.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
