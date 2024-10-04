---
title: Synchronize contracts (preview)
description: This article describes scenarios, data entities and integration methods available for synchronizing contracts and related purchase agreements from external contract lifecycle management system to Dynamics 365 Supply Chain Management.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: XXXX
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---

# Synchronize contracts (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.43 GA  -->

This article describes scenarios, data entities and integration methods available for synchronizing contracts and related purchase agreements from external contract lifecycle management system to Dynamics 365 Supply Chain Management. The integration process establishes a workflow that transfers contracts and related purchase agreements from the contract lifecycle management system to Supply Chain Management. The contract lifecycle management system is assumed to function as the master system for managing contracts.

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Supply Chain Management version 10.0.42.

## Scenarios

This section outlines various integration scenarios supported in Supply Chain Management, including the following:

- NDA creation
- purchase contract creation
- purchase contract amendment

The images provided later in this article illustrate process diagrams.

### Create NDA

Non-disclosure agreements are independent contracts that are not related to any document within Supply Chain Management. The integration points involve creating the contract and updating its status once the approval and signing process is complete.

:::image type="content" source="../media/create-nda.png" alt-text="Create NDA diagram." lightbox="../media/create-nda.png":::

### Create purchase contract

Purchase contract is a contract which is associated with the purchase agreement in Supply Chain Management. The integration points include creating the contract, validating the purchase agreement prior to submitting it for approval and signing, updating the contract status upon completion of the approval and signing process, and ultimately creating the purchase agreement.

:::image type="content" source="../media/create-purchase-contract.png" alt-text="Create purchase contract diagram." lightbox="../media/create-purchase-contract.png":::

### Amend purchase contract

Purchase contract amendment and NDA amendment is a document that changes the terms of an existing agreement. The integration points include updating the contract with amendment information, validating the purchase agreement prior to submitting it for approval and signing, updating the contract status upon completion of the approval and signing process, and ultimately updating the purchase agreement. In Supply Chain Management, the amended information is updated within the same contract and purchase agreement record.

:::image type="content" source="../media/amend-purchase-contract.png" alt-text="Amend purchase contract
 diagram." lightbox="../media/amend-purchase-contract.png":::

## Available data entities

Supply Chain Management offers several out-of-the-box data entities that external contract lifecycle management systems can use to synchronize contract data. The following table describes the available data entities necessary for synchronizing contracts and purchase agreements.

| **Entity** |**Target entity** | **Public name (OData)** | **Company specific** | **Direction** |
| --- | --- | --- | --- | --- |
| CLM integration contract | `CLMIntegrationContractEntity` | `CLMIntegrationContracts` | Yes | CLM -\> Supply Chain Management |
| CLM integration purchase agreements | `CLMIntegrationPurchaseAgreementHeaderEntity` | `CLMIntegrationPurchaseAgreements` | Yes | CLM -\> Supply Chain Management |
| CLM integration purchase agreement lines | `CLMIntegrationPurchaseAgreementLineEntity` | `CLMIntegrationPurchaseAgreementLines` | Yes | CLM -\> Supply Chain Management |

> [!NOTE]
> Company-specific data entities include the _dataAreaId_ field, which indicates the legal entity to which the record belongs. Your contract lifecycle management system must adopt the same behavior that supports both company-specific and cross-company records. For more information about the cross-company behavior, see [Cross-company behavior of data entities](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/cross-company-behavior).

### Contract entity

This entity provides information about the contract.

#### Properties

| Physical name | Property | Type | Description |
|---|---|---|---|
| `ContractId` (PK) | Contract ID | String | Contract identifier in the CLM. |
| `LegalEntityId` (PK) | Legal entity ID | String | N/A |
| `ExternalContractId` | External contract ID | String | Internal system-generated contract identifier in the CLM. |
| `ContractType` | Contract type | String | Contract type name reference. |
| `ContractStatus` | Contract status | Enum | Values: `Draft`, `WaitingForApproval`, `Approved`, `Rejected`, `WaitingForSignatures`, `WaitingForExternalSignatures`, `WaitingForInternalSignatures`, `Executed`, `Terminated`, `Expired`, `OnHold`, `Cancelled`, `WaitingForReview`, `Reviewed`. |
| `ContractName` | Contract title | String | N/A |
| `EffectiveDate` | Effective date | Date | N/A |
| `ExpirationDate` | Expiration date | Date | N/A |
| `RequesterWorkerName` | Requester name | String | Requester worker name.<br/>If the specified worker name is not found in the system, the `RequesterWorkerEmail` field is used to identify the worker. |
| `RequesterWorkerEmail` | Requester email | String | Requester worker email. |
| `AccountType` | Account type | Enum | Determines the type of contracting party.<br/>Values: `Vend`, `Cust`, `Party`. |
| `AccountRelationId` | Account number | String | Contracting account identifier that corresponds to the chosen AccountType. |
| `PartyNumber` | Party ID | String | Party number in the global address book. |
| `ContactPersonId` | Contact person ID | String | N/A |
| `LatestAmendmentId` | Latest amendment ID | String | Latest amendment identifier in the CLM. |
| `LatestExternalAmendmentId` | Latest amendment external ID | String able | Internal system-generated latest amendment identifier in the CLM. |
| `AmendmentInProcess` | Amendment in process | Enum | Values: `Yes`, `No`. |

