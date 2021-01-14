---
# required metadata

title: Multiple VAT registration numbers - Preview
description: This topic provides information about the functionality of Multiple VAT registration numbers.
Please note that all settings that are described in this document are under the scope of the tax service preview. The content is subjected to change later.
author: epodkolz
manager: AnnBe
ms.date:
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region:
# ms.search.industry: 
ms.author: epodkolz
ms.search.validFrom:
ms.dyn365.ops.version: AX 10.0.18
---

# Multiple VAT registration numbers – Private preview

[!include [banner](../includes/banner.md)]

This topic provides information about the functionality of Multiple VAT registration numbers.
Please note that all settings that are described in this document are under the scope of the tax service private preview. The content is subjected to change later.
This functionality provides a possibility to set up tax registration numbers of a legal entity and its customers and vendors in different EU Member States and post and settle taxes per registration in the country.

The main steps to configure and use this functionality are as following:
 - The Registration type for VAT registration must be assigned to the VAT ID registration category.
 - Legal entity VAT registration as long as its Customer and Vendors VAT registration must be set up in the Registration IDs.
 - The Legal entity’s VAT registration number must be specified at the Sales tax authority, and further in the Settlement period. Thus, the sales tax code(s) assigned to the settlement period will identify the Legal entity’s VAT registration.
 - The Customer/Vendor VAT registration numbers for transactions are identified by the Tax service matrix.
 - The identified tax registration numbers are available in the sales tax transactions.
 - The sales tax settlement procedure uses the country/region code of the registration ID. 

## How to enable feature

Enable flighting:
•	TaxIntegrationFlight 
•	TaxMultipleVATIDFlighting

•	TaxMultipleVATIDFeature

Enable feature **Support multiple VAT registration numbers** in the **Feature management** workspace.

On the **Tax service parameters** page switch on the **Enable tax service** option (see document **Get started with tax service – Private Preview for details**).

## Set up VAT ID for legal entity and customer/vendor

In order to set up VAT ID for the legal entity and its counterparties (customers/vendors) the following settings must be done.
VAT IDs must be created using the Registration IDs framework, see https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-registration-ids

### Set up registration types and registrations categories

On the **Registration types** page (Organization administration > Global address book > Registration types > Registration types) create Registration type, e.g. VAT ID

![Tax-Service-MultVATID-Registration-type-01](./media/Tax-Service-MultVATID-Registration-type-01.png)

Create as many lines as the legal entity and its counterparties have registrations in Country/regions:

![Tax-Service-MultVATID-Registration-type-02](./media/Tax-Service-MultVATID-Registration-type-02.png)

On the **Registration categories** page (Organization administration > Global address book > Registration types > Registration categories) assign the created registration types to the VAT ID registration category:

![Tax-Service-MultVATID-Registration-categories-03](./media/Tax-Service-MultVATID-Registration-categories-03.png)


### Assign VAT IDs to legal entity and customer/vendor

On the **Legal entities** page (Organization administration > Organizations > Legal entities), click **Registration IDs** button and assign VAT ID registration to the respective address where the legal entity has VAT registration:

![Tax-Service-MultVATID-Registration-Legal-entity-04](./media/Tax-Service-MultVATID-Registration-Legal-entity-04.png)


For customers/vendors use the Registration IDs to create their VAT registrations.
NOTE: For the automatic identification of the counterparties VAT registration numbers for the sales tax transactions and sales/purchase documents, these numbers should be created in the tax matrix (see **Get started with tax service – Private Preview** and **Set up customer/vendor tax registration number in Tax feature setup** for details).

### Number sequences per legal entity's registration numbers

To get separate number sequences for documents (packing slips, invoices), create a Number sequence group. 

Assign the **Number sequence group** to the respective VAT ID of the legal entity (Registration ID fasttab, tab General):

![Tax-Service-MultVATID-Number-sequence-group-05](./media/Tax-Service-MultVATID-Number-sequence-group-05.png)


Set up necessary **Number sequences codes** for the supported references, e.g. Sales invoice, Sales invoice voucher, Packing slip, Packing slip voucher.

This Number sequence group code will be defaulted to the Sales order/Purchase order header once the legal entity's tax registration is determined. The documents will be numbered as according to the **Number sequences** assigned to the **References**:

![Tax-Service-MultVATID-Number-sequence-group-06](./media/Tax-Service-MultVATID-Number-sequence-group-06.png)


NOTE. In the Preview, the defaulting logic is supported for Sales order and Purchase order only.

### Set up Tax authorities

