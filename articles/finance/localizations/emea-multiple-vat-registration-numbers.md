---
title: Multiple VAT registration numbers
description: This article provides information about the functionality for multiple value-added tax (VAT) registration numbers.
author: liza-golub
ms.date: 04/05/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: 
ms.author: wangchen
ms.search.validFrom: 
ms.dyn365.ops.version: AX 10.0.18
---

# Multiple VAT registration numbers

[!include [banner](../includes/banner.md)]

This article provides information about the functionality for multiple value-added tax (VAT) registration numbers. This functionality lets users set up the tax registration numbers of a legal entity and its customers and vendors in different countries, and then post and settle taxes according to registration in the appropriate country.

Here are the main steps to configure and use this functionality:

- Assign the registration type for VAT registration to the VAT ID registration category.
- Set up the legal entity's, customers and vendors VAT registration numbers on the **Registration ID** FastTab on the **Manage addresses** page.
- Specify the legal entity's VAT registration number for the sales tax authority, and specify the settlement period. The sales tax codes that are assigned to the settlement period will identify the legal entity's VAT registration.

The customer and vendor VAT registration numbers for transactions can be identified by the tax calculation service. The identified tax registration numbers are available in the sales tax transactions.

The sales tax settlement procedure uses the country/region code of the registration ID.

## Prerequisites

Before you begin, the Tax Calculation service must be configured. For more information, see [Tax Calculation](global-tax-calcuation-service-overview.md).

## Enable the feature

1. In the **Feature management** workspace, turn on the **Support multiple VAT registration numbers** feature.
2. Go to **Tax** \> **Setup** \> **Tax configuration** \> **Tax calculation parameters**, and turn on the **Enable tax calculation service** option.

## Set up a VAT ID for a legal entity, customers, and vendors

To set up the VAT registration numbers for a legal entity and its customers and vendors, you must use the registration ID framework to create these registration numbers. For more information, see [Registration IDs](emea-registration-ids.md).

### Set up registration types and categories

1. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration types**, and create a new registration type, such as **VATID**.

    ![Enter registration type details dialog box.](./media/Tax-Service-MultVATID-Registration-type-01.png)

2. On the **Applicable countries/regions, uses, and validation rules** FastTab, create a registration type line for each country or region where the legal entity, customers, and vendors have registrations

    ![Registration type lines on the Registration types page.](./media/Tax-Service-MultVATID-Registration-type-02.png)

3. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration categories**, and assign the registration types that you just created to the **VAT ID** registration category.

    ![Registration types assigned to the VAT ID registration category on the Registration categories page.](./media/Tax-Service-MultVATID-Registration-categories-03.png)

### Create VAT registration numbers for a legal entity, customers, and vendors

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select **Registration IDs**, and assign VAT ID registration to each address where the legal entity has VAT registrations.

    ![Assigning VAT ID registration to addresses on the Legal entities page.](./media/Tax-Service-MultVATID-Registration-Legal-entity-04.png)

> [!NOTE]
> To automatically identify customer and vendor VAT registration numbers for sales tax transactions, sales documents, and purchase documents, create the numbers in the tax calculation service on the **Customer tax registration number applicability** and **Vendor tax registration number applicability** tabs.

### Set up number sequences for a legal entity's registration numbers

To generate separate number sequences for documents such as packing slips and invoices, create a number sequence group. Then, on the **Manage addresses** page, on the **Registration ID** FastTab, on the **General** tab, assign the number sequence group to the VAT ID of the legal entity.

![Assigning a number sequence group to the VAT ID of a legal entity on the Manage addresses page.](./media/Tax-Service-MultVATID-Number-sequence-group-05.png)

Next, on the  **Number sequence groups** page, in the **Reference** section, set up the required number sequences codes for the supported references.

The code for the number sequence group is then entered by default on the sales order or purchase order header after the legal entity's tax registration is determined. The documents are numbered according to the number sequences that are assigned to the references.

![Number sequence codes on the Number sequence groups page.](./media/Tax-Service-MultVATID-Number-sequence-group-06.png)

> [!NOTE]
> Currently, the default logic supports only sales orders and purchase orders.

### Set up tax authorities

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax authorities**, and create all the tax authorities that the legal entity must report to.
2. On the **Tax registration** FastTab, add the appropriate VAT registration number.

![VAT registration number added on the Sales tax authorities page.](./media/Tax-Service-MultVATID-Sales-tax-authorities-07.png)

