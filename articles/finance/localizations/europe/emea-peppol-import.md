---
title: Import vendor electronic invoices
description: Learn how to configure and use the vendor electronic invoices import in PEPPOL-based formats in Microsoft Dynamics 365 Finance.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Europe
ms.search.validFrom: 2023-01-01
---

# Import vendor electronic invoices

[!include [banner](../../includes/banner.md)]

This article explains how to configure and import vendor electronic invoices in formats based on the Pan-European Public Procurement Online ([PEPPOL](https://peppol.org/)) into Microsoft Dynamics 365 Finance.

The import supports the following electronic invoice formats:

- Standard **PEPPOL** format
- Germany-specific **XRechnung** format in the Universal Business Language (UBL) syntax

## Prerequisites

Before you complete the tasks in this article, import the following or latest versions of Electronic reporting (ER) configurations from the repository. For more information, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

- **Invoice model** version 280
- **Vendor Invoice Mapping to Destination** version 280.46
- **Vendor Invoice Import** version 280.7

## Configure parameters

### Reference the imported ER format configurations

1. Go to **Accounts payable** > **Setup** > **Accounts payable parameters**.
1. On the **Electronic documents** tab, on the **Electronic reporting** FastTab, in the **Vendor invoice** field, select the imported **Vendor Invoice Import** format.

### Configure the sources to import files in batch mode

Configure a SharePoint folder as a source location for incoming vendor invoice files.

1. Go to **Organization administration** > **Document management** > **Document types**.
1. Create a new document type, or select an existing one.
1. On the **General** tab, in the **Location** field, select **SharePoint**.
1. In the **SharePoint Address** field, select the folder where import files will be located.
1. Go to **Organization administration** > **Electronic reporting** > **Electronic reporting source**.
1. Create a new ER source.
1. In the **Format** field, select the **Vendor Invoice Import** format configuration.
1. On the **File source** tab, in the **Name** field, assign a source name.
1. Select **Settings**.
1. In the **Source settings** dialog box, enable the **Sharepoint** option.
1. In the **Document type for input sources** field, select the document type that you created earlier.
1. (Optional) Set up three more document types, and use them to define different *post-process* locations:

    - **Document type for imported files** – Move the files that were successfully imported.
    - **Document type for files with warnings** – Move the files that were imported with warnings.
    - **Document type for failed files** – Move the files that failed with errors.

    :::image type="content" source="../media/emea-dnk-er-source.jpg" alt-text="Screenshot of the fields in the Move processed files to another location section of the Source settings dialog box.":::

> [!NOTE]
> If you don't define a source for import in batch mode, the system prompts you to define an individual import file before the start of the import process.

### Configure vendor data

During the import process, the system identifies vendors by their tax-exempt number. To enable correct vendor identification, follow these steps:

1. Go to **Accounts payable** > **Vendors** > **All vendors**, and select a vendor.
1. On the **Invoice and delivery** FastTab, in the **Tax exempt number** field, enter a valid tax registration number for the vendor. The system uses this number to identify the vendor during import by matching it to the value of the **Invoice\\cac:AccountingSupplierParty\\cac:Party\\cac:PartyTaxScheme\\cbc:CompanyID** element in the import XML file.

### Configure products

During the import process, the system identifies products by their external descriptions. These descriptions are usually vendor-specific. To enable correct product identification, follow these steps:

1. Go to **Product information management** > **Products** > **Released products**.
1. Select a product, and then, on the **Purchase** menu, in the **Related information** section, select **External item description**.
1. Create a new external description for the selected product.
1. In the **Account code** column, select **Table** to define an external product description for a specific vendor.
1. In the **Vendor relation** column, select a vendor.
1. In the **External item number** column, enter an external product code. The system uses this code to identify the product during import by matching the code to the value of the **Invoice\\cac:InvoiceLine\\cac:Item\\cac:SellersItemIdentification\\cbc:ID** element in the import XML file.

### Configure units of measure (optional)

You can configure external codes for units of measure if specific units are explicitly defined in the incoming import files.

1. Go to **Organization administration** > **Setup** > **Units** > **Units**.
1. Select a unit ID, and then select **External codes**.
1. On the **External codes** page, in the **Overview** section, enter a code that corresponds to the selected unit ID.
1. In the **Value** section, enter the external unit code that's expected in import files.

## Import vendor electronic invoices

To run the import of vendor electronic invoices, follow these steps:

1. Go to **Accounts payable** > **Periodic tasks** > **Import vendor invoices**.
1. On **Electronic report parameters**, on the **File source** section, in the **Source settings** field, select the source location for batch mode import. If you don't define a source for batch import, the system prompts you to select a single file for import.

> [!NOTE]
> Leave the **Description** field empty.

:::image type="content" source="emea-e-invoice-import-description.jpg" alt-text="Screenshot of empty description before the import.":::

1. Select **OK** to immediately start the import process or to schedule the import to run in the background.

### Import process description

The following overview describes the steps in the import process.

1. The system identifies vendors by using the tax-exempt number that's defined in the vendor record. If no vendor matches the data that's being searched, the import process fails, and the system shows a related error message.
1. The system identifies products that are used on invoice lines by using an external item number, which might be vendor-specific. If no product matches the external description, the import process fails, and the system shows a related error message.
1. If units of measure are used on invoices lines, the system identifies them by using external codes values. If the system doesn't find a unit with a matching external code value, the import process fails, and the system shows a related error message.
1. If an incoming import file contains information about purchase orders and their lines in the **Invoice\\cac:OrderReference\\cbc:ID** and **Invoice\\cac:InvoiceLine\\cac:OrderLineReference\\cbc:LineID** elements, the system uses the numbers to match invoices with purchase orders and lines that are entered in the system.
1. If no order or line references are defined in an incoming file, the system tries to automatically match incoming vendor invoices with existing **confirmed** purchase orders. The system uses products purchase **prices** for matching.
1. If the system doesn't find a purchase order, it raises a warning but continues the import. The system now considers the products on invoice lines **Non-stock** items. Therefore, the system expects that these products belong to an item model group where the **Stocked product** checkbox is cleared on the **Inventory policy** page.
1. If no related **Non-stock** products exist, the system tries to import invoice lines by referring to a default item. You must configure the default item in the system as a released product where the code is defined exactly as **DEFAULT\_ITEM**, and the product must belong to an item model group where the **Stocked product** checkbox is cleared on the **Inventory policy** page.
The system imports the details of incoming invoice lines' descriptions into the **Text** field of the related line's **Line details** section.
If you don't configure a default item in the system, the import process fails, and the system shows a related error message.
1. The system calculates taxes based on the imported data and tax settings. The system doesn't import taxes as fixed amounts from the incoming XML file. You can manually adjust the results of the calculation as required.
1. The import process supports file attachments. All attached files that you specify in the **Invoice\\cac:AdditionalDocumentReference** element of import files should have extensions. If an attached file has no extension, the system raises a warning, and the import process skips the attachment.

The system shows successfully imported vendor electronic invoices as pending invoices. To review imported invoices, go to **Accounts payable** > **Invoices** > **Pending vendor invoices**.

> [!NOTE]
> There are some limitations to this import process:
>
> - The import process doesn't support the import of miscellaneous charges.
> - The import process supports only the import of line-level discounts.

## Additional resources

[Use the electronic invoicing service to import vendor invoices](../global/e-invoicing-get-started-import-vendor-invoices.md)

[Supported standards for electronic invoicing in Europe](emea-oioubl-standards-electronic-invoicing.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
