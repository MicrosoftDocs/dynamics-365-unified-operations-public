---
# required metadata

title: Fiscal document text placeholders for Brazil
description: Fiscal document text placeholders are predefined tags that represent specific values. You can include the placeholders in the <strong>Text </strong>field on the <strong>Fiscal document source texts </strong>page when you create a fiscal document source text.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 101
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 268684
ms.assetid: b949485b-6f02-4f4b-9599-d35864c4b574
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Fiscal document text placeholders for Brazil

[!include[banner](../includes/banner.md)]


Fiscal document text placeholders are predefined tags that represent specific values. You can include the placeholders in the <strong>Text </strong>field on the <strong>Fiscal document source texts </strong>page when you create a fiscal document source text.

You can also include placeholders in the **Note** field on the **Fiscal document texts** page when you attach a fiscal document text to a sales order, purchase order, or free text invoice. When you post a sales order, purchase order, or free text invoice that has a fiscal document text that includes placeholders, the placeholders are replaced by the values in the predefined tags.

The following tables contain the predefined tags that support fiscal document text and its value.
Tags that support fiscal document text for referenced processes
---------------------------------------------------------------

| Predefined tag                  | Value                                 |
|---------------------------------|---------------------------------------|
| %RefProcess\_TaxAuthorityName   | The name of the tax authority.        |
| %RefProcess\_TaxAuthorityAgency | The agency of the tax authority.      |
| %RefProcess\_RefProcessNumber   | The number of the referenced process. |

## Tag that supports fiscal document text for SUFRAMA
| Predefined tag       | Value                        |
|----------------------|------------------------------|
| %Suframa\_CustNumber | The SUFRAMA customer number. |

## Tags that support fiscal document text for taxes
| Predefined tag | Value                                                                                    |
|----------------|------------------------------------------------------------------------------------------|
| %ICMS          | The Imposto Sobre Circulação de Mercadorias e Serviços (ICMS) tax amount.                |
| %PIS           | The Programa de Integração Social (PIS) contribution amount.                             |
| %COFINS        | The Contribuição para o financiamente da securidade social (COFINS) contribution amount. |

## Tags that support fiscal document text for fiscal references
| Predefined tag                  | Value                                                                                                               |
|---------------------------------|---------------------------------------------------------------------------------------------------------------------|
| %FiscalRef\_InvNoRef            | The number of the reference invoice.                                                                                |
| %FiscalRef\_InvSeriesRef        | The series of the reference invoice.                                                                                |
| %FiscalRef\_InvDateRef          | The date of the reference invoice.                                                                                  |
| %FiscalRef\_InvAccNameRef       | The account name of the reference invoice.                                                                          |
| %FiscalRef\_InvAccAddressRef    | The address of the reference invoice.                                                                               |
| %FiscalRef\_InvAccIENumberRef   | The Inscrição Estadual (IE), or state registration number, of the reference invoice account.                        |
| %FiscalRef\_InvAccCNPJCPFNumRef | The Cadastro Nacional da Pessoa Jurídica (CNPJ), or taxpayer registration number, of the reference invoice account. |

## Tags that support fiscal document text that involve vendor information
| Predefined tag     | Value                                                                                                                              |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------|
| %Vendor\_Name      | The name of the vendor.                                                                                                            |
| %Vendor\_CNPJ\_CPF | The Cadastro Nacional da Pessoa Jurídica (CNPJ)/Cadastro de Pessoas Físicas (CPF), or taxpayer registration number, of the vendor. |
| %Vendor\_IE        | The IE of the vendor.                                                                                                              |
| %Vendor\_Address   | The address of the vendor.                                                                                                         |

## Tags that support fiscal document text that involve customer information
| Predefined tag       | Value                         |
|----------------------|-------------------------------|
| %Customer\_Name      | The name of the customer.     |
| %Customer\_CNPJ\_CPF | The CNPJ/CPF of the customer. |
| %Vendor\_IE          | The IE of the customer.       |
| %Vendor\_Address     | The address of the customer.  |

## Tags that support fiscal document text for withholding taxes
| Predefined tag       | Value                          |
|----------------------|--------------------------------|
| %TaxWithhold\_Code   | The withholding tax code.      |
| %TaxWithhold\_Value  | The rate of withholding tax.   |
| %TaxWithhold\_Amount | The amount of withholding tax. |

## Tags that support fiscal document text for imports
| Predefined tag | Value                                                                    |
|----------------|--------------------------------------------------------------------------|
| %DI\_Number    | The identifier of the import declaration document.                       |
| %DI\_Date      | The date that the import declaration document was issued.                |
| %ImportTax     | The import tax amount.                                                   |
| %Freight       | The freight amount for the import.                                       |
| %Insurance     | The insurance amount for the import.                                     |
| %Siscomex      | The charge amount for Sistema Integrado de Comércio Exterior (Siscomex). |
| %ExchRate      | The exchange rate that is used in the import.                            |

## Tags for ICMSDIF final consumer
| Predefined tag           | Value                                                                          |
|--------------------------|--------------------------------------------------------------------------------|
| %DifICMS\_vBCUFDest      | Tax base amount used for tax type ICMS-DIF.                                    |
| %DifICMS\_pICMSUFDest    | Tax value for recipient federal state.                                         |
| %DifICMS\_pICMSInter     | Tax value for interstate transaction.                                          |
| %DifICMS\_pICMSInterPart | Percentage defined to recipient federal state (based on fiscal document year). |
| %DifICMS\_vICMSUFDest    | Tax amount for recipient state.                                                |
| %DifICMS\_vICMSUFRemet   | Tax amount for issuer state.                                                   |





