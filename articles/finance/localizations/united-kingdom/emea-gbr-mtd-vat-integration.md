---
title: Making Tax Digital – VAT return submission in the United Kingdom
description: Learn how to set up and use the Making Tax Digital for VAT (MTD VAT) feature for VAT return submission in the United Kingdom.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 12/05/2024
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Making Tax Digital – VAT return submission in the United Kingdom

[!include [banner](../../includes/banner.md)]

This article explains how to set up the Making Tax Digital for VAT (MTD VAT) feature in Microsoft Dynamics 365 Finance and use it to submit a VAT return in the United Kingdom (UK).

On July 13, 2017, the Financial Secretary to the Treasury and Paymaster General in the UK announced that MTD for VAT would take effect on April 1, 2019.

MTD introduces an obligation for VAT-registered businesses to keep their records digitally (for VAT purposes only) and to provide VAT return information to Her Majesty's Revenue and Customs (HMRC) through software that is functionally compatible with MTD. As of April 1, 2019, MTD for VAT is mandatory for businesses that have turnover that exceeds the VAT registration threshold (currently £85,000). For VAT-registered businesses that have turnover that is below the VAT registration threshold, MTD for VAT will remain voluntary.

VAT returns must be submitted to HMRC by using software that is compatible with MTD. VAT returns can no longer be submitted by using the HMRC portal. Software that is compatible with MTD must support the following requirements:

- The required records are stored in digital form.
- The required records are preserved in digital form for up to six years.
- A VAT return can be created from the digital records that are held in functionally compatible software, and this information can be digitally provided to HMRC.
- The company can provide VAT data to HMRC on a voluntary basis.
- The MTD for VAT application programming interface (API) platform can be used to receive information from HMRC about a relevant entity's compliance with obligations under the regulations.

In the UK, VAT returns are filed quarterly or monthly. The deadline for submitting a VAT return online and paying HMRC is one calendar month plus seven days after the end of the VAT period.

As HMRC states on the official website, the current amendment process will stay in place for VAT:

- If the net value of the errors on the VAT return is less than £10,000, the company will amend those errors on the next VAT return.
- If the net value of the errors exceeds £10,000, the company must complete the VAT 652 form, which is available on the Gov.UK website.

For more information about MTD for VAT, see [Making Tax Digital for VAT: legislation overview](https://www.gov.uk/government/consultations/making-tax-digital-reforms-affecting-businesses/making-tax-digital-for-vat-legislation-overview).

As HMRC mentions in the Making Tax Digital for Business VAT Guide for Vendors, users must sign up for the MTD service for VAT, even if they have already signed up to use the MTD service for income tax. For more information about how to get ready for MTD, see [Making Tax Digital: how VAT businesses and other VAT entities can get ready](https://www.gov.uk/government/publications/making-tax-digital-how-vat-businesses-and-other-vat-entities-can-get-ready).

The solution that supports the [MTD for VAT requirements](https://developer.service.hmrc.gov.uk/api-documentation/docs/api/service/vat-api/1.0) is based on the [Electronic messages](../../general-ledger/electronic-messaging.md) functionality. This functionality provides a flexible approach for setting up and supporting reporting processes. The setup package for MTD VAT feature covers the following scope of interoperation to help companies in the UK meet their MTD obligations:

- **Retrieve VAT obligations (Mandatory):** Users can initiate a request to HMRC to obtain VAT obligations for a specific period. In response to each user's request, HMRC posts information about the company's VAT obligations that is defined in the company's profile on the HMRC side. VAT obligations contain information about the VAT period, the due date for submission, and the status of the obligation. Finance reflects this information.
- **Submit VAT return for period (Mandatory):** The system collects information about VAT returns. The information that is collected is based on the sales tax payment transactions that are posted in the system by using the sales tax settlement process, with respect to the VAT obligations that are registered in the system. After this information is collected, a VAT return report in JavaScript Object Notation (JSON) format is generated. The user submits this report to HMRC. Finance reflects the HMRC response to the submission.
- **Retrieve VAT liabilities (Optional):** Users can initiate a request to HMRC to obtain their company's VAT liabilities for a specific period. In response to each user's request, HMRC posts information about the company's VAT liabilities that is defined in the company's profile on the HMRC side. This information is stored in Finance as an attachment of the related electronic message. This attachment is in JSON format.
- **Retrieve VAT payments (Optional):** Users can initiate a request to HMRC to obtain their company's VAT payments for a specific period. In response to each user's request, HMRC posts information about the company's VAT payments that is defined in the company's profile on the HMRC side. This information is stored in Finance as an attachment of the related electronic message. This attachment is in JSON format.

The setup package for MTD VAT feature doesn't cover the View VAT Return endpoint that might be required. However, the Electronic messages functionality lets you set up and support this endpoint.

The MTD VAT feature in Finance supports filing a VAT return for [Multiple VAT registrations](../global/emea-multiple-vat-registration-numbers.md) and for companies that report as a [VAT group](https://www.gov.uk/hmrc-internal-manuals/vat-groups) in the same system database.

> [!NOTE]
> To meet security requirements, we are implementing modifications to the Dynamics 365 Finance direct system-to-system integration with the HMRC web service for submitting VAT returns for companies registered for VAT in the UK. This enhancement involves the adoption of an Electronic Invoicing service as an intermediary that facilitates secure access to the storage of credentials essential for software authorization within the HMRC APIs. **These services won’t be accessible from on-premises deployments by June 6, 2025**.
>
> By June 6, 2025, we plan to no longer support **batch mode for submission** of VAT return in the **Making Tax Digital** feature. It’s still possible to generate in batch the report (VAT 100) in Excel and JSON formats.

## <a name="privacy-notice"></a>Privacy notice

When you enable Finance to interoperate with HMRC's MTD for VAT API, both customer content and personal data will be shared with HMRC as part of the submission of VAT information to the MTD for VAT report. This information might include location information and other personal identifiers, such as IP addresses. To learn more about the kinds of information that is included in your submission, you can view HMRC's requirements on the [HMRC website](https://go.microsoft.com/fwlink/?linkid=2099326). A system administrator can disable the interoperation with HMRC's web service in Finance by going to **Tax \> Setup \> Electronic Messages**. 

Your privacy is important to us. To learn more, read our [Privacy and Cookies notice](https://go.microsoft.com/fwlink/?LinkId=521839).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