> [!NOTE]
> The lookup for the **Tax registration number** field on the **Tax registration** FastTab contains only the registration numbers of the legal entity that have a VAT ID registration category. The list of registration IDs is available for the corresponding country or region of the tax authority.
>
> Date effectivity isn't supported for assigned registration numbers. If the registration number of the legal entity is changed or expired, you must manually update the tax registration in the setup of the tax authority and sales tax settlement period.

### Set up the sales tax settlement period

On the **Sales tax settlement periods** page, create sales tax settlement periods. In the **Tax registration number** field, verify that the corresponding legal entity's VAT registration number is assigned.

![VAT ID assigned on the Sales tax settlement periods page.](./media/Tax-Service-MultVATID-Sales-tax-settlement-periods-08.png)

### Set up customer and vendor tax registration numbers in the Tax feature setup

1. In Regulatory Configuration Service (RCS), open the tax calculation feature setup. 
2. On the **Customer Tax Registration Number Applicability** tab, under **Applicability rules**, verify that the registration IDs for customers are defined. 
3. On the **Vendor Tax Registration Number Applicability** tab, under **Applicability rules**, verify that the registration IDs for vendors are defined.

   ![Customer and vendor registration IDs on the Tax feature setup page.](./media/tax-service-multvatid-tax-feature-setup-09-2NewUI.png)

    > [!NOTE]
    > This step is optional unless the customer or vendor has multiple tax registration numbers, and you want the Tax Calculation service to determine the ID. As the default value for the customer/vendor tax registration number, the Tax Calculation service will use the value that is entered in the **Tax exempt number** field on the header of sales and purchase documents. It will replace that default value with the value that you defined in customer/vendor tax registration number applicability rules.
    >
    > During sales tax calculation and document posting, the tax service returns the customer's or vendor's tax registration number to Dynamics 365 Finance and updates the **Tax exempt number** field on the sales order or purchase order. If the corresponding value isn't set up on the **Registration ID** FastTab on the **Manage addresses** page for the customer or vendor, the registration ID is left blank, and you receive the following message: "Customer tax registration 'xxx' is not found in the customer's Registration IDs setup. To add customer tax registration to sales tax transactions and posted documents, make sure the registration is defined in the Registration IDs setup."

## Sales order and purchase order processing

On the **Tax service parameters** page, make sure that the **Enable tax service** option is turned on, and that **Sales** and **Purchase** are selected in the **Business process** field.

If the sales tax codes on lines that are created for a sales order or purchase order are assigned to different sales tax settlement periods and tax registrations, there are multiple registration numbers for the order. To control the system behavior in this scenario, the **Check Tax registration number in document lines** option has been added on the **Accounts receivable parameters** and **Accounts payable parameters** pages.

Currently, the scenario where sales tax codes are assigned to different registration numbers on a sales order or purchase order isn't supported. During sales tax calculation and document posting, you receive an error message and can't continue the process. For information about the item ID, sales tax codes, settlement periods, and tax registration numbers that are identified for the order lines, view the message details.

![Error message about different tax registration numbers on document lines.](./media/Tax-Service-MultVATID-Order-processing-10.png)

### Temporary sales tax and posted sales tax

On the **Temporary sales tax** page, you can preview the identified VAT registration numbers of the legal entity, customers, and vendors. The following new fields have been added to the page:

- **Tax registration number** – The VAT registration number of the legal entity.
- **Customer tax registration number** – The VAT registration number of the customer. This field is available only for sales orders.
- **Vendor tax registration number** – The VAT registration number of the vendor. This field is available only for purchase orders.

On the **Posted sales tax** page, the following new fields have been added. You can sort and filter sales tax transactions by these fields.

- **Tax registration number** – The VAT registration number of the legal entity.
- **Counterparty tax registration number** – The VAT registration number of the counterparty.

### Sales tax settlement procedure updates

The **Settle and post sales tax** periodic task has been updated so that it uses the country/region code of the legal entity's tax registration.

> [!NOTE]
> If the tax registration number isn't set for a tax period, you receive the following error message: "Tax registration number is not set up for the tax settlement period xxx" and settlement process is stopped.

After the settlement process is completed, no sales tax payment report is printed. Instead, you receive the following message: "The sales tax settlement and posting is completed. The voucher 'xxxx, m/d/yyyy' has been posted."

You can still manually run the sales tax payment report by going to **Tax** \> **Inquiries and reports** \> **Sales tax inquiries** \> **Sales tax payments**.

> [!NOTE]
> Even if the feature isn't enabled on the **Tax service parameters** page, the tax registration ID will be copied from the original sales tax transactions to the offset sales tax transactions.
