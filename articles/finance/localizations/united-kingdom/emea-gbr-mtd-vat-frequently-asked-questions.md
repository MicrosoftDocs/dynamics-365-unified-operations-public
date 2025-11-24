title: Making Tax Digital (MTD) – VAT return integration - frequently asked questions
description: Making Tax Digital (MTD) – VAT return integration - frequently asked questions.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 11/24/2025
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2025-03-25
---

# Making Tax Digital (MTD) – VAT return integration - frequently asked questions


## 1. I can't enable the new "Security enhancements in UK MTD VAT integration (cloud-based deployments only)" feature, what should I do?

Ensure you have:
- The latest ER configurations.
- Imported the data package `UK MTD VAT setup_v6_KB5008136 from 10.0.22 ONLY.zip`.
- Installed the E-Invoicing add-in.

For more details, see [Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)](emea-gbr-mtd-vat-security-enhancements.md#prerequisites).

## 2. I have enabled the "Security enhancements in UK MTD VAT integration (cloud-based deployments only)" feature, but I get an error with 500 response code during submission. What should I do?

Check that you are using:
- The correct combination of HMRC test user ID and password to generate the auth code.
- The correct VAT registration number.

To confirm the correct test VAT registration number:
1. Go to **Tax** > **Setup** > **Electronic messages** > **Electronic message processing** > **UK MTD VAT testing**)
2. Expand the **Message additional fields** FastTab
3. Check the value of the **Tax registration number** additional field is the VAT registration number obtained from HMRC test user.

For more details, see [Obtain test user credentials](emea-gbr-mtd-vat-integration-sandbox#user).

## 3. I have enabled the "Security enhancements in UK MTD VAT integration (cloud-based deployments only)" feature, but it gives a 404 response during submission. What should I do?

This issue could happen if the `UK MTD VAT setup_v6_KB5008136 from 10.0.22 ONLY.zip` package was re-imported after enabling the "Security enhancements in UK MTD VAT integration (cloud-based deployments only)" feature.

If so,  follow these steps to mitigate the problem:
1. Go to **Tax** > **Setup** > **Electronic messages** > **Executable class settings** and change **Action type** field to **Web service** for the folowing executable classes:
   - RequestVATLiabilities
   - RequestVATPayments
   - RetrieveVATObligations
   - SubmitVATReturn
   - TestRetrieveVATObligations
   - TestSubmitVATReturn
2. Go to **Tax** > **Setup** > **Electronic messages** > **Message processing actions** and change the **Action type** to **Message execution level** for the following actions:
   - Retrieve VAT obligations
   - Submit VAT return
   - Request VAT payments
   - Request VAT liabilities
   - Test retrieve VAT obligations
   - Test submit VAT return
3. On the same **Tax** > **Setup** > **Electronic messages** > **Message processing actions** page, change the **Executable class** to:
   
| Action | Executeble class |
|--------|------------------|
| Retrieve VAT obligations | RetrieveVATObligations |
| Submit VAT return | SubmitVATReturn |
| Request VAT payments | RequestVATPayments |
| Request VAT liabilities | RequestVATLiabilities |
| Test retrieve VAT obligations | TestRetrieveVATObligations |
| Test submit VAT return | TestSubmitVATReturn |

These settings are provided automaticaty to you system when you enable the "Security enhancements in UK MTD VAT integration (cloud-based deployments only)" feature. However, these setting can be reverted back to the previouse state when the `UK MTD VAT setup_v6_KB5008136 from 10.0.22 ONLY.zip` package was re-imported. 
This causes the error 404 during submission of queries to HMRC's APIs, when the feature is enabled.