#### Example query for the CLM integration contract entity

**Request**

```http
GET https://[baseURI]/data/CLMIntegrationContracts
```

**Response**

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

This entity provides information about the purchase agreement header. The most common properties can be found in the following table.

| Physical name | Property | Type | Description |
|---|---|---|---|
| `PurchaseAgreementId` (PK) | Purchase agreement ID | String | Purchase agreement identifier from Supply Chain Management. |
| `BuyingLegalEntityId` (PK) | Legal entity ID | String | N/A |
| `ExternalContractId` | External contract ID | String | Internal system-generated purchase agreement identifier in the CLM. |
| `ContractId` | Contract ID | String | Contract identifier reference to associate the purchase agreement with the contract. |
| `ContractLegalEntity` | Contract legal entity ID | String | Contract legal entity identifier reference to associate the purchase agreement with the contract. |
| `AgreementOwnership` | Purchase agreement ownership type | Enum | Values: `SCM`, `CLM`. |
| `AgreementStatus` | Agreement status | Enum | Values: `OnHold`, `Effective`, `Closed`. |
| `DocumentTitle` | Document title | String | N/A |
| `PurchaseAgreementClassificationName` | Purchase agreement classification | String | Purchase agreement classification name reference. |
| `DefaultEffectiveDate` | Default effective date | Date | N/A |
| `DefaultExpirationDate` | Default expiration date | Date | N/A |
| `AgreementVendorAccountNumber` | Vendor account | String | Agreement vendor account reference. |
| `InvoiceVendorAccountNumber` | Invoice account | String | Invoicing vendor account reference. |
| `VendorReference` | Vendor reference | String | N/A |
| `PrimaryResponsibleWorkerEmail` | Primary responsible worker email | String | Primary responsible worker email.  |
| `PrimaryResponsibleWorkerName` | Primary responsible worker name | String | Primary responsible worker name.<br/>If the specified worker name is not found in the system, the `PrimaryResponsibleWorkerEmail` field is used to identify the worker. |
| `SecondaryResponsibleWorkerEmail` | Secondary responsible worker email | String | Secondary responsible worker email. |
| `SecondaryResponsibleWorkerName` | Secondary responsible worker name | String | Secondary responsible worker name.<br/>If the specified worker name is not found in the system, the `SecondaryResponsibleWorkerEmail` field is used to identify the worker. |
| `CashDiscountCode` | Cash discount | String | N/A |
| `ContactPersonId` | Contact person ID | String | N/A |
| `CurrencyCode` | Currency | String | N/A |
| `DefaultCommitmentType` | Default commitment type | Enum | Values: `ProductQuantity`, `ProductVolume`, `ProductCategory`, `ProductRootCategory`. |
| `BuyerGroupId` | Buyer group ID | String | N/A |
| `ProjectId` | Project ID | String | N/A |
| `PaymentTermsName` | Payment terms | String | N/A |
| ... | ... | ... | N/A |

#### Example query for the CLM integration purchase agreements entity

**Request**

```http
GET https://[baseURI]/data/CLMIntegrationPurchaseAgreements
```

**Response**

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

This entity provides information about the purchase agreement line. The most common properties can be found in the following table.

