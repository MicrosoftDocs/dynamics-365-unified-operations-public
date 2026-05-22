---
title: Generate printable FTI forms
description: Learn how to use the Electronic reporting (ER) framework to generate printable free text invoice (FTI) forms as Microsoft Office documents.
author: kfend
ms.author: filatovm
ms.topic: how-to
ms.date: 04/08/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-04-01
ms.dyn365.ops.version: Release 8.0
ms.assetid: 2685df16-5ec8-4fd7-9495-c0f653e82567
ms.custom: sfi-image-nochange
---

# Generate printable FTI forms

[!include[banner](../includes/banner.md)]

The Electronic reporting (ER) framework lets you generate printable free text invoice (FTI) forms as Microsoft Office documents. This article provides information about how to build your own configurations as well as details of available configuration templates.

## Overview

In addition to the existing capability of generating printable FTI forms by using Microsoft SQL Server Reporting Services (SSRS), you can now use the ER framework. You can manage printable FTI forms in Microsoft Office Excel and Word. You can also modify the layout, data flow, and formatting to meet specific requirements without making code changes.

> [!NOTE]
> If you want to start with an overview of existing ER configurations for this sample of the printable FTI forms solution, you can go directly to section **Download sample ER configurations to generate printable FTI forms** later in this article.

## Create customized configurations for FTI printable forms

As part of your customized solution for printable FTI forms, you must create a set of ER configurations.

### Configure the ER data model

Your application must include the ER data model configuration that contains a data model that describes the customer invoicing business domain. As a requirement, the name of the data model must be **CustomersInvoicing**. For information about how to design ER data models, see [ER Design domain specific data model](tasks/er-design-domain-specific-data-model-2016-11.md).

### Configure the ER model mapping

Your application must include the ER model mapping for the CustomersInvoicing data model. You can add the model mapping to either the ER data model configuration or the ER model mapping configuration. However, the name of the root descriptor of the model mapping must be **FreeTextInvoice**.

The mapping must contain the following data sources:

- Data source type: **Table records**

  - This data source must be named **CustInvoiceJour**.
  - It must refer to the CustInvoiceJour application table.
  - At runtime, it passes from the application to the ER model mapping the list of invoices that you select for printing.

- Data source type: **Object**

  - This data source must be named **PrintMgmtPrintSettingDetail**.
  - It must refer to the **PrintMgmtPrintSettingDetail** application class.
  - At runtime, it passes from the application to the ER model mapping details of the print management settings for the ER format that is running.

You can find the details of the application integration with the ER framework in the **ERPrintMgmtReportFormatSubscriber** class (ER Application Suite integration model) in the source code of the application.

For more information about the design of ER model mappings, see [Define ER model mappings and select data sources for them](tasks/er-define-model-mapping-select-data-sources-2016-11.md).

### Configure the ER format

In your application instance, you must have the ER format configuration that you use to generate FTI forms.

> [!NOTE]
> Create this format configuration for the **CustomersInvoicing** data model. Use the model mapping that has the **FreeTextInvoice** root descriptor.

For information about how to configure ER formats, see [ER Create a format configuration (November 2016)](tasks/er-format-configuration-2016-11.md). For information about how to design ER formats to generate reports in OpenXML format, see [ER Design a configuration for generating reports in OPENXML format (November 2016)](tasks/er-design-reports-openxml-2016-11.md).

## Configure print management

To generate FTI forms by using the ER framework, assign ER formats in the same way that you assign SSRS reports. To associate the ER format with all Accounts receivable FTIs, go to **Accounts receivable** > **Setup** > **Forms** > **Form setup** > **General** > **Print management** > **Free text invoice** > **Original**. To associate the ER format with a specific customer or invoice, follow these steps:

1. Go to **Accounts receivable** > **Invoices** > **All free text invoices**.
1. Select the FTI to associate the ER format with, and open the **Print management setup** page.
1. Select the document level to specify the scope of invoices for processing.
1. Select the ER format for the specified document level.

:::image type="content" source="media/FTIbyGER-PMSetting.png" alt-text="Screenshot of the Print management setup page.":::

> [!NOTE]
> Only ER formats that use the **FreeTextInvoice** root descriptor of the **CustomersInvoicing** data model appear in the **Report format lookup** field for the selected format.

