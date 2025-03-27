---
title: Security enhancements in UK MTD VAT integration (cloud-based deployments only)
description: Learn how to enable the \[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\) feature.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2025
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2025-03-25
ms.dyn365.ops.version: AX 10.0.43
---

# \[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)

[!INCLUDE[banner](../../includes/banner.md)]

We’re updating the Dynamics 365 Finance direct system-to-system integration with the HMRC web service for submitting VAT returns for companies registered for VAT in the UK to meet security requirements. 
These changes involve the adoption of an Electronic Invoicing service as an intermediary that facilitates secure access to the storage of credentials essential for software authorization within the HMRC APIs.
This article explains how to enable the **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)** feature. The article also includes changes to the user experience that are introduced with this feature. This feature does not introduce any changes to on-premises deployments of Dynamics 365 Finance.

> [!IMPORTANT]
> This is a production ready preview feature.
> This feature is subject to supplemental terms of use. By enabling this feature, you are confirming that you have read and understand the preview feature terms and conditions. [View preview terms](https://go.microsoft.com/fwlink/?linkid=2105274).

> [!NOTE]
> The direct integration with external endpoints provided by HMRC for submission of the VAT return from **on-premises deployments** of Dynamics 365 Finance **won’t be accessible by June 6, 2025**. Learn more in [Features removed or deprecated in the Finance 10.0.43 release](../../get-started/removed-deprecated-features-finance.md#making-tax-digital--vat-return-submission-in-the-united-kingdom-for-on-premises-deployments).
>
> By June 6, 2025, we plan to no longer support **batch mode for submission** of VAT return in the **Making Tax Digital** feature. It’s still possible to generate in batch the report (VAT 100) in Excel and JSON formats. Learn more in [Features removed or deprecated in the Finance 10.0.43 release](../../get-started/removed-deprecated-features-finance.md#batch-submission-of-vat-returns-in-the-uk-via-making-tax-digital-for-vat-in-cloud-deployments).

## Prerequisites

Prerequisites are essential requirements and foundational elements needed before proceeding with feature enablement. Ensuring that these conditions are met is critical to achieving optimal functionality and a seamless transition to the more secure integration with external web service. 

### Check system version

The **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)** feature is introduced in **10.0.43** version of Finance.

It is also available in the following versions of Finance:

- 10.0.41 - 10.0.2015.**155**
- 10.0.42 - 10.0.2095.**77**

### Import the required ER configuration updates

To work with the **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)** feature the following or higher versions of Electronic Reporting (ER) configurations must be imported into Finance:

- MTD VAT model mapping - version **46.74**, under the Electronic Messages framework model.
- MTD VAT authorization format (UK) - version **46.17**, under the Electronic Messages framework model.
- MTD VAT web request headers format (UK) - version **46.48**, under the Electronic Messages framework model.
- MTD VAT interoperation (UK) - version **31.11**, under the Tax declaration model.

Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

### Enable the E-Invoicing Add-In

To comply with security requirements, it is essential that you enable the **Electronic Invoicing add-in**. This add-in acts as an intermediary, ensuring secure storage and management of credentials required for software authorization within the HMRC APIs. Enabling this functionality is a crucial step in maintaining a secure and compliant integration between Dynamics 365 Finance and the HMRC web service for VAT return submissions.

Learn more about enabling the electronic invoicing add-in in [Enable the E-Invoicing Add-In](../global/gs-e-invoicing-set-up-overview.md#install-the-add-in-for-electronic-invoicing-microservices).

## How to enable Security enhancements in UK MTD VAT integration

To enable the **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)** feature in Finance, follow these steps.

1. Go to **Workspaces** > **Feature management** workspace.
1. Search for **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)** feature in the list.
1. Select **Enable now**.

> [!NOTE]
> This is a **Production Ready Preview** feature for companies using direct integration of their **cloud-based** Dynamics 365 Finance with MTD VAT APIs of HMRC.
>
> When you enable this feature, your `UK MTD VAT TEST` and `UK MTD VAT returns` electronic messaging processing automatically updates to enhance the security of your Dynamics 365 Finance integration for direct VAT return submissions for your UK VAT registration.
>
> The following actions of type `Web service` have been changed to `Executable class`: Retrieve VAT obligations, Test retrieve VAT obligations, Submit VAT return, Test submit VAT return, Request VAT liabilities, and Request VAT payments.
>
> Once this feature is enabled, it cannot be disabled.

If the **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)** feature status is shown as unavailable (error), this can be due to the prerequisites are not being fulfilled. If the prerequisites are fulfilled and the feature is still unavailable, contact customer support.

## How to proceed once the feature is activated in your sandbox

Once the **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)** feature is enabled on your Finance sandbox, your environment is ready to work with MTD endpoints of HMRC.

To integrate with sandbox MTD endpoints of HMRC and to create a test user, follow these steps.

