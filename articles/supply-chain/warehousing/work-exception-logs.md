---
title: Work exceptions log
description: Learn about work exceptions log. This functionality lets you register issues from your operational workflows to be tracked and addressed.
author: sservulo
ms.author: samuoliveira
ms.topic: article
ms.date: 11/15/2024
ms.custom:
ms.reviewer: --
ms.search.form: WHSWorkExceptionLog
---

# Work exceptions log

[!include [banner](../includes/banner.md)]

Work exceptions let you register work related errors that occur in your warehouse operations, for example: discrepancies in inventory, missing goods on given locations, etc. Registering these exceptions in the work exceptions log can be used to help track and diagnose issues related to warehouse work workflows such as pick or pack procedures.

To view the work exceptions log, navigate to **Warehouse management \> Work \> Work exceptions log**), where it can be further filtered based **Status** or other characteristics inherited from the Work.

Work exceptions can also be visualized from other forms, such as **Outbound work monitoring** (found in **Warehouse management \> Workspaces \> Outbound work monitoring**), where **Locations** with open exceptions can be further explored.

![Outbound work monitoring form](media/outbound-work-monitoring-form.png)

![Locations with open work exceptions form](media/locations-with-open-exceptions-form.png)

Take note that even once resolved, logs are kept in the system until explicitly removed either manually or using a clean-up job.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
