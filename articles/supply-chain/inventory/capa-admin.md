---
title: CAPA management administration (preview)
description: Learn how to set up corrective and preventive action (CAPA) management features in Dynamics 365 Supply Chain Management.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# CAPA management administration (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This topic describes how to enable and set up corrective and preventive action (CAPA) management features in Dynamics 365 Supply Chain Management.

## Prerequisites

To use CAPA management features in Supply Chain Management, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The feature that is named *(Preview) Advanced quality management* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- If you also want to require electronic signature for closing CAPA cases, then feature that is named *(Preview) Electronic signature improvements* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

<!-- KFM: Do we need any of the other new feature? Signatures maybe? -->
<!-- KFM: describe here how to set up Outlook integration? If not, then where? -->

## Set up CAPA parameters

Before users can start to set up and use CAPA features, you must make a few administrator settings to configure the feature.

1. Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters**.
1. Open the **Quality management** tab.
1. Make the following settings:
    - **CAPA administrator** – Choose the worker who should administer the CAPA program. For each [CAPA worker group](capa-set-up-case-components.md), you can choose to set the CAPA administrator chosen here as an automatic group member and/or default worker.<!-- KFM: More info would help. What powers does this user have? Why do we need this? Mention whether this is mandatory to use CAPA. -->
    - **Use case management workflow** – Choose whether to allow the case management workflow to work with CAPA cases. <!-- KFM: More info would help. What does this mean, what effect does it have? -->
    - **Require CAPA type** – Choose whether users must specify a CAPA type when creating a CAPA case. If set to *No*, then the CAPA type setting is optional. <!-- KFM: My guess. Please confirm. -->
    - **Empty case category** – <!-- KFM: description needed. What is this for? Any advice for which value to choose? Mention whether this is mandatory to use CAPA.  -->
    - **Require root cause** – Choose whether users must specify a root cause when creating a CAPA case. If set to *No*, then the root cause setting is optional. <!-- KFM: My guess. Please confirm. -->
    - **Copy documents** – Choose whether the system should copy document handling details from CAPA processes to new CAPA cases. <!-- KFM: If set to *No*, is this still an option? -->

## Load standard worker groups and processes from the template

To get started quickly, you can load a set of standard CAPA processes and worker groups from a template provided with Supply Chain Management. You can use the standard records as-is or modify them to meet your specific needs. Learn more about how to work with CAPA processes in [Set up CAPA case components](capa-set-up-case-components.md).

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **Create standard CAPA process templates**.
1. In the **Create standard CAPA process templates** dialog, make the following settings:
    - **Load** – Set to *Yes*.
    - **Name** – Leave set to *CAPAProcessTemplate* (the template provided by default) unless you have another template available that you want to load. <!-- KFM: Confirm this. There are lots of strange options available here, and *CAPAProcessTemplate* isn't actually one of them if you change it; what's going on?-->

1. Select **OK**.

## Require an electronic signature to close, cancel, or reopen a CAPA case

You can set up the CAPA feature so that it requires an electronic signature from any user that closes, cancels, and/or reopens a CAPA case.

An electronic signature confirms the identity of a person who is about to start or approve a computing process. In some industries, an electronic signature is as legally binding as a handwritten one.

### Set up the electronic signature feature

CAPA cases use the standard electronic signature feature provided for Microsoft finance and operations apps. You must configure the feature and issue certificates to each relevant user before you can use it. To learn more, see [Electronic signatures overview](../../fin-ops-core/fin-ops/organization-administration/electronic-signature-overview.md) and [Set up electronic signatures](../../fin-ops-core/fin-ops/organization-administration/tasks/set-up-electronic-signatures.md).

### Turn the electronic signature requirement for CAPA cases on or off

To set up the electronic signature requirements for CAPA cases, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **Electronic signature** \> **Electronic signature requirements**.
1. In the left pane, select the row with **Name** *Close/Cancel CAPA case*.
1. In the right pane, set **Signature required** to *Yes* to turn on the feature. Set it to *No* to turn off the feature.

### Status changes that require a signature

The following table describes which CAPA case status changes require a signature when you turn on the signature requirement for CAPA cases.

| Initial status | New status | Signature required |
|----------------|------------|--------------------|
| Opened         | In Process | NO                 |
| Opened         | Canceled   | YES                |
| In Process     | Opened     | NO                 |
| In Process     | Canceled   | YES                |
| In Process     | Closed     | YES                |
| Canceled       | Opened     | YES                |
| Canceled       | In Process | YES                |
| Closed         | Opened     | YES                |
| Closed         | In Process | YES                |