## Generate FTI forms

The ER framework generates FTI forms the same way it generates SSRS reports.

To generate FTI forms, select invoices by range or by selection.

:::image type="content" source="media/FTIbyGER-InvoiceSelection.png" alt-text="Screenshot of the invoice selection options.":::

:::image type="content" source="media/FTIbyGER-InvoiceExcelPreview.png" alt-text="Screenshot of the invoice preview in Excel format.":::

When you use ER formats to print FTI forms, the default ER file destinations are used. You can't change the destination. For more information about how to configure the ER destinations for ER formats, see [Electronic reporting (ER) destinations](electronic-reporting-destinations.md).

You can also generate FTI forms when you post an FTI, by turning **Print invoice** on and turning **Use print management destinations** off.

> [!NOTE]
> When you use ER formats to print FTI forms, the default ER file destinations are used. You can change the default destination at runtime if the destination is already configured. To change the destination, you must have the following security privilege:
>
> - **Name:** ERFormatDestinationRuntimeMaintain
> - **Label:** Maintain electronic reporting format destination during runtime

:::image type="content" source="media/FTIbyGER-ERFileDestinationSetting.png" alt-text="Screenshot of the Electronic reporting destination settings.":::

:::image type="content" source="media/FTIbyGER-ERFileDestinationUsage.png" alt-text="Screenshot of the Electronic reporting format destination usage.":::

The ER framework currently supports the following destinations for generated documents:

- **Downloaded file** – You can save generated forms by downloading them through the browser.
- **Screen** – Microsoft 365 Excel previews generated FTI forms in Excel format.
- **SharePoint folder** – The Document management framework settings store generated forms.
- **Application archive** – Microsoft Azure Storage stores generated forms as attachments of execution log records.
- **Email** – Generated forms are sent as email attachments.

> [!NOTE]
> You can't send the generated FTI forms directly to the printer, because direct printing that uses the Dynamics Printer Routing Agent isn't currently supported.

## Download sample ER configurations to generate printable FTI forms

You can download sample ER configurations to use as a template for your FTI solution. Microsoft Dynamics Lifecycle Services stores these configurations in the Shared asset library. The configurations include:

- The **Customer invoicing model** configuration contains the required data model and model mapping.
- The **Customer FTI report (GER)** configuration contains the sample format.

> [!NOTE]
> These configurations are samples to help clarify possible scenarios. The future of these configurations depends on the results of this evaluation and any feedback that you provide.

### Features implemented in the sample ER format

In the sample ER format configuration, an Excel file is used as a template to generate FTI forms.

:::image type="content" source="media/FTIbyGER-ERFormat.png" alt-text="Screenshot of the Format designer.":::

Currently, this sample ER format supports the following features to generate FTI forms:

- The system generates FTI forms for both original invoices that you posted and original invoices that you didn't post yet. Corrected invoices and credit notes aren't supported.
- The system generates FTI forms in the invoice language. The format of values and dates in the generated forms is based on the settings of the user's client locale.
- Generated invoices show data unavailability notifications if there are no lines in the invoices that are processed.
- Generated invoice headers are based on the paper format that you select for the FTI form on the **Accounts receivable parameters** page. Company details appear in the header of the generated invoice form only if the paper format is blank.
- Generated invoice forms show company and customer tax exempt numbers when you select the appropriate option for the FTI form on the **Accounts receivable parameters** page.
- The generated invoice lines and invoice totals sections show the default invoice's monetary details in the invoice registration currency.
- The generated invoice totals section can show monetary details in the euro currency and the invoice registration currency when you enable the **Print amount in currency representing the euro** option on the **Accounts receivable parameters** page.
- Generated invoice forms show any process invoice notes that are available, based on settings on the **Accounts receivable parameters** page. Notes are included for both the whole invoice and each invoice line.
- Generated invoice forms include notes for the customer FTI form and the processing invoice language when you configure them in the AR form notes list.
- Depending on the Print management settings, generated invoices include custom footer text when you configure it for the invoice language, the ER format, and the FTI document scope.
- The totals section of generated invoice forms includes any cash discount information that is available.
- The payment schedule section of generated invoice forms includes any payment schedule details that are available.
- The markup section of generated invoice forms includes any charges transactions that are available.
- Generated invoice forms include sales tax details, based on the **Sales tax specification** setting on the **Accounts receivable parameters** page. This section can show tax details either in the invoice registration currency only, or in the invoice registration currency and the company accounting currency at the same time.
- Generated invoice forms show direct debit notification details. For example, they show when the method of payment that has the mandatory direct debit mandate ID was selected for the invoice, when the processing invoice was registered in the euro currency, and when the direct debit mandate ID was defined for the invoice.
- Generated invoices show any prepayment details that are available for posted invoices.
- Generated invoice forms can be sent to an invoice customer as an email attachment. You should configure the appropriate ER file destination for the ER format that you're using.

