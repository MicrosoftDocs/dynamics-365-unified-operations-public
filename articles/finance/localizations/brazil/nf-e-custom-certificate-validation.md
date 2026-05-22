---
title: NF-e custom certificate validation
description: Learn how to enable and use the NF-e custom certificate.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/05/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2020-07-08
---
# NF-e custom certificate validation

[!include [banner](../../includes/banner.md)]

The **Server authentication purpose** property is turned off by default in certificates issued by the Brazilian Root Certificate Authority. You must manually enable this property. In some circumstances, the automatic certificate update can switch this property off. If this property is off, the TLS connection is affected and can no longer be trusted. This problem affects the ability to issue the Brazilian electronic fiscal document model 55 (NF-e) in production environments for the states of Minas Gerais (MG) and Paraná (PR).

To enable the fix for **NF-e custom certificate validation**, go to **Feature management**. This feature provides an alternative solution for the V5 and V10 certificate validations. It ensures a trusted connection with the web services, which is required for the secure transmission of the NF-e and the receipt of the authorization from SEFAZ.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
