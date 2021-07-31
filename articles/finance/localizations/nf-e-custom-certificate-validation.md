---
# required metadata

title: NF-e custom certificate validation
description: This topic provides information about enabling and using the NF-e custom certificate.
author: gionoder
ms.date: 07/29/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
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

The **Server authentication purpose** property from the certificates issued by the Brazilian Root Certificate Authority is turned off by default and must be manually enabled. In some circumstances, the automatic certificate update can switch this property to no longer be enabled. If this happens, the TLS connection is affected and can no longer be trusted. The ability to issue the Brazilian electronic fiscal document model 55 (NF-e) on production environments for states of Minas Gerais (MG) and Paraná (PR) is impacted.

To enable the fix for **NF-e custom certificate validation**, go to **Feature management**. This feature allows an alternative solution for the V5 and V10 certificate validations and permits a trusted connection with the web services, which is required for the secure transmission of the NF-e and receipt of the authorization from SEFAZ.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
