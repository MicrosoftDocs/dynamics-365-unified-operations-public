---
# required metadata

title: Health check for point of sale peripherals and services
description: This topic provides an overview of the health check operation in the point of sale..
author: rubendel
manager: AnnBe
ms.date: 05/09/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Health check for point of sale peripherals and services


[!include [banner](../includes/banner.md)]

This topic describes the new health check operation in the point of sale.

## Overview

Retail stores can be complex environments with many applications and devices in use. As operations grow, it can become difficult to ensure that operations are always running smoothly due to dependencies on things like peripherals that can break or accidentally become unplugged over the course of the day. Troubleshooting issues related to devices and services can become very costly for larger merchants and equally frustrating for smaller operations. 

For 10.0.10, a new operation is being introduced which can alleviate some of this pain by providing a method to check these devices from the point of sale, outside of normal operations. This new health check operationswill help retailers detect problems before they occur with a customer standing in line. 

## Key terms

| Term | Description |
|---|---|
| Peripherals | Any device that the point of sale application uses to facilitate transactions and other operations within the store. Examples include cash drawers, bar code scanners, and payment terminals. |
| Services | For the purpose of this document, services describe ancillary applications that the point of sale application depends on to perform transactions and daily operations. Examples include services that aid in tax or shipping calculations. |