1. Create a test user on HMRC Developer Hub. Learn more in [Create test user - HMRC Developer Hub - GOV.UK](https://developer.service.hmrc.gov.uk/api-test-user).
1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**, and select the **UK MTD VAT TEST** processing.
1. On the **Message additional fields** FastTab, select the **Tax registration number** additional field, and enter the **VAT Registration Number** value of the test user that you created in the HMRC portal.  

To validate the integration from your sandbox with sandbox MTD endpoint of HMRC, follow these steps.

1. In Finance, go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and select the **UK MTD VAT TEST** processing. 
1. On the **Messages** FastTab, select **New**.
1. In the **Run processing** dialog box, in the **Action** field, select **Create VAT obligation request**. Then select **OK**. A new electronic message is created that has a status of **New obligation request**.
1. Enter dates in the **From date** and **To date** fields. These fields are mandatory for electronic messages that retrieve VAT obligations. However, the response from HMRC's sandbox application doesn't depend on the values. It always contains the same information about obligation periods.
1. In the **Description** field, enter a description of your message. This field is optional for electronic messages that retrieve VAT obligations.
1. Select **Send report** to initialize the retrieval of VAT obligation information from HMRC.
1. In the **Run processing** dialog box, the **Test retrieve VAT obligations** action is automatically defined, and information is filled in by the system. Select **OK**.
1. See the warning message in the dialog: *By selecting this action, a request will be sent to HMRC's **sandbox** endpoint. Do you want to proceed?* This message informs the user which endpoint (sandbox or production) the request will be sent to. Select **Yes** to proceed or **No** to cancel.
1. In the next dialog you can see the **System administrator consent**. It is shown only for the first time the integration is enabled in your Finance. Select **Agree** to proceed or **Disagree** to cancel.
1. You are transferred to `https://test-www.tax.service.gov.uk/oauth/…` page for authorization, select **Continue**.
1. In HMRC portal, select **Sign in** and provide your test user ID and password.
1. In HMRC portal, select **Give permission**.
1. In HMRC portal, on the next page, the authorization code is shown. Select **Copy** to copy the code to the clipboard.
1. In your browser, switch to the Finance page where you are working with **Electronic messages**. See the dialog with **Authorization code** parameter and past the authorization code from the clipboard. Select **OK** to proceed.
1. On this step, the authorization is completed, and the VAT obligation request starts. You will see the **Fraud prevention headers** dialog. Select **Submit** to continue.
1. As a result of the successful VAT obligation request to HMRC's sandbox you can see the two new electronic messages are created on the **Messages** FastTab.

## How to proceed once the feature is activated in your production environment

Once the **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)** feature is enabled on your production Finance, your environment is ready to work with MTD endpoints of HMRC.

For integration with production MTD endpoints of HMRC, you need to authorize with the User ID and Password. 
- **User ID** – The name that is used to access HMRC while an authorization code is being requested.
- **Password** – The password that is used to access HMRC while an authorization code is being requested.

To validate the integration from your production with production MTD endpoint of HMRC, follow these steps.

1. In Finance, go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and select the **UK MTD VAT returns** processing. 
1. On the **Messages** FastTab, select **New**.
1. In the **Run processing** dialog box, in the **Action** field, select **Create VAT obligation request**. Then select **OK**. A new electronic message is created that has a status of **New obligation request**.
1. Enter dates in the **From date** and **To date** fields. 
1. In the **Description** field, enter a description of your message. This field is optional for electronic messages that retrieve VAT obligations.
1. Select **Send report** to initialize the retrieval of VAT obligation information from HMRC.
1. In the **Run processing** dialog box, the **Retrieve VAT obligations** action is automatically defined, and information is filled in by the system. Select **OK**.
1. See the warning message in the dialog: *By selecting this action, a request will be sent to HMRC's **production** endpoint. Do you want to proceed?* This message informs the user which endpoint (sandbox or production) the request will be sent to. Select **Yes** to proceed or **No** to cancel.
1. In the next dialog you can see the **System administrator consent**. It is shown only for the first time the integration is enabled in your Finance. Select **Agree** to proceed or **Disagree** to cancel.
1. You are transferred to the HMRC's web portal for authorization, select **Continue**.
1. In HMRC portal, select **Sign in** and provide your user ID and password.
1. In HMRC portal, select **Give permission**.
1 In HMRC portal, on the next page, the authorization code is shown. Select **Copy** to copy the code to the clipboard.
1. In your browser, switch to the Finance page where you are working with **Electronic messages**. See the dialog with **Authorization code** parameter and past the authorization code from the clipboard. Select **OK** to proceed.
1. On this step, the authorization is completed and the VAT obligation request starts. You will see the **Fraud prevention headers** dialog. Select **Submit** to continue.
1. As a result of the successful VAT obligation request to HMRC's production endpoint you can see the new electronic messages are created on the **Messages** FastTab.

The authorization lasts 100 days. After the authorization expires, it is initiated again automatically when a request to an HMRC's endpoint is initiated. You do not need to re-authorize from the **Web application** page.

## Further details

When the **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration \(cloud-based deployments only\)** feature is enabled in Finance you don't need to authorize from the **Web application** page. The authorization from the **Web application** page isn't available any longer. The system automatically controls the authorization period (100 days), and initiates it when necessary, during a request to an HMRC's endpoint. 

**Client ID** and **Client secret** fields that were previously available on the **Web application** page aren't used any longer in **UK MTD VAT TEST** and **UK MTD VAT returns**. This information is automatically provided by the E-invoicing add-in while transferring the requests to HMRC's endpoints. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
