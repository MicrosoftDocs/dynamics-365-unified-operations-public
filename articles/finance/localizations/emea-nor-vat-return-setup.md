---
# required metadata

title: Prepare your environment to interoperate with ID-porten and Altinn web services
description: This topic explains how to prepare your environment to interoperate with ID-porten and Altinn web services.
author: liza-golub
ms.date: 11/18/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Norway
# ms.search.industry: 
ms.author: elgolu
ms.search.validFrom: 2021-11-18
ms.dyn365.ops.version: AX 10.0.22

---

# Prepare your environment to interoperate with ID-porten and Altinn web services

After your company [registered integration point](emea-nor-vat-return-integration-point.md) in ID-porten web portal, complete the following tasks. 
These tasks will prepare your Microsoft Dynamics 365 Finance environment to interoperate with ID-porten and Altinn web services to submit VAT returns.

- [Import and set up Electronic reporting (ER) configurations](#er-setup)
- [Set up application-specific parameters for the VAT Declaration format](#application-specific-parameters)
- [Import a package of data entities that includes a predefined Electronic messaging (EM) setup](#em-setup)
- [Set up the VAT registration number of the company that is reporting VAT return](#vat-registration-number)
- [Set up paper format to preview VAT return](#preview-format)
- [Enable VAT return reporting for companies that report as a VAT group in the same system database](#vat-group)
- [Define a sales tax settlement period](#settlement-period)
- [Set up number sequences for Electronic messages functionality](#number-sequences)
- [Set up document management parameters](#document-management-parameters)
- [Set up validation results transformation schema](#transformation-schema)
- [Set up security roles for electronic message processing](#em-security-roles)
- [Set up security roles to interoperate with ID-porten and Altinn web services](#web-security-roles)
- [Set up client ID and client secret of your ID-porten integration point in Finance](#client-credentials)
- [Set up the internet address of ID-porten and Altinn web services](#internet-address)

ID-porten and Altinn web services require that you use TLS 1.2. For more information about how to enable TLS 1.2, see [How to enable TLS 1.2](https://docs.microsoft.com/en-us/mem/configmgr/core/plan-design/security/enable-tls-1-2).
