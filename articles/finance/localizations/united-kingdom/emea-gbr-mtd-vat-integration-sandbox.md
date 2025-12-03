---
title: Test interoperation with the MTD VAT sandbox
description: Learn how to test the interoperation of Microsoft Dynamics 365 Finance with the Making Tax Digital for value-added tax application programming interface of Her Majesty's Revenue and Customs.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 11/25/2025
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2021-08-06
---

# Test interoperation with the MTD VAT sandbox

[!include [banner](../../includes/banner.md)]

This article explains how to test the interoperation of Microsoft Dynamics 365 Finance with the Making Tax Digital for value-added tax (MTD VAT) application programming interface (API) of His Majesty's Revenue and Customs (HMRC).

> [!NOTE]
> - To meet security requirements, we implemented modifications to the Dynamics 365 Finance direct system-to-system integration with the HMRC web service for submitting VAT returns for companies registered for VAT in the UK. This enhancement involves the adoption of an Electronic Invoicing service as an intermediary that facilitates secure access to the storage of credentials essential for software authorization within the HMRC APIs. **These services won't be accessible from on-premises deployments by June 6, 2025**.
> - As of June 6, 2025, we no longer support **batch mode for submission** of VAT return in the **Making Tax Digital** feature. You can still generate the report (VAT 100) in Excel and JSON formats in batch.

> [!IMPORTANT]
> - We recommend enabling the **Security enhancements in UK MTD VAT integration (cloud-based deployments only)** feature to activate the implemented security enhancements and comply with Microsoft security requirements.
> - Learn about the transition of cloud-based deployments to the **Security enhancements in UK MTD VAT integration (cloud-based deployments only)** feature in [Security enhancements in UK MTD VAT integration (cloud-based deployments only)](emea-gbr-mtd-vat-security-enhancements.md).

For testing purposes, you can use the **UK MTD VAT TEST** Electronic messaging (EM) processing in Finance to try to interoperate with HMRC's sandbox environment. When you enable the **Security enhancements in UK MTD VAT integration (cloud-based deployments only)** feature, you don't need to register as a developer in the HMRC Developer Hub and access the sandbox environment. You can use the **UK MTD VAT TEST** Electronic messaging (EM) processing in Finance to interoperate with HMRC's sandbox environment.

## <a id="user"></a>Obtain test user credentials

To test the interoperation of Finance with sandbox of HMRC's MTD VAT API, you must acquire test user credentials:

- **User ID** – The name that you use to access HMRC while requesting an authorization code.
- **Password** – The password that you use to access HMRC while requesting an authorization code.
- **VRN** – The testing VAT registration number that you use during testing of the interoperation with the HMRC sandbox environment.

Use these three parameters together.

To get your test user credentials, follow these steps:

1. In the HMRC portal, complete the steps that are described in the [Create a test user](https://developer.service.hmrc.gov.uk/api-test-user) section. The test user that you create contains information about the **UserID**, **Password**, and **VAT Registration Number** fields, and their respective values.
1. Save the **UserID**, **Password**, and **VAT Registration Number** values of the test user that you created. You use them in later steps of the process.
1. In Dynamics 365 Finance, go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**, and select the **UK MTD VAT TEST** processing.
1. On the **Message additional fields** FastTab, select the **Tax registration number** field, and enter the **VAT Registration Number** value of the test user that you created in the HMRC portal.

## Retrieve VAT obligations from HMRC for testing interoperation

After you enable the **Security enhancements in UK MTD VAT integration (cloud-based deployments only)** feature in your Finance sandbox environment, your environment is ready to work with MTD endpoints of HMRC.

To validate the integration with sandbox MTD endpoints of HMRC from your sandbox environment, follow these steps:

1. In Finance, go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and select the **UK MTD VAT TEST** processing.
1. On the **Messages** FastTab, select **New**.
1. In the **Run processing** dialog, in the **Action** field, select **Create VAT obligation request**. Then select **OK**. A new electronic message is created that has a status of **New obligation request**.
1. Enter dates in the **From date** and **To date** fields. These fields are mandatory for electronic messages that retrieve VAT obligations. However, the response from HMRC's sandbox application doesn't depend on the values. It always contains the same information about obligation periods.
1. In the **Description** field, enter a description of your message. This field is optional for electronic messages that retrieve VAT obligations.
1. Select **Send report** to initialize the retrieval of VAT obligation information from HMRC.
1. In the **Run processing** dialog, the **Test retrieve VAT obligations** action is automatically defined, and information is filled in by the system. Select **OK**.
1. You receive the following warning message in the dialog. The message indicates which endpoint (sandbox or production) the request is sent to.

    > By selecting this action, a request will be sent to HMRC's **sandbox** endpoint. Do you want to proceed?

    Select **Yes** to continue or **No** to cancel.

1. The **System administrator consent** dialog is shown the first time that you enable the integration in your Finance instance. Select **Agree** to continue or **Disagree** to cancel. Once consent for the system administrator agreement is granted, this dialog won't appear again for subsequent requests related to the specified electronic message processing.
1. You're automatically redirected to HMRC's web portal for authorization if your current authorization has expired or if you're using the integration for the first time within the specified legal entity in Finance. (The address of the page begins with `https://test-www.tax.service.gov.uk/oauth/`.) Select **Continue**.

> [!NOTE]
> This step isn't initiated by the system if you previously authorized the integration for the specified legal entity in Finance and the authorization is still valid.
> **The authorization is valid for 100 days**, after which you must reauthorize every 100 days.

1. In the HMRC portal, select **Sign in**, and provide the user ID and password of the test user that you created.
1. Select **Give permission**.
1. The next page shows the authorization code. Select **Copy** to copy the code to the clipboard.

> [!IMPORTANT]
> An **authorization code is valid for only 10 minutes**. You must proceed further with the next steps during that time. Otherwise, the authorization code expires. In that case, you can use the same test user credentials to get a new authorization code.

1. In your browser, switch to the Finance page where you're working with electronic messages. There should be a dialog that includes an **Authorization code** parameter. As the value of this parameter, paste the authorization code that you copied. Then select **OK** to continue.
1. In this step, the authorization is completed, and the VAT obligation request starts. In the **Fraud prevention headers** dialog, select the checkbox to consent to providing the information in fraud prevention headers as part of the VAT request to HMRC. Then select **Submit**. Your privacy is important to us. To learn more, read our [privacy notice](emea-gbr-mtd-vat-integration.md#privacy-notice).

   > [!NOTE]
   > A request in JavaScript Object Notation (JSON) format is created and sent to the HMRC web application. The response that is received from HMRC is attached to the electronic message. Based on the response, new electronic messages for the VAT return are created.

1. On the **Messages** FastTab, you should notice that two new electronic messages were created as a result of the successful VAT obligation request to HMRC's sandbox endpoint.

   > [!NOTE]
   > HMRC uniquely identifies each VAT return period by using a **periodKey** parameter. This parameter is stored in Finance. However, according to HMRC requirements, users must not be able to see the **periodKey** value in the UI. Therefore, the **periodKey** additional field is used to store the **periodKey** value in the **UK MTD VAT TEST** processing. This field is set up as a hidden field, so that users can't see its value. To ensure compliance with HMRC requirements, don't change this setup for the **periodKey** additional field.

The following illustration shows the lifecycle of electronic message processing for the retrieval of VAT obligations.

:::image type="content" source="../media/mkd-process.png" alt-text="Screenshot of the lifecycle of electronic message processing for VAT obligation retrieval.":::

The last step of the processing is an **Import VAT obligations** action of the **Electronic reporting import** type. The system defines the following behavior for this step:

- If a VAT obligation from the response doesn't exist in the database, and the status of that VAT obligation in HMRC is **Open**, a new electronic message is created that has a status of **New VAT return**.
- If a VAT obligation from the response doesn't exist in the database, and the status of that VAT obligation in HMRC is **Fulfilled**, a new electronic message is created that has a status of **Completed VAT return**.
- If a VAT obligation from the response exists in the database, the system verifies the values of the **HMRC status**, **Due date**, and **Received date** additional fields. It then syncs those values with the information from the response.

All the actions that are performed for electronic messages are logged and can be viewed on the **Action log** FastTab.

## Collect data for a VAT return

The process of preparing and submitting a VAT return for a period is based on sales tax payment transactions that the [Settle and post sales tax](../../general-ledger/tasks/create-sales-tax-payment.md) job posts. For more information about sales tax settlement and reporting, see [Sales tax overview](../../general-ledger/indirect-taxes-overview.md).

Before you start to prepare and submit a VAT return to HMRC, complete the regular **Settle and post sales tax** job for the period that you report to HMRC. When you run this job, it creates new sales tax payment transactions. To view these sales tax payments, go to **Tax** \> **Inquiries and reports** \> **Sales tax Inquiries** \> **Sales tax payments**. You can review the resulting values for each sales tax payment transaction on the **VAT 100** report in Excel format.

You can run the **Settle and post sales tax** job several times for the same period before you submit a VAT return to HMRC. You can include all the sales tax payment transactions on the same VAT return report for a period. The transactions that the system fills in for reporting depend on the sales tax settlement period that you define in the **Populate VAT return records** action for the processing. You can also include sales tax payment transactions from several legal entities in one VAT return that you report as a VAT group. For more information, see [Define a sales tax settlement period](emea-gbr-mtd-vat-integration-setup.md#settlement).

> [!IMPORTANT]
> MTD VAT lets you submit a VAT return only one time for each reporting period. As HMRC states on the official website, the current amendment process remains in place for VAT:
>
> - If the net value of the errors on the VAT return is less than £10,000, the company amends those errors on the next VAT return.
> - If the net value of the errors exceeds £10,000, the company must complete the VAT 652 form, which is available on the Gov.UK website.

When the **Settle and post sales tax** job completes, you can prepare a report for electronic submission. The first step of data preparation is to collect sales tax payment transactions that relate to the period.

To collect sales tax payment transactions, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and select the **UK MTD VAT TEST** processing.
1. On the **Message** FastTab, select the electronic message that is created in **New VAT return** status.
1. Update the **Start date** and **End date** fields of the record, so that the dates are consistent with the sales tax settlement period that you previously completed the sales tax settlement procedure during. You can collect VAT data only for electronic messages that have a status of **New VAT return**.
1. On the **Message** FastTab, select **Collect data**.
1. In the **Run processing** dialog, the **Populate VAT return records** action is predefined. Select **OK**.
1. The system collects the sales tax payment transactions that it posted in the period that you define by the **From date** and **To date** fields. You can review the collected sales tax payment transactions on the **Message items** FastTab.
1. If, for some reason, a sales tax payment transaction that the system entered must be excluded from the report, you can delete it. Alternatively, you can update its status to **Excluded** by selecting **Update status** on the **Message items** FastTab. Transactions that have a status of **Excluded** aren't considered for reporting. You can also change the status of a transaction from **Excluded** back to **Populated** by selecting **Update status** on the **Message items** FastTab.
1. You can repeatedly select **Collect data** on the **Message** FastTab until the electronic message moves to the next status.
1. After data is collected, select **Update status** on the **Messages** FastTab.
1. In the **Update status** dialog, the **Ready to generate VAT return** status is predefined. Select **OK** to mark the electronic message as ready for report generation. The status of the electronic message items that are linked to the electronic message is updated to **To be reported**.
1. If, for some reason, you must go back to step 4 and continue to collect data or change the status of electronic message items, select **Update status** on the **Messages** FastTab, select **New VAT return** in the **New status** field, and then select **OK**.

The **Action log** FastTab saves information about all the actions that you perform for the electronic message.

After an electronic message has a status of **Ready to generate VAT return**, you can initialize report generation. Two options are available:

- **Preview VAT return** – The file is generated in Excel format and attached to the electronic message. No statuses are changed.
- **Generate file for submission** – The file is generated in JSON format and attached to the electronic message. The status of the electronic message is updated to **Generated VAT return**, and the status of the linked electronic message items is updated to **Reported**.

## Generate a VAT return in Excel format for preview

To generate a VAT return in **VAT 100** report format in Excel, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and select the **UK MTD VAT TEST** processing.
1. On the **Messages** FastTab, select the electronic message record that relates to the period for which you want to generate a file, then select **Generate report**. The **Generate report** button is available only for electronic messages that have the following statuses:

    - **Ready to generate VAT return** – The user changes the electronic message status to this value by selecting **Update status**.
    - **Error VAT return generation** – If an error occurs during report generation, the electronic message status changes to this value.
    - **Error VAT return submission** – If an error occurs during report submission, the electronic message status changes to this value. The response that includes a description of the error is attached to the action log.

1. In the **Run processing** dialog, select **Preview VAT return**, then select **OK**. The file is generated in Excel format and attached to the electronic message. No statuses change.
1. To view the file, select the electronic message, then select **Attachments** (the paper clip symbol) in the upper-right corner of the page.
1. On the **Attachments** page for the selected message, select the last attachment (**VAT statement.xlsx**) then on the Action Pane, select **Open**. The file opens in Excel.

You can regenerate the **VAT 100** report several times before you generate the report in JSON format. At that point, the electronic message status changes to **Generated VAT return**.

## Generate a VAT return in JSON format

MTD VAT accepts VAT returns in JSON format only.

To generate a VAT return in JSON format, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and select the **UK MTD VAT TEST** processing.
1. On the **Messages** FastTab, select the electronic message record that relates to the period that you want to generate a file for, then select **Generate report**.
1. In the **Run processing** dialog, select **Generate file for submission**, then select **OK**. The system generates the file in JSON format and attaches it to the electronic message. The system updates the electronic message status to **Generated VAT return**, and updates the status of the electronic message items linked to the electronic message to **Reported**.
1. To view the file, select the electronic message, then select **Attachments** (the paper clip symbol) in the upper-right corner of the page.
1. On the **Attachments** page for the selected message, select the last attachment (**VAT\_return.json**) then on the Action Pane, select **Open**.

If you need to regenerate a VAT return in JSON format before you submit it to HMRC, select **Update status** on the **Messages** FastTab to update the status of the related electronic message to either **New VAT return** or **Ready to generate VAT return**, depending on whether you need to return to the data collection step or the file generation step.

## Submit VAT returns to HMRC for testing interoperation

When you generate a VAT return in JSON format and are ready to submit it to HMRC, initialize its submission to the sandbox application. The last JSON file that you attached to the electronic message is used for the submission. To help prevent discrepancies, delete any unnecessary JSON files that you attached to the electronic message that you submit to HMRC. To find and clean up unnecessary attachments, select the electronic message, then select **Attachments** (the paper clip symbol) in the upper-right corner of the page. The **Attachments** page for the selected message opens.

To submit a VAT return, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and select the **UK MTD VAT TEST** processing.
1. On the **Messages** FastTab, select the electronic message record that is related to the period that you want to submit the VAT return for, then select **Send report**. The **Send report** button is available only for electronic messages that have the following statuses:

    - **Generated VAT return** – The electronic message status is automatically updated to this value when a VAT return in JSON format is successfully generated and attached to the electronic message.
    - **Error VAT return submission** – If an error occurs during report submission, the electronic message status changes to this value. The response that includes a description of the error is attached to the action log.

1. In the **Run processing** dialog, the **Test submit VAT return** action is predefined. Select **OK**.
1. The dialog that appears contains mandatory declaration text that HMRC requires. To remain compliant with HMRC requirements, don't modify or delete this declaration text in the setup of the **Test submit VAT return** action. By selecting **OK** in this dialog, you submit VAT information, and you confirm that the information is true and complete. A false declaration can lead to prosecution.

   > [!IMPORTANT]
   > You can submit a VAT return to HMRC only one time for each period. Therefore, make sure that you want to submit the VAT return before you accept the declaration. If you aren't sure whether the VAT return is ready to be submitted, select **Cancel**.
   >
   > When you select **OK**, the VAT return in JSON format that is related to the selected electronic message is submitted to HMRC. If the VAT return is successfully submitted to HMRC, the status of the electronic message is updated to **Sent VAT return**, and the response from HMRC is attached to the electronic message.

1. In the **Request identification information** dialog, select the checkbox to consent to providing the information in fraud prevention headers as part of the VAT request to HMRC. Then select **Submit**. Your privacy is important to us. To learn more, read our [privacy notice](emea-gbr-mtd-vat-integration.md#privacy-notice).

   > [!NOTE]
   > The system automatically runs the **Import response for VAT return** action. This action causes the **Processing date** additional field of the electronic message to reflect information from the response. Additionally, the system updates the status of the electronic message to **Completed VAT return** and updates the status of the electronic message items to **Submitted**.
   >
   > :::image type="content" source="../media/uk-mtd-vat-return.png" alt-text="Screenshot of submitting VAT returns to HMRC.":::
   >
   > If, for some reason, the **Import response for VAT return** action isn't automatically run, you can manually initialize it by selecting **Import response** on the **Messages** FastTab. The **Import response** button is available only for electronic messages that have a status of **Sent VAT return**. The electronic message status is automatically updated to this value when a VAT return in JSON format is successfully submitted to the electronic message.

The **Action log** FastTab saves information about all the actions that you perform for the electronic message.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
