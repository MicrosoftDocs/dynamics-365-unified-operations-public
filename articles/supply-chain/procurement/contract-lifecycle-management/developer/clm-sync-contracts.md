---
title: Synchronize contracts (preview)
description: Learn about the scenarios, data entities, and integration methods that are available for the synchronization of contracts and related purchase agreements from an external contract lifecycle management (CLM) system to Microsoft Dynamics 365 Supply Chain Management.
author: ShriramSivasankaran
ms.author: shriramsiv
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
<!-- KFM: Preview until 10.0.43 GA -->

This article describes the scenarios, data entities, and integration methods that are available for the synchronization of contracts and related purchase agreements from an external contract lifecycle management (CLM) system to Microsoft Dynamics 365 Supply Chain Management. The integration process establishes a workflow that transfers contracts and related purchase agreements from the CLM system to Supply Chain Management. The CLM system is assumed to function as the master system for managing contracts.

## Access the data integration APIs

Learn which data integration APIs are available in [Data integration APIs](clm-data-integration-apis.md). There, you can also learn how to enable change tracking, and how to authenticate with Supply Chain Management so that your CLM system can access the data entities that are described in this article.

## Scenarios

Supply Chain Management supports the following integration scenarios:

- Create a non-disclosure agreement (NDA)
- Create a purchase contract
- Create a contract amendment

This section outlines each scenario and provides a process diagram for it.

### Create an NDA

NDAs are independent contracts that aren't related to any document in Supply Chain Management. The integration points involve creating the contract and updating its status after it's approved and signed.

The following illustration shows how NDAs are created and synced between systems.

:::image type="content" source="../media/create-nda.png" alt-text="Diagram that shows the process for creating NDAs and syncing them between systems." lightbox="../media/create-nda.png":::

### Create a purchase contract

Purchase contracts are contracts that are associated with a purchase agreement in Supply Chain Management. The integration points include creating the contract, validating the purchase agreement, submitting it for approval and signing, updating the contract's status after it's approved and signed, and eventually creating the purchase agreement.

The following illustration shows how purchase contracts are created and synced between systems.

:::image type="content" source="../media/create-purchase-contract.png" alt-text="Diagram that shows the process for creating purchase contracts and syncing them between systems." lightbox="../media/create-purchase-contract.png":::

### Amend a contract

Purchase contract amendments and NDA amendments are documents that change the terms of an existing agreement. The integration points include updating the contract with amendment information, validating the purchase agreement, submitting it for approval and signing, updating the contract's status after it's approved and signed, and eventually updating the purchase agreement. In Supply Chain Management, the amendment information is updated in the same contract and purchase agreement record.

The following illustration shows how contract amendments are created and synced between systems.

:::image type="content" source="../media/amend-purchase-contract.png" alt-text="Diagram that shows the process for creating contract amendments and syncing between systems." lightbox="../media/amend-purchase-contract.png":::

## Available data entities for syncing contracts and purchase agreements

Supply Chain Management offers several out-of-box data entities that external CLM systems can use to sync contract data. The following table describes the available data entities that are required for the synchronization of contracts and purchase agreements.

| Entity | Target entity | Public name (OData) | Company-specific | Direction |
|---|---|---|---|---|
| CLM integration contract | `CLMIntegrationContractEntity` | `CLMIntegrationContracts` | Yes | CLM &rarr; Supply Chain Management |
| CLM integration purchase agreements | `CLMIntegrationPurchaseAgreementHeaderEntity` | `CLMIntegrationPurchaseAgreements` | Yes | CLM &rarr; Supply Chain Management |
| CLM integration purchase agreement lines | `CLMIntegrationPurchaseAgreementLineEntity` | `CLMIntegrationPurchaseAgreementLines` | Yes | CLM &rarr; Supply Chain Management |

