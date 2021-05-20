---
# required metadata

title: NF-e certificates
description: This topic provides information about NF-e certificates for Microsoft Dynamics 365 Finance and the solution you should use for each state tax authority.
author: sndray
ms.date: 01/31/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustTable, EcoResProductDetails, LogisticsAddressSetup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# NF-e certificates

[!include [banner](../includes/banner.md)]

In the Brazilian localization, you must generate a Nota Fiscal eletrônica (NF e) to register the movement of items and services between two parties.
The NF-e fiscal document must be signed and transmitted to the state tax authority using a client certificate issued by a Brazilian certificate authority (CA).
Before you can generate an NF e, you must complete the following tasks:
- Set up web services, rejection codes, and schemas.
- For each fiscal establishment, set up:

    - The client certificate
    - An environment
    - An NF-e version
    - An authority
    - A template
    - Schema validation
    - A contingency mode for NF-e
    
- Set up automatic printing of the Documento auxiliar da Nota fiscal eletrônica (DANFE), so that the DANFE is automatically printed after NF-e approval.
- Set up web services that are related to a fiscal authority.
- Set up a fiscal document type for NF-e.

## Set up certificates
The process that you use to install certificates varies, depending on the state where the NF e fiscal document is issued. Use the correct certificate installation process so that Dynamics 365 Finance can connect with the state web services.

The Brazilian government updated the root certification authority (CA) that is used to issue the certificate required  to establish a Secure Sockets Layer (SSL) connection on the server side. The current version of the root CA is AC Raiz v5. By default, the previous version (AC Raiz v2) is deployed on Microsoft Windows.

## Solutions
- Manually install root CA v5 (AC Raiz v5) – The root certificate must be installed in Trusted Root Certification Authorities store. Although the Brazilian government created a new root certificate (v5), Windows Security hasn’t yet added this certificate to the Trusted Root Certification Authorities store. This means you must open an incident in Windows Support and then manually install the certificate. You can use this workaround until the Windows Security group reaches an agreement with the Brazilian government.
- Install the NF-e proxy on an on-premises VM – The tax authorities for the states of Ceará (CE), Goias (GO), and Pernambuco (PE) didn’t enable the most secure and market-standard protocol, Transport Layer Security (TLS) 1.2, in their web servers. However, the Windows virtual machines (VMs) that are used to run Finance follow Microsoft security policy and allow only connections that use TLS 1.2. Therefore, the system can’t connect directly to these web services. To route communications to those three states, customers must install a proxy web service on an on-premises Windows VM in their Microsoft Azure subscription.

Brazilian certificates must be installed via Azure Key Vault. Key Vault lets you store encrypt keys, certificates, and secrets (such as authentication keys, storage account keys, data encryption keys, .pxf files, and passwords) by using keys that are protected by hardware security modules (HSMs).

For more information about how to use keys and secrets with Key Vault, see [About keys, secrets, and certificates](/rest/api/keyvault/about-keys--secrets-and-certificates).
The following table lists each tax authority and the solution that you should use to install certificates for it.

|Tax authority|	States|	Solution|
|-------------|-------|---------|
|Sefaz Amazonas - (AM)|	AM|	Manually install root CA v5.|
|Sefaz Bahia (BA)|	BA|	Manually install root CA v5.|
|Sefaz Ceará (CE)|	CE|	Install the NF e proxy on an on-premises VM.|
|Sefaz Goias (GO)|	GO|	Install the NF e proxy on an on-premises VM.|
|Sefaz Minas Gerais (MG)|	MG|	Manually install root CA v5.|
|Sefaz Mato Grosso do Sul (MS)|	MS|	No additional solution is required|
|Sefaz Mato Grosso (MT)|	MT|	No additional solution is required|
|Sefaz Pernambuco (PE)|	PE|	Install the NF e proxy on an on-premises VM.|
|Sefaz Paraná (PR)|	PR|	Manually install root CA v5.|
|Sefaz Rio Grande do Sul (RS)|	RS|	No additional solution is required|
|Sefaz São Paulo (SP)|	SP|	No additional solution is required|
|Sefaz Virtual Ambiente Nacional (SVAN)|	MA, PA|	No additional solution is required|
|Sefaz Virtual Rio Grande do Sul (SVRS)|	AC, AL, AP, DF, ES, PB, PI, RJ, RN, RO, RR, SC, SE, TO|	No additional solution is required|

### Contingency authorization authorities (used when the authority is down or offline)

|Tax authority|	States|	Solution|
|-------------|-------|---------|
|Sefaz Virtual de Contingência Ambiente Nacional (SVC-AN)|	AC, AL, AP, DF, ES, MG, PB, RJ, RN, RO, RR, RS, SC, SE, SP, TO|	Manually install root CA v5.|
Sefaz Virtual de Contingência Rio Grande do Sul (SVC-RS)|	AM, BA, CE, GO, MA, MS, MT, PA, PE, PI, PR|	No additional solution is required|




[!INCLUDE[footer-include](../../includes/footer-banner.md)]