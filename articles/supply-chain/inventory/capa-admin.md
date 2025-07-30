---
title: CAPA management administration (preview)
description: Learn how to set up corrective and preventive action (CAPA) management features in Microsoft Dynamics 365 Supply Chain Management.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: InventParameters, SIGProcSetup
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# CAPA management administration (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.45 GA -->

This topic explains how to enable and set up corrective and preventive action (CAPA) management features in Microsoft Dynamics 365 Supply Chain Management.

## Prerequisites

Before you can use CAPA management features in Supply Chain Management, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.44 or later.
- The feature that is named *Advanced quality management* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- If you want to require electronic signatures when CAPA cases are closed, the feature that is named *Electronic signature improvements* must also be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up CAPA parameters

Before users can start to set up and use CAPA features, you must configure a few administrator settings.

1. Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters**.
1. On the **Quality management** tab, set the following fields:

    - **CAPA administrator** – Select the worker who should administer the CAPA program. For each [CAPA worker group](capa-set-up-case-components.md), the CAPA administrator that you specify here can be selected as an automatic group member and/or a default worker.
    - **Use case management workflow** – Select whether the case management workflow can work with CAPA cases.
    - **Require CAPA type** – Set this option to *Yes* if users must specify a CAPA type when they create a CAPA case. If you set this option to *No*, a CAPA type is optional.
    - **Empty case category** – Select the category to apply to new, empty cases. You must select a value if you want to use CAPA.
    - **Require root cause** – Set this option to *Yes* if users must specify a root cause when they create a CAPA case. If you set this option to *No*, a root cause is optional.
    - **Copy documents** – Select whether the system should copy document handling details from CAPA processes to new CAPA cases.

## Load standard worker groups and processes from a template

To get started quickly, you can load a set of standard CAPA processes and worker groups from a template that is provided with Supply Chain Management. You can use the standard records as-is or modify them to meet your specific needs. Learn more about how to work with CAPA processes in [Set up CAPA case components (preview)](capa-set-up-case-components.md).

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **Create standard CAPA process templates**.
1. In the **Create standard CAPA process templates** dialog, set the following fields:

    - **Load** – Set this option to *Yes*.
    - **Name** – Leave this field set to *CAPAProcessTemplate* (the default template that is provided) unless you have another template that you want to use instead.

1. Select **OK**.

## Require an electronic signature to close, cancel, or reopen a CAPA case

You can set up the CAPA features so that an electronic signature is required from any user who closes, cancels, and/or reopens a CAPA case.

An electronic signature confirms the identity of the person who is about to start or approve a computing process. In some industries, an electronic signature is as legally binding as a handwritten one.

### Set up the electronic signature feature

CAPA cases use the standard electronic signature feature that is provided in finance and operations apps. Before you can use this feature, you must configure it and issue certificates to each relevant user. Learn more in [Electronic signatures overview](../../fin-ops-core/fin-ops/organization-administration/electronic-signature-overview.md) and [Set up electronic signatures](../../fin-ops-core/fin-ops/organization-administration/tasks/set-up-electronic-signatures.md).

### Turn the electronic signature requirement for CAPA cases on or off

To set up the electronic signature requirements for CAPA cases, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **Electronic signature** \> **Electronic signature requirements**.
1. In the left pane, select the row where the **Name** field is set to *Close/Cancel CAPA case*.
1. In the right pane, set the **Signature required** option to *Yes* to turn on the feature. Set it to *No* to turn off the feature.

### Status changes that require a signature

The following table shows which status changes for CAPA cases require a signature when the electronic signature requirement is turned on.

| Initial status | New status | Signature required |
|----------------|------------|--------------------|
| Opened         | In Process | No                 |
| Opened         | Canceled   | Yes                |
| In Process     | Opened     | No                 |
| In Process     | Canceled   | Yes                |
| In Process     | Closed     | Yes                |
| Canceled       | Opened     | Yes                |
| Canceled       | In Process | Yes                |
| Closed         | Opened     | Yes                |
| Closed         | In Process | Yes                |
