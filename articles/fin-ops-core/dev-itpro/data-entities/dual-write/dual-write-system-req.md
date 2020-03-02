---
# required metadata

title: System requirements for dual-write
description: This topic describes the system requirements for the setup of a dual-write connection.
author: ramasri
manager: AnnBe
ms.date: 01/14/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 21311
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 2020-01-14
ms.dyn365.ops.version: AX 7.0.0

---

# System requirements for dual-write

[!include [banner](../../includes/banner.md)]

[!include [preview banner](../../includes/preview-banner.md)]

The setup of a dual-write connection has the following requirements:

+ Finance and Operations apps that have build version 10.0.9 and platform update 33 or later
+ Model-driven apps in Microsoft Dynamics 365 that have platform version 9.1.0000.11732 or later

> [!IMPORTANT]
> You can't run dual-write and the [Prospect to cash solution](https://docs.microsoft.com/dynamics365/unified-operations/supply-chain/sales-marketing/accounts-template-mapping-direct) for Data integrator side by side. If you're running the Prospect to cash solution for Data integrator, you must uninstall it.

## One Version

Future updates of the dual-write solution will be available through One Version.
