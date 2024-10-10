---
title: Integrate with Icertis CLM (preview)
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

# Integrate with Icertis CLM (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.43 GA  -->

<!-- KFM: We need to resolve the Icertis trademark, which appears to be "Icertis for Microsoft Dynamics 365 SCM", but we don't like to use "SCM". -->

This article describes *Icertis for Microsoft Dynamics 365 Supply Chain Management*, which is a full-featured, third-party contract lifecycle management system (CLM) that leverages the [CLM integration capabilities](clm-overview.md) of Supply Chain Management. The article describes the solution's:

- Capabilities
- Key features
- Benefits
- Set up

This article provides an overview. For complete instructions on how to set up and use the system, go to <!-- KFM: Link to AppSource or Icertis docs, or maybe https://appsource.microsoft.com/en-US/marketplace/apps?search=icertis-->

## Capabilities

Supply Chain Management enables organizations to streamline and automate their source-to-pay processes. Icertis for Supply Chain Management enhances these functionalities by integrating capabilities for contract authoring, assembly, redlining, and analytics.

This integration supports the following workflows:

- **Contract authoring** – Create Procurement contracts and NDAs by using configured attributes, templates, clauses, master data, and rules. You can get started with seeded configurations right away, but configurations always be tailored as per the needs of your business.
- **Reviews & negotiations** – Leverage pre-approved legal templates and playbooks to review, redline, and approve contracts. Post approval you can also send the contracts for digital signatures seamlessly.
- **Post execution workflows** – Once the contract is executed, the associated purchase agreement is created in Supply Chain Management in an activated state so that it can be used for operational purposes such as release order creation and invoicing.
- **Update Contracts** – You can amend an executed contract using the same safeguards applied when drafting new contracts. Additionally, contracts can be terminated seamlessly, following the necessary due processes.
- **Risk Assessment Copilot** – Risk Assessment Copilot significantly accelerates the contract review process while reducing risk by using AI to compare contract terms to a company's predefined risk parameters based on the contract type.
- **Pre-seeded information** – This capability in the Icertis for Supply Chain Management comes with extensive pre-seeded attributes and entities that let users derive the benefits of the integration with little implementation time.

For more information on Icertis for Supply Chain Management, see <!-- KFM (ICI AppSource link.) -->

## Key Features

The above capabilities are available via following key features that Icertis for Supply Chain Management currently offers:

### Manage and operationalize procurement contracts

Icertis for Supply Chain Management offers a seamless source to contract workflow with an embedded experience within Supply Chain Management sourcing and procurement. This integration enables you to leverage the robust contract lifecycle management capabilities of Icertis to create and manage procurement contracts.

Once you conclude a sourcing event and shortlist a vendor, you can initiate the creation of the procurement contract from Supply Chain Management. After initiation, the embedded Icertis experience, enables you do the following:

- Define the terms, conditions, and specifics of the procurement contract with Icertis.
- Add line items for the procurement contract.
- Confirm that the pricing, quantities, and other terms align with the business needs.
- Obtain all necessary approvals.
- Validate the contract details to comply with Supply Chain Management rules.
- Review and negotiate the contract with all relevant parties.
- Execute the contract.

Once the Icertis Procurement Contract is executed, an effective purchase agreement is created in Supply Chain Management procurement and sourcing. The statuses of Icertis procurement contract and the corresponding Dynamics 365 Purchase Agreements are synchronized regularly.

Here's a depiction of the contractual workflow between the two applications.

![A screenshot of a computer Description automatically generated](media/image3.png)

### Create and manage NDAs

Icertis for Supply Chain Management offers an embedded experience within Dynamics 365 sourcing and procurement enabling you to leverage the robust contract lifecycle management capabilities of Icertis for creating and managing NDAs.

Once you decide to transact with a vendor, you can seamlessly initiate the creation of an NDA from Supply Chain Management. After initiation, the embedded Icertis experience, enables you do the following:

- Specify details of Effective, Expiry dates, Signature type, Signatory details and other details. The statuses of Icertis procurement contract and the corresponding Dynamics 365 Purchase Agreements are synchronized regularly.
- Proceed with system provided template, review details and create and publish contract.
- Add supporting documents, team members, and so on.
- Review and negotiate the contract with the vendor.
- Once approved, you can send it for signature.