| Physical name | Property | Type | Description |
|---|---|---|---|
| PurchaseAgreementId (PK) | Purchase agreement ID | String | Purchase agreement identifier reference. |
| PurchaseAgreementLegalEntityId (PK) | Purchase agreement legal entity ID | String | Purchase agreement legal entity identifier reference. |
| LineNumber (PK) | Line number | Real | N/A |
| ExternalContractId | External contract ID | String | Internal system-generated purchase agreement identifier reference in the CLM. Can be used instead of the PurchaseAgreementId field when creating a record. |
| ExternalContractLineId | External contract line ID | String | Internal system-generated purchase agreement line identifier in the CLM. |
| CommitmentType | Commitment type | Enum | Values: **ProductQuantity, ProductVolume, ProductCategory, ProductRootCategory.** |
| CommittedAmount | Committed amount | Real | Committed amount for volume-based commitment types **(ProductVolume, ProductCategory, ProductRootCategory)**. |
| CommittedQuantity | Committed quantity | Real | Committed quantity for quantity-based commitment types **(ProductQuantity)**. |
| EffectiveDate | Effective date | Date | N/A |
| ExpirationDate | Expiration date | Date | N/A |
| ItemNumber | Item number | String | Required by the **ProductQuantity** and **ProductVolume** commitment type. |
| ProductVariantNumber | Product variant number | String | Relevant if specified product contains product variants. |
| ProcurementProductCategoryName |  Procurement category | String | Required by the **ProductCategory** commitment type. |
| Price | Item price | Real | Item price for **ProductQuantity** commitment type. |
| PriceQuantity | Price unit | Real | Item price unit for **ProductQuantity** commitment type. |
| LineDiscountAmount | Line discount amount | Real | Item line discount amount for **ProductQuantity** commitment type. |  |
| LineDiscountPercentage | Line discount percentage | Real | Available for all commitment types. |
| MinimumReleaseAmount | Minimum release amount | Real | N/A |
| MaximumReleaseAmount | Maximum release amount | Real | N/A |
| IsCommitmentMaximumEnforced | Is max enforced | Enum | Values: Yes, No. |
| IsPriceAndDiscountFixed | Is price and discount fixed | Enum | Values: Yes, No. |
| UnitSymbol | Unit of measure | String | N/A |
| ProjectId | Project ID | String | N/A |
| ProjectCategoryId | Project category ID | String | N/A |
| ProjectActivityNumber | Project activity number | String | N/A |
| ReceivingSiteId | Site | String | N/A |
| ReceivingWarehouseId | Warehouse | String | N/A |
| ... | ... | ... | N/A |

#### Example query for the CLM integration purchase agreement lines entity

**Request**

```http
GET https://[baseURI]/data/CLMIntegrationPurchaseAgreementLines
```

**Response**

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

### Integration diagram

![Contract](./images/contract.png)

## Data integration APIs

This section describes integration patters available in the Supply Chain Management and guidelines for synchronizing contract data between Supply Chain Management and Contract Lifecycle Management system. Recommended integration patterns for contract lifecycle management integration are listed in the following table:

| Pattern | Timing | Batch | Documentation |
| --- | --- | --- | --- |
| OData | Synchronous | No | [Open Data Protocol (OData)](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/odata) |
| Data management package REST API | Asynchronous | Yes | [Data management package REST API](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/data-management-api) |

### Guidelines

Integration pattern should be selected based on data volume and real-time requirements. As a general recommendation, for integrations requiring real-time data synchronization and error handling, it is advised to use the _OData protocol_, provided the peak data volume is not excessively high. For handling large volumes of data, it is recommended to use the _Data Management Package API_ instead. For more information about the integration patterns and scenarios, see [Integration between finance and operations apps and third-party services](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/integration-overview).

### Configure service-based authentication

Authentication with Microsoft Entra ID provides a secure way of authenticating external Contract Lifecycle Management with Supply Chain Management. To access resources within Supply Chain Management, you must register an application in Microsoft Entra ID. Once the application (client ID) is created, it should be registered as an external application on the **Microsoft Entra applications** page in Supply Chain Management. For the service account **User ID**, it's recommended to create a new user and assign them the **CLM integration role**. For more information about how to register an application in Microsoft Entra ID and how to register external application in the Supply Chain Management, see the following [Article](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/services-home-page#authentication).

## Purchase agreement validation entities

In the scenario of creating and amending purchase contracts, Supply Chain Management provides data entities specifically designed for validation purposes. These validation entities contain the same list of fields as regular entities but do not persist data in the database. Instead, they perform validation and return the result either in the **ValidationResult** field or as an exception. The table below outlines the data entities available for validating purchase agreements.

