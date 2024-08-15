---
title: Configure the Invoice capture solution
description: Learn about how to configure the Invoice capture solution, including a step-by-step process that outlines various system preferences.
author: leizi2015
ms.author: zezhangzhao
ms.topic: overview
ms.date: 08/05/2024
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-09-28
ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
ms.dyn365.ops.version: 
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
---

# Configure the Invoice capture solution

[!include [banner](../includes/banner.md)]

After the Invoice capture solution is installed, default configurations for using it are provided. These default configurations might not fully meet the customer's requirements. In Invoice capture, configurations can be found in **System preference**.

## System preference

1. **AI Builder model** – The default model is set to **Invoice processing model**. This prebuilt model can handle the most common invoices in various languages. However, it can't handle more complex invoice layouts. For those layouts, customers can introduce their own models by uploading additional sample invoices, tagging the fields, and training the model. Additionally, customers can define new model fields and map them to the fields in Invoice capture. These additional captured fields can then be transferred to Dynamics 365 Finance to fulfill specific business requirements. A custom invoice model is built on top of the prebuilt model. However, before you apply it, you should be aware of the following limitations:

    - Key-value pairs aren't returned, and the **Map key-value pair fields** icon is disabled.
    - Confidence scores aren't returned.
    - The position of invoice lines isn't returned.
    - Only one decimal precision formatting is allowed when a new currency field is defined.
    - Currency codes aren't returned. This limitation might affect the derivation of the currency code.

2. **Channel for file upload** – The channel that's used to directly upload invoice files.
3. **File filter** – Select the file filter to apply additional filtering to incoming files at the application level. In this case, invoice file processing is halted at the **Received files** stage.
4. **Configuration group** – The configuration group that is used if a configuration group isn't set at the legal entity or vendor account level during invoice processing.
5. **Use continuous learning** – Select this option to turn on the continuous learning feature. The continuous learning feature tries to record patterns between the invoice context and manually selected entities. Immediately after the invoice is successfully transferred, the relationship is recorded and applied to any invoice that arrives in the future and has the same context. 
6. **Auto invoice cleanup** – Select this option to automatically clean up transferred invoices and voided invoices that are older than 180 days every day. The job deletes both the invoice data and the original invoice file.

## Manage processing rules

In invoice capture processing, different derivation rules are applied to ensure that the invoices are complete and correct. Because some rules aren't applicable to all customers, the processing uses the following parameters to enable or disable the logic:

- **Format purchase order** – Select this parameter to check the number sequence settings in Microsoft Dynamics 365 Finance and format the purchase order number accordingly. This parameter can increase the touchless rate when the purchase order number doesn't follow the format that's set in the number sequence settings.

    Here are some supported format examples:

    - Purchase order number: "125", Format: "\#\#\#\#\#\#\#\#", Formatted purchase order number: "00000125"
    - Purchase order number: "00125", Format: "\#\#\#\#\#\#\#\#", Formatted purchase order number: "00000125"
    - Purchase order number: "125", Format: "USMF-\#\#\#\#\#\#\#\#", Formatted purchase order number: "USMF-00000125"
    - Purchase order number: "PO00125", Format: "\#\#\#\#\#\#\#\#", Formatted purchase order number: "00000125"
    - Purchase order number: "P.O.125", Format: "USMF-\#\#\#\#\#\#\#\#", Formatted purchase order number: "USMF-00000125"
    - Purchase order number: "125", Format: "PO-\#\#\#\#\#\#\#\#", Formatted purchase order number: "PO-00000125"