The NDAs can be amended, terminated, or updated as necessary in a similar manner.

![A screenshot of a computer Description automatically generated](media/image4.png)

### Amend and update agreements

Icertis for Supply Chain Management offers options to update or modify executed contracts to add line items, modify expiry dates, or terminate contracts. Updating contracts might involve one of the following:

- **Synchronized amendments** – The statuses of Icertis procurement contract and the corresponding Supply Chain Management Purchase Agreements are synchronized regularly. Users can initiate amendment creation directly in Supply Chain Management. Contract Managers add an amendment to a signed or executed contract in Icertis so that the downstream consumption can leverage the revised information in Supply Chain Management.
- **Contract termination** – When an Icertis procurement contract is terminated within Icertis Contract Intelligence (ICI), the associated Dynamics 365 Purchase Agreement within the Dynamics 365 SCM system is automatically terminated.
- **Reset expiry** – Renewing agreements or resetting expiry dates can be done seamlessly with the ability to reset the expiry date of the agreements and amendments based on the business need.

### Master data Integration

All the above-mentioned workflows are possible through master data integration that stores the less frequently changing data and business information. Master data entity is based on Attributes and Rules and can be reused for different organizations that you work with.

### Comprehensive pre-seeded information for seamless integration

For the application and integration to work seamlessly, Icertis for Supply Chain Management comes with extensive pre-seeded attributes and entities that let users derive the benefits of the integration with little implementation time.

If bespoke configurations are required, an administrator or an implementation team can tailor the configurations.

![A diagram of a company Description automatically generated](media/image5.png)

This pre-seeded information includes:

- Data models for procurement contracts, NDAs, line items and associated documents
- Attributes that are part of contract types and master data
- Master data and rules
- Standard reports and saved searches
- Clauses and templates
- eSign configurations
- Role-action mappings
- Entities for notifications, reasons, organizations, cascade teams, and implementation tasks

### Risk Assessment Copilot

The Risk Assessment copilot, powered by the Icertis ExploreAI Service, can be added to the integration. It significantly accelerates the contract review process while reducing risk by using AI to compare contract terms to a company's predefined risk parameters based on the contract type.

## Benefits

- **Accelerate contract turnaround times** – The seamless integration enables organizations to quickly author and negotiate contracts, and operationalize them in Supply Chain Management.
- **Plug cost leakage** – Maximize the value of every contract by leveraging the negotiated commercial terms and enforcing them during procurement and payable processes.  
- **Effectively manage legal and business risks** – Manage legal and business risks using pre-approved legal templates, predefined corporate policies, and monitoring contractual obligations and SLAs (Service Level Agreements) constantly.
- **Effectively collaborate on contracts with all parties** – Reduce rework and improve supplier satisfaction with accurate redlining, versioning, and approval workflows, reducing risk exposure for your company. Enable secure communication with suppliers, customers, and partners.  
- **Gain deeper insights into purchases and contracts** – Manage agreements across multiple departments to gain deeper insights and align supplier and customer terms with AI-supported search, digitization, and negotiation. 

## Setting up Icertis for Supply Chain Management

**Prerequisite:** To proceed with the integration steps, ensure you are provisioned with the necessary admin roles and privileges to perform the configuration and initial setup of Icertis for Supply Chain Management.

Here's a depiction of set up between the two applications.

![A purple rectangular box with white text Description automatically generated](media/image6.png)

Setting up Icertis for Microsoft Dynamics involves the following:

1. Purchase a subscription for Icertis for Supply Chain Management.
1. Once the subscription is confirmed, the designated administrator received an email from Icertis with instructions for downloading and deploying the package.
1. Deploy the package using the Lifecycle Service.
1. Configure SSO(optional)
1. Configure the Icertis Contract Intelligence with attributes, templates, clauses, master data, rules and other useful metadata to integrate the two products seamlessly.  

For detailed instructions on deploying the package and setting up the instance, go to <!-- KFM: Add link to Icertis Help Center. -->.

<!-- KFM: We are describing two different ways for how to get to the help center (above and below). Can we pick one?  -->

> [!NOTE]
> To access the Icertis Help Center, follow these steps:
>
> 1. Sign in to your Icertis Contract Intelligence (ICI) instance.
> 1. Select the **Help** icon.
