---
# required metadata

title: SPED-Reinf (Brazil)
description: This topic provides information about setting up SPED-Reinf events using Fiscal books and the electronic message framework in Microsoft Dynamics 365 Finance for Brazil.
author: sndray
manager: AnnBe
ms.date: 01/19/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: 8.1

---

# SPED-Reinf overview (Brazil)

[!include [banner](../includes/banner.md)]


The SPED-Reinf is a new tax statement report that gathers information about withholding tax and other tax information that is of interest from the Brazilian Internal Revenue Service (RFB) and Social Security. (In Brazilian Portuguese, Reinf stands for "Retenções e Outras Informações Fiscais.") The statement consists of a set of events that must be delivered, in specific layouts, through
the environment of the public digital bookkeeping system (SPED). Additionally, they must be delivered by using a valid digital certificate that is issued by an entity that is accredited by the Brazilian Public Key Infrastructure (ICP-Brasil). The statement will be considered valid after receipt is confirmed and the contents of the files are validated.

The SPED-Reinf was created to assess federal taxes that are withheld, for Social Security and income taxes purposes, for activities that aren't related to labor. Examples of these activities include fiscal documents, payments, and other events.

Microsoft Dynamics supports the generation of SPED-Reinf events through the **Fiscal books** module and the SII reporting register framework. Users can exchange XML messages for every event that is required by the tax authority.

**Scope**

-   Supported SPED-Reinf version: 1.4 and 1.5.1

-   Supported versions: Microsoft Dynamics AX 2012 R3 and Microsoft Dynamics 365
    for Finance and Operations.

-   Electronic power of attorney (procuração eletronica) isn't supported.

**Table of events**

| Event | Description | Event type | Supported |
|-|-|-|-|
| R-1000     | Taxpayer information | Initial | **Yes** |
| R-1070     | Administrative and Judicial process | When a process is in place | **Yes** |
| R-2010     | Acquired services | Periodic event | **Yes** |
| R-2020     | Provided services | Periodic event | **Yes** |
| R-2030     | Amounts received by sport associations | Periodic event | **No** |
| R-2040     | Amounts paid to sport associations | Periodic event | **No** |
| R-2050     | Trade of rural production by rural legal entities or agribusiness | Periodic event | **No** |
| R-2055     | Acquisition from agriculture vendor | Periodic event | **Yes** |
| R-2060     | INSS-CPRB assessment | Periodic event | **Yes** |
| R-2098     | Reopening of periodic | Periodic event | **Yes** |
| R-2099     | Closing | Periodic event | **Yes** |
| R-3010     | Sport shows revenue | Non-periodic event | **No** |
| R-5001     | Consolidated tax calculation basis by taxpayer | Non-periodic event | **No** |
| R-5011     | Consolidated base and tax amount | Non-periodic event | **Yes** |
| R-9000     | Deletion | Non-periodic event | **Yes** |

> [!NOTE]
> Events R-2010 and R-2020 are supported for CNPJ third parties. Event R-5011 is used is used to inquire about the status of closing event R-2099.*


-   Only taxpayers that comply with SPED-ECD are supported.

-   No support for taxpayers as public departments.

-   No support for services that are provided on civil constructions projects.

-   No support for service takers on civil constructions projects.

-   Manual bookkeeping of the payment for settlement of the CPRB amount that is due.

-   Payment of the CPRB amount that is due are out of scope.

In order to generate and submit the related events to tax authority you'll need to follow these steps

1. [Set up electronic message functionality](latam-bra-sped-reinf-electronic-messages.md). 
2. [Set up fiscal books](latam-bra-sped-reinf-setup-fiscal-books.md)
3. [Process and submit the events](latam-bra-sped-reinf-process.md)