### Country/region-specific features

The sample ER format includes the following country/region-specific features to show how you can handle specific requirements in ER configurations.

#### Norway

The generated invoice form header includes the Enterprise register term when you process the invoice for a legal entity that you configure as follows:

- Use the country/region context for Norway.
- Activate the **Print Foretaksregisteret** parameter on sales documents.

#### Spain

The generated invoice form header includes the **Special regime for cash accounting method** term when you process the invoice for a legal entity that you configure as follows:

- Use the country/region context for Spain.
- Enable the special regime for the cash accounting method on the invoice processing date.

When cash discount details, such as the cash discount amount and invoice line net amount, are available, present them in the invoice totals section of the generated invoice form when you process the invoice for a legal entity that you configure as follows:

- Use the country/region context for Spain.
- Turn on **Cash discount is applied in the invoice** in the invoice option (**General ledger parameters** > **Sales tax section**).

#### Italy

Include the goods discount mark on the invoice lines of the generated invoice when you process the invoice for a legal entity that you configure by using the country/region context for Italy.

#### Finland

In addition to the generated invoice form, you can generate Giro money transfer slips as follows:

- For the legal entity that uses the country/region context for Finland, and that has at least one bank account that is marked as **Giro account** and **Bank bar code**.
- For an invoice that is marked as required for the **Finnish** associated payment attachment.

:::image type="content" source="media/FTIbyGER-GiroSlip.PNG" alt-text="Screenshot of the Giro money transfer slip.":::

> [!NOTE]
> The sample ER format is configured to optionally generate the Giro money transfer slips in the separate worksheet.

> [!NOTE]
> You must first install the font that is used to generate the bar code on the local machine where you preview the generated invoice form in Excel format.

### Use the sample ER format to configure email destinations

Use the following elements of the sample ER format to configure email destinations:

- Access the email address of a customer contact through the following ER expression: **model.InvoiceBase.Contact.ElectronicMail**.
- Access the email subject text through the following ER expression: **Emailing.TxtToUse.Subject**.
- Access the email body text through the following ER expression: **Emailing.TxtToUse.Body**.

:::image type="content" source="media/FTIbyGER-ERFileDestinationSettingEmail.png" alt-text="Screenshot of the email destination settings.":::

The sample ER format defines the default text of the email's subject and body. The language depends on the format's labels. If you don't add a custom organization email template that uses the predefined **ERFTITMP** ID, this default text is used for emails.

> [!NOTE]
> The sample ER format defines the **ERFTITMP** email template ID. You can change this ID as needed in a new ER format that you create from this sample format.

If you add the organization email template that uses the predefined **ERFTITMP** ID for the legal entity that you're processing the invoice for, the template for the email subject and body text is used to generate the email.

:::image type="content" source="media/FTIbyGER-EmailTemplate.png" alt-text="Screenshot of the Organization email templates page.":::

:::image type="content" source="media/FTIbyGER-EmailTemplateBody.png" alt-text="Screenshot of the upload email template body.":::

The **Emailing.TxtToUse.Subject** ER expression of the sample ER format is configured to replace any occurrences of the placeholder %1 with the processing invoice ID.

The **Emailing.TxtToUse.Body** expression of the sample format is configured for the following substitutions for placeholders:

- "%1" is replaced with the name of the customer's contact person.
- "%2" is replaced with the company name.
- "%3" is replaced with the customer name.
- "%4" is replaced with the name of the company's contact person.
- "%5" is replaced with the job title of the company's contact person.
- "%6" is replaced with the email address of the company's contact person.

:::image type="content" source="media/FTIbyGER-Email.PNG" alt-text="Screenshot of the generated email.":::

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