> [!NOTE]
> Company-specific data entities include the `dataAreaId` field, which indicates the legal entity that a record belongs to. Your CLM system must adopt the same behavior to support both company-specific records and cross-company records. Learn more about cross-company behavior in [Cross-company behavior of data entities](../../../../fin-ops-core/dev-itpro/data-entities/cross-company-behavior.md).

The following illustration shows how contracts and purchase agreements are integrated and synced.

:::image type="content" source="../media/contract.png" alt-text="Diagram that shows the integration of contracts and purchase agreements." lightbox="../media/contract.png":::

### Contract entity

The *CLM integration contract* entity provides information about the contract. The following table describes its properties.

| Physical name | Property | Type | Description |
|---|---|---|---|
| `ContractId` (entity key) | Contract ID | String | The contract identifier in the CLM system. |
| `LegalEntityId` (entity key) | Legal entity ID | String | The legal entity ID. |
| `ExternalContractId` | External contract ID | String | The internal, system-generated contract identifier in the CLM system. |
| `ContractType` | Contract type | String | The contract type name reference. |
| `ContractStatus` | Contract status | Enum | The contract status. The possible values are `Draft`, `WaitingForApproval`, `Approved`, `Rejected`, `WaitingForSignatures`, `WaitingForExternalSignatures`, `WaitingForInternalSignatures`, `Executed`, `Terminated`, `Expired`, `OnHold`, `Cancelled`, `WaitingForReview`, and `Reviewed`. |
| `ContractName` | Contract title | String | The contract title. |
| `EffectiveDate` | Effective date | Date | The effective date. |
| `ExpirationDate` | Expiration date | Date | The expiration date. |
| `RequesterWorkerName` | Requester name | String | <p>The name of the requester worker.</p><p>If the specified worker name isn't found in the system, the `RequesterWorkerEmail` field is used to identify the worker.</p> |
| `RequesterWorkerEmail` | Requester email | String | The email address of the requester worker. |
| `AccountType` | Account type | Enum | A value that determines the type of contracting party. The possible values are `Vend`, `Cust`, and `Party`. |
| `AccountRelationId` | Account number | String | The contracting account identifier that corresponds to the specified account type. |
| `PartyNumber` | Party ID | String | The party number in the global address book. |
| `ContactPersonId` | Contact person ID | String | The contact person ID. |
| `LatestAmendmentId` | Latest amendment ID | String | The latest amendment identifier in the CLM system. |
| `LatestExternalAmendmentId` | Latest amendment external ID | String able | The internal, system-generated latest amendment identifier in the CLM system. |
| `AmendmentInProcess` | Amendment in process | Enum | A value that indicates whether amendment is in progress. The possible values are `Yes` and `No`. |

The following example shows a request query for the *CLM integration contract* entity.

```http
GET https://[baseURI]/data/CLMIntegrationContracts
```

The following example shows a response to the preceding query.

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

The *CLM integration agreement header* entity provides information about the purchase agreement header. The following table describes the most common properties of this entity. You might also use other properties, depending on your business requirements.

