---
# required metadata

title: Referenced fiscal documents for Brazil
description: This topic provides an overview of referenced fiscal documents that are used in Brazil.
author: sndray
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: FiscalDocument_BR, SalesEditLines, TmpFiscalReference_BR
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 270224

ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Referenced fiscal documents for Brazil

[!include[banner](../includes/banner.md)]


This topic provides an overview of referenced fiscal documents that are used in Brazil.

In some scenarios, a fiscal document must include another fiscal document's information. You can attach the information for a referenced fiscal document in two ways:

-   **Manual** – Register related information when the fiscal document isn't available. All information is required, and validation makes sure that the information fulfills the fiscal requirements.
-   **Automatic** – Select an available fiscal document.

### Examples

-   If you try to reference a fiscal document that isn't in Microsoft Dynamics 365 for Operations, all the fiscal document information must be entered.
-   When you return an item to a vendor or receive a return from a customer, a reference to the original document is added.
-   Enter a manual fiscal document, model 01, in the system. You will create a fiscal document that references the original fiscal document.
-   Enter a Sales Order for Retail Sales or NF-e (model 55). The fiscal document will reference the original retail document and fiscal printer.
-   Create a sales order, and post the invoice. Then create a return order that references the previous order. The return fiscal document will create a fiscal document that references the original fiscal document.

## Manual
When a fiscal document isn't available, you can attach customer or vendor fiscal documents as fiscal references to a fiscal document. You can also view the fiscal references that are attached to a posted fiscal document.

### Fiscal reference

| Field          | Description                                                                                                                                                                                                                                             |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Document model | The document model for the fiscal document. If the **Is for NF-e (federal)** option is selected for the document model on the **Document model** page, the **Access key** field is available, and the **Number** and **Series** fields are unavailable. |
| Access key     | The access key for the electronic fiscal document (NF-e).                                                                                                                                                                                               |
| Number         | The identification number of the fiscal document.                                                                                                                                                                                                       |
| Series         | The series number of the fiscal document.                                                                                                                                                                                                               |
| Date           | The document date of the fiscal document.                                                                                                                                                                                                               |
| Direction      | Select whether the fiscal document is related to incoming or outgoing products or services.                                                                                                                                                             |
| Issuer         | Select whether the fiscal document was issued by the fiscal establishment or a third party.                                                                                                                                                             |
| Account type   | Select **Customer**, **Vendor**, or **Fiscal establishment** as the type of account.                                                                                                                                                                    |
| Account        | Select the customer account, vendor account, or fiscal establishment that generated the fiscal document.                                                                                                                                                |
| Text ID        | Select the fiscal document source text for the referenced fiscal document.                                                                                                                                                                              |

## Automatic
Use the **Fiscal reference** button to attach existing customer, vendor, or transfer fiscal documents as fiscal references to a fiscal document. You can reference only posted fiscal documents that are issued or received by the same fiscal establishment that issues or receives the fiscal document that will be posted. You can view the fiscal references that are attached to a posted fiscal document.

### Fiscal document

| Field         | Description                                                                                                                                                           |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Number        | The fiscal document number of the customer, vendor, or transfer fiscal document.                                                                                      |
| Series        | The series number of the customer, vendor, or transfer fiscal document.                                                                                               |
| Document date | The date when the customer, vendor, or transfer fiscal document was issued.                                                                                           |
| Account       | The identification number of the customer, vendor, or fiscal establishment.                                                                                           |
| Account type  | The type of account. The options are **Customer**, **Vendor**, or **Fiscal establishment**.                                                                           |
| Name          | The name of the customer, vendor, or fiscal establishment.                                                                                                            |
| CNPJ/CPF      | The taxpayer registration number, or Cadastro Nacional da Pessoa Jurídica (CNPJ)/Cadastro de Pessoas Físicas (CPF), of the customer, vendor, or fiscal establishment. |
| IE            | The state registration number, or Inscrição Estadual (IE), of the customer, vendor, or fiscal establishment.                                                          |

### Fiscal reference placeholders

Fiscal document text placeholders are predefined tags that represent specific values. When you create a fiscal document source text on the **Fiscal document source texts** page, you can include placeholders in the **Text ID** field. You can also include placeholders in the **Note** field when you attach a fiscal document text to a sales order, purchase order, or free text invoice. When you post a sales order, purchase order, or free text invoice that has a fiscal document text that includes placeholders, the placeholders are replaced by the values in the predefined tags. The following table describes the predefined tags that support fiscal document texts for fiscal references.

| Tag                                   | Description                                                                   |
|---------------------------------------|-------------------------------------------------------------------------------|
| %FiscalRef\_InvNoRef                  | The number of the reference invoice.                                          |
| %FiscalRef\_InvSeriesRef              | The series number of the reference invoice.                                   |
| %FiscalRef\_InvDateRef                | The date of the reference invoice.                                            |
| %FiscalRef\_InvAccNameRef             | The account name for the reference invoice.                                   |
| %FiscalRef\_InvAccAddressRef          | The address for the reference invoice.                                        |
| %FiscalRef\_InvAccIENumberRef         | The state registration number (IE) of the reference invoice account.          |
| %FiscalRef\_InvAccCNPJCPFNumRef       | The taxpayer registration number (CNPJ/CPF) of the reference invoice account. |
| %FiscalRef\_FiscalPrinterSerialNumber | The serial number of the fiscal printer.                                      |
| %FiscalRef\_ECFNumber                 | The fiscal printer number in the retail store.                                |





