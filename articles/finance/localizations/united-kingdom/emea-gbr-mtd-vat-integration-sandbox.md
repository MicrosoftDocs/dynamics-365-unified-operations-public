---
title: Test interoperation with the MTD VAT sandbox
description: Learn how to test the interoperation with the Making Tax Digital for value-added tax application programming interface of Her Majesty's Revenue and Customs.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2021-08-06
---

# Test interoperation with the MTD VAT sandbox

[!include [banner](../../includes/banner.md)]

This article explains how to test the interoperation of Microsoft Dynamics 365 Finance with the Making Tax Digital for value-added tax (MTD VAT) application programming interface (API) of Her Majesty's Revenue and Customs (HMRC).

For testing purposes, HMRC lets you register as a developer in the [HMRC Developer Hub](https://developer.service.hmrc.gov.uk/developer/registration) and access the sandbox environment. When you're registered as a developer, you can use the **UK MTD VAT TEST** Electronic messaging (EM) processing in Finance to try to interoperate with HMRC's sandbox environment.

## Create a sandbox application in the HMRC Developer Hub

When you're registered as a developer in the HMRC Developer Hub, you can create a sandbox application. This sandbox application is used to test the interoperation of Finance with HMRC's MTD VAT API.

1. In the HMRC Developer Hub, use the [Add an application to the sandbox](https://developer.service.hmrc.gov.uk/developer/applications/add/sandbox) section of your developer's account to create a sandbox application.
2. Select the **VAT (MTD)** API to subscribe your sandbox application.
3. When the application is added to the sandbox, select **View application credentials**, and copy the value in the **Client ID** field.
4. In Finance, go to **Tax** \> **Setup** \> **Electronic messages** \> **Web applications**, and select the **Sandbox HMRC** web application. In the **Client ID** field, paste the value that you copied in the previous step.
5. In the HMRC portal, select **Generate a client secret**.
6. Copy the client secret that is generated.
7. In Finance, go to **Tax** \> **Setup** \> **Electronic messages** \> **Web applications**, and select the **Sandbox HMRC** web application. In the **Client secret** field, paste the value that you copied in the previous step.
8. In the HMRC portal, select **View your application details** \> **Redirect URIs**.
9. Select **Add a redirect URI**, and enter **urn:ietf:wg:oauth:2.0:oob**.

## <a id="user"></a>Obtain test user credentials

To test the interoperation of Finance with sandbox of HMRC's MTD VAT API, you must acquire test user credentials:

- **User ID** – The name that is used to access HMRC while an authorization code is being requested.
- **Password** – The password that is used to access HMRC while an authorization code is being requested.
- **VRN** – The testing VAT registration number that is used during testing of the interoperation with the HMRC sandbox environment.

These three parameters must be used together.

Follow these steps to get your test user credentials.

1. In the HMRC portal, complete the steps that are described in the [Create a test user](https://developer.service.hmrc.gov.uk/api-test-user) section. The test user that you create there contains information about the **UserID**, **Password**, and **VAT Registration Number** fields, and their respective values.
2. Save the **UserID**, **Password**, and **VAT Registration Number** values of the test user that you created. You will use them in later steps of the process.
3. In Finance, go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic message processing**, and select the **UK MTD VAT TEST** processing.
4. On the **Message additional fields** FastTab, select the **Tax registration number** additional field, and enter the **VAT Registration Number** value of the test user that you created in the HMRC portal.

## <a id='auth'></a>Obtain an authorization code for testing interoperation

Follow these steps to get an authorization code.

> [!IMPORTANT]
> The authorization code is valid for only 10 minutes. You must obtain the access token during that time. Otherwise, the authorization code expires. In that case, you can use the same test user credentials to get a new authorization code.

1. In Finance, go to **Tax** \> **Setup** \> **Electronic messages** \> **Web applications**, and select the **Sandbox HMRC** web application.
2. On the Action Pane, select **Get authorization code**.
3. Select **Yes** to confirm that you want to initialize the authorization process.
4. In the **Electronic reporting parameters** dialog box, in the **Scope** field, enter **read:vat write:vat**. Then select **OK**.
5. In the **System administrator consent** dialog box, select the checkbox to confirm that you want to enable interoperation with HMRC's MTD API and use external web services. Your privacy is important to us. To learn more, read our [privacy notice](emea-gbr-mtd-vat-integration.md#privacy-notice).
6. Select **Agree** to continue, and then, in the HMRC portal, select **Continue** at the bottom of the page.
7. In the HMRC portal for authorization, on the **Sign in** page, enter the **User ID** and **Password** values that you saved in the [Obtain test user credentials](#user) section of this article.
8. Select **Grant authority**.
9. The **Authorisation granted** page shows the authorization code that HMRC granted to you for testing in the sandbox application. Copy this authorization code to the clipboard.

## Obtain an access token for testing interoperation

You should initialize retrieval of an access token within 10 minutes after HMRC grants an authorization code. Otherwise, the authorization code expires, and you must get a new one.

1. In Finance, go to **Tax** \> **Setup** \> **Electronic messages** \> **Web applications**, and select the **Sandbox HMRC** web application.
2. On the **Web applications** page, on the Action Pane, select **Obtain access token** to request an access token from HMRC.
3. In the **Authorization code** field, paste the authorization code that you copied from the HMRC portal in the previous procedure. Then select **OK**. The access token request is sent to HMRC, and the access token from the response that is received is automatically saved in Finance. You can't view the access token from the user interface (UI). However, the **Access token will expire in** field shows the validity period of the access token.

![Obtaining an access token.](../media/uk-mtd-token.png)

Every access token is valid for four hours after HMRC creates it. During interoperation with HMRC, the system automatically handles the process of refreshing the access token. Therefore, you don't have to manually refresh it. However, if you want to manually refresh the access token, on the **Web applications** page, on the Action Pane, select **Refresh access token**. A refresh access token request is sent to HMRC, and a new access token from the response that is received is automatically saved in Finance.

## Retrieve VAT obligations from HMRC for testing interoperation

After you successfully obtain an access token, your sandbox application is ready to interoperate with HMRC.

1. In Finance, go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and select the **UK MTD VAT TEST** processing. The page shows information about VAT obligations and returns, and is used for interoperation with the HMRC web service.
2. On the **Messages** FastTab, select **New**.
3. In the **Run processing** dialog box, in the **Action** field, select **Create VAT obligation request**. Then select **OK**. A new electronic message is created that has a status of **New obligation request**.
4. Enter dates in the **From date** and **To date** fields. These fields are mandatory for electronic messages that retrieve VAT obligations. However, the response from HMRC's sandbox application doesn't depend on the values. It always contains the same information about obligation periods.
5. In the **Description** field, enter a description of your message. This field is optional for electronic messages that retrieve VAT obligations.

    No additional fields are applicable to this type of electronic message.

6. Select **Send report** to initialize the retrieval of VAT obligation information from HMRC.
7. In the **Run processing** dialog box, the **Test retrieve VAT obligations** action is automatically defined, and information is filled in by the system. Select **OK**.

    ![Retrieving VAT obligations from HMRC.](../media/uk-mtd-obligation.png)

8. In the **Request identification information** dialog box, select the checkbox to consent to providing the information in fraud prevention headers as part of the VAT request to HMRC. Then select **Submit**. Your privacy is important to us. To learn more, read our [privacy notice](emea-gbr-mtd-vat-integration.md#privacy-notice).

    A request in JavaScript Object Notation (JSON) format is created and sent to the HMRC web application. The response that is received from HMRC is attached to the electronic message. Based on the response, new electronic messages for the VAT return will be created.

    ![VAT obligation information received.](../media/uk-mtd-response.png)

HMRC uniquely identifies each VAT return period by using a **periodKey** parameter. This parameter is stored in Finance. However, according to HMRC requirements, users must not be able to see the **periodKey** value in the UI. Therefore, the **periodKey** additional field is used to store the **periodKey** value in the **UK MTD VAT TEST** processing. This field is set up as a hidden field, so that users can't see its value. To ensure compliance with HMRC requirements, don't change this setup for the **periodKey** additional field.

The following illustration shows the lifecycle of electronic message processing for the retrieval of VAT obligations.

![Lifecycle of electronic message processing for VAT obligation retrieval.](../media/mkd-process.png)

The last step of the processing is an **Import VAT obligations** action of the **Electronic reporting import** type. The system defines the following behavior for this step:

- If a VAT obligation from the response doesn't exist in the database, and the status of that VAT obligation in HMRC is **Open**, a new electronic message is created that has a status of **New VAT return**.
- If a VAT obligation from the response doesn't exist in the database, and the status of that VAT obligation in HMRC is **Fulfilled**, a new electronic message is created that has a status of **Completed VAT return**.
- If a VAT obligation from the response does exist in the database, the system verifies the values of the **HMRC status**, **Due date**, and **Received date** additional fields. It then syncs those values with the information from the response.

All the actions that are performed for electronic messages are logged and can be viewed on the **Action log** FastTab.

## Collect data for a VAT return

The process of preparing and submitting a VAT return for a period is based on sales tax payment transactions that were posted during the [Settle and post sales tax](../../general-ledger/tasks/create-sales-tax-payment.md) job. For more information about sales tax settlement and reporting, see [Sales tax overview](../../general-ledger/indirect-taxes-overview.md).

Before you start to prepare and submit a VAT return to HMRC, complete the regular **Settle and post sales tax** job for the period that you will report to HMRC. When this job is run, new sales tax payment transactions are created. To view these sales tax payments, go to **Tax** \> **Inquiries and reports** \> **Sales tax Inquiries** \> **Sales tax payments**. You can review the resulting values for each sales tax payment transaction on the **VAT 100** report in Excel format.

You can run the **Settle and post sales tax** job several times for the same period before you submit a VAT return to HMRC. All the sales tax payment transactions can be included on the same VAT return report for a period. The transactions that the system fills in for reporting depend on the sales tax settlement period that is defined in the **Populate VAT return records** action for the processing. You can also include sales tax payment transactions from several legal entities in one VAT return that will be reported as a VAT group. For more information, see [Define a sales tax settlement period](emea-gbr-mtd-vat-integration-setup.md#settlement).

> [!IMPORTANT]
> MTD VAT lets you submit a VAT return only one time for each reporting period. As HMRC states on the official website, the current amendment process will remain in place for VAT:
>
> - If the net value of the errors on the VAT return is less than £10,000, the company will amend those errors on the next VAT return.
> - If the net value of the errors exceeds £10,000, the company must complete the VAT 652 form, which is available on the Gov.UK website.

When the **Settle and post sales tax** job is completed, you can prepare a report for electronic submission. The first step of data preparation is to collect sales tax payment transactions that are related to the period.

1. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and select the **UK MTD VAT TEST** processing.
2. On the **Message** FastTab, select the electronic message that is created in **New VAT return** status.
3. Update the **Start date** and **End date** fields of the record, so that the dates are consistent with the sales tax settlement period that you previously completed the sales tax settlement procedure during. VAT data can be collected only for electronic messages that have a status of **New VAT return**.
4. On the **Message** FastTab, select **Collect data**.
5. In the **Run processing** dialog box, the **Populate VAT return records** action is predefined. Select **OK**.
6. The system collects the sales tax payment transactions that were posted in the period that is defined by the **From date** and **To date** fields. You can review the collected sales tax payment transactions on the **Message items** FastTab.
7. If, for some reason, a sales tax payment transaction that the system entered must be excluded from the report, you can delete it. Alternatively, you can update its status to **Excluded** by selecting **Update status** on the **Message items** FastTab. Transactions that have a status of **Excluded** aren't considered for reporting. You can also change the status of a transaction from **Excluded** back to **Populated** by selecting **Update status** on the **Message items** FastTab.
8. You can repeatedly select **Collect data** on the **Message** FastTab until the electronic message is moved to the next status.
9. After data is collected, select **Update status** on the **Messages** FastTab.
10. In the **Update status** dialog box, the **Ready to generate VAT return** status is predefined. Select **OK** to mark the electronic message as ready for report generation. The status of the electronic message items that are linked to the electronic message is updated to **To be reported**.
11. If, for some reason, you must go back to step 4 and continue to collect data or change the status of electronic message items, select **Update status** on the **Messages** FastTab, select **New VAT return** in the **New status** field, and then select **OK**.

The **Action log** FastTab saves information about all the actions that are performed for the electronic message.

After an electronic message has a status of **Ready to generate VAT return**, you can initialize report generation. Two options are available:

- **Preview VAT return** – The file is generated in Excel format and attached to the electronic message. No statuses are changed.
- **Generate file for submission** – The file is generated in JSON format and attached to the electronic message. The status of the electronic message is updated to **Generated VAT return**, and the status of the linked electronic message items is updated to **Reported**.

## Generate a VAT return in Excel format for preview

Follow these steps to generate a VAT return in **VAT 100** report format in Excel.

1. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and select the **UK MTD VAT TEST** processing.
2. On the **Messages** FastTab, select the electronic message record that is related to the period that you want to generate a file for, and then select **Generate report**. The **Generate report** button is available only for electronic messages that have the following statuses:

    - **Ready to generate VAT return** – The user changes the electronic message status to this value by selecting **Update status**.
    - **Error VAT return generation** – If an error occurs during report generation, the electronic message status is changed to this value.
    - **Error VAT return submission** – If an error occurs during report submission, the electronic message status is changed to this value. The response that includes a description of the error is attached to the action log.

3. In the **Run processing** dialog box, select **Preview VAT return**, and then select **OK**. The file is generated in Excel format and attached to the electronic message. No statuses are changed.
4. To view the file, select the electronic message, and then select **Attachments** (the paper clip symbol) in the upper-right corner of the page.
5. On the **Attachments** page for the selected message, select the last attachment (**VAT statement.xlsx**), and then, on the Action Pane, select **Open**. The file is opened in Excel.

You can regenerate the **VAT 100** report several times before you generate the report in JSON format. At that point, the electronic message status is changed to **Generated VAT return**.

## Generate a VAT return in JSON format

MTD VAT accepts VAT returns in JSON format only. Follow these steps to generate a VAT return in JSON format.

1. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and select the **UK MTD VAT TEST** processing.
2. On the **Messages** FastTab, select the electronic message record that is related to the period that you want to generate a file for, and then select **Generate report**.
3. In the **Run processing** dialog box, select **Generate file for submission**, and then select **OK**. The file is generated in JSON format and attached to the electronic message. The electronic message status is updated to **Generated VAT return**, and the status of the electronic message items that are linked to the electronic message are updated to **Reported**.
4. To view the file, select the electronic message, and then select **Attachments** (the paper clip symbol) in the upper-right corner of the page.
5. On the **Attachments** page for the selected message, select the last attachment (**VAT\_return.json**), and then, on the Action Pane, select **Open**.

If, for some reason, you must regenerate a VAT return in JSON format before it's submitted to HMRC, select **Update status** on the **Messages** FastTab to update the status of the related electronic message to either **New VAT return** or **Ready to generate VAT return**, depending on whether you must go back to the data collection step or the file generation step.

## Submit VAT returns to HMRC for testing interoperation

When a VAT return in JSON format is generated and ready to be submitted to HMRC, initialize its submission to the sandbox application. The last JSON file that was attached to the electronic message is used for the submission. To help prevent discrepancies, we recommended that you delete any unnecessary JSON files that are attached to the electronic message that you will submit to HMRC. To find and clean up unnecessary attachments, select the electronic message, and then select **Attachments** (the paper clip symbol) in the upper-right corner of the page. The **Attachments** page for the selected message is opened.

Follow these steps to submit a VAT return.

1. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and select the **UK MTD VAT TEST** processing.
2. On the **Messages** FastTab, select the electronic message record that is related to the period that you want to submit the VAT return for, and then select **Send report**. The **Send report** button is available only for electronic messages that have the following statuses:

    - **Generated VAT return** – The electronic message status is automatically updated to this value when a VAT return in JSON format is successfully generated and attached to the electronic message.
    - **Error VAT return submission** – If an error occurs during report submission, the electronic message status is changed to this value. The response that includes a description of the error is attached to the action log.

3. In the **Run processing** dialog box, the **Test submit VAT return** action is predefined. Select **OK**.
4. The dialog box that appears contains mandatory declaration text that is required by HMRC. To remain compliant with HMRC requirements, don't modify or delete this declaration text in the setup of the **Test submit VAT return** action. By selecting **OK** in this dialog box, you submit VAT information, and you confirm that the information is true and complete. A false declaration can lead to prosecution.

    A VAT return can be submitted to HMRC only one time for each period. Therefore, make sure that you want to submit the VAT return before you accept the declaration. If you aren't sure whether the VAT return is ready to be submitted, select **Cancel**.

    When you select **OK**, the VAT return in JSON format that is related to the selected electronic message is submitted to HMRC. If the VAT return is successfully submitted to HMRC, the status of the electronic message is updated to **Sent VAT return**, and the response from HMRC is attached to the electronic message.

5. In the **Request identification information** dialog box, select the checkbox to consent to providing the information in fraud prevention headers as part of the VAT request to HMRC. Then select **Submit**. Your privacy is important to us. To learn more, read our [privacy notice](emea-gbr-mtd-vat-integration.md#privacy-notice).

    The system automatically runs the **Import response for VAT return** action. This action causes the **Processing date** additional field of the electronic message to reflect information from the response. Additionally, the system updates the status of the electronic message to **Completed VAT return** and updates the status of the electronic message items to **Submitted**.

    ![Submitting VAT returns to HMRC.](../media/uk-mtd-vat-return.png)

    If, for some reason, the **Import response for VAT return** action isn't automatically run, you can manually initialize it by selecting **Import response** on the **Messages** FastTab. the **Import response** button is available only for electronic messages that have a status of **Sent VAT return**. The electronic message status is automatically updated to this value when a VAT return in JSON format is successfully submitted to the electronic message.

The **Action log** FastTab saves information about all the actions that are performed for the electronic message.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