| Physical name | Property | Type | Description |
|---|---|---|---|
| `PurchaseAgreementId` (entity key) | Purchase agreement ID | String | The purchase agreement identifier from Supply Chain Management. |
| `BuyingLegalEntityId` (entity key) | Legal entity ID | String | The legal entity ID. |
| `ExternalContractId` | External contract ID | String | The internal, system-generated purchase agreement identifier in the CLM system. |
| `ContractId` | Contract ID | String | The contract identifier reference that is used to associate the purchase agreement with the contract. |
| `ContractLegalEntity` | Contract legal entity ID | String | The contract legal entity identifier reference that is used to associate the purchase agreement with the contract. |
| `AgreementOwnership` | Purchase agreement ownership type | Enum | The ownership type of the purchase agreement. The possible values are `SCM` and `CLM`. |
| `AgreementStatus` | Agreement status | Enum | The purchase agreement status. The possible values are `OnHold`, `Effective`, and `Closed`. |
| `DocumentTitle` | Document title | String | The document title. |
| `PurchaseAgreementClassificationName` | Purchase agreement classification | String | The purchase agreement classification name reference. |
| `DefaultEffectiveDate` | Default effective date | Date | The default effective date. |
| `DefaultExpirationDate` | Default expiration date | Date | The default expiration date. |
| `AgreementVendorAccountNumber` | Vendor account | String | The agreement vendor account reference. |
| `InvoiceVendorAccountNumber` | Invoice account | String |The invoicing vendor account reference. |
| `VendorReference` | Vendor reference | String | The vendor reference. |
| `PrimaryResponsibleWorkerEmail` | Primary responsible worker email | String | The email address of the primary responsible worker. |
| `PrimaryResponsibleWorkerName` | Primary responsible worker name | String | <p>The name of the primary responsible worker.</p><p>If the specified worker name isn't found in the system, the `PrimaryResponsibleWorkerEmail` field is used to identify the worker.</p> |
| `SecondaryResponsibleWorkerEmail` | Secondary responsible worker email | String | The email address of the secondary responsible worker. |
| `SecondaryResponsibleWorkerName` | Secondary responsible worker name | String | <p>The name of the secondary responsible worker.</p><p>If the specified worker name isn't found in the system, the `SecondaryResponsibleWorkerEmail` field is used to identify the worker.</p> |
| `CashDiscountCode` | Cash discount | String | The cash discount. |
| `ContactPersonId` | Contact person ID | String | The contact person ID. |
| `CurrencyCode` | Currency | String | The currency. |
| `DefaultCommitmentType` | Default commitment type | Enum | The default commitment type. The possible values are `ProductQuantity`, `ProductVolume`, `ProductCategory`, and `ProductRootCategory`. |
| `BuyerGroupId` | Buyer group ID | String | The buyer group ID. |
| `ProjectId` | Project ID | String | The project ID. |
| `PaymentTermsName` | Payment terms | String | The payment terms. |

The following example shows a request query for the *CLM integration agreement header* entity.

```http
GET https://[baseURI]/data/CLMIntegrationPurchaseAgreements
```

The following example shows a response to the preceding query.

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

The *CLM integration purchase agreement line* entity provides information about the purchase agreement line. The following table describes the most common properties of this entity. You might also use other properties, depending on your business requirements.

