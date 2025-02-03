---
title: CAPA administration
description:
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# CAPA administration

[!include [banner](../../includes/banner.md)]

<!-- KFM: Describe prerequisites here (SCM version, Feature management). Either as a standard section or as a link to a topic that describes Advanced Quality Management features/configuration. -->

<!-- KFM: describe here how to set up Outlook integration? If not, then where? -->

## Set up CAPA parameters

Before users can start to set up and use CAPA features, you must make a few administrator settings to configure the feature.

1. Go to **Inventory management** \> **Setup** \> **Inventory management parameters**. <!-- KFM: This might be moved? -->
1. Open the **Quality management** tab.
1. Make the following settings:
    - **CAPA administrator** – <!-- KFM: description needed. -->
    - **Empty case category** – <!-- KFM: description needed -->

## Load standard worker groups and processes from the template

<!-- KFM: maybe more types of records are created by this template? We should list them all. What can go wrong if we do this after already configuring these elements in the system? -->

To get started quickly, you can load a set of standard CAPA processes and worker groups from a template provided with Supply Chain Management. You can use the standard records as-is or modify them to meet your specific needs. Learn more about how to work with CAPA processes in [Set up CAPA case components](quality-capa-set-up-case-components.md).


1. Go to **System administration** \> **Setup** \> **Setup Advanced Quality Management**.
1. On the **General** tab, select **Create CAPA process templates**.
1. In the **Create standard CAPA process templates** dialog, make the following settings:
    - **Load** – Set to *Yes*.
    - **Name** – Leave set to *CAPAProcessTemplate* (the template provided by default) unless you have another template available that you want to load. <!-- KFM: Confirm this. -->

1. Select **OK**.

<!-- KFM: maybe describe that the **CAPA administrator** should now be added to a worker group (which?). Errors are shown. -->
