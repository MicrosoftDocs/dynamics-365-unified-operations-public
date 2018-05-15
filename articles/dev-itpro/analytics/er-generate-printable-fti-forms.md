---
# required metadata

title: Generate printable FTI forms 
description: This topic explains how to use the Electronic reporting (ER) framework to generate printable free text invoice (FTI) forms as Microsoft Office documents.
author: NickSelin
manager: AnnBe
ms.date: 05/14/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 220314
ms.assetid: 2685df16-5ec8-4fd7-9495-c0f653e82567
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2018-04-01
ms.dyn365.ops.version: Release 8.0

---

# Generate printable FTI forms

[!include[banner](../includes/banner.md)]

In addition to the existing capability of generation of printable free text invoice (FTI) forms by using SSRS, you can now use for this purpose the ER framework. It gives you the possibility to manage FTI printable forms in Microsoft Office formats (Excel, Word) and modify them (layout, data flow, formatting, etc.) without application code changes to satisfy specific requirements. If you want to start with overview of  existing FTI configurations, you can go directly to section Download sample ER configurations to generate FTI printable forms.

## Create your customized configurations for FTI printable forms
You need to create a set of ER configurations as parts of your customized solution for FTI printable forms.

### Configure ER data model
You need to create to your application instance the ER data model configuration that contains a data model describing the customers invoicing business domain.
Note. It is required that the included data model must be named as CustomersInvoicing. 
Explore the related page for more details about the design of ER data models.

### Configure ER model mapping
You need to have in your application instance the ER model mapping for the CustomersInvoicing data model. It can be a model mapping that is enclosed either in the ER data model configuration or in the ER model mapping configuration.
Note. It is required to name the root descriptor of this model mapping for FTI forms handling as FreeTextInvoice.
Note. It is required that this model mapping contains the following data sources:
1.	Data source of the Table records type
a.	Named as CustInvoiceJour;
b.	Refers to the CustInvoiceJour application table;
c.	Using to pass at run-time from the application to the executing ER model mapping the list of invoices selected for printing.
2.	Data source of the Object type
a.	Named as PrintMgmtPrintSettingDetail;
b.	Refers to the PrintMgmtPrintSettingDetail application class;
c.	Using to pass at run-time from the application to the executing ER model mapping details of Print management settings for the executing ER format.
The details of the application integration with the ER framework can be found in the source code of the application ERPrintMgmtReportFormatSubscriber class (ER Application Suite integration model).
Explore the related page for more details about the design of ER model mappings.

### Configure ER format
You need to have in your application instance the ER format configuration that will be used to generate FTI forms. 
Note. It is required that this format configuration has been created for the CustomersInvoicing data model and uses the model mapping with the FreeTextInvoice root descriptor.
Explore this page to learn how ER formats can be configured. Review this page to learn how ER formats can be designed to generate reports in OpenXML format.

## Configure Print management
Assignment of ER formats for generation of FTI forms by using ER framework can be done in the same way as for the assignment of SSRS reports. You may associate the created ER format with all Accounts receivable free text invoices by using the following application path: Accounts receivable > Setup > Forms > Form setup > General > Print management > Free text invoice > Original. If you want to associate the created ER format with a specific customer or an invoice, you need to do the following:
1.	Open the Accounts receivable > Invoices > All free text invoices form;
2.	Select the desire free text invoice;
3.	Open the Print management setup form;
4.	Choose the documents’ level to identify the scope of invoices for processing with using ER formats;
5.	Select the desired ER format for chosen documents’ level:
Note. The only ER formats that use the root descriptor FreeTextInvoice of the CustomersInvoicing data model can be visible in this Report format lookup field for format’s selection.

## Generate FTI forms
Same execution points are used to generate FTI forms by using ER framework as for execution of SSRS reports.
1.	Generate FTI forms choosing invoices either by range or by selection.
Note. When you use ER formats to print FTI forms this way, the default ER file destinations are used for executed ER format. User have no option to change this behavior. Review this page to learn how the ER destinations can be configured for ER formats.
2.	Generate FTI forms during free text invoice posting:
a.	Post free text invoice.
b.	Turn Print invoice on.
c.	Turn Use print management destination off.
Note. When you use ER formats to print FTI forms this way, the default ER file destination is used for executed ER format. User will be able to change the default destination at run-time when this destination has been previously configured. To have this capability, the user must be granted the following security privilege:
-	Name	ERFormatDestinationRuntimeMaintain
-	Label	Maintain electronic reporting format destination during runtime
Currently, the following destinations are supported by ER framework for generated documents:
-	Downloaded file
o	Generated forms are offered by using browser as downloads
-	Screen
o	Office 365 Microsoft Excel is used to preview FTI forms in Excel format
-	SharePoint folder
o	Generated forms are stored based on setting of the Document management framework
-	Application archive
o	Files of Azure storage as attachments of records of execution log
-	Email
o	Generated forms are sent as e-mail attachment
Note. You can’t send the generated FTI form directly to the printer as the direct printing by using the Dynamics Printer Routing Agent is not supported by the ER framework yet.

## Download sample ER configurations to generate FTI printable forms
You can download sample ER configurations to start using them as a template for your FTI solutions. They are stored in the Shared asset library of the Microsoft Lifecycle Services:
-	Customer invoicing model configuration containing the required data model and model mapping;
-	Customer FTI report (GER) configuration that contains the sample format.
Note.  Be aware that these configurations have been created as samples for helping to understand possible scenarios and this feature needs. The future of these configurations will depend on the results of this evaluation and received feedbacks.

