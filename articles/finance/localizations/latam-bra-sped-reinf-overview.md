---
# required metadata

title: SPED-Reinf (Brazil)
description: This topic provides information about how you can use Fiscal books and the electronic message framework to set up SPED-Reinf events.
author: sndray
ms.date: 04/09/2021
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 

# ms.assetid: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: 8.1

---

# SPED-Reinf (Brazil) 

[!include [banner](../includes/banner.md)]

The SPED-Reinf is a tax statement report that gathers information about withholding tax and other tax information from the Brazilian Internal Revenue Service (RFB) and Social Security. In Brazilian Portuguese, the abbreviation *Reinf* stands for "retenções e outras informações fiscais," or "withholdings and other tax information." The SPED-Reinf was created to assess federal taxes that are withheld for the purpose of Social Security and income taxes, and for activities that aren't related to labor. Examples of these activities include fiscal documents and payments.  

The statement consists of a set of events. These events must be delivered in specific layouts through the public digital bookkeeping system (SPED), and a valid digital certificate must be used to deliver them. This certificate must be issued by an entity that has been accredited by the Brazilian Public Key Infrastructure (ICP-Brasil).

The statement is considered valid after receipt is confirmed and the contents of the files are validated.

Microsoft Dynamics 365 Finance supports the generation of SPED-Reinf events through the **Fiscal books** module and the Immediate Provision of Information (SII) reporting register framework. You can exchange XML messages for every event that the tax authority requires.

## Support scope

- **Supported SPED-Reinf versions:** 1.4 and 1.5.1.
- **Supported product versions:** Microsoft Dynamics AX 2012 R3 and Dynamics 365 Finance.
- Electronic power of attorney (procuração eletronica) isn't supported.

## Table of events

| Event | Description | Event type | Supported |
|---|---|---|---|
| R-1000 | Taxpayer information | Initial | Yes |
| R-1070 | Administrative and Judicial process | When a process is in place | Yes |
| R-2010 | Acquired services | Periodic event | Yes |
| R-2020 | Provided services | Periodic event | Yes |
| R-2030 | Amounts received by sport associations | Periodic event | No |
| R-2040 | Amounts paid to sport associations | Periodic event | No |
| R-2050 | Trade of rural production by rural legal entities or agribusiness | Periodic event | No |
| R-2055 | Acquisition from agriculture vendor | Periodic event | Yes |
| R-2060 | INSS-CPRB assessment | Periodic event | Yes |
| R-2098 | Reopening of periodic | Periodic event | Yes |
| R-2099 | Closing | Periodic event | Yes |
| R-3010 | Sport shows revenue | Non-periodic event | No |
| R-5001 | Consolidated tax calculation basis by taxpayer | Non-periodic event | No |
| R-5011 | Consolidated base and tax amount | Non-periodic event | Yes |
| R-9000 | Deletion | Non-periodic event | Yes |

> [!NOTE]
> Events R-2010 and R-2020 are supported for National Registry of Legal Entities (CNPJ) third parties. Event R-5011 is used to inquire about the status of closing event R-2099.

Only taxpayers that comply with SPED-ECD are supported.

- Taxpayers as public departments aren't supported.
- Services that are provided on civil constructions projects aren't supported.
- Service takers on civil constructions projects aren't supported.
- Manual bookkeeping is required for the payment for settlement of the Social Security contribution on gross revenue (CPRB) amount that is due.
- Payment of the CPRB amount that is due is out of scope.

To generate and submit the related events to the tax authority, follow these steps.

1. [Set up electronic message functionality](latam-bra-sped-reinf-electronic-messages.md). 
2. [Set up fiscal books](latam-bra-sped-reinf-setup-fiscal-books.md).
3. [Process and submit the events](latam-bra-sped-reinf.md).
