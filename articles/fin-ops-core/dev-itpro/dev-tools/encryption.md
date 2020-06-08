---
# required metadata

title: Encryption
description: This topic provides information about encryption
author: nedb
manager: 
ms.date: 06/01/2020
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
ms.custom: 21631
ms.search.region: Global
# ms.search.industry: 
ms.author: nedb
ms.search.validFrom: 2020-01-01
ms.dyn365.ops.version: AX 7.0.0

---

# Encryption in Dynamics 365 for Finance and Operations

[!include [banner](../includes/banner.md)]

## Encryption at rest

Microsoft uses encryption technology to protect customer data while at rest in an environment's SQL Server database and Azure Storage.

All instances utilize [Microsoft SQL Server Transparent Data Encryption (TDE)](https://docs.microsoft.com/en-us/sql/relational-databases/security/encryption/transparent-data-encryption?redirectedfrom=MSDN&view=sql-server-ver15) and/or [Azure Storage encryption](https://docs.microsoft.com/en-us/azure/storage/common/storage-service-encryption) to perform real-time encryption of data when written to disk (at rest). 

Dynamics 365 for Finance and Operations uses server-side encryption using service-managed keys leaving all key management aspects such as key issuance, rotation, and backup to Microsoft.

In addition to the default encryption at rest provided above, customers can take advantage of the encryption API available in the Global X++ class. The methods Global::editEncryptedField() and Global::editEncryptedStringField() take use the environment specific Data Encryption certificate to perform data encryption and decryption. These methods can be used as an additional layer of protection beyond the default encryption at rest technology used for data storage.

## Encryption in transit

Connections established between customers and Microsoft datacenters are encrypted, and all public endpoints are secured using industry-standard TLS 1.2. TLS effectively establishes a security-enhanced browser-to-server connection to help ensure data confidentiality and integrity between desktops and datacenters. 

### Supported TLS versions

Dynamics 365 for Finance and Operations supports TLS 1.2 only. Earlier TLS versions - 1.0 and 1.1 - are not supported.

### Supported Cipher Suites

Dynamics 365 for Finance and Operations supports the following cipher suites only:

* TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384
* TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256
* TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
* TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
* TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384
* TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256
* TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384
* TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256

## Additional resources

* [Azure Data Encryption-at-Rest](https://docs.microsoft.com/azure/security/fundamentals/encryption-atrest)
* [Microsoft SQL Server Transparent Data Encryption (TDE)](https://docs.microsoft.com/sql/relational-databases/security/encryption/transparent-data-encryption?redirectedfrom=MSDN&view=sql-server-ver15)
* [Azure Storage encryption](https://docs.microsoft.com/azure/storage/common/storage-service-encryption)
* [Insider tips on development](https://community.dynamics.com/ax/b/newdynamicsax)
