---
# required metadata

title: NF-e custom certificate validation
description: This topic provides information about enabling and using the NF-e custom certificate.
author: gionoder
manager: AnnBe
ms.date: 10/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# NF-e custom certificate validation

[!include [banner](../includes/banner.md)]

When you turn on this feature, custom validation allows a connection with the web services. This connection is required to transmit NF-e and receive authorization from SEFAZ.

The property, **Server authentication purpose** from the certificate V5 is issued by the Brazilian Root Certificate Authority. The property is disabled by default, and must be manually enabled. In some circumstances, the automatic certificate update can switch this property to no longer be enabled. When this happens, the TLS connection is affected and is no longer trusted. The ability to issue NF-e on production environments for states of Minas Gerais (MG) and Paraná (PR) states is also impacted.

This update allows for an alternative solution for certificate validation, which permits establishing a secure communication.

