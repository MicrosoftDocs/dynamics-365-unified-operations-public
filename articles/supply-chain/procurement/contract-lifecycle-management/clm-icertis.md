---
title: Integrate with Icertis for Microsoft Dynamics 365 Supply Chain Management (preview)
description: Integrate with Icertis CLM.
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
<!-- KFM: Preview until 10.0.43 GA  -->

This article describes *Icertis for Microsoft Dynamics 365 Supply Chain Management*, which is a full-featured, third-party contract lifecycle management (CLM) solution that uses the [CLM integration capabilities](clm-overview.md) of Microsoft Dynamics 365 Supply Chain Management. This article summarizes the following aspects of the integrated solution:

- Capabilities
- Key features
- Benefits
- Set up

This article provides an overview of the integrated solution. For complete instructions on how to set up and use Icertis for Microsoft Dynamics 365 Supply Chain Management, go to [Link](.). <!-- KFM: Link to AppSource or Icertis docs, or maybe https://appsource.microsoft.com/en-US/marketplace/apps?search=icertis-->

## Capabilities

Supply Chain Management enables organizations to streamline and automate their source-to-pay processes. Icertis for Microsoft Dynamics 365 Supply Chain Management enhances these functionalities by integrating capabilities for contract authoring, assembly, redlining, and analytics.

This integration supports the following workflows:

- **Contract authoring** – Create procurement contracts and non-disclosure agreements (NDAs) by using configured attributes, templates, clauses, master data, and rules. You can get started with seeded configurations right away, but configurations are always tailored according to the needs of your business.
- **Reviews & negotiations** – Use pre-approved legal templates and playbooks to review, redline, and approve contracts. Post approval, you can send the contracts for digital signatures seamlessly.
- **Post execution workflows** – Once a contract is executed, an associated purchase agreement is created in Supply Chain Management. The purchase agreement is created in an activated state so that it can be used for operational purposes such as creating a release order and invoicing.
- **Update contracts** – You can amend an executed contract using the same safeguards applied when drafting new contracts. Additionally, contracts can be terminated seamlessly, following the necessary due processes.
- **Risk Assessment Copilot** – Risk Assessment Copilot significantly accelerates the contract review process while reducing risk by using artificial intelligence to compare contract terms to a company's predefined risk parameters based on the contract type.
- **Pre-seeded information** – Icertis for Microsoft Dynamics 365 Supply Chain Management comes with extensive pre-seeded attributes and entities that let you derive the benefits of the integration with little implementation time.

To learn more about Icertis for Microsoft Dynamics 365 Supply Chain Management, go to [Link](.). <!-- KFM (ICI AppSource link.) -->

## Key Features

The following subsections describe the key features of Icertis for Microsoft Dynamics 365 Supply Chain Management.

### Manage and operationalize procurement contracts

Icertis for Microsoft Dynamics 365 Supply Chain Management offers a seamless source to contract workflow with an embedded experience within Supply Chain Management. This integration lets Supply Chain Management users take advantage of the robust contract lifecycle management capabilities of Icertis to create and manage procurement contracts.

Once you conclude a sourcing event and shortlist a vendor, you can initiate the creation of the procurement contract from Supply Chain Management. The embedded Icertis experience enables you to do the following actions:

- Define the terms, conditions, and specifics of the procurement contract with Icertis.
- Add line items for the procurement contract.
- Confirm that the pricing, quantities, and other terms align with your business needs.
- Obtain all necessary approvals.
- Validate the contract details to comply with Supply Chain Management rules.
- Review and negotiate the contract with all relevant parties.
- Execute the contract.

Once the Icertis procurement contract is executed, an effective purchase agreement is created in Supply Chain Management. The statuses of the Icertis procurement contract and the corresponding Supply Chain Management purchase agreements are synchronized regularly.

The following illustration shows the contractual workflow between the two applications.

:::image type="content" source="media/icertis-contractual-workflow.png" alt-text="Contractual workflow between the two applications" lightbox="media/icertis-contractual-workflow.png":::

### Create and manage non-disclosure agreements

Icertis for Microsoft Dynamics 365 Supply Chain Management offers an embedded experience within Supply Chain Management, which enables you to take advantage of the robust CLM capabilities of Icertis for creating and managing NDAs.

Once you decide to transact with a vendor, you can seamlessly initiate the creation of an NDA from Supply Chain Management. After initiation, the embedded Icertis experience enables you to do the following actions:

