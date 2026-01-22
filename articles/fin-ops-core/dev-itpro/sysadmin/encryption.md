---
title: Encryption in finance and operations apps
description: Learn about the encryption technology that is used to protect customer data while at rest in an environment's SQL Server database and Azure Storage.
author: nedb
ms.author: johnmichalak
ms.topic: article
ms.date: 06/15/2020
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2020-01-01
ms.dyn365.ops.version: AX 7.0.0
---

# Encryption in finance and operations apps

[!include [banner](../includes/banner.md)]

## Encryption at rest

Microsoft uses encryption technology to protect customer data while at rest in an environment's SQL Server database and Azure Storage.

All instances use [Microsoft SQL Server Transparent Data Encryption (TDE)](/sql/relational-databases/security/encryption/transparent-data-encryption) and [Azure Storage encryption](/azure/storage/common/storage-service-encryption) to encrypt data in real time when the system writes it to the disk at rest. 

Finance and operations apps use server-side encryption with service-managed keys. Microsoft handles all key management tasks, including key issuance, rotation, and backup.

In addition to the default encryption at rest, you can use the encryption API available in the **Global** X++ class. The methods **Global::editEncryptedField()** and **Global::editEncryptedStringField()** use the environment-specific data encryption certificate to encrypt and decrypt data. Use these methods as an extra layer of protection beyond the default encryption at rest technology for data storage.

## Encryption in transit

Connections between customers and Microsoft datacenters are encrypted. All public endpoints use industry-standard Transport Layer Security (TLS) 1.2. TLS establishes a security-enhanced browser-to-server connection to help ensure data confidentiality and integrity between desktops and datacenters. 

### Supported TLS versions

Finance and operations apps support only TLS 1.2. Earlier TLS versions 1.0 and 1.1 aren't supported.

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
