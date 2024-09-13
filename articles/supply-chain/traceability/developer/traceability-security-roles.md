---
title: Traceability security roles in Power Apps (preview)
description: The Traceability Add-in adds a security role called *Traceability service role* to your Power Platform environment. Use this role to grant access to the Traceability Add-in.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 07/29/2024
ms.custom: 
  - bap-template
---

# Traceability security roles in Power Apps (preview)

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

The Traceability Add-in for Dynamics 365 Supply Chain Management uses the *System Administrator* and *Finance and Operations Basic User* Power Platform security roles to control access to Traceability app features.

Use the [Power Platform admin center](https://admin.powerplatform.microsoft.com) to grant Traceability permissions to the following types of users:

- **Administrator users** – Assign the default *System Administrator* role, as provided, to users who need to configure the Traceability app with full access.
- **Business users** – Assign the *Finance and Operations Basic User* role to business users who only need inquiry access.

For more information about how to complete these steps, see [Assign a security role to a user](/power-platform/admin/assign-security-roles), [Save time creating a security role by copying one](/power-platform/admin/copy-security-role), and [Create or edit a security role to manage access](/power-platform/admin/create-edit-security-role).
