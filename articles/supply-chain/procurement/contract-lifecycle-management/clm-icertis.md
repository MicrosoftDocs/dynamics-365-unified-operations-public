---
title: Integrate with Icertis for Microsoft Dynamics 365 Supply Chain Management (preview)
description: Learn how to integrate with the Icertis contract lifecycle management (CLM) system.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---

# Integrate with Icertis for Microsoft Dynamics 365 Supply Chain Management (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.43 GA -->

Icertis for Microsoft Dynamics 365 Supply Chain Management is a full-featured third-party contract lifecycle management (CLM) solution that uses the [CLM integration capabilities](clm-overview.md) of Microsoft Dynamics 365 Supply Chain Management. This article provides an overview of Icertis for Microsoft Dynamics 365 Supply Chain Management. It summarizes the following aspects of the integrated solution:

- Capabilities
- Key features
- Benefits
- Setup

You can learn more about the solution at [Icertis Integrations for Microsoft](https://www.icertis.com/products/integrations/microsoft/) and on the [Icertis for Microsoft Dynamics 365 Supply Chain Management page on Microsoft AppSource](https://appsource.microsoft.com/product/dynamics-365-for-operations/icertiscontractmanagement.icertis-dynamics-supply-chain-operations).

## Capabilities

Supply Chain Management provides functionality that organizations can use to streamline and automate their source-to-pay processes. Icertis for Microsoft Dynamics 365 Supply Chain Management enhances this functionality by integrating capabilities for contract authoring, assembly, redlining, and analytics. This integration supports the following workflows:

- **Contract authoring** – Create procurement contracts and non-disclosure agreements (NDAs) by using configured attributes, templates, clauses, master data, and rules. You can use seeded configurations to get started right away, but configurations are always tailored to the needs of your business.
- **Reviews and negotiations** – Use preapproved legal templates and playbooks to review, redline, and approve contracts. After contract are approved, you can seamlessly send them for digital signature.
- **Post-execution workflows** – After a contract is executed, an associated purchase agreement is created in Supply Chain Management. The purchase agreement is created in an activated state, so that it can be used for operational purposes such as creating a release order and invoicing.
- **Update contracts** – You can amend an executed contract by using the same safeguards that are applied when new contracts are drafted. Additionally, contracts can be seamlessly terminated. In this case, the required due processes are followed.
- **Risk Assessment Copilot** – Risk Assessment Copilot significantly accelerates the contract review process. At the same time, it helps reduce risk by using AI to compare contract terms to a company's predefined risk parameters, based on the contract type.
- **Pre-seeded information** – Icertis for Microsoft Dynamics 365 Supply Chain Management includes extensive pre-seeded attributes and entities. Therefore, you can benefit from the integration without having to spend lots of time on implementation.

To learn more about Icertis for Microsoft Dynamics 365 Supply Chain Management, follow these steps.

1. Sign in to your Icertis Contract Intelligence (ICI) instance.
1. Select the **Help** button.
1. Go to [Welcome to Icertis for Microsoft Dynamics 365 Supply Chain Management](https://help.icertis.com/welcome-to-icertis-for-microsoft-dynamics-365-supply-chain-management/).

## Key features

This section describes the key features of Icertis for Microsoft Dynamics 365 Supply Chain Management.

### Manage and operationalize procurement contracts

Icertis for Microsoft Dynamics 365 Supply Chain Management offers a seamless source-to-contract workflow that includes an embedded experience in Supply Chain Management. This integration lets Supply Chain Management users take advantage of the robust CLM capabilities of Icertis to create and manage procurement contracts.

After you conclude a sourcing event and shortlist a vendor, you can initiate the creation of a procurement contract from Supply Chain Management. The embedded Icertis experience lets you perform the following actions:

- Define the terms, conditions, and specifics of the procurement contract with Icertis.
- Add line items for the procurement contract.
- Confirm that the pricing, quantities, and other terms are aligned with your business needs.
- Obtain all the required approvals.
- Validate the contract details to ensure that they comply with Supply Chain Management rules.
- Review and negotiate the contract with all relevant parties.
- Execute the contract.

After the Icertis procurement contract is executed, an effective purchase agreement is created in Supply Chain Management. The statuses of the Icertis procurement contract and the corresponding Supply Chain Management purchase agreements are regularly synced.

The following illustration shows the contract workflow between the two applications.

:::image type="content" source="media/icertis-contractual-workflow.png" alt-text="Diagram that shows the contract workflow between Icertis and Supply Chain Management." lightbox="media/icertis-contractual-workflow.png":::

### Create and manage NDAs

Icertis for Microsoft Dynamics 365 Supply Chain Management offers an embedded experience in Supply Chain Management. This integration lets you take advantage of the robust CLM capabilities of Icertis to create and manage NDAs.

After you decide to transact business with a vendor, you can seamlessly initiate the creation of an NDA from Supply Chain Management. The embedded Icertis experience lets you perform the following actions:

- Specify effective dates, expiry dates, signature types, signatory details, and other details. The statuses of Icertis procurement contracts and their corresponding Supply Chain Management purchase agreements are regularly synced.
- Use a system-provided template, review details, and create and publish the contract.
- Add supporting documents, team members, and so on.
- Review and negotiate the contract with the vendor.
- After the agreement is approved, send it for signature.

NDAs can be amended, terminated, or updated as required. The process is similar.

The following illustration shows the NDA workflow between the two applications.

:::image type="content" source="media/icertis-nda-workflow.png" alt-text="Diagram that shows the NDA workflow between Icertis and Supply Chain Management." lightbox="media/icertis-nda-workflow.png":::

### Amend and update agreements

Icertis for Microsoft Dynamics 365 Supply Chain Management offers options that let you update or modify executed contracts. You can add line items, modify expiry dates, or terminate contracts. Updates to contracts can cause one of the following events:

- **Synchronize amendments** – The statuses of an Icertis procurement contract and the corresponding Supply Chain Management purchase agreements are regularly synced. Users can create amendments directly in Supply Chain Management. Contract managers can add an amendment to a signed or executed contract in Icertis. Downstream consumption then uses the revised information in Supply Chain Management.
- **Termination of contract** – If an Icertis procurement contract is terminated in Icertis Contract Intelligence (ICI), the associated purchase agreement in Supply Chain Management system is automatically terminated.
- **Reset expiry** – You can renew agreements or reset expiry dates as you require, based on your business needs.

### Integrate master data

All the previously mentioned workflows are enabled through the integration of master data that stores less frequently changing data and business information. The master data entity is based on attributes and rules. It can be reused for the various organizations that you work with.

### Comprehensive pre-seeded information for seamless integration

Icertis for Microsoft Dynamics 365 Supply Chain Management includes extensive pre-seeded attributes and entities. This pre-seeded information enables the application and integration to work seamlessly. It also lets users benefit from the integration after only minimal implementation time.

If configuration of the pre-seeded attributes and entities is required, an administrator or an implementation team can do it.

The pre-seeded information includes the following elements:

- Data models for procurement contracts, NDAs, line items, and associated documents
- Attributes that are part of contract types and master data
- Master data and rules
- Standard reports and saved searches
- Clauses and templates
- eSign configurations
- Role–action mappings
- Entities for notifications, reasons, organizations, cascade teams, and implementation tasks

### Risk Assessment Copilot

You can enhance the integration by adding Risk Assessment Copilot, which is powered by the Icertis ExploreAI Service. Risk Assessment Copilot significantly accelerates the contract review process. At the same, it helps reduce risk by using AI to compare contract terms to a company's predefined risk parameters, based on the contract type.

## Benefits

Icertis for Microsoft Dynamics 365 Supply Chain Management provides the following benefits:

- **Accelerate contract turnaround times** – The seamless integration enables organizations to quickly author and negotiate contracts, and operationalize them in Supply Chain Management.
- **Plug cost leakage** – Maximize the value of every contract by using the negotiated commercial terms and enforcing them during procurement and payable processes.
- **Effectively manage legal and business risks** – Manage legal and business risks by using preapproved legal templates and predefined corporate policies, and by constantly monitoring contractual obligations and service-level agreements (SLAs).
- **Effectively collaborate on contracts with all parties** – Reduce rework, improve supplier satisfaction, and help reduce risk exposure for your company through accurate redlining, versioning, and approval workflows. Enable secure communication with suppliers, customers, and partners.
- **Gain deeper insights into purchases and contracts** – Manage agreements across multiple departments to gain deeper insights. Align supplier and customer terms through AI-supported search, digitization, and negotiation.

## Set up Icertis for Microsoft Dynamics 365 Supply Chain Management

To set up Icertis for Microsoft Dynamics 365 Supply Chain Management, follow these steps.

1. Purchase a subscription for Icertis for Microsoft Dynamics 365 Supply Chain Management.

    After the subscription is confirmed, the designated administrator receives an email from Icertis. This email includes instructions for downloading and deploying the package.

1. Deploy the package by using Microsoft Dynamics Lifecycle Service.
1. Optional: Configure single sign-on (SSO).
1. Configure ICI with attributes, templates, clauses, master data, rules, and other useful metadata to seamlessly integrate the two products.

To get detailed instructions for deploying the package and setting up an instance, follow these steps.

1. Sign in to your Icertis Contract Intelligence (ICI) instance.
1. Select the **Help** button.
1. Go to [Icertis for Microsoft Dynamics 365 SCM Package Installation & Setup](https://help.icertis.com/docs/integrate/ms-d365-experience/packages-installation/).