### Features implemented in the sample ER format
Microsoft Excel document is used as a template in the sample ER format configuration for generation of FTI forms.
Currently, this sample ER format supports the following features for generation of FTI forms:
1.	FTI forms can be generated for not posted yet and posted original invoices. Corrected invoices as well as credit notes are not supported.
2.	FTI forms is generated on the invoice language. Note that the values and dates in the generated form are formatted based on the settings of the user’s client locale.
3.	Instead of the invoice lines, the section with the notification about data unavailability will be shown in the generated form when there are no lines in the processing invoice.
4.	Invoice header will be generated based on the paper format that has been chosen in Accounts receivable (AR) forms parameters for the FTI form. Company details will be placed to the header of the generated invoice form only for the blank paper format.
5.	Company and customer tax exempt numbers are shown in the generated invoice form when the appropriate option has been selected in AR forms parameters for the FTI form.
6.	Invoice lines as well as invoice totals sections are shown presenting by default invoice’s monetary details in the invoice registration currency.
7.	In addition to the invoice registration currency, invoice totals section can show monetary details in the euro currency. It will happen when the option Print amount in currency representing the euro option of the AR forms parameters has been turned on.
8.	Processing invoice notes are presented (when available) in the generated invoice form based on the corresponding setting of the AR forms parameters for the FTI form (notes for the entire invoice as well as for each invoice line).
9.	Form notes are presented in the generated invoice form when they have been configured in the AR form notes list:
a.	for the customer FTI form;
b.	for the processing invoice language.
10.	Custom footer text is presented at the end of the generated invoice when it has been configured by using Print management tool:
a.	for the processing invoice language;
b.	for using ER format and FTI documents scope.
11.	Cash discount information is presented (when available) in the invoice’s totals section.
12.	Payment schedule details are presented (when available) in the invoice’s payment schedule section.
13.	Charges transactions are presented (when available) in the invoice’s markup section.
14.	Sales tax details are optionally shown in the dedicated for that section of the generated invoice form depending on the Sales tax specification option of the AR forms parameters. This section can present tax details either in the invoice registration currency only or in the invoice registration currency and company accounting currency simultaneously.
15.	The direct debit notification details will be shown in the dedicated for that section of the generated invoice form:
a.	when the method of payment with mandatory direct debit mandate ID has been selected for the invoice;
b.	when the processing invoice has been registered in euro currency;
c.	when the direct debit mandate ID has been defined for the invoice.
16.	When available, prepayment details can be shown in the dedicated for that section (for posted invoices only).
17.	Generated invoice form can be sent to an invoice customer via email as an attachment. The appropriate ER file destination should be configured to do so for using ER format (see more details below).

### Country specific features implemented in the sample ER format
The following country specific features have been implemented in the sample ER format to shown how the specific requirements can be handled in such ER configurations.

#### Norway
1.	The Enterprise register term will be placed to the header of the generated invoice form when this invoice has been processed for the legal entity configured as follows:
a.	Using the country context for Norway;
b.	Having the parameter Print Foretaksregisteret on sales documents turned on.

#### Spain
2.	The Special regime for cash accounting method term will be placed to the header of the generated invoice form when this invoice has been processed for the legal entity configured as follows:
a.	Using the country context for Spain;
b.	Configured as having the special regime for cash accounting method enabled on the date of the invoice processing.
3.	Cash discount details (cash discount amount and invoice line net amount) are presented in the invoice totals section (when available) of the generated invoice form when this invoice has been processed for the legal entity configured as follows:
a.	Using the country context for Spain;
b.	Configured as having the turned-on Cash discount is applied in the invoice option (General ledger parameters, Sales tax section).

#### Italy
4.	Goods discount mark is presented in the invoice line section (when applicable for an invoice line) of the generated invoice form when this invoice has been processed for the legal entity configured as follows:
a.	Using the country context for Italy.

#### Finland
5.	In addition to the generated invoice form, the Giro money transfer slips can be generated:
a.	For the legal entity configured as follows:
i.	Using the country context for Finland;
ii.	Having at least one bank account marked as Giro account and Bank bar code;
b.	For an invoice defined as follows:
i.	Marked as required the Finnish associated payment attachment.

Note that the sample ER format has been configured to optionally generate the Giro money transfer slips in the separated worksheet.

Be aware that you need to install beforehand the font generating the barcode on the local machine where the generated invoice form in Microsoft Excel format will be previewed.

### Elements of the sample ER format to configure the email destination
The following elements of the sample ER format can be used to configure the email destination:
1.	The email address of a customer contact of the processing invoice can be accessed by the following ER expression: model.InvoiceBase.Contact.ElectronicMail.
2.	The email subject text can be accessed by the following ER expression: Emailing.TxtToUse.Subject.
3.	The email body text can be accessed by the following ER expression: Emailing.TxtToUse.Body.

The default text of email’s subject and body is defined in the sample ER format as language dependent format’s labels. It will be used for emailing when a custom organization email template with the predefined ID ERFTITMP has not been added.

Note. The email template ID ERFTITMP has been defined in the sample ER format and can be changed if needed in a new ER format derived from this sample ER format.

If the organization email template with the predefined ID ERFTITMP has been added for the legal entity in which you process the invoice, the configured in this email template subject and body text will be used to generate the email. 

Note that the ER expression of the sample ER format Emailing.TxtToUse.Subject configured to substitute any occurrences of characters %1 by the processing invoice ID.

Note that the ER expression of the sample ER format Emailing.TxtToUse.Body configured to do the following characters’ substitutions:
•	%1 characters by the name of the customer’s contact person
•	%2 characters by the company name
•	%3 characters by the customer name
•	%4 characters by the name of the company’s contact person
•	%5 characters by the job title of the company’s contact person
•	%6 characters by the email of the company’s contact person

