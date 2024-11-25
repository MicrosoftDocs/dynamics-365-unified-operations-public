---
title: Set up extended sign-in functionality for Store Commerce
description: This article describes how to set up and use the extended sign-on functionality for the Microsoft Dynamics 365 Commerce Store Commerce app and Store Commerce for web.
author: boycezhu
ms.date: 01/09/2024
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: global
ms.author: boycez
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.assetid: 7473e237-fbc8-41d5-8ba0-920242747488
ms.search.industry: Retail
ms.search.form: RetailFunctionalityProfile
---

# Set up extended sign-in functionality for Store Commerce

[!include [banner](includes/banner.md)]

This article describes how to set up and use the extended sign-in functionality for the Microsoft Dynamics 365 Commerce Store Commerce app and Store Commerce for web.

The Store Commerce app and Store Commerce for web provide an extended sign-in capability that lets retail store workers sign in to the point of sale (POS) application by scanning a barcode or swiping a card by using a magnetic stripe reader (MSR).

Before implementing the extended sign-in capability, you must create your own custom extensions because the out-of-box implementation isn't intended for use in production. For more information, see [Extend extended sign-in](#extend-extended-sign-in) section for details.

## User credential and credential ID

User credential and credential ID are two important concepts related to the extended sign-in capability. 

- A *user credential* is a secret string recorded in a physical staff card or barcode, which is scanned during sign-in. For security reasons, Microsoft recommends that the user credential should be at least 256 bits to meet the industry standard, which is 44 characters encoded as a Base64 string.
- A *credential ID* is an internal concept that is generated according to user credential and grant type. The credential ID must be unique to identify staff members. The maximum allowed length of a credential ID is 256 bits due to a data store restriction.

The following example demonstrates the uniqueness requirement of credential IDs. You have two staff cards, one of which has the credentials 12345ABCDE, and one of which has the credentials 12345FGHIJ. The out-of-box extended sign-in implementation uses the first five characters as the credential ID. As a result, the two cards have the same credential ID (12345), and therefore can't both be used to uniquely identify staff workers.

## Set up extended sign-in

To set up extended sign-in for POS registers in a retail store, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**. 
2. In the left navigation pane, select the functionality profile that is associated with the retail store.
3. On the **Functions** FastTab, under **Additional logon authentication options**, set the following options to **Yes** or **No** as appropriate:

    - **Staff bar code logon** – Set this option to **Yes** if you want your workers to sign in to POS by scanning a barcode. 
    - **Staff bar code logon requires password** – Set this option to **Yes** if you want your workers to enter a password when they sign in to POS by scanning a barcode.
    - **Staff card logon** – Set this option to **Yes** if you want your workers to sign in to POS by swiping a card.
    - **Staff card logon requires password** – Set this option to **Yes** if you want your workers to enter a password when they sign in to POS by swiping a card.

The barcode or card is associated with credentials that can be assigned to a worker.

## Assign extended sign-in

By default, only managers can assign extended sign-in to workers. To assign extended sign-in, go to **Extended log on** in POS. Then search for a worker by entering the worker's operator ID in the search field. Select the worker, and then click **Assign**. On the next page, swipe or scan the extended sign-in to assign to the worker. If the swipe or scan is successfully read, the **OK** button becomes available. Click **OK** to save the extended sign-in for that worker.

## Delete extended sign-in

To delete the extended sign-in that is assigned to a worker, search for the worker by using the **Extended log on** operation. Select the worker, and then click **Unassign**. All extended sign-in credentials that are associated with that worker are removed.

## Use extended sign-in

After extended sign-in is configured and a barcode or magnetic stripe is assigned to a worker, the worker just has to swipe or scan their card while the POS sign-in page is displayed. If a password is also required before sign-in can continue, the worker is prompted to enter their password.

## Extend extended sign-in

The first consideration of extending the extended sign-in is to enhance security, because a physical staff card or barcode can be lost and easily duplicated. The second consideration is to provide customers with the flexibility to, for example, use a custom length of credential or credential ID per a business requirement.

In the [extended sign-in sample](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.48/src/ExtendedLogon), a more secure end-to-end extension solution is provided with two factor authentication by PIN number, including both POS and Commerce runtime extensions. The sample covers the entire lifecycle of extended sign-in, including the enrollment of user credentials, staff card or barcode sign-in, the unlocking of terminals, and the elevation of user scenarios. The key extension points described in the following sections must work together to make the whole scenario complete.

### POS extensions

For POS extensions, the key actions are to collect the PIN number from an input dialog immediately after the user swipes the card or scans the barcode, and then pass the PIN number on to the corresponding requests. This operation can be done using an input dialog (**PinInputDialog**) and four pretriggers (**PreEnrollUserCredentialsTrigger**, **PreLogOnTrigger**, **PreUnlockTerminalTrigger**, and **PreElevateUserTrigger**).

### Commerce runtime extensions

There are two important service requests that require customizations.

- **OverrideUserCredentialServiceRequest** is used in both user the credential enrollment and sign-in token validation scenarios, which are used to generate new credentials based on old credentials, and the extra parameters dictionary that contains the PIN number. The PIN number and the original credentials aren't persisted in the data store. Instead, the hashed value of the new credential is persisted.

- **GetUserAuthenticationCredentialIdServiceRequest** is used to calculate the credential ID based on user credentials and the extra parameters dictionary, and also performs a minimum credential length check. The out-of-box implementation of the extended sign-in capability requires that credentials have a minimum length of six characters, and that the first five characters (the credential ID) are unique. This behavior must be changed in the service handler according to security considerations and business requirements.

You can also extend the sign-in service to support additional extended sign-in devices, such as palm scanners. For more information, see the [POS extensibility documentation](dev-itpro/pos-extension/pos-extension-overview.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
