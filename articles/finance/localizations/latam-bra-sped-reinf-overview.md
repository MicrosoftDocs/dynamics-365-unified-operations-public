---
title: SPED-Reinf (Brazil)
description: This article provides information about how you can use Fiscal books and the electronic message framework to set up SPED-Reinf events.
author: AdamTrukawka
ms.date: 08/09/2023
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Brazil
ms.author: atrukawk
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: 8.1
ms.search.form: 
---

# SPED-Reinf (Brazil) 

[!include [banner](../includes/banner.md)]

The SPED-Reinf is a tax statement report that gathers information about withholding tax and other tax information from the Brazilian Internal Revenue Service (RFB) and Social Security. In Brazilian Portuguese, the abbreviation *Reinf* stands for "retenções e outras informações fiscais," or "withholdings and other tax information." The SPED-Reinf was created to assess federal taxes that are withheld for the purpose of Social Security and income taxes, and for activities that aren't related to labor. Examples of these activities include fiscal documents and payments.  

The statement consists of a set of events. These events must be delivered in specific layouts through the public digital bookkeeping system (SPED), and a valid digital certificate must be used to deliver them. This certificate must be issued by an entity that has been accredited by the Brazilian Public Key Infrastructure (ICP-Brasil).

The statement is considered valid after receipt is confirmed and the contents of the files are validated.

Microsoft Dynamics 365 Finance supports the generation of SPED-Reinf events through the **Fiscal books** module and the Immediate Provision of Information (SII) reporting register framework. You can exchange XML messages for every event that the tax authority requires.

## Support scope

- **Supported SPED-REINF versions:** 1.4, 1.5.1, and 2.1.2. (Version 2.1.2 is supported only in Dynamics 365.)
- **Supported product versions:** Dynamics 365 Finance.
- Electronic power of attorney (procuração eletronica) isn't supported.

## Table of events

| Event  | Description                                                       | Event type                 | Supported |
|--------|-------------------------------------------------------------------|----------------------------|-----------|
| R-1000 | Taxpayer information                                              | Initial                    | Yes       |
| R-1050 | Table of linked entities                                          | When a process is in place | Yes       |
| R-1070 | Administrative and Judicial process                               | When a process is in place | Yes       |
| R-2010 | Acquired services                                                 | Periodic event             | Yes       |
| R-2020 | Provided services                                                 | Periodic event             | Yes       |
| R-2030 | Amounts received by sport associations                            | Periodic event             | No        |
| R-2040 | Amounts paid to sport associations                                | Periodic event             | No        |
| R-2050 | Trade of rural production by rural legal entities or agribusiness | Periodic event             | No        |
| R-2055 | Acquisition from agriculture vendor                               | Periodic event             | Yes       |
| R-2060 | INSS-CPRB assessment                                              | Periodic event             | Yes       |
| R-2098 | Reopening of periodic                                             | Periodic event             | Yes       |
| R-2099 | Closing                                                           | Periodic event             | Yes       |
| R-4010 | Payments/credits to individual beneficiaries                      | Periodic event             | Yes       |
| R-4020 | Payment/credits and legal entity beneficiary                      | Periodic event             | Yes       |
| R-4040 | Payment/credit to unidentified beneficiaries                      | Periodic event             | Yes       |
| R-4080 | Withholding on Receipt: Known as auto-withhold                    | Periodic event             | Yes       |
| R-4099 | Closing/Reopening of periodic events series R-4000                | Periodic event             | Yes       |
| R-3010 | Sport shows revenue                                               | Non-periodic event         | No        |
| R-5001 | Consolidated tax calculation basis by taxpayer                    | Non-periodic event         | No        |
| R-5011 | Consolidated base and tax amount                                  | Non-periodic event         | No        |
| R-9000 | Deletion                                                          | Non-periodic event         | Yes       |
| R-9005 | Bases and taxes, withholdings                                     | Non-periodic event         | No        |
| R-9015 | Consolidation of withholdings                                     | Non-periodic event         | Yes       |

> [!NOTE]
> Events R-2010 and R-2020 are supported for National Registry of Legal Entities (CNPJ) third parties. Event R-5011 is used to inquire about the status of closing event R-2099.
> Events R-9005 and R-9015 are considered the totalizers and aren't delivered by taxpayers. Instead, they are delivered by the Federal Revenue as the return of the bases to the taxpayers.

Only taxpayers that comply with SPED-ECD are supported.

- Taxpayers as public departments aren't supported.
- Services that are provided on civil constructions projects aren't supported.
- Service takers on civil constructions projects aren't supported.
- Manual bookkeeping is required for the payment for settlement of the Social Security contribution on gross revenue (CPRB) amount that is due.
- Payment of the CPRB amount that is due is out of scope.

To generate events for R-4000 records, the following parameters are required for the related registrations:

- Individual Supplier Registration
- Legal Entity Registration
- Unidentified Beneficiary
- Purchase Order Receipts 
- General ledger with emphasis on Income Tax (IRRF)
- Service item registration with the **Income code** field

For each event, the Brazilian tax authority provides a specific table that contains the Income Nature Codes. In this case, the client must analyze which code best fits each event.

1. [Set up electronic message functionality](latam-bra-sped-reinf-electronic-messages.md). 
2. [Set up fiscal books](latam-bra-sped-reinf-setup-fiscal-books.md).
3. [Process and submit the events](latam-bra-sped-reinf.md).
