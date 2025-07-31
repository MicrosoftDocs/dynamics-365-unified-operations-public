---
title: Security enhancements in UK MTD VAT integration for cloud-based deployments (preview)
description: Learn how to enable the security enhancements in the UK Making Tax Digital (MTD) value-added tax (VAT) integration for cloud-based deployments feature in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/07/2025
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2025-03-25
---

# Security enhancements in UK MTD VAT integration (cloud-based deployments only)(preview)

[!INCLUDE[banner](../../includes/banner.md)]
[!INCLUDE[banner](../../includes/preview-banner.md)]

> [!IMPORTANT]
> - This feature is a production-ready preview feature.
> - This feature is subject to supplemental terms of use. By enabling this feature, you confirm that you've read and understood the preview feature terms and conditions. [View the preview terms.](https://go.microsoft.com/fwlink/?linkid=2105274)

This article explains how to enable the security enhancements in the UK Making Tax Digital (MTD) value-added tax (VAT) integration for cloud-based deployments feature in Microsoft Dynamics 365 Finance. It also describes changes to the user experience that are introduced together with this feature. This feature doesn't introduce any changes to on-premises deployments of Dynamics 365 Finance.

To meet security requirements, Microsoft is updating the direct system-to-system integration of Dynamics 365 Finance with the His Majesty's Revenue and Customs (HMRC) web service that's used to submit (VAT) returns for companies that are registered for VAT in the United Kingdom. These changes involve the adoption of an electronic Invoicing service as an intermediary that facilitates secure access to the storage of credentials that are essential for software authorization in the HMRC application programming interfaces (APIs).

