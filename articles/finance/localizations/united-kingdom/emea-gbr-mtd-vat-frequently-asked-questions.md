---
title: Making Tax Digital (MTD) – VAT return integration - frequently asked questions
description: Making Tax Digital (MTD) – VAT return integration - frequently asked questions.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 11/25/2025
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2025-03-25
---

# Frequently Asked Questions: Making Tax Digital (MTD) VAT return integration

This section provides answers to frequently asked questions about Making Tax Digital (MTD) – VAT return integration in Dynamics 365 Finance. It helps organizations, partners, and customers resolve common configuration and operational issues when working with the MTD VAT integration feature. The guidance covers setup requirements, security enhancements, troubleshooting submission errors, and best practices for compliance with HMRC standards.
Use this FAQ as a quick reference when:

- Enabling or configuring the MTD VAT integration feature.
- Encountering errors during VAT return submission.
- Verifying prerequisites for secure communication with HMRC.

For detailed implementation steps, see the official documentation linked in each answer.

## 1. I can't enable the new "Security enhancements in UK MTD VAT integration (cloud-based deployments only)" feature, what should I do?

Ensure you have:
- The latest ER configurations.
- Imported the data package `UK MTD VAT setup_v6_KB5008136 from 10.0.22 ONLY.zip`.
- Installed the E-Invoicing add-in.

For more information, see [Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)](emea-gbr-mtd-vat-security-enhancements.md#prerequisites).

## 2. I enabled the "Security enhancements in UK MTD VAT integration (cloud-based deployments only)" feature, but I get an error with response code 500 during submission. What should I do?

Check that you're using:
- The correct combination of HMRC test user ID and password to generate the authorization code.
- The correct VAT registration number provided with test is ID.

To confirm the correct test VAT registration number:
1. Go to **Tax** > **Setup** > **Electronic messages** > **Electronic message processing** > **UK MTD VAT testing**)
1. Expand the **Message additional fields** FastTab
1. Check the value of the **Tax registration number** other field is the VAT registration number obtained from HMRC test user.

For more information, see [Obtain test user credentials](emea-gbr-mtd-vat-integration-sandbox.md#user).

## <a id="q-3"></a> 3. I enabled the "Security enhancements in UK MTD VAT integration (cloud-based deployments only)" feature, but I get an error with response code 404 during submission. What should I do?

This issue can happen if you reimport the `UK MTD VAT setup_v6_KB5008136 from 10.0.22 ONLY.zip` package after enabling the "Security enhancements in UK MTD VAT integration (cloud-based deployments only)" feature.

If so, follow these steps to fix the problem:
1. Go to **Tax** > **Setup** > **Electronic messages** > **Executable class settings** and change the **Action type** field to **Web service** for the following executable classes:
   - RequestVATLiabilities
   - RequestVATPayments
   - RetrieveVATObligations
   - SubmitVATReturn
   - TestRetrieveVATObligations
   - TestSubmitVATReturn
1. Go to **Tax** > **Setup** > **Electronic messages** > **Message processing actions** and change the **Action type** to **Message execution level** for the following actions:
   - Retrieve VAT obligations
   - Submit VAT return
   - Request VAT payments
   - Request VAT liabilities
   - Test retrieves VAT obligations
   - Test submits VAT return
1. On the same **Tax** > **Setup** > **Electronic messages** > **Message processing actions** page, change the **Executable class** to:
   
| Action | Executable class |
|--------|------------------|
| Retrieve VAT obligations | RetrieveVATObligations |
| Submit VAT return | SubmitVATReturn |
| Request VAT payments | RequestVATPayments |
| Request VAT liabilities | RequestVATLiabilities |
| Test retrieves VAT obligations | TestRetrieveVATObligations |
| Test submits VAT return | TestSubmitVATReturn |

These settings are automatically provided to your system when you enable the "Security enhancements in UK MTD VAT integration (cloud-based deployments only)" feature. However, these settings can revert back to the previous state when you reimport the `UK MTD VAT setup_v6_KB5008136 from 10.0.22 ONLY.zip` package. 
This issue causes the error 404 during submission of queries to HMRC's APIs when the feature is enabled.

## 4. I enabled the "Security enhancements in UK MTD VAT integration (cloud-based deployments only)" feature, but I still get a warning to enable the new feature during submission. What should I do?

This warning usually means that you set up HMRC data after enabling the new security feature.

Follow the mitigation steps suggested in the [previous question](emea-gbr-mtd-vat-frequently-asked-questions.md#q-3).

## 5. I enabled the feature, but I get a Forbidden error with code 403 during submission. What should I do?

This error can appear when you didn't enable the Security enhancements in UK MTD VAT integration (cloud-based deployments only) feature and you're using your own sandbox web application that you created in your developer account on the HMRC portal. In this situation, make sure that your sandbox web application on the HMRC portal is subscribed to the `VAT (MTD) API`.

For more information, see [Create a sandbox application in the HMRC Developer Hub](emea-gbr-mtd-vat-integration-sandbox.md#create-a-sandbox-application-in-the-hmrc-developer-hub).

## 6. I successfully retrieved VAT obligations, but I don't get any records when I select the "Collect data" button on the Electronic messages page. What should I do?

The **Sales tax payments** table is the source of **Message items** for UK MTD VAT feature when you select the **Collect data** button on the **Electronic messages** page. If the expected **Sales tax payment** record isn't collected, it could mean that it's already linked to another electronic message.

To check this issue, follow these steps.
1. Go to **Tax** > **Electronic messages** > **Electronic message items**.
1. Locate the corresponding **Sales tax payment** record in the list of message items.
1. Review the status of the **Electronic message item** line and act accordingly. If it was incorrectly linked to another electronic message, you can delete that **Electronic message item** line. This action allows you to add the line again to the new electronic message.

## 7. I don't see the 'fraud prevention headers' confirmation page or get an error related to fraud prevention headers during submission. What should I do?

Ensure you complete the fraud prevention headers setup as specified in the documentation: [Set up application-specific parameters for MTD VAT web request headers format](emea-gbr-mtd-vat-integration-setup.md#headers).

## 8. I didn't enable the "Security enhancements in UK MTD VAT integration (cloud-based deployments only)" feature, but I don't see the auth code box when trying to get the access token.

If you don't enable the **Security enhancements in UK MTD VAT integration (cloud-based deployments only)** feature but you don't see the dialog on **Web applications** page by **Get authorization code** button on the Action pane, 
make sure you're using the following version ER configurations:

- MTD VAT model mapping, version 46.**72**, under the Electronic Messages framework model
- MTD VAT authorization format (UK), version 46.**15**, under the Electronic Messages framework model
- MTD VAT web request headers format (UK), version 46.**47**, under the Electronic Messages framework model
- MTD VAT return response importing JSON (UK), version 46.**13**, under the Electronic Messages framework model
- MTD VAT interoperation (UK), version 31.**10**, under the Tax declaration model