| Entity |Target entity | Public name (OData) | Company specific | Direction |
| --- | --- | --- | --- | --- |
| CLM integration validation purchase agreements | CLMIntegrationValidationPurchaseAgreementHeaderEntity | CLMIntegrationValidationPurchaseAgreements | Yes | CLM -\> Supply Chain Management |
| CLM integration validation purchase agreement lines | CLMIntegrationValidationPurchaseAgreementLineEntity | CLMIntegrationValidationPurchaseAgreementLines | Yes | CLM -\> Supply Chain Management |

> [!NOTE]
> The entity CLMIntegrationValidationPurchaseAgreementHeaderEntity can only perform validation for update operation, whereas CLMIntegrationValidationPurchaseAgreementLineEntity can handle validation for insert, update, and delete operations.

## Create shareable, secured deep links

The following APIs create shareable and secured URLs (also known as deep links) to specific forms within Supply Chain Management, such as vendor form, contract form or purchase agreement form. These APIs enable scenarios such as embedding links directly in external Contract Lifecycle Management system, enabling users to quickly and easily locate the specified forms and records by simply navigating using the generated link. For more information about deep links, see [Create shareable, secured URLs (deep links)](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/user-interface/create-deep-links).

### Generate deep link for a vendor

This API generates a deep link to open the form for a specific vendor within Supply Chain Management.

**Request**

```http
POST https://[baseURI]/data/VendorsV2/Microsoft.Dynamics.DataEntities.GenerateVendorDetailFormURL
```
```json
{
    "_vendAccount": "1001",
    "_companyId": "USMF"
}
```

**Response**

```json
{
    "@odata.context": "https://[baseURI]/data/$metadata#Edm.String",
    "value": "https://[baseURI]/?cmp=usmf&prt=initial&mi=display:VendTable&pageType=Details&q=[queryValue]"
}
```

### Generate deep link for a contract by contract ID

This API generates a deep link to open the form for a specific contract within Supply Chain Management.

**Request**

```http
POST https://[baseURI]/data/CLMIntegrationContracts/Microsoft.Dynamics.DataEntities.GenerateContractDetailFormURLByContractId
```
```json
{
    "_contractId": "C00001",
    "_companyId": "USMF"
}
```

**Response**

```json
{
    "@odata.context": "https://[baseURI]/data/$metadata#Edm.String",
    "value": "https://[baseURI]/?cmp=usmf&prt=initial&mi=display:CLMIntegrationContractTable&pageType=Details&q=[queryValue]"
}
```

### Generate deep link for a contract by contract external ID

This API generates a deep link to open the form for a specific contract within Supply Chain Management.

**Request**

```http
POST https://[baseURI]/data/CLMIntegrationContracts/Microsoft.Dynamics.DataEntities.GenerateContractDetailFormURLByExternalContractId
```
```json
{
    "_externalContractId": "EXTC00001",
    "_companyId": "USMF"
}
```

**Response**

```json
{
    "@odata.context": "https://[baseURI]/data/$metadata#Edm.String",
    "value": "https://[baseURI]/?cmp=usmf&prt=initial&mi=display:CLMIntegrationContractTable&pageType=Details&q=[queryValue]"
}
```

### Generate deep link for a purchase agreement by agreement ID

This API generates a deep link to open the form for a specific purchase agreement within Supply Chain Management.

**Request**

```http
POST https://[baseURI]/data/CLMIntegrationPurchaseAgreements/Microsoft.Dynamics.DataEntities.GenerateAgreementFormURLByAgreementId
```
```json
{
    "_agreementId": "000026",
    "_companyId": "USMF"
}
```

**Response**

```json
{
    "@odata.context": "https://[baseURI]/data/$metadata#Edm.String",
    "value": "https://[baseURI]/?cmp=usmf&prt=initial&mi=display:PurchAgreementDetails&pageType=Details&q=[queryValue]"
}
```

### Generate deep link for a purchase agreement by agreement external ID

This API generates a deep link to open the form for a specific purchase agreement within Supply Chain Management.

**Request**

```http
POST https://[baseURI]/data/CLMIntegrationPurchaseAgreements/Microsoft.Dynamics.DataEntities.GenerateAgreementFormURLByExternalContractId
```

```json
{
    "_externalContractId": "EXT000026",
    "_companyId": "USMF"
}
```

**Response**

```json
{
    "@odata.context": "https://[baseURI]/data/$metadata#Edm.String",
    "value": "https://[baseURI]/?cmp=usmf&prt=initial&mi=display:PurchAgreementDetails&pageType=Details&q=[queryValue]"
}
```
