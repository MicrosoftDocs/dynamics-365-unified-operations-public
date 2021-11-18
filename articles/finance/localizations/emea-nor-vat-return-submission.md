---
# required metadata

title: Submit a VAT return to Altinn web service
description: This topic explains how to submit a VAT return to Altinn web service of Norway.
author: liza-golub
ms.date: 11/18/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Norway
# ms.search.industry: 
ms.author: elgolu
ms.search.validFrom: 2021-11-18
ms.dyn365.ops.version: AX 10.0.22

---

# Submit a VAT return to Altinn web service

When you successfully obtained an access token for Altinn, your Finance is ready to interoperate with Altinn web service to submit VAT return.
Process of VAT return submission to Altinn is composed of lots of steps. For full description of the submission process, see [API](https://skatteetaten.github.io/mva-meldingen/english/api/) page.

The process of VAT return generation and direct submission to Altinn from Finance is supported by using [Electronic Messaging](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/electronic-messaging) (EM) functionality. When you [Import a package of data entities that includes a predefined Electronic messaging (EM) setup](emea-nor-vat-return-setup#em-setup) to your legal entity, all the necessary actions are imported to you system to submit VAT return to Altinn. The following diagram represents simplified schema of the EM processing delivered with **NO VAT return – Altinn** setup file.

![Schema of the EM processing delivered with NO VAT return – Altinn setup file.](media/emea-nor-vat-return-em-processing.png)

To simplify the process of VAT return submission for the user, most of actions are aggregated into inseparable sequences and are run automatically by the system once the first action from the sequence is initiated.

This allows to significantly simplify the process for the user and reduce user’s steps to the following list.

1.	[Create message](#create-message)
2.	[Collect sales tax payments](#collect-sales-tax-payments)
3.	[Mark message as ready to generate VAT return](#ready-to-generate)
4.	[Preview VAT return in Excel](#preview-vat-return)
5.	[Generate VAT return](#generate-vat-return)
6.	[Validate VAT return in Tax Administration web service](#validate-vat-return)
7.	[Submit VAT return](#submit-vat-return)
8.	[Download attachments](#download-attachments)

## <a id="create-message"></a>Create message

This step is composed of one single action – **NO VAT Create message**.

1.	Go to **Tax** > **Inquires and reports** > **Electronic messages** > **Electronic messages**.
2.	Select **NO VAT return** EM processing on the lefthand side of the page.
3.	Click **New** button on the Messages tab.
4.	**NO VAT Create message** action is predefined in the **Run processing** dialog. Click **OK**.
5.	As a result, new electronic message is created.
6.	Fill in **From date** and **To date** for the message with dates of the period for which you want to submit VAT return.
7.	Fill in **Description** field with some free test description. This description will not be included into report. This is an optional field.

![Create message.](media/emea-nor-vat-return-create-message.png)

## <a id="collect-sales-tax-payments"></a>Collect sales tax payments

This step is composed of one single action – **NO VAT Collect sales tax payments**.

1.	On the **Tax** > **Inquires and reports** > **Electronic messages** > **Electronic messages** page, select the message created on the previous step within **NO VAT return** EM processing.
2.	Click **Collect data** on the **Message** tab.
3.	**NO VAT Collect sales tax payments** action is predefined in the Run processing dialog. Click **OK**.
4.	As a result, sales tax payment lines posted during the period specified for the message are populated on the **Message items** tab in relation with the message selected.

![Collect sales tax payments.](media/emea-nor-vat-return-collect-sales-tax-payments.png)

According XSD schema of VAT return, VAT return can include a note containing either a value from the enumerated list of values or a free text note limited to 4000 symbols. 

To add a note containing value from the enumerated list, complete the following steps.

1.	Select electronic message for which you want to specify the note on the **Messages** FastTab.
2.	Expand **Message additional fields** FastTab and select **NO VAT Note for VAT return** additional field. 
3.	Select necessary value from the lookup field in the **Field value** column.

To add a note containing free text note limited to 4000 symbols, complete the following steps.

1.	Select electronic message for which you want to specify the note on the **Messages** FastTab.
2.	Expand **Message additional fields** FastTab and select **NO VAT Note for VAT return** additional field. 
3.	Select **fritekstnotat** value from the lookup field in the **Field value** column.
3.	Click on the clip button in the righthand corner of the page.
4.	Click **New** > **Note** on the Action pane.
5.	Specify your note in the **Note** field.
6.	This note will be included into the VAT return in XML format when generated.

## <a id="ready-to-generate"></a>Mark message as ready to generate VAT return

This step is composed of one single action – **NO VAT Ready to generate VAT return**.

1.	On the **Tax** > **Inquires and reports** > **Electronic messages** > **Electronic messages** page, select the message created on the previous step within **NO VAT return** EM processing.
2.	Click **Update status** on the **Message** tab.
3.	**NO VAT Ready to generate VAT return** action and **NO VAT Ready to generate VAT return** new status are predefined in the **Run processing** dialog. Click **OK**.
4.	As a result, message status is changed to **NO VAT Ready to generate VAT return** and **Generate report** button is enabled.

![Mark message as ready to generate VAT return.](media/emea-nor-vat-return-ready-to-generate.png)

To continue collecting data for the report, you can change status of the message back to **NO VAT New message created** by using **Update status** button.

## <a id="preview-vat-return"></a>Preview VAT return in Excel

This step is composed of one single action – **NO VAT Preview VAT return in Excel**.

1.	On the **Tax** > **Inquires and reports** > **Electronic messages** > **Electronic messages** page, select the message created on the previous step within **NO VAT return** EM processing.
2.	Click **Generate report** on the **Message** tab.
3.	Select **NO VAT Preview VAT return in Excel** action in the **Run processing** dialog. 
4.	For reporting periods containing big volume of tax transactions, we recommend running the report in batch. Expand **Run in the background** FastTab of the **Run processing** dialog and select **Batch processing** check box. Specify **Task description** and other parameters of the batch.
5.	Click **OK**.
6.	As a result, message status does not change, and new file is attached to the message.
7.	Click on the clip button in the righthand corner of the page, select **VAT return preview.xls**.
8.	Click **Open** button on the Action pane to preview VAT return in Excel format.

## <a id="generate-vat-return"></a>Generate VAT return

This step is composed of one single action – **NO VAT Generate VAT return**.

1.	On the **Tax** > **Inquires and reports** > **Electronic messages** > **Electronic messages** page, select the message created on the previous step within **NO VAT return** EM processing.
2.	Click **Generate report** on the **Message** tab.
3.	Select **NO VAT Generate VAT return** action in the **Run processing** dialog. 
4.	For reporting periods containing big volume of tax transactions, we recommend running the report in batch. Expand **Run in the background** FastTab of the **Run processing** dialog and select **Batch processing** check box. Specify **Task description** and other parameters of the batch.
5.	Click **OK**.

![Generate VAT return.](media/emea-nor-vat-return-generate-vat-return.png)

6.	As a result, message status changes to **NO VAT Return XML generated**, and new **mvamelding.xml** file is attached to the message.
7.	Click on the clip button in the righthand corner of the page, select **mvamelding.xml**.
8.	Click **Open** button on the Action pane to preview VAT return in XML format.

## <a id="validate-vat-return"></a>Validate VAT return in Tax Administration web service

This step is composed of **NO VAT Validation** sequence, including the following actions:

-	**NO VAT Send validation request** – this action transfers **mvamelding.xml** to Tax Administration API, receives **valideringsresultat.xml** file containing results of business validation of the **mvamelding.xml** and attaches **valideringsresultat.xml** file to the electronic message.
-	**NO VAT Import validation response** – this action parses information from the **valideringsresultat.xml** file and updates the status of the electronic message to **NO VAT Return validation passed successfully** in case when business validation by Tax Administration passes successfully or to **NO VAT Error VAT return validation** in case when there are some errors identified during business validation by Tax Administration. When there are some errors identified during business validation by Tax Administration, this action applies an XSLT transformation to the **valideringsresultat.xml** file and attaches transformed file to the record in the action log for further review by the user.
-	**NO VAT Generate request for instance** – this action prepares a request for the next step - **Submit VAT return**.

To run the **Validate VAT return in Tax Administration web service** step, you must complete the following tasks.

1.	On the **Tax** > **Inquires and reports** > **Electronic messages** > **Electronic messages** page, select the message created on the previous step within **NO VAT return** EM processing.
2.	Click **Send report** button on the **Message** tab.
3.	**NO VAT Send validation request** action is predefined in the Run processing dialog. 
4.	Click **OK** button.
5.	**NO VAT Send validation request**, **NO VAT Import validation response** and **NO VAT Generate request for instance** actions will be run automatically by the system one-by-one. As a result, electronic message status will be **NO VAT Return validation passed successfully** in case when business validation by Tax Administration passes successfully or to **NO VAT Error VAT return validation** in case when there are some errors identified during business validation by Tax Administration. 
6.	When there are some errors identified during business validation by Tax Administration, to review information about errors, expand **Action log** FastTab and select the line for **NO VAT Import validation response** action. Click on the clip button in the righthand corner of the page, select attached **html** file. Click **Open** on the Action pane. File will be open in a browser and user can review its content in table representation. When corrections are applied, you can regenerate the XML file again going back to the [Generate VAT return](#generate-vat-return) step.

## <a id="submit-vat-return"></a>Submit VAT return

When your **mvamelding.xml** file was successfully validated by the Tax Administration, the electronic message is in **NO VAT Return validation passed successfully** status and you can submit **mvamelding.xml** file to Altinn.

Submit VAT return step is composed of the following actions:

-	**NO VAT Send request to create instance** – this action sends a request to Altinn3-App API to create an instance for further VAT return submission, receives the response and attaches this response to the electronic message.
-	**NO VAT Import instance creation response** – this action imports necessary information from the response to the system for further submission.
-	**NO VAT Generate VAT return submission** – this action a creates special **konvolutt.xml** technical file that must be sent to Altinn3-App API preliminary to **mvamelding.xml** file.
-	**NO VAT Upload VAT return submission** – this action sends **konvolutt.xml** technical file to Altinn3-App API.
-	**NO VAT Upload VAT return** – this action sends **mvamelding.xml** file to Altinn3-App API.
-	**NO VAT Complete data filling** – this action sends request to complete transferring of VAT return to Altinn3-App API.
-	**NO VAT Complete VAT return submission** – this action request to complete submission process to Altinn3-App API.
-	**NO VAT Send feedback status request** – this action requests a status of validation process of the VAT return that was submitted. 
-	**NO VAT Import feedback status response** – this action imports status of the validation of VAT return to the system.
-	**NO VAT Send feedback request** – this action requests results of the validation of the VAT return that was submitted. 
-	**NO VAT Import feedback response** – this action imports necessary information from the response containing results of the validation of the VAT return.
-	**NO VAT Download validation result** – this action downloads the details of validation of VAT return.
-	**NO VAT Import final validation result** – this action imports information about the details of validation of VAT return to the system and updates the status of the electronic message to **NO VAT SUCCESSFUL VAT return submission to the Tax Administr** in case when no error were identified in the VAT return that was submitted or to **NO VAT Error validation of uploaded VAT return** in case when there are some errors identified in the VAT return that was submitted.

To run the **Submit VAT return** step, you must complete the following tasks.

1.	On the **Tax** > **Inquires and reports** > **Electronic messages** > **Electronic messages** page, select the message created on the previous step within **NO VAT return** EM processing.
2.	Click **Send report** button on the **Message** tab.
3.	**NO VAT Send request to create instance** action is predefined in the **Run processing** dialog. 
4.	Click **OK** button.
5.	All the actions included into the **Submit VAT return** step will be run automatically one-by-one.
6.	Sometimes it may take several minutes before feedback on the VAT return is ready on Tax Administration side. In this case **Submit VAT return** step will stop in the **NO VAT Feedback not provided** status. When **Submit VAT return** step is stopped in **NO VAT Feedback not provided status**, you should wait several minutes (5-10) and click **Send report** button on the **Message** tab again.
7.	**NO VAT Send feedback status request** action is predefined in the **Run processing** dialog. 
8.	Click **OK** button.
9.	**Submit VAT return** step is completed successfully when electronic message is in **NO VAT SUCCESSFUL VAT return submission to the Tax Administr** status.

## <a id="download-attachments"></a>Download attachments

After submission of VAT return is successfully completed, you can additionally download payment information in XML format and receipt in PDF.

1.	On the **Tax** > **Inquires and reports** > **Electronic messages** > **Electronic messages** page, select the message created on the previous step within **NO VAT return** EM processing.
2.	Click **Send report** button on the **Message** tab.
3.	Select** NO VAT Download receipt** or **NO VAT Download payment information** action in the **Run processing** dialog. 
4.	Click **OK** button.
5.	As a result, b**etalingsinformasjon.xml** (**NO VAT Download payment information**) or **kvittering.pdf** (**NO VAT Download receipt**) file will be attached to the electronic message.
6.	Click on the clip button in the righthand corner of the page, select **betalingsinformasjon.xml** or **kvittering.pdf**.
7.	Click **Open** button on the Action pane.
