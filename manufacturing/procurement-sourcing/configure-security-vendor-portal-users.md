---
# required metadata

title: Vendor portal user security | Microsoft Docs
description: This article explains how to set up security for external vendors who use the Vendor portal. This information applies only to the February 2016 &amp; May 2016 versions of Dynamics AX.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-01-28 15:01:52
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: SysUserManagement
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 2084
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 30231
ms.assetid: 50cb0ca7-30cf-4746-9c25-4bc8eeec69b8
ms.region: Global
# ms.industry: 
ms.author: mkirknel

---

# Vendor portal user security

This article explains how to set up security for external vendors who use the Vendor portal. This information applies only to the February 2016 &amp; May 2016 versions of Dynamics AX.

The Vendor portal functionality has been replaced by extended vendor collaboration functionality in Dynamics 365 for Operations version 1611. For more information about setting up security for vendor collaboration, see [Set up and maintain vendor collaboration](https://docs.microsoft.com/en-us/dynamics365/operations/core/organization-administration/set-up-and-maintain-vendor-collaboration). The Vendor portal exposes a limited set of information about purchase orders (POs) to external vendors. It's important that you correctly set up user permissions for the Vendor portal in Microsoft Dynamics AX, so that vendors don't have unintended access to additional information in your Dynamics AX installation. **Important:** Unlike other users, external vendors should not have the **SystemUser** role. The **SystemUser** role grants access to a set of privileges that aren't suitable for external users.

## Setting up a Vendor portal user
Before you create a user account for someone who will use the Vendor portal, you must set up the vendor to allow for Vendor portal collaboration. Use the **Purchase order collaboration** field on the **General** tab on the **Vendors** page. External vendors that use the Vendor portal must have the following setup:

-   A Microsoft Azure Active Directory (AAD) user account must be registered for the vendor on the **Users** page in Dynamics AX.
-   The vendor must have the **Vendor (external)** security role, not the **SystemUser** role. **Note:** The **SystemUser** role is automatically granted when you create a new user account in Dynamics AX. Therefore, you must remove that role and acknowledge the warning message that you receive.
-   The vendor user should not be granted permission to add additional fields from the PO tables to their view of the PO. On the **Personalization** tab, on the **Users** tab, set the **Explicit personalization allowed** option for the user to **No**.
-   The user account must be associated with a registered contact person. On the **Users** page, select a contact person in the **Name** field. The person that you select should have the **Contact** role for the relevant vendor.

If the same person requires access to the Vendor portal for multiple vendor accounts (for different legal entities, perhaps), each of that person's user accounts must be associated with the same registered contact person. The **Vendor (external)** role includes all the basic capabilities that are required in order to use the functionality that is available in the Vendor portal. This setup helps guarantee that the user interface that the external user sees is focused on the intended scenario only.

See also
--------

[Vendor collaboration](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/procurement-sourcing/collaborating-with-vendors-using-the-vendor-portal)

