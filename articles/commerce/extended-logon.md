---
title: Set up extended sign-in functionality for Store Commerce app and Store Commerce for web
description: This article describes how to set up and use the extended sign-on functionality for the Microsoft Dynamics 365 Commerce Store Commerce app and Store Commerce for web.
author: boycezhu
ms.date: 01/30/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: global
ms.author: boycez
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.custom: 92353
ms.assetid: 7473e237-fbc8-41d5-8ba0-920242747488
ms.search.industry: Retail
ms.search.form: RetailFunctionalityProfile
---

# Set up extended sign-in functionality for Store Commerce app and Store Commerce for web

[!include [banner](includes/banner.md)]

This article describes how to set up and use the extended sign-on functionality for the Microsoft Dynamics 365 Commerce Store Commerce app and Store Commerce for web.

The Store Commerce app and Store Commerce for web provide an extended sign-on capability that lets retail store workers sign in to the POS application by scanning a bar code or swiping a card by using a magnetic stripe reader (MSR).

## Set up extended sign-in

To set up extended sign-in for POS registers in a retail store, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. 
2. In the left navigation pane, select the functionality profile that is associated with the retail store.
3. On the **Functions** FastTab, under **Additional logon authentication options**, set the following options to **Yes** or **No** as appropriate:

    - **Staff bar code logon** – Set this option to **Yes** if you want your workers to sign in to POS by scanning a bar code. 
    - **Staff bar code logon requires password** – Set this option to **Yes** if you want your workers to enter a password when they sign in to POS by scanning a bar code.
    - **Staff card logon** – Set this option to **Yes** if you want your workers to sign in to POS by swiping a card.
    - **Staff card logon requires password** – Set this option to **Yes** if you want your workers to enter a password when they sign in to POS by swiping a card.

The bar code or card is associated with credentials that can be assigned to a worker. The credentials must have at least six characters. The string that contains the first five characters must be unique and is considered a *credential ID* that is used to look up a worker. The remaining characters are used for security verification. For example, you have two cards, one of which has the credentials 12345DGYDEYTDW, and one of which has the credentials 12345EWUTBDAJH. Because these two cards have the same credential ID, 12345, they can't both be successfully assigned to workers.

## Assign extended sign-in

By default, only managers can assign extended sign-in to workers. To assign extended sign-in, go to **Extended log on** in POS. Then search for a worker by entering the worker's operator ID in the search field. Select the worker, and then click **Assign**. On the next page, swipe or scan the extended sign-in to assign to the worker. If the swipe or scan is successfully read, the **OK** button becomes available. Click **OK** to save the extended sign-in for that worker.

## Delete extended sign-in

To delete the extended sign-in that is assigned to a worker, search for the worker by using the **Extended log on** operation. Select the worker, and then click **Unassign**. All extended sign-in credentials that are associated with that worker are removed.

## Use extended sign-in

After extended sign-in is configured, and a bar code or magnetic stripe is assigned to a worker, the worker just has to swipe or scan their card while the POS sign-in page is shown. If a password is also required before sign-in can continue, the worker is prompted to enter their password.

## Extend extended sign-in

The out-of-box implementation of the extended sign-in capability requires that credentials have a minimum length of six characters, and that the first five characters (the credential ID) be unique. It was originally intended as a sample that developers could customize to meet the requirements of a specific implementation. (For example, it could be customized to support more characters or use different security verification rules.) For detailed information about how to build extensions for extended sign-in, see [Extending the extended sign-on functionality for Store Commerce app and Store Commerce for web](https://cloudblogs.microsoft.com/dynamics365/no-audience/2018/12/14/extending-the-extended-logon-functionality-for-mpos-and-cloud-pos/).

The sign-in service can also be extended to support additional extended sign-in devices, such as palm scanners. For more information, see the [POS extensibility documentation](dev-itpro/pos-extension/pos-extension-overview.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
