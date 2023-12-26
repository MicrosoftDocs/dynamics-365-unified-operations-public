---
title: Encryption in finance and operations apps
description: This article describes the encryption technology that is used to protect customer data while at rest in an environment's SQL Server database and Azure Storage.
author: nedb
ms.date: 06/15/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: nedb
ms.search.validFrom: 2020-01-01
ms.dyn365.ops.version: AX 7.0.0
---

# Encryption in finance and operations apps

[!include [banner](../includes/banner.md)]

## Encryption at rest

Microsoft uses encryption technology to protect customer data while at rest in an environment's SQL Server database and Azure Storage.

All instances utilize [Microsoft SQL Server Transparent Data Encryption (TDE)](/sql/relational-databases/security/encryption/transparent-data-encryption) and [Azure Storage encryption](/azure/storage/common/storage-service-encryption) to perform real-time encryption of data when written to the disk at rest. 

Finance and operations apps use server-side encryption using service-managed keys. All key management aspects such as key issuance, rotation, and backup are handled by Microsoft.

In addition to the default encryption at rest provided above, you can use the encryption API available in the **Global** X++ class. The methods **Global::editEncryptedField()** and **Global::editEncryptedStringField()** use the environment-specific data encryption certificate to perform data encryption and decryption. You can use these methods as an additional layer of protection beyond the default encryption at rest technology used for data storage.

## Encryption in transit

Connections established between customers and Microsoft datacenters are encrypted, and all public endpoints are secured using industry-standard Transport Layer Security (TLS) 1.2. TLS effectively establishes a security-enhanced browser-to-server connection to help ensure data confidentiality and integrity between desktops and datacenters. 

### Supported TLS versions

Finance and operations apps support TLS 1.2 only. Earlier TLS versions, 1.0 and 1.1, are not supported.

### Supported cipher suites

Finance and operations apps only support the following cipher suites:

* TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384
* TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256
* TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
* TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
* TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384
* TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256
* TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384
* TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256

## Additional resources

* [Azure Data Encryption-at-Rest](/azure/security/fundamentals/encryption-atrest)
* [Microsoft SQL Server Transparent Data Encryption (TDE)](/sql/relational-databases/security/encryption/transparent-data-encryption)
* [Azure Storage encryption](/azure/storage/common/storage-service-encryption)
* [Insider tips on development](https://community.dynamics.com/ax/b/newdynamicsax)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
