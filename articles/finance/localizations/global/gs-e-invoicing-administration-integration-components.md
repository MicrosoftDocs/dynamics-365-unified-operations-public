---
title: Electronic invoicing components
description: Access an overview of the administration and integration components for Electronic invoicing, including an overview on Microsoft Azure.
author: ilikond
ms.author: ikondratenko
ms.topic: article
ms.date: 01/29/2024
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2024-01-29
ms.dyn365.ops.version: 10.0.39
---

# Electronic invoicing components

[!INCLUDE[banner](../../includes/banner.md)]

This article provides information about the components that are related to the administration of Electronic invoicing. It includes information about their roles in the setup and operation of Electronic invoicing.

## Microsoft Azure

You use Microsoft Azure to set up a storage account and create secrets for an Azure key vault. These resources must be set up in your Azure subscription. They're fully owned and managed by you.

A storage account is a mandatory component of the Electronic Invoicing service. It's used to store all electronic files that Electronic invoicing processes or generates. Here are some examples of these files:

- Business data from Dynamics 365 Finance and Dynamics 365 Supply Chain Management in a unified structure (JavaScript Object Notation \[JSON\] format)
- Files that are generated during file generation and transformation
- Incoming external data, such as responses from external web services
- Inbound electronic invoices

A key vault is another mandatory component for working with Electronic invoicing. It's used to store the following items:

- The shared access signature (SAS) token of your storage account. Microsoft supports a high level of security and data privacy. Therefore, you must store your SAS token as a secret in Azure Key Vault instead of using it directly.
- Secrets, accounts, and passwords that you'll use in different scenarios.
- Certificates that have secrets for digital signing and for establishing a trusted connection with external web services.

## Microsoft Dynamics Lifecycle Services

You use Microsoft Dynamics Lifecycle Services to enable the Electronic invoicing add-in for your Lifecycle Services deployment project.

> [!NOTE]
> Installation of add-ins in Lifecycle Services requires at least a Tier 2 environment. For more information about environment planning, see [Environment planning](../../../fin-ops-core/dev-itpro/organization-administration/environment-planning.md).

## Finance and Supply Chain Management

Currently, Microsoft supports out-of-box integration with Finance and Supply Chain Management as the main billing system that works with the Electronic Invoicing service to generate and submit electronic invoices (*outbound electronic documents*), and to receive electronic invoices from vendors (*inbound electronic documents*).

Finance and Supply Chain Management generate business data in a unified structure and then submit it, together with additional metadata (*context*), to Electronic invoicing. They then request the status of the documents that Electronic invoicing is processing.

The detailed results are received as a log that's linked to the generated electronic files or other data that's related to the submitted documents. Depending on the scenario, the system updates Finance and Supply Chain Management data. For example, it updates the invoice status or externally provided universally unique identifiers (UUIDs) of invoices that are registered with the tax authority.

For more information about Electronic invoicing components and how to set them up, see [Set up Electronic invoicing](gs-e-invoicing-set-up-overview.md).