| Physical name | Property | Type | Description |
|---|---|---|---|
| `PurchaseAgreementId` (entity key) | Purchase agreement ID | String | The purchase agreement identifier reference. |
| `PurchaseAgreementLegalEntityId` (entity key) | Purchase agreement legal entity ID | String | The purchase agreement legal entity identifier reference. |
| `LineNumber` (entity key) | Line number | Real | The line number. |
| `ExternalContractId` | External contract ID | String | The internal, system-generated purchase agreement identifier reference in the CLM system. This field can be used instead of the `PurchaseAgreementId` field when a record is created. |
| `ExternalContractLineId` | External contract line ID | String | The internal, system-generated purchase agreement line identifier in the CLM system. |
| `CommitmentType` | Commitment type | Enum | The commitment type. The possible values are `ProductQuantity`, `ProductVolume`, `ProductCategory`, and `ProductRootCategory`. |
| `CommittedAmount` | Committed amount | Real | The committed amount for volume-based commitment types (`ProductVolume`, `ProductCategory`, and `ProductRootCategory`). |
| `CommittedQuantity` | Committed quantity | Real | The committed quantity for quantity-based commitment types (`ProductQuantity`). |
| `EffectiveDate` | Effective date | Date | The effective date. |
| `ExpirationDate` | Expiration date | Date | The expiration date. |
| `ItemNumber` | Item number | String | The item number. This field is required by the `ProductQuantity` and `ProductVolume` commitment types. |
| `ProductVariantNumber` | Product variant number | String | The product variant number. This field is relevant if the specified product contains product variants. |
| `ProcurementProductCategoryName` | Procurement category | String | The procurement category. This field is required by the `ProductCategory` commitment type. |
| `Price` | Item price | Real | The item price. This field is available for the `ProductQuantity` commitment type. |
| `PriceQuantity` | Price unit | Real | The item price unit. This field is available for the `ProductQuantity` commitment type. |
| `LineDiscountAmount` | Line discount amount | Real | The item line discount amount. This field is available for the `ProductQuantity` commitment type. |
| `LineDiscountPercentage` | Line discount percentage | Real | The line discount percentage. This field is available for all commitment types. |
| `MinimumReleaseAmount` | Minimum release amount | Real | The minimum release amount. |
| `MaximumReleaseAmount` | Maximum release amount | Real | The maximum release amount. |
| `IsCommitmentMaximumEnforced` | Is max enforced | Enum | A value that indicates whether a commitment maximum is enforced. The possible values are `Yes` and `No`. |
| `IsPriceAndDiscountFixed` | Is price and discount fixed | Enum | A value that indicates whether the price and discount are fixed. The possible values are `Yes` and `No`. |
| `UnitSymbol` | Unit of measure | String | The unit of measure. |
| `ProjectId` | Project ID | String | The project ID. |
| `ProjectCategoryId` | Project category ID | String | The project category ID. |
| `ProjectActivityNumber` | Project activity number | String | The project activity number. |
| `ReceivingSiteId` | Site | String | The site. |
| `ReceivingWarehouseId` | Warehouse | String | The warehouse. |

The following example shows a request query for the *CLM integration purchase agreement line* entity.

```http
GET https://[baseURI]/data/CLMIntegrationPurchaseAgreementLines
```

The following example shows a response to the preceding query.

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

In the scenario for creating and amending purchase contracts, Supply Chain Management provides data entities that are designed for the validation of purchase agreements. These validation entities contain the same list of fields as regular entities, but they don't persist data in the database. Instead, they perform validation and return the result as an exception if a validation error occurs. The following table describes the data entities that are available for the validation of purchase agreements.

| Entity | Target entity | Public name (OData) | Validated operations | Company-specific | Direction |
|---|---|---|---|---|---|
| CLM integration validation purchase agreements | `CLMIntegrationValidationPurchaseAgreementHeaderEntity` | `CLMIntegrationValidationPurchaseAgreements` | Update | Yes | CLM &rarr; Supply Chain Management |
| CLM integration validate insert purchase agreement lines | `CLMIntegrationValidateInsertPurchaseAgreementLineEntity` | `CLMIntegrationValidateInsertPurchaseAgreementLines` | Insert | Yes | CLM &rarr; Supply Chain Management |
| CLM integration update, delete validation purchase agreement lines | `CLMIntegrationValidateUpdateDeletePurchaseAgreementLineEntity` | `CLMIntegrationValidateUpdateDeletePurchaseAgreementLines` | Update, Delete | Yes | CLM &rarr; Supply Chain Management |

> [!NOTE]
> As the preceding table shows, each validation entity can validate only specific database operations. No entity for validating purchase agreement insert operations is supported. Therefore, data can be validated only by persisting it through the regular `CLMIntegrationPurchaseAgreementHeaderEntity` entity.

## Create shareable, secured deep links

The following APIs create shareable, secured URLs that point to specific pages in Supply Chain Management, such as the vendor, contract, or purchase agreement page. These URLs are also known as *deep links*.

The APIs enable scenarios such as embedding links directly in an external CLM system. In this way, users can quickly and easily find the specified pages and records just by selecting the link that is generated.

Learn more about deep links in [Create shareable, secured URLs (deep links)](../../../../fin-ops-core/dev-itpro/user-interface/create-deep-links.md).

### Generate a deep link for a vendor