- **Derive currency code for cost invoice** – Select this parameter to automatically derive the currency code from invoices of the **Cost** type in Dynamics 365 Finance. For purchase order invoices, if the currency codes on the derived purchase orders are unique, those currency codes are used for the invoices.
- **User confidence score** – Select this parameter to skip the validation of confidence scores.
- **Validate unit of measure for PO invoice** – Select this parameter to ensure the consistency of the unit of measure between the invoice line and its associated purchase order line.
- **Validate total sales tax amount** – Select this parameter to validate the consistency between the sales tax amount on the **Sales tax** card and the total sales tax amount. If there's no sales tax line, the validation logic is skipped.
- **Validate total amount** – Select this parameter to confirm alignment between the calculated total invoice amount and the captured total amount.

    - If the line amount has a zero or null value, the line net amount is calculated as *Unit price* &times; *Quantity*.
    - If the total sale tax has a zero or null value, the total sales tax is the sum of the sales tax lines.

    *Total amount* == *Sum (line amount)* + *Sum (charge lines)* &minus; *ABS(Discount)* + *Total sales tax*

    If there's no invoice line, or if the sum of the line amount is zero, the total amount validation is skipped.

- **Credit note process** – Select the **Support credit note** parameter to automatically classify a document as a credit note if the document header contains terms such as **Credit note** or **Credit memo**.

## Manage file filters (optional)

**Manage file filters** lets administrators define additional filters for incoming invoice files. Files that don't meet the filter criteria are received, but they appear in the **Received files (Pending)** list with a status of **Canceled**. Clerks can review the files and decide whether to void and obsolete them. 

> [!NOTE]
> This behavior differs from the behavior that's defined in the flow behind the channel. In that flow, files that don't meet the criteria aren't received.

After the Invoice capture solution is installed, a default file filter is provided. This file filter is global. If you want a different filter setting, you can create a file filter and update the default filter.

File filters are flexible and can be applied at different channel levels. When an invoice document is received, the channel is checked first for a file filter. If no file filter is assigned to the channel level, the file filter at the system level is used.

### File filter settings

Configure the following settings in the file filter:

1. **Accepted file size** – Define the minimum and maximum accepted file sizes for invoice documents. The maximum file size can't exceed 20 megabytes (MB).
2. **Supported file types** – Select at least one of the following file types that are currently supported for AI Builder recognition service:

    - PDF
    - PNG
    - JPG
    - JPEG
    - TIF
    - TIFF

3. **Supported file names** – Use file name rules to filter out files that aren't relevant to invoices. Different rules can be applied to accept files only when the name contains predefined strings, or to exclude files that contain the defined strings.

## Definition of master data

Invoice capture processing requires two basic data types to classify invoices: legal entities and vendors.

**Legal entities** are organizations that are registered with legal authorities and defined in Dynamics 365 Finance. Business activities are performed and recorded separately for each legal entity. In Microsoft Power Platform, business units, security roles, and users are linked to conform to the role-based security model. This link controls data access through business units and security roles, and allows Accounts payable clerks to view only the invoices that are assigned to their users.

**Vendors** are individuals or organizations that supply goods or services to a business. In Dynamics 365 Finance, if a vendor provides services or product to multiple legal entities, a vendor account has to be created for each legal entity and business activity can be recorded. In Invoice capture, the vendor master data is used to automatically derive the vendor account and helps increase the touchless rate in invoice processing.

### Sync legal entities

In the **Manage legal entities** process, users can't manually create legal entities. Instead, you must sync the legal entities by following these steps.

1. Go to **Setup** \> **System setup** \> **Manage legal entities**.
2. Select **Sync**.
3. In the confirmation message box, select **OK**.

After synchronization is completed, a message shows the number of new legal entities. The list view is automatically refreshed to show the new legal entities.

### Sync vendors
In **Manage vendors**, there are three options to sync the vendor accounts:

- **Sync all** – all vendor accounts are synced. This will potentially cause a performance issue.
- **Sync by legal entity** – The administrator can select one or multiple legal entities and sync the vendors in the selected legal entities.
- **Sync by selection** – Administrators can search and select one or multiple vendors and sync the selected vendors.

An Accounts payable administrator can initiate the vendor synchronization manually or in real time. To enable real-time synchronization, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable** \> **Setup** \> **Invoice capture**.
2. Select the **Sync all vendors** checkbox next to the onboarded legal entity.