> [!NOTE]
> - By June 6, 2025, the direct integration with external endpoints that His Majesty's Revenue and Customs (HMRC) provides for the submission of VAT returns from on-premises deployments of Finance will no longer be accessible. Learn more in [Features removed or deprecated in the Finance 10.0.43 release](../../get-started/removed-deprecated-features-finance.md#making-tax-digital--vat-return-submission-in-the-united-kingdom-for-on-premises-deployments).
> - By June 6, 2025, we plan to end support for batch-mode submission of VAT returns in the Making Tax Digital feature. However, the report (VAT 100) in Excel and JavaScript Object Notation (JSON) formats can still be generated in batch mode. Learn more in [Features removed or deprecated in the Finance 10.0.43 release](../../get-started/removed-deprecated-features-finance.md#batch-submission-of-vat-returns-in-the-uk-via-making-tax-digital-for-vat-in-cloud-deployments).

## Prerequisites

Prerequisites are essential requirements and foundational elements that are needed before you can enable the feature. Completion of these prerequisites is critical to achieving optimal functionality and a seamless transition to the more secure integration with the external web service.

### Check the system version

The **Security enhancements in UK MTD VAT integration (cloud-based deployments only)** feature is introduced in Finance version 10.0.43.

It's also available in the following versions of Finance:

- 10.0.41 - 10.0.2015.236
- 10.0.42 - 10.0.2095.186
- 10.0.43 - 10.0.2177.108
- 10.0.44 - 10.0.2263.30

### Import the required ER configuration updates

To work with the **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration (cloud-based deployments only)** feature, you must import the following versions or later of Electronic Reporting (ER) configurations into Finance:

- MTD VAT model mapping, version 46.74, under the Electronic Messages framework model
- MTD VAT authorization format (UK), version 46.17, under the Electronic Messages framework model
- MTD VAT web request headers format (UK), version 46.48, under the Electronic Messages framework model
- MTD VAT return response importing JSON (UK), version 46.14, under the Electronic Messages framework model
- MTD VAT interoperation (UK), version 31.11, under the Tax declaration model
  
Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

### Enable the Electronic Invoicing add-in

To comply with security requirements, it's essential that you enable the Electronic Invoicing add-in. This add-in acts as an intermediary, and ensures secure storage and management of credentials that are required for software authorization in the HMRC APIs. Enabling this functionality is a crucial step in maintaining a secure and compliant integration between Finance and the HMRC web service for the submission of VAT returns.

Learn more in [Install the add-in for Electronic invoicing microservices](../global/gs-e-invoicing-set-up-overview.md#install-the-add-in-for-electronic-invoicing-microservices).

## Enable security enhancements in UK MTD VAT integration

To enable the **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration (cloud-based deployments only)** feature in Finance, follow these steps.

1. Go to **Workspaces** \> **Feature management**.
1. In the list of features, search for **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration (cloud-based deployments only)**.
1. Select **Enable now**.

> [!NOTE]
> - This feature is a production-ready preview feature for companies that use direct integration of their **cloud-based** Finance instance with MTD VAT APIs of HMRC.
> - When you enable this feature, your UK MTD VAT TEST and UK MTD VAT returns electronic messaging processing is automatically updated to enhance the security of your Finance integration for direct submission of VAT returns for your UK VAT registration.
> - The following actions of the **Web service** type have been changed to the **Executable class** type: Retrieve VAT obligations, Test retrieve VAT obligations, Submit VAT return, Test submit VAT return, Request VAT liabilities, and Request VAT payments.
> - After this feature is enabled, it can't be disabled.

If the status of the  feature is shown as unavailable (error), the prerequisites might not be met. If the prerequisites are met, but the feature is still unavailable, contact customer support.

## Steps after the feature is activated in your sandbox environment

After the **Security enhancements in UK MTD VAT integration (cloud-based deployments only)** feature is enabled in your Finance sandbox environment, the environment is ready to work with MTD endpoints of HMRC.

To integrate with sandbox MTD endpoints of HMRC and create a test user, follow these steps.

1. On HMRC Developer Hub, create a test user. Learn more in [Create test user - HMRC Developer Hub - GOV.UK](https://developer.service.hmrc.gov.uk/api-test-user).
1. In Finance, go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**, and select the **UK MTD VAT TEST** processing.
1. On the **Message additional fields** FastTab, select the **Tax registration number** additional field, and enter the **VAT Registration Number** value of the test user that you created.  

To validate the integration with sandbox MTD endpoints of HMRC from your sandbox environment, follow these steps.

1. In Finance, go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and select the **UK MTD VAT TEST** processing.
1. On the **Messages** FastTab, select **New**.
1. In the **Run processing** dialog, in the **Action** field, select **Create VAT obligation request**. Then select **OK**. A new electronic message is created that has a status of **New obligation request**.
1. Enter dates in the **From date** and **To date** fields. These fields are mandatory for electronic messages that retrieve VAT obligations. However, the response from HMRC's sandbox application doesn't depend on the values. It always contains the same information about obligation periods.
1. In the **Description** field, enter a description of your message. This field is optional for electronic messages that retrieve VAT obligations.
1. Select **Send report** to initialize the retrieval of VAT obligation information from HMRC.
1. In the **Run processing** dialog, the **Test retrieve VAT obligations** action is automatically defined, and information is filled in by the system. Select **OK**.
1. You receive the following warning message in the dialog. The message indicates which endpoint (sandbox or production) the request will be sent to.

    > By selecting this action, a request will be sent to HMRC's **sandbox** endpoint. Do you want to proceed?

    Select **Yes** to continue or **No** to cancel.

1. The **System administrator consent** dialog is shown the first time that the integration is enabled in your Finance instance. Select **Agree** to continue or **Disagree** to cancel.
1. You're taken to the HMRC's web portal for authorization. (The address of the page begins with `https://test-www.tax.service.gov.uk/oauth/`.) Select **Continue**.
1. In the HMRC portal, select **Sign in**, and provide the user ID and password of the test user that you created.
1. Select **Give permission**.
1. The next page shows the authorization code. Select **Copy** to copy the code to the clipboard.
1. In your browser, switch to the Finance page where you're working with electronic messages. There should be a dialog that includes an **Authorization code** parameter. As the value of this parameter, paste the authorization code that you copied. Then select **OK** to continue.
1. In this step, the authorization is completed, and the VAT obligation request starts. In the **Fraud prevention headers** dialog, select **Submit** to continue.
1. On the **Messages** FastTab, you should notice that two new electronic messages were created as a result of the successful VAT obligation request to HMRC's sandbox endpoint.

## Steps after the feature is activated in your production environment

After the **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration (cloud-based deployments only)** feature is enabled in your Finance production environment, the environment is ready to work with MTD endpoints of HMRC.

For integration with production MTD endpoints of HMRC, you must use the user ID and password for authorization.

- **User ID** – The name that is used to access HMRC while an authorization code is being requested.
- **Password** – The password that is used to access HMRC while an authorization code is being requested.

To validate the integration with production MTD endpoints of HMRC from your production environment, follow these steps.

1. In Finance, go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and select the **UK MTD VAT returns** processing.
1. On the **Messages** FastTab, select **New**.
1. In the **Run processing** dialog, in the **Action** field, select **Create VAT obligation request**. Then select **OK**. A new electronic message is created that has a status of **New obligation request**.
1. Enter dates in the **From date** and **To date** fields.
1. In the **Description** field, enter a description of your message. This field is optional for electronic messages that retrieve VAT obligations.
1. Select **Send report** to initialize the retrieval of VAT obligation information from HMRC.
1. In the **Run processing** dialog, the **Retrieve VAT obligations** action is automatically defined, and information is filled in by the system. Select **OK**.
1. You receive the following warning message in the dialog. The message indicates which endpoint (sandbox or production) the request will be sent to.

    > By selecting this action, a request will be sent to HMRC's **production** endpoint. Do you want to proceed?

    Select **Yes** to continue or **No** to cancel.

1. The **System administrator consent** dialog is shown the first time that the integration is enabled in your Finance instance. Select **Agree** to continue or **Disagree** to cancel.
1. You're taken to the HMRC's web portal for authorization. Select **Continue**.
1. In the HMRC portal, select **Sign in**, and provide your user ID and password.
1. Select **Give permission**.
1. The next page shows the authorization code. Select **Copy** to copy the code to the clipboard.
1. In your browser, switch to the Finance page where you're working with electronic messages. There should be a dialog that includes an **Authorization code** parameter. As the value of this parameter, paste the authorization code that you copied. Then select **OK** to continue.
1. In this step, the authorization is completed, and the VAT obligation request begins. In the **Fraud prevention headers** dialog, select **Submit** to continue.
1. On the **Messages** FastTab, you should notice that new electronic messages were created as a result of the successful VAT obligation request to HMRC's production endpoint.

The authorization lasts 100 days. After the authorization expires, it's automatically reinitiated when a request to an HMRC endpoint is initiated. You don't have to reauthorize from the **Web application** page.

## Further details

When the **\[Production Ready Preview\] Security enhancements in UK MTD VAT integration (cloud-based deployments only)** feature is enabled in Finance, you don't have to authorize from the **Web application** page. The authorization from the **Web application** page is no longer available. Instead, the system automatically controls the authorization period (100 days). It initiates the authorization when it's required during a request to an HMRC endpoint.

The **Client ID** and **Client secret** fields that were previously available on the **Web application** page are no longer used in the **UK MTD VAT TEST** and **UK MTD VAT returns** processing. The Electronic Invoicing add-in automatically provide client ID and client secret information while it transfers the requests to HMRC endpoints.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