This API generates a deep link that opens the page for a specific vendor in Supply Chain Management.

The following example shows a request for a deep link for a vendor.

```http
POST https://[baseURI]/data/VendorsV2/Microsoft.Dynamics.DataEntities.GenerateVendorDetailFormURL
```

```json
{
    "_vendAccount": "1001",
    "_companyId": "USMF"
}
```

The following example shows a response to the preceding request.

```json
{
    "@odata.context": "https://[baseURI]/data/$metadata#Edm.String",
    "value": "https://[baseURI]/?cmp=usmf&prt=initial&mi=display:VendTable&pageType=Details&q=[queryValue]"
}
```

### Generate a deep link for a contract by contract ID

This API generates a deep link that opens the page for a specific contract in Supply Chain Management by using the contract ID.

The following example shows a request for a deep link for a contract by contract ID.

```http
POST https://[baseURI]/data/CLMIntegrationContracts/Microsoft.Dynamics.DataEntities.GenerateContractDetailFormURLByContractId
```

```json
{
    "_contractId": "C00001",
    "_companyId": "USMF"
}
```

The following example shows a response to the preceding request.

```json
{
    "@odata.context": "https://[baseURI]/data/$metadata#Edm.String",
    "value": "https://[baseURI]/?cmp=usmf&prt=initial&mi=display:CLMIntegrationContractTable&pageType=Details&q=[queryValue]"
}
```

### Generate a deep link for a contract by contract external ID

This API generates a deep link that opens the page for a specific contract in Supply Chain Management by using the contract's external ID.

The following example shows a request for a deep link for a contract by contract external ID.

```http
POST https://[baseURI]/data/CLMIntegrationContracts/Microsoft.Dynamics.DataEntities.GenerateContractDetailFormURLByExternalContractId
```

```json
{
    "_externalContractId": "EXTC00001",
    "_companyId": "USMF"
}
```

The following example shows a response to the preceding request.

```json
{
    "@odata.context": "https://[baseURI]/data/$metadata#Edm.String",
    "value": "https://[baseURI]/?cmp=usmf&prt=initial&mi=display:CLMIntegrationContractTable&pageType=Details&q=[queryValue]"
}
```

### Generate a deep link for a purchase agreement by agreement ID

This API generates a deep link that opens the page for a specific purchase agreement in Supply Chain Management by using the agreement ID.

The following example shows a request for a deep link for a purchase agreement by agreement ID.

```http
POST https://[baseURI]/data/CLMIntegrationPurchaseAgreements/Microsoft.Dynamics.DataEntities.GenerateAgreementFormURLByAgreementId
```

```json
{
    "_agreementId": "000026",
    "_companyId": "USMF"
}
```

The following example shows a response to the preceding request.

```json
{
    "@odata.context": "https://[baseURI]/data/$metadata#Edm.String",
    "value": "https://[baseURI]/?cmp=usmf&prt=initial&mi=display:PurchAgreementDetails&pageType=Details&q=[queryValue]"
}
```

### Generate a deep link for a purchase agreement by agreement external ID

This API generates a deep link that opens the page for a specific purchase agreement in Supply Chain Management by using the agreement's external ID.

The following example shows a request for a deep link for a purchase agreement by agreement external ID.

```http
POST https://[baseURI]/data/CLMIntegrationPurchaseAgreements/Microsoft.Dynamics.DataEntities.GenerateAgreementFormURLByExternalContractId
```

```json
{
    "_externalContractId": "EXT000026",
    "_companyId": "USMF"
}
```

The following example shows a response to the preceding request.

```json
{
    "@odata.context": "https://[baseURI]/data/$metadata#Edm.String",
    "value": "https://[baseURI]/?cmp=usmf&prt=initial&mi=display:PurchAgreementDetails&pageType=Details&q=[queryValue]"
}
```

## Related information

- [Data integration APIs](clm-data-integration-apis.md)
