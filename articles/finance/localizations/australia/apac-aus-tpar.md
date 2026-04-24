---
title: Taxable Payments Annual Report
description: Learn how to set up and generate the Taxable Payments Annual Report (TPAR), including outlines on configuration and how to prepare a TPAR.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 03/02/2026
ms.reviewer: johnmichalak
ms.search.region: APAC
ms.search.validFrom: 2023-08-10
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Taxable Payments Annual Report

This article explains how to set up and generate the Taxable Payments Annual Report (TPAR) that's required by the Australian Taxation Office (ATO).

Some businesses and government entities in Australia must provide a TPAR to the ATO by August 28 each year. The purpose of a TPAR is to report payments that are made to contractors or subcontractors for specific services, such as building and construction, cleaning, courier, road freight, IT, security, investigation, and surveillance services. The ATO uses the information on a TPAR to identify contractors who didn't meet their tax obligations because, for example, they didn't report all their income or register for goods and services tax (GST). A TPAR also helps contractors verify the income that they report on their tax returns.

A TPAR provides information about the total amount that's paid to a contractor, including any GST. It also provides details such as the contractor's name, Australian Business Number (ABN), address, and telephone number.

You can submit your TPAR online by using the Business Portal.

## General configuration

Before you generate a TPAR, complete the setup of legal entity (company) information and vendor information in terms of the company name, address, ABN, and contact person. To generate a final report, import the required electronic configurations.

### Create a contact person for your company

A TPAR requires that you provide information to the company contact person who is responsible for information on the report. To set up contact information that the TPAR reports, follow these steps:

1. Go to **Sales and marketing** \> **Relationships** \> **Contacts** \> **All contacts**.
1. Select **New** to create a contact for your legal entity. Select a legal entity in the **Contact for** field.
1. Check the **Party ID** value to make sure that you select the legal entity that Standard Audit File for Tax (SAF-T) reports from.

### Import Electronic reporting configurations

In Microsoft Dynamics 365 Finance, import the latest available version of these Electronic reporting (ER) configurations from the Global repository:

- Payment model
- TPAR model mapping (AU)
- TPAR (AU) report format

For more information about how to import ER configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Prepare a TPAR

Before you generate a TPAR, collect the data required for the report. This process resembles the process for payment time reporting. The process collects all payments in the reporting period for a specific group of vendors. You can run the process in real time, or you can schedule it to run in the background through batch processing.

1. Go to **Accounts payable** \> **Periodic tasks** \> **Taxable payments annual report**, and select **New**.
1. In the **From date** and **To date** fields, enter values to define the reporting period.
1. In the **Run type** field, select a value. If you're testing report data, select **Test**. To generate a report to send to the ATO, select **Production**.

    :::image type="content" source="../media/apac-au-tpar-create.png" alt-text="Screenshot of generating a TPAR.":::

1. In the report versions, select **New** to start collecting data for the report. Then select **Operations** \> **Collect data**.
1. On the report, provide the vendor's selection criteria according to the TPAR reporting requirements. You can select vendors based on their posting profile or vendor group. You can also specify whether the process of collecting data should be run through batch processing.

    After the data is collected, a report version is created. The report version changes the status from **New** to **Populated**.

1. Select **Payees** to review the collected data.

    :::image type="content" source="../media/apac-au-tpar-payees.png" alt-text="Screenshot of collected data for payees.":::

    Use this view to review the gross amount that's paid to vendors, together with GST and withholding tax information.

    > [!NOTE]
    > If a contractor doesn't quote an ABN and provides a valid reason for not doing so, **Statement by supplier** information should be provided on the TPAR. A statement by the supplier is a form that a contractor can complete and give to the payer if they aren't required to have an ABN, or if they're an individual under 18 years of age and the payment doesn't exceed $350 per week.

1. After you validate and approve all the collected data, select to generate either a test version of the report to submit to the ATO and validate on the Business Portal, or a production version for final submission.
1. Select **TPAR** to start preparing the TPAR as a text file that contains data in a format that's ready for submission to the ATO. 
1. After you submit the report and it's accepted in the ATO online portal, the status of the report in **Operations** updates to **Sent**.
1. To make changes to your report after you send it, add a new version of the report. A new version generates a text file that the ATO recognizes as an amendment.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
