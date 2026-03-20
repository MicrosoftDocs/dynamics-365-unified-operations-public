---
title: Electronic invoicing components
description: This article provides an overview of the administration and integration components for Electronic invoicing.
author: ilikond
ms.author: ikondratenko
ms.topic: overview
ms.date: 03/18/2026
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2024-01-29
ms.custom: 
  - bap-template
---

# Electronic invoicing components

[!INCLUDE[banner](../../includes/banner.md)]

This article provides an overview of the administration and integration components for Electronic invoicing. It includes information about their roles in the setup and operation of Electronic invoicing.

## Microsoft Azure

Set up a storage account and create secrets for an Azure Key Vault in your Azure subscription. You fully own and manage these resources.

A storage account is a mandatory component of the Electronic Invoicing service. Use it to store all electronic files that Electronic invoicing processes or generates. Here are some examples of these files:

- Business data from Dynamics 365 Finance and Dynamics 365 Supply Chain Management in a unified structure (JavaScript Object Notation \[JSON\] format)
- Files that are generated during file generation and transformation
- Incoming external data, such as responses from external web services
- Inbound electronic invoices

A key vault is another mandatory component for working with Electronic invoicing. Use it to store the following items:

- The shared access signature (SAS) token of your storage account. Microsoft supports a high level of security and data privacy. Therefore, store your SAS token as a secret in Azure Key Vault instead of using it directly.
- Secrets, accounts, and passwords that you use in different scenarios.
- Certificates that have secrets for digital signing and for establishing a trusted connection with external web services.

## Microsoft Dynamics Lifecycle Services

Use Microsoft Dynamics Lifecycle Services to enable the Electronic invoicing add-in for your Lifecycle Services deployment project.

> [!NOTE]
> Installation of add-ins in Lifecycle Services requires at least a Tier 2 environment. For more information about environment planning, see [Environment planning](../../../fin-ops-core/dev-itpro/organization-administration/environment-planning.md).

## Finance and Supply Chain Management

Currently, Microsoft supports out-of-the-box integration with Finance and Supply Chain Management as the main billing system that works with the Electronic Invoicing service to generate and submit electronic invoices (*outbound electronic documents*), and to receive electronic invoices from vendors (*inbound electronic documents*).

Finance and Supply Chain Management generate business data in a unified structure and then submit it, together with additional metadata (*context*), to Electronic invoicing. They then request the status of the documents that Electronic invoicing is processing.

The detailed results come as a log that's linked to the generated electronic files or other data that's related to the submitted documents. Depending on the scenario, the system updates Finance and Supply Chain Management data. For example, it updates the invoice status or externally provided universally unique identifiers (UUIDs) of invoices that are registered with the tax authority.

For more information about Electronic invoicing components and how to set them up, see [Set up Electronic invoicing](gs-e-invoicing-set-up-overview.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]