- Specify details of effective dates, expiry dates, signature types, signatory details, and other details. The statuses of Icertis procurement contracts and their corresponding Supply Chain Management purchase agreements are synchronized regularly.
- Proceed with a system-provided template, review details, and create and publish contract.
- Add supporting documents, team members, and so on.
- Review and negotiate the contract with the vendor.
- Send the agreement to be signed after it's approved.

NDAs can be amended, terminated, or updated as necessary and in a similar manner.

The following illustration shows the NDA workflow between the two applications.

:::image type="content" source="media/icertis-nda-workflow.png" alt-text="NDA workflow between the two applications" lightbox="media/icertis-nda-workflow.png":::

### Amend and update agreements

Icertis for Microsoft Dynamics 365 Supply Chain Management offers options to update or modify executed contracts to add line items, modify expiry dates, or terminate contracts. Updating contracts can result in one of the following events:

- **Synchronize amendments** – The statuses of an Icertis procurement contract and the corresponding Supply Chain Management purchase agreements are synchronized regularly. Users can create amendments directly in Supply Chain Management. Contract managers can add an amendment to a signed or executed contract in Icertis, with downstream consumption using the revised information in Supply Chain Management.
- **Termination of contract** – When an Icertis procurement contract is terminated within *Icertis Contract Intelligence* (ICI), the associated purchase agreement in Supply Chain Management system is also terminated automatically.
- **Reset expiry** – You can renew agreements or reset expiry dates as needed, based on your business needs.

### Integrate master data

All of the mentioned workflows are made possible by integrating master data that stores the less frequently changing data and business information. The master data entity is based on attributes and rules, and can be reused for the various organizations that you work with.

### Comprehensive pre-seeded information for seamless integration

For the application and integration to work seamlessly, Icertis for Microsoft Dynamics 365 Supply Chain Management comes with extensive pre-seeded attributes and entities that let users derive the benefits of the integration with minimal implementation time.

If configuration is required, an administrator or an implementation team can tailor it as needed.

Pre-seeded information includes the following elements:

- Data models for procurement contracts, NDAs, line items, and associated documents
- Attributes that are part of contract types and master data
- Master data and rules
- Standard reports and saved searches
- Clauses and templates
- eSign configurations
- Role-action mappings
- Entities for notifications, reasons, organizations, cascade teams, and implementation tasks

### Risk Assessment Copilot

You can enhance the integration by adding the Risk Assessment Copilot (powered by the *Icertis ExploreAI Service*). It significantly accelerates the contract review process while reducing risk by using AI to compare contract terms to a company's predefined risk parameters based on the contract type.

## Benefits

Icertis for Microsoft Dynamics 365 Supply Chain Management provides the following benefits:

- **Accelerate contract turnaround times** – The seamless integration enables organizations to quickly author and negotiate contracts and operationalize them in Supply Chain Management.
- **Plug cost leakage** – Maximize the value of every contract by using the negotiated commercial terms and enforcing them during procurement and payable processes.  
- **Effectively manage legal and business risks** – Manage legal and business risks using pre-approved legal templates, using predefined corporate policies, and constantly monitoring contractual obligations and service level agreements (SLAs).
- **Effectively collaborate on contracts with all parties** – Reduce rework and improve supplier satisfaction with accurate redlining, versioning, and approval workflows, thereby reducing risk exposure for your company. Enable secure communication with suppliers, customers, and partners.  
- **Gain deeper insights into purchases and contracts** – Manage agreements across multiple departments to gain deeper insights and align supplier and customer terms with AI-supported search, digitization, and negotiation.

## Setting up Icertis for Microsoft Dynamics 365 Supply Chain Management

Setting up Icertis for Microsoft Dynamics 365 Supply Chain Management requires the following steps:

1. Purchase a subscription for Icertis for Microsoft Dynamics 365 Supply Chain Management.
1. Once the subscription is confirmed, the designated administrator received an email from Icertis with instructions for downloading and deploying the package.
1. Deploy the package using the Lifecycle Service.
1. Configure single sign-on (optional).
1. Configure the Icertis Contract Intelligence with attributes, templates, clauses, master data, rules, and other useful metadata to integrate the two products seamlessly.  

For detailed instructions on how to deploy the package and set up an instance, follow these steps:

1. Go to [Link](.)<!-- KFM: Add link to Icertis Help Center. -->.
1. Sign in to your Icertis Contract Intelligence (ICI) instance.
1. Select the **Help** icon.
1. Follow the instructions provided.
