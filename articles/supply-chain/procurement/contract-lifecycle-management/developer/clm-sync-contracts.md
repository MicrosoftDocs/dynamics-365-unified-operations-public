---
title: Synchronize contracts (preview)
description: This article describes scenarios, data entities, and integration methods available for synchronizing contracts and related purchase agreements from an external contract lifecycle management system to Dynamics 365 Supply Chain Management.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---

# Synchronize contracts (preview)

[!include [banner](../../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.43 GA  -->

This article describes scenarios, data entities, and integration methods available for synchronizing contracts and related purchase agreements from an external contract lifecycle management (CLM) system to Dynamics 365 Supply Chain Management. The integration process establishes a workflow that transfers contracts and related purchase agreements from the CLM system to Supply Chain Management. The CLM system is assumed to function as the master system for managing contracts.

## Access the data integration APIs

For information about which data integration APIs are available, how to enable change tracking, and how to authenticate with Supply Chain Management so your CLM system can access that data entities described in this article, see [Data integration APIs](clm-data-integration-apis.md).

## Scenarios

This section outlines the following integration scenarios supported by Supply Chain Management:

- Create a non-disclosure agreement (NDA)
- Create a purchase contract
- Create a contract amendment

The images provided later in this article illustrate process diagrams.

### Create an NDA

NDAs are independent contracts that aren't related to any document within Supply Chain Management. The integration points involve creating the contract and updating its status once the approval and signing process is complete.

The following illustration shows a flowchart of how NDAs are created and synchronized between systems.

:::image type="content" source="../media/create-nda.png" alt-text="Flowchart of how NDAs are created and synchronized between systems." lightbox="../media/create-nda.png":::

### Create a purchase contract

A purchase contract is a contract that's associated with a purchase agreement in Supply Chain Management. The integration points include creating the contract, validating the purchase agreement before submitting it for approval and signing, updating the contract status upon completion of the approval and signing process, and ultimately creating the purchase agreement.

The following illustration shows a flowchart of how purchase contracts are created and synchronized between systems.

:::image type="content" source="../media/create-purchase-contract.png" alt-text="Flowchart of how purchase contracts are created and synchronized between systems." lightbox="../media/create-purchase-contract.png":::

### Amend a contract

Purchase contract amendments and NDA amendments are documents that change the terms of an existing agreement. The integration points include updating the contract with amendment information, validating the purchase agreement before submitting it for approval and signing, updating the contract status upon completion of the approval and signing process, and ultimately updating the purchase agreement. In Supply Chain Management, the amended information is updated within the same contract and purchase agreement record.

The following illustration shows a flowchart of how contract amendments are created and synchronized between systems.

:::image type="content" source="../media/amend-purchase-contract.png" alt-text="Flowchart of how contract amendments are created and synchronized between systems." lightbox="../media/amend-purchase-contract.png":::

## Available data entities for synchronizing contracts and purchase agreements

Supply Chain Management offers several out-of-the-box data entities that external CLM systems can use to synchronize contract data. The following table describes the available data entities necessary for synchronizing contracts and purchase agreements.

| **Entity** |**Target entity** | **Public name (OData)** | **Company specific** | **Direction** |
| --- | --- | --- | --- | --- |
| CLM integration contract | `CLMIntegrationContractEntity` | `CLMIntegrationContracts` | Yes | CLM -\> Supply Chain Management |
| CLM integration purchase agreements | `CLMIntegrationPurchaseAgreementHeaderEntity` | `CLMIntegrationPurchaseAgreements` | Yes | CLM -\> Supply Chain Management |
| CLM integration purchase agreement lines | `CLMIntegrationPurchaseAgreementLineEntity` | `CLMIntegrationPurchaseAgreementLines` | Yes | CLM -\> Supply Chain Management |

> [!NOTE]
> Company-specific data entities include the `dataAreaId` field, which indicates the legal entity to which each record belongs. Your CLM system must adopt the same behavior to support both company-specific and cross-company records. Learn more about cross-company behavior in [Cross-company behavior of data entities](../../../../fin-ops-core/dev-itpro/data-entities/cross-company-behavior.md)

The following diagram shows how contracts and purchase agreements are integrated and synchronized.

:::image type="content" source="../media/contract.png" alt-text="Contracts and purchase agreements integration diagram." lightbox="../media/contract.png":::

### Contract entity

This entity provides information about the contract. Its properties are listed in the following table.

| Physical name | Property | Type | Description |
|---|---|---|---|
| `ContractId` (Entity key) | Contract ID | String | Contract identifier in the CLM. |
| `LegalEntityId` (Entity key) | Legal entity ID | String | Legal entity ID |
| `ExternalContractId` | External contract ID | String | Internal system-generated contract identifier in the CLM. |
| `ContractType` | Contract type | String | Contract type name reference. |
| `ContractStatus` | Contract status | Enum | Values: `Draft`, `WaitingForApproval`, `Approved`, `Rejected`, `WaitingForSignatures`, `WaitingForExternalSignatures`, `WaitingForInternalSignatures`, `Executed`, `Terminated`, `Expired`, `OnHold`, `Cancelled`, `WaitingForReview`, `Reviewed`. |
| `ContractName` | Contract title | String | Contract title |
| `EffectiveDate` | Effective date | Date | Effective date |
| `ExpirationDate` | Expiration date | Date | Expiration date |
| `RequesterWorkerName` | Requester name | String | Requester worker name.<br/>If the specified worker name isn't found in the system, the `RequesterWorkerEmail` field is used to identify the worker. |
| `RequesterWorkerEmail` | Requester email | String | Requester worker email. |
| `AccountType` | Account type | Enum | Determines the type of contracting party.<br/>Values: `Vend`, `Cust`, `Party`. |
| `AccountRelationId` | Account number | String | Contracting account identifier that corresponds to the chosen `AccountType`. |
| `PartyNumber` | Party ID | String | Party number in the global address book. |
| `ContactPersonId` | Contact person ID | String | Contact person ID |
| `LatestAmendmentId` | Latest amendment ID | String | Latest amendment identifier in the CLM. |
| `LatestExternalAmendmentId` | Latest amendment external ID | String able | Internal system-generated latest amendment identifier in the CLM. |
| `AmendmentInProcess` | Amendment in process | Enum | Values: `Yes`, `No`. |

Here's an example request query for the CLM integration contract entity:

```http
GET https://[baseURI]/data/CLMIntegrationContracts
```

Here's an example response to that query:

```json
{
    "ContractId": "C00001",
    "LegalEntityId": "USMF",
    "ExternalContractId": "EXTC00001",
    "ContractType": "NDA",
    "ContractStatus": "Draft",
    "ContractName": "Non-disclosure agreement",
    "EffectiveDate": "2024-12-31T12:00:00Z",
    "ExpirationDate": "2024-01-01T12:00:00Z",
    "RequesterWorkerEmail": "julia.funderburk@constoso.com",
    "RequesterWorkerName": "Julia Funderburk",
    "AccountType": "Vend",
    "AccountRelationId": "1001",
    "PartyNumber": "000001745",
    "ContactPersonId": "",
    "LatestAmendmentId": "A00001",
    "LatestExternalAmendmentId": "EXTA00001",
    "AmendmentInProcess": "No"
}
```

### Purchase agreement header entity

This entity provides information about the purchase agreement header. The most common properties can be found in the following table. You might also use other properties, depending on your business requirements.

| Physical name | Property | Type | Description |
|---|---|---|---|
| `PurchaseAgreementId` (Entity key) | Purchase agreement ID | String | Purchase agreement identifier from Supply Chain Management. |
| `BuyingLegalEntityId` (Entity key) | Legal entity ID | String | Legal entity ID |
| `ExternalContractId` | External contract ID | String | Internal system-generated purchase agreement identifier in the CLM. |
| `ContractId` | Contract ID | String | Contract identifier reference to associate the purchase agreement with the contract. |
| `ContractLegalEntity` | Contract legal entity ID | String | Contract legal entity identifier reference to associate the purchase agreement with the contract. |
| `AgreementOwnership` | Purchase agreement ownership type | Enum | Values: `SCM`, `CLM`. |
| `AgreementStatus` | Agreement status | Enum | Values: `OnHold`, `Effective`, `Closed`. |
| `DocumentTitle` | Document title | String | Document title |
| `PurchaseAgreementClassificationName` | Purchase agreement classification | String | Purchase agreement classification name reference. |
| `DefaultEffectiveDate` | Default effective date | Date | Default effective date |
| `DefaultExpirationDate` | Default expiration date | Date | Default expiration date |
| `AgreementVendorAccountNumber` | Vendor account | String | Agreement vendor account reference. |
| `InvoiceVendorAccountNumber` | Invoice account | String | Invoicing vendor account reference. |
| `VendorReference` | Vendor reference | String | Vendor reference |
| `PrimaryResponsibleWorkerEmail` | Primary responsible worker email | String | Primary responsible worker email.  |
| `PrimaryResponsibleWorkerName` | Primary responsible worker name | String | Primary responsible worker name.<br/><br/>If the specified worker name isn't found in the system, the `PrimaryResponsibleWorkerEmail` field is used to identify the worker. |
| `SecondaryResponsibleWorkerEmail` | Secondary responsible worker email | String | Secondary responsible worker email. |
| `SecondaryResponsibleWorkerName` | Secondary responsible worker name | String | Secondary responsible worker name.<br/><br/>If the specified worker name isn't found in the system, the `SecondaryResponsibleWorkerEmail` field is used to identify the worker. |
| `CashDiscountCode` | Cash discount | String | Cash discount |
| `ContactPersonId` | Contact person ID | String | Contact person ID |
| `CurrencyCode` | Currency | String | Currency |
| `DefaultCommitmentType` | Default commitment type | Enum | Values: `ProductQuantity`, `ProductVolume`, `ProductCategory`, `ProductRootCategory`. |
| `BuyerGroupId` | Buyer group ID | String | Buyer group ID |
| `ProjectId` | Project ID | String | Project ID |
| `PaymentTermsName` | Payment terms | String | Payment terms |

Here's an example request query for the CLM integration agreement header entity:

```http
GET https://[baseURI]/data/CLMIntegrationPurchaseAgreements
```

Here's an example response to that query:

```json
{
    "PurchaseAgreementId": "000026",
    "BuyingLegalEntityId": "USMF",
    "ExternalContractId": "EXT000026",
    "ContractId": "C00003",
    "ContractLegalEntityId": "USMF",
    "AgreementOwnership": "CLM",
    "AgreementStatus": "Effective",
    "DocumentTitle": "Purchase agreement title",
    "PurchaseAgreementClassificationName": "General purchases",
    "DefaultEffectiveDate": "2024-01-01T12:00:00Z",
    "DefaultExpirationDate": "2024-12-31T12:00:00Z",
    "AgreementVendorAccountNumber": "1001",
    "InvoiceVendorAccountNumber": "1001",
    "VendorReference": "VENREF00001",
    "PrimaryResponsibleWorkerEmail": "julia.funderburk@constoso.com",
    "PrimaryResponsibleWorkerName": "Julia Funderburk",
    "SecondaryResponsibleWorkerEmail": "charlie.carson@constoso.com",
    "SecondaryResponsibleWorkerName": "Charlie Carson",
    "CashDiscountCode": "0.5%D10",
    "ContactPersonId": "",
    "CurrencyCode": "USD",
    "DefaultCommitmentType": "ProductQuantity",
    "BuyerGroupId": "",
    "ProjectId": "",
    "PaymentTermsName": "Net30"
}
```

### Purchase agreement line entity

This entity provides information about the purchase agreement line. The most common properties can be found in the following table. You might also use other properties, depending on your business requirements.

| Physical name | Property | Type | Description |
|---|---|---|---|
| `PurchaseAgreementId` (Entity key) | Purchase agreement ID | String | Purchase agreement identifier reference. |
| `PurchaseAgreementLegalEntityId` (Entity key) | Purchase agreement legal entity ID | String | Purchase agreement legal entity identifier reference. |
| `LineNumber` (Entity key) | Line number | Real | Line number |
| `ExternalContractId` | External contract ID | String | Internal system-generated purchase agreement identifier reference in the CLM. Can be used instead of the `PurchaseAgreementId` field when creating a record. |
| `ExternalContractLineId` | External contract line ID | String | Internal system-generated purchase agreement line identifier in the CLM. |
| `CommitmentType` | Commitment type | Enum | Values: `ProductQuantity`, `ProductVolume`, `ProductCategory`, `ProductRootCategory`. |
| `CommittedAmount` | Committed amount | Real | Committed amount for volume-based commitment types (`ProductVolume`, `ProductCategory`, `ProductRootCategory`). |
| `CommittedQuantity` | Committed quantity | Real | Committed quantity for quantity-based commitment types (`ProductQuantity`). |
| `EffectiveDate` | Effective date | Date | Effective date |
| `ExpirationDate` | Expiration date | Date | Expiration date |
| `ItemNumber` | Item number | String | Required by the `ProductQuantity` and `ProductVolume` commitment type. |
| `ProductVariantNumber` | Product variant number | String | Relevant if specified product contains product variants. |
| `ProcurementProductCategoryName` |  Procurement category | String | Required by the `ProductCategory` commitment type. |
| `Price` | Item price | Real | Item price for `ProductQuantity` commitment type. |
| `PriceQuantity` | Price unit | Real | Item price unit for `ProductQuantity` commitment type. |
| `LineDiscountAmount` | Line discount amount | Real | Item line discount amount for `ProductQuantity` commitment type. |
| `LineDiscountPercentage` | Line discount percentage | Real | Available for all commitment types. |
| `MinimumReleaseAmount` | Minimum release amount | Real | Minimum release amount |
| `MaximumReleaseAmount` | Maximum release amount | Real | Maximum release amount |
| `IsCommitmentMaximumEnforced` | Is max enforced | Enum | Values: `Yes`, `No`. |
| `IsPriceAndDiscountFixed` | Is price and discount fixed | Enum | Values: `Yes`, `No`. |
| `UnitSymbol` | Unit of measure | String | Unit of measure |
| `ProjectId` | Project ID | String | Project ID |
| `ProjectCategoryId` | Project category ID | String | Project category ID |
| `ProjectActivityNumber` | Project activity number | String | Project activity number |
| `ReceivingSiteId` | Site | String | Site |
| `ReceivingWarehouseId` | Warehouse | String | Warehouse |

Here's an example request query for the CLM integration purchase agreement line entity:

```http
GET https://[baseURI]/data/CLMIntegrationPurchaseAgreementLines
```

Here's an example response to that query:

```json
{
    "PurchaseAgreementId": "000026",
    "PurchaseAgreementLegalEntityId": "USMF",
    "LineNumber": 1,
    "ExternalContractId": "EXT000026",
    "ExternalContractLineId": "EXT000026_1",
    "CommitmentType": "ProductVolume",
    "CommittedAmount": 1100,
    "CommittedQuantity": 0,
    "EffectiveDate": "2024-01-01T12:00:00Z",
    "ExpirationDate": "2024-12-31T12:00:00Z",
    "ItemNumber": "1000",
    "ProductVariantNumber": "",
    "ProcurementProductCategoryName": "",
    "Price": 0,
    "PriceQuantity": 0,
    "LineDiscountAmount": 0,
    "LineDiscountPercentage": 10,
    "MinimumReleaseAmount": 0,
    "MaximumReleaseAmount": 0,
    "IsCommitmentMaximumEnforced": "No",
    "IsPriceAndDiscountFixed": "No",
    "UnitSymbol": "",
    "ProjectId": "000057",
    "ProjectCategoryId": "ProjItem",
    "ProjectActivityNumber": "",
    "ReceivingSiteId": "",
    "ReceivingWarehouseId": ""
}
```

## Purchase agreement validation entities

In the scenario of creating and amending purchase contracts, Supply Chain Management provides data entities designed for validating purchase agreements. These validation entities contain the same list of fields as regular entities but don't persist data in the database. Instead, they perform validation and return the result as an exception if a validation error occurs. The following table outlines the data entities available for validating purchase agreements.

| Entity |Target entity | Public name (OData) | Operations validated | Company specific | Direction |
| --- | --- | --- | --- | --- | --- |
| CLM integration validation purchase agreements | `CLMIntegrationValidationPurchaseAgreementHeaderEntity` | `CLMIntegrationValidationPurchaseAgreements` | Update | Yes | CLM -\> Supply Chain Management |
| CLM integration validate insert purchase agreement lines | `CLMIntegrationValidateInsertPurchaseAgreementLineEntity` | `CLMIntegrationValidateInsertPurchaseAgreementLines` | Insert | Yes | CLM -\> Supply Chain Management |
| CLM integration update, delete validation purchase agreement lines | `CLMIntegrationValidateUpdateDeletePurchaseAgreementLineEntity` | `CLMIntegrationValidateUpdateDeletePurchaseAgreementLines` | Update, Delete | Yes | CLM -\> Supply Chain Management |

> [!NOTE]
> Each validation entity can only validate specific database operations, as outlined in the table. The purchase agreement insert validation entity isn't supported, so data can only be validated by persisting it through the regular `CLMIntegrationPurchaseAgreementHeaderEntity` entity.

## Create shareable, secured deep links

The following APIs create shareable and secured URLs (also known as deep links) to specific pages within Supply Chain Management, such as vendor page, contract page, or purchase agreement page. These APIs enable scenarios such as embedding links directly in an external CLM system, which enables users to quickly and easily locate the specified pages and records simply by selecting the generated link. Learn more about deep links in [Create shareable, secured URLs (deep links)](../../../../fin-ops-core/dev-itpro/user-interface/create-deep-links.md).

### Generate a deep link for a vendor

This API generates a deep link to open the page for a specific vendor within Supply Chain Management.

Here's an example request for a deep link for a vendor:

```http
POST https://[baseURI]/data/VendorsV2/Microsoft.Dynamics.DataEntities.GenerateVendorDetailFormURL
```

```json
{
    "_vendAccount": "1001",
    "_companyId": "USMF"
}
```

Here's an example response to that request:

```json
{
    "@odata.context": "https://[baseURI]/data/$metadata#Edm.String",
    "value": "https://[baseURI]/?cmp=usmf&prt=initial&mi=display:VendTable&pageType=Details&q=[queryValue]"
}
```

### Generate deep link for a contract by contract ID

This API generates a deep link to open the form for a specific contract within Supply Chain Management.

Here's an example request for a deep link for a contract using a contract ID:

```http
POST https://[baseURI]/data/CLMIntegrationContracts/Microsoft.Dynamics.DataEntities.GenerateContractDetailFormURLByContractId
```

```json
{
    "_contractId": "C00001",
    "_companyId": "USMF"
}
```

Here's an example response to that request:

```json
{
    "@odata.context": "https://[baseURI]/data/$metadata#Edm.String",
    "value": "https://[baseURI]/?cmp=usmf&prt=initial&mi=display:CLMIntegrationContractTable&pageType=Details&q=[queryValue]"
}
```

### Generate deep link for a contract by contract external ID

This API generates a deep link to open the page for a specific contract within Supply Chain Management.

Here's an example request for a deep link for a contract using a contract external ID:

```http
POST https://[baseURI]/data/CLMIntegrationContracts/Microsoft.Dynamics.DataEntities.GenerateContractDetailFormURLByExternalContractId
```

```json
{
    "_externalContractId": "EXTC00001",
    "_companyId": "USMF"
}
```

Here's an example response to that request:

```json
{
    "@odata.context": "https://[baseURI]/data/$metadata#Edm.String",
    "value": "https://[baseURI]/?cmp=usmf&prt=initial&mi=display:CLMIntegrationContractTable&pageType=Details&q=[queryValue]"
}
```

### Generate deep link for a purchase agreement by agreement ID

This API generates a deep link to open the page for a specific purchase agreement within Supply Chain Management.

Here's an example request for a deep link for a purchase agreement using an agreement ID:

```http
POST https://[baseURI]/data/CLMIntegrationPurchaseAgreements/Microsoft.Dynamics.DataEntities.GenerateAgreementFormURLByAgreementId
```

```json
{
    "_agreementId": "000026",
    "_companyId": "USMF"
}
```

Here's an example response to that request:

```json
{
    "@odata.context": "https://[baseURI]/data/$metadata#Edm.String",
    "value": "https://[baseURI]/?cmp=usmf&prt=initial&mi=display:PurchAgreementDetails&pageType=Details&q=[queryValue]"
}
```

### Generate deep link for a purchase agreement by agreement external ID

This API generates a deep link to open the page for a specific purchase agreement within Supply Chain Management.

Here's an example request for a deep link for a purchase agreement using an agreement external ID:

```http
POST https://[baseURI]/data/CLMIntegrationPurchaseAgreements/Microsoft.Dynamics.DataEntities.GenerateAgreementFormURLByExternalContractId
```

```json
{
    "_externalContractId": "EXT000026",
    "_companyId": "USMF"
}
```

Here's an example response to that request:

```json
{
    "@odata.context": "https://[baseURI]/data/$metadata#Edm.String",
    "value": "https://[baseURI]/?cmp=usmf&prt=initial&mi=display:PurchAgreementDetails&pageType=Details&q=[queryValue]"
}
```

## Related information

- [Data integration APIs](clm-data-integration-apis.md)
