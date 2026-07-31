---
title: Manage Supplier Engagement app users (preview)
description: Learn about the security roles available in the Supplier Engagement app and how they map to Supply Chain Management roles.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Manage Supplier Engagement app users (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The Supplier Engagement app defines security roles in Dataverse that control what internal users can do in the app. These roles determine access to features such as configuration management, vendor lifecycle processes, user administration, and feedback. Each Dataverse role maps to a corresponding role in Supply Chain Management to ensure consistent access across both systems.

## Supplier Engagement app security roles

The Supplier Engagement app defines four security roles for Dataverse. The following table summarizes each of these roles and their key permissions. In addition, each internal user must also have the *Finance and Operations Basic User Role*.

| Security role | Description | Key permissions |
|---|---|---|
| *Supplier Relationship Management System Administrator* | Has full access to all Supplier Engagement operations. Manages configurations, master data, user access, and flow history. Oversees the full lifecycle of global vendor records. | Can create configuration data, approve or reject registrations, update records, and initiate legal entity transfers. Can delete all records, including configuration data. |
| *Supplier Portal User Admin* | Manages portal user access. Invites users, approves or rejects requests, assigns roles, and manages vendor portal access. | Has access specifically to manage portal user access to vendor records and therefore has limited access to other Supplier Engagement features. |
| *Global Vendor Manager* | Oversees global vendor operations, including certificates, feedback, risk assessment, onboarding, and qualification. | Can approve or reject registrations, update records, and initiate legal entity transfers. Can delete records they created. |
| *Global Vendor Professional User* | Supports onboarding, maintains vendor data, manages certificates, provides feedback, and participates in qualification and approval workflows for assigned vendors. | Can delete records they created, but not those created by others or configuration data. |

## Detailed permissions by area

The following table provides a detailed overview of which areas of the Supplier Engagement app each security role has access to.

| Category | Scenario | *Supplier Relationship Management System Administrator* | *Supplier Portal User Admin* | *Global Vendor Manager* | *Global Vendor Professional User* |
|---|---|---|---|---|---|
| **Configuration data** | Capabilities | Yes | No | No | No |
| | Risks | Yes | No | No | No |
| | Self-assessment | Yes | No | No | No |
| | Settings | Yes | No | No | No |
| **Registration request** | View registration requests | Yes | No | Yes | Yes |
| | Review registration requests | Yes | No | Yes | Yes |
| | Approve/disapprove registration requests | Yes | No | Yes | Yes |
| **Global vendor** | General information | Yes | No | Yes | Yes |
| | Contacts | Yes | No | Yes | Yes |
| | Certificate management | Yes | No | Yes | Yes |
| | Feedback | Yes | No | Yes | Yes |
| | Risk management | Yes | No | Yes | Yes |
| | Portal contacts | Yes | Yes | Yes | No |
| | Lifecycle and vendors | Yes | No | Yes | Yes |

## Map Supplier Engagement roles to Supply Chain Management roles

Each Supplier Engagement app security role maps to a corresponding role in Supply Chain Management. The following table shows these mappings.

| Supplier Engagement app role | Supply Chain Management role |
|---|---|
| *Supplier Relationship Management Admin* | *Purchasing Manager* |
| *Supplier Portal User Admin* | *Purchasing Manager* |
| *Global Vendor Manager* | *Purchasing Manager* |
| *Global Vendor Professional User* | *Purchasing Agent* |

In Supply Chain Management, the *Purchasing Manager* role manages the full procurement lifecycle, including requisitions, orders, vendor interactions, and purchasing policies. The *Purchasing Agent* role supports day-to-day procurement tasks such as creating and managing purchase orders and maintaining vendor details, with more limited access than the manager role.

## Related information

- [Manage users of the Supplier Engagement app and supplier portal](supplier-engagement-manage-users.md)
- [Manage supplier portal users](supplier-engagement-portal-users.md)
- [Supplier Engagement overview](supplier-engagement-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