In the **Sales tax authorities** page (Tax > Indirect taxes > Sales tax > Sales tax authorities) create as many tax authorities as legal entity need to report to.
In the new **Tax registration** tab add the respective VAT registration number:

![Tax-Service-MultVATID-Sales-tax-authorities-07](./media/Tax-Service-MultVATID-Sales-tax-authorities-07.png)

NOTE. The **Tax registration number** lookup will have only registration numbers of the legal entity with VAT ID registration category. The list of registration IDs is available for the corresponding country/region of the tax authority. 
NOTE. The Date effectiveness is not supported for the assigned registration IDs. In case the number is changed/expired in the Legal entity Registration IDs, user need to update the tax registration in the tax authority manually. 

### Set up Sales tax settlement period

Create **Sales tax settlement periods** and in the **Tax registration number** filed make sure the corresponding legal entity’s VAT ID is assigned:

![Tax-Service-MultVATID-Sales-tax-settlement-periods-08](./media/Tax-Service-MultVATID-Sales-tax-settlement-periods-08.png)

### Set up customer/vendor tax registration number in Tax feature setup

In the **Microsoft Dynamics 365 Regulatory Service** for the Tax feature (see how to create a **Tax feature** in document **Get started with tax service – Private Preview**), make sure the registration IDs for the counterparties are defined on the **Customer Tax Registration Number Applicability** and **Vendor Tax Registration Applicability** tabs respectively.

![Tax-Service-MultVATID-Tax-feature-setup-09](./media/Tax-Service-MultVATID-Tax-feature-setup-09.png)

NOTE. During sales tax calculation and documents posting, Tax service will return a value of Customer/Vendor tax registration number to Dynamics 365 Finance and update the **Tax exempt number** field of the Sales/Purchase order. In case the corresponding value is not set up in the Registration IDs of Customer/Vendor (see how to set up the registration IDs in **Assign VAT IDs to legal entity and customer/vendor**), the prompt message will pop out and registration ID will be left blank:
“Customer tax registration ‘xxx’ is not found in the customer’s Registration IDs setup. To add customer tax registration to sales tax transactions and posted documents, make sure the registration is defined in the Registration IDs setup.”

## Sales order/Purchase order processing

Make sure the **Enable tax service** option is switched ON in the **Tax service parameters**, and *Sales* and *Purchase* are selected in the **Business process** (see document **Get started with tax service – Private Preview** for details).

When the lines of a sales or purchase order are created with sales tax codes that are assigned to different sales tax settlement periods (sales tax authorities), and thus, Tax registrations, this results in multiple registration IDs for the order. To control the system behavior for such scenario, a parameter **Check Tax registration number in document lines** is added on the **AP/AR parameter** page. In the Private Preview only *Error* option is available.
In the Private Preview, the scenario when Sales and/or Purchase order has sales tax codes assigned to different registration IDs is not supported. During a sales tax calculation and documents posting an error message will be shown and further process will be terminated:

![Tax-Service-MultVATID-Order-processing-10](./media/Tax-Service-MultVATID-Order-processing-10.png)

In the Message details the info about Item ID, Sales tax codes, Settlement periods, and Tax registration numbers identified for the order lines can be found.

### Temporary sales tax and Posted sales tax

On the **Temporary sales tax** page you can preview the identified legal entity’s and customer/vendor VAT registration numbers. Two new fields are added: **Tax registration number** – a VAT ID of the legal entity and **Customer tax registration number** for Sales order and **Vendor tax registration number** for Purchase order – a VAT ID of the counterparty, i.e. customer/vendor.
In the **Posted sales tax** two new field are added: **Tax registration number** – a VAT ID of the legal entity and **Counterparty tax registration number** – a VAT ID of the counterparty, i.e. customer/vendor.
You can sort and filter sales tax transactions by these fields.

### Sales tax settlement procedure updates

The **Settle and post sales tax** periodic is updated to use the county/region code of the legal entity tax registration.
NOTE. If tax registration number is not set on tax period, an error message is shown "Tax registration number is not set up for the tax settlement period xxx" and settlement process is stopped.
After settlement process is completed, the sales tax payment report is not printed. Instead, the following message will be displayed: "The sales tax settlement and posting is completed. The voucher 'xxxx, m/d/yyyy' has been posted."
The report can still be run from the **Sales tax payments** page (Tax > Inquiries and reports > Sales tax inquiries > Sales tax payments).
NOTE. Even if the feature is not enabled in the Tax service parameters, the tax registration ID will be copied from the original sales tax transactions to the offset sales tax transactions. 
