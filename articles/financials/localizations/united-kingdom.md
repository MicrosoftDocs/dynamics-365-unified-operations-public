---
# required metadata

title: United Kingdom
description: This topic provides links to Microsoft Dynamics 365 for Finance and Operations documentation resources for the United Kingdom. 
author: ShylaThompson
manager: AnnBe
ms.date: 07/17/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: United Kingdom
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# United Kingdom 

[!include [banner](../includes/banner.md)]

This topic provides links to documentation resources for United Kingdom. 

- [Construction Industry Scheme](emea-gbr-cis-construction-industry-scheme.md)
- [Create a credit on the settlement discount](tasks/gb-00009-credit-note-settlement-discount.md)
- [Create a purchase order that includes items subject to reverse charge VAT](tasks/purchase-order-reverse-charge-vat.md)
- [Create a sales order that includes items subject to reverse charge VAT](tasks/gb-00002-sales-order.md)
- [Set up item sales tax groups for reverse charge VAT](tasks/gb-00002-item-sales-tax-groups-reverse-charge-vat.md)
- [Set up reverse charge VAT item groups, rules, and parameters](tasks/gb-00002-reverse-charge-vat-item-groups.md)
- [Set up sales tax groups for reverse charge VAT](tasks/gb-00002-sales-tax-groups-reverse-charge-vat.md)

## Regulatory updates for the United Kingdom

For a complete list of regulatory updates for all countries/regions, see [Regulatory updates](regulatory-updates.md).

### Making Tax Digital - VAT Statement submission 

On July 13, 2017, the Financial Secretary to the Treasury and Paymaster General in the United Kingdom announced that Making Tax Digital (MTD) for value-added tax (VAT) will take effect on April 1, 2019. 

MTD introduces an obligation for VAT-registered businesses to keep their records digitally (for VAT purposes only) and to provide VAT return information to Her Majesty’s Revenue and Customs (HMRC) through software that is functionally compatible with MTD. Starting April 1, 2019, MTD for VAT will be mandatory for businesses that have turnover which exceeds the VAT registration threshold (currently £85,000). It will remain voluntary for VAT-registered businesses below the VAT threshold until 2020 at the earliest. 
VAT returns will have to be submitted to HMRC using software that is compatible with MTD. VAT returns can no longer be submitted by the former method using the HMRC portal. 

VAT returns are filed quarterly or monthly in the UK. The deadline for submitting the return online and paying HMRC is one calendar month and seven days after the end of the VAT period. 

As HMRC states on the official website, the current amendment process will stay in place for VAT: 
- If the net value of the errors on the VAT return is less than £10,000, the company will amend them in the next VAT return. 
- If the net value of the errors exceeds £10,000, the company must complete the VAT 652 form, which is available on the GOV.UK website. 
For more information about MTD for VAT, see Making Tax Digital for VAT: legislation overview.

Software that is compatible with MTD must support the following requirements: 
- Keep the required records in a digital form. 
- Preserve those records in digital form for up to 6 years. 
- Create a VAT return from the digital records that are held in functionally compatible software, and digitally provide this information to HMRC. 
- Provide VAT data to HMRC on a voluntary basis. 
- Receive, via the MTD for VAT application programming interface (API) platform, information from HMRC about a relevant entity’s compliance with obligations under the regulations. 
As HMRC mentions in Making Tax Digital for Business VAT Guide for Vendors, users must sign up for the MTD service for VAT, even if they have already signed up to use the MTD service for income tax. For more information about how to get ready for MTD, see Making Tax Digital: how VAT businesses and other VAT entities can get ready.

To support the MTD for VAT requirements in Dynamics 365 for Finance and Operations the solution is based on Electronic messages functionality which provides a flexible approach of setting up and supporting of reporting processes. The setup package for the UK MTD for VAT covers the mandatory scope of interoperation to let companies in the UK fulfill their VAT obligations:
- **Retrieve VAT obligations**: Users can initiate a request to HMRC to obtain their company’s VAT obligations for a specific period. HMRC will post, as a response to each user’s request, information about the company’s VAT obligations that is defined in the company’s profile on the HMRC side. VAT obligations contain information about the VAT period, the due date for submission, and the status of the obligation. This information will be reflected in Dynamics 365 for Finance and Operations. 
- **Submit VAT return for period**: The system will collect information about VAT returns. The information collected is based on the Sales tax payment transactions that have been posted in the system via the sales tax settlement process, with respect to the VAT obligations that are registered in the system. After this information is collected a VAT return report in JavaScript Object Notation (JSON) file generated, user will submit the report to HMRC. The HMRC response to the submission will be reflected in Dynamics 365 for Finance and Operations. 
The setup package for the UK MTD for VAT also covers the following endpoints of optionally required scope of interoperation:
- **Retrieve VAT liabilities**: Users can initiate a request to HMRC to obtain their company’s VAT liabilities for a specific period. HMRC will post, as a response to each user’s request, information about the company’s VAT liabilities that is defined in the company’s profile on the HMRC side. This information will be stored in Dynamics 365 for Finance and Operations as an attachment in JSON format to the related electronic message.
- **Retrieve VAT payments**: Users can initiate a request to HMRC to obtain their company’s VAT payments for a specific period. HMRC will post, as a response to each user’s request, information about the company’s VAT payments that is defined in the company’s profile on the HMRC side. This information will be stored in Dynamics 365 for Finance and Operations as an attachment in JSON format to the related electronic message.
The setup package for the UK MTD for VAT will not cover the optionally required “View VAT Return” endpoint. Electronic messages functionality allows to set up and support this endpoint.

For more information, see [Prepare Finance and Operations for integration with MTD for VAT](emea-gbr-mtd-vat-integration.md). 
