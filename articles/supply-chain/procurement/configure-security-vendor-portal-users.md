---
# required metadata

title: Vendor portal user security
description: This article explains how to set up security for external vendors who use the Vendor portal. This information applies only to the February 2016 &amp; May 2016 versions of Dynamics AX.
author: mkirknel
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: SysUserManagement
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: yuyus
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 30231
ms.assetid: 3574db17-81c7-4c5a-999b-0098aa0b9cda
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Vendor portal user security

[!include[banner](../includes/banner.md)]


This article explains how to set up security for external vendors who use the Vendor portal. This information applies only to the February 2016 &amp; May 2016 versions of Dynamics AX.

The Vendor portal functionality has been replaced by extended vendor collaboration functionality in Dynamics 365 for Operations version 1611. For more information about setting up security for vendor collaboration, see [Set up and maintain vendor collaboration](set-up-maintain-vendor-collaboration.md). The Vendor portal exposes a limited set of information about purchase orders (POs) to external vendors. It's important that you correctly set up user permissions for the Vendor portal in Microsoft Dynamics AX, so that vendors don't have unintended access to additional information in your Dynamics AX installation. **Important:** Unlike other users, external vendors should not have the **SystemUser** role. The **SystemUser** role grants access to a set of privileges that aren't suitable for external users.

## Setting up a Vendor portal user
Before you create a user account for someone who will use the Vendor portal, you must set up the vendor to allow for Vendor portal collaboration. Use the **Purchase order collaboration** field on the **General** tab on the **Vendors** page. External vendors that use the Vendor portal must have the following setup:

-   A Microsoft Azure Active Directory (AAD) user account must be registered for the vendor on the **Users** page in Dynamics AX.
-   The vendor must have the **Vendor (external)** security role, not the **SystemUser** role. **Note:** The **SystemUser** role is automatically granted when you create a new user account in Dynamics AX. Therefore, you must remove that role and acknowledge the warning message that you receive.
-   The vendor user should not be granted permission to add additional fields from the PO tables to their view of the PO. On the **Personalization** tab, on the **Users** tab, set the **Explicit personalization allowed** option for the user to **No**.
-   The user account must be associated with a registered contact person. On the **Users** page, select a contact person in the **Name** field. The person that you select should have the **Contact** role for the relevant vendor.

If the same person requires access to the Vendor portal for multiple vendor accounts (for different legal entities, perhaps), each of that person's user accounts must be associated with the same registered contact person. The **Vendor (external)** role includes all the basic capabilities that are required in order to use the functionality that is available in the Vendor portal. This setup helps guarantee that the user interface that the external user sees is focused on the intended scenario only.

See also
--------

[Vendor collaboration](collaborate-vendors-vendor-portal.md)



