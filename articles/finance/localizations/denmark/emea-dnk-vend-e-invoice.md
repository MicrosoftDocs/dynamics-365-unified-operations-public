---
title: Vendor electronic invoices import in Denmark
description: This article explains how to configure and use vendor electronic invoices import in Denmark in Microsoft Dynamics 365 Finance.
author: ilikond
ms.date: 10/13/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Denmark
ms.author: ikondratenko
ms.search.validFrom: 2023-11-03
ms.dyn365.ops.version: AX 10.0.38
ms.custom: 853863
ms.assetid: 
ms.search.form: 
---

# Vendor electronic invoices import in Denmark

[!include [banner](../../includes/banner.md)]

This article explains how to configure and use vendor electronic invoices import for Denmark from the country specific **OIOUBL** format in Microsoft Dynamics 365 Finance.

## Prerequisites

Before you complete the tasks in this article, the following prerequisites must be met:

- The primary address of the legal entity must be in Denmark.
- The latest version of the Electronic reporting (ER) format configuration, **Vendor Invoice Import (DK)** must be imported. For more information, see [Import Electronic reporting (ER) configurations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations.md).
        
> [!NOTE]
> The ER format is based on the **Invoice model** configuration and uses the **Vendor Invoice Mapping to Destination** configuration. All required additional configurations are automatically imported.

## Configure parameters

### Reference the imported ER format configurations

1. Go to **Accounts payable** > **Setup** > **Accounts payable parameters**.
2. On the **Electronic documents** tab, on the **Electronic reporting** FastTab, in the **Vendor invoice** field, select the imported format **Vendor Invoice Import (DK)**.
    
### Configure the sources to import files in a batch mode
You can configure a SharePoint folder as a source location of incoming vendors invoices files.

1. Go to **Organization administration** > **Document management** > **Document types**.
2. Create a new or configure an existing Document type.
3. On the **General** FastTab, in the **Location** field, select the **SharePoint** value.
4. In the **SharePoint Address** field, select the folder where import files will be located.
5. Go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting source**.
6. Create a new Electronic reporting source.
7. In the **Format** field select, **Vendor Invoice Import (DK)** format configuration.
8. On the **File source** FastTab, assign a source name in the **Name** field and then select **Settings**.
9. On the **Source settings** page, enable the **Sharepoint** option.
10. In the **Document type for input sources** field, select the document type you created in step 2.
11. Optionally, you can set up three more Document types and use them to define different *post-process* locations:
  - Move the files that were successfully imported in the **Document type for imported files** field.
  - Move the files that were imported with warnings in the **Document type for files with warnings** field.
  - Move the files that failed with errors in the **Document type for failed files** field.
    
    ![ER source settings](../media/emea-dnk-er-source.jpg)

> [!NOTE]
> If no source is defined for import in batch mode, the system requests to define an individual import file before the start of import process.

### Configure vendor data

During the import process, vendors are identified by using their tax exempt numbers. To enable proper vendor identification, complete the following steps.

1. Go to **Accounts payable** \> **Vendors** \> **All vendors**, and select a vendor.
2. On the **Invoice and delivery** FastTab, in the **Tax exempt number** field, enter a valid tax registration number for the vendor. This number is used to identify the vendor during import by matching it to the **Invoice\cac:AccountingSupplierParty\cac:Party\cac:PartyLegalEntity\cbc:CompanyID** element's value in the import XML file.

### Configure products

During the import process, products are identified by using their external descriptions which are usually vendor specific. To enable proper product identification, do the following steps.

1. Go to **Product information management** \> **Products** \> **Released products**.
2. Select a product, and in the **Purchase** menu, in the **Related information** section, select **External item description**.
3. Create a new external description for the selected product.
4. In the **Account code** column, select the **Table** value to define an external product description for a specific vendor. 
5. In the **Vendor relation** columnn, select a vendor.
6. In the **External item number** columnn, enter an external product code. This code is used for the product identification during import by matching the code to the **Invoice\cac:InvoiceLine\cac:Item\cbc:Name** element's value in the import XML file.

### Configure units of measure

Optionally, you can configure external codes for units of measure, if specific units are explicitly defined in the incoming import files. Complete the following steps.

1. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**.
2. Select a unit ID, and then select **External codes**.
3. On the **External codes** page, in the **Overview** section, in the **Code** field, enter a code that corresponds to the selected unit ID.
4. In **Value** section, in **Value** field, enter the external unit code that's expected to be used in import files.


## Import vendor electronic invoices

To run the import vendor electronic invoices, use the following steps.

1. Go to **Accounts payable** \> **Periodic tasks** \> **Import vendor invoices**.
2. On the **Electronic report parameters** page, on the **File source** FastTab, in the **Source settings** field, select the source location for batch mode import. If no source for batch import is defined, the system has you select a single file for import.
3. Select **OK** to immediately start import process or to schedule import to run in the background.

### Import process description
The following list of steps provides an overview of the import process and the order in which it haapens.

1. Vendors are identified using the tax exempt number defined in the vendor record. If no vendor matches the data being searched, the import process fails with a related error-message.
2. Products used in invoice lines are identified using an external item number which can be vendor-specific. If no product matches with the external description, the import process fails with a related error-message.
3. Units of measure, if used in invoices lines, are identified useing external codes values. If no unit with matching external code value is found in the system, the import process fails with a related error-message.
4. If an incoming import file contains the information about purchase orders and its lines in the **Invoice\cac:OrderReference\cbc:ID** and **Invoice\cac:InvoiceLine\cac:OrderLineReference\cbc:LineID** elements, the numbers are used for invoice matching with purchase orders and lines entered in the system.
5. If no order or line references are defined in an incoming file, the system tries to automatically match incoming vendor invoices with existing purchase orders.
6. If no purchase order is found, the system raises a warning but continues import while considering products on invoice lines as **Non-stock** items. The system expects that these products belong to an item model group that doesn't have the **Stocked product** check-box selected on the **Inventory policy**. 
7. If no related **Non-stock** products exist, the system tries to import invoice lines by refering to a **DEFAULT_ITEM**. The default item must be configured in the system as a released product with the code defined exactly as **DEFAULT_ITEM** and must belong to an item model group with an unmarked **Stocked product** check-box on the **Inventory policy** page. If no default item is configured in the system, the import process fails with a related error-message.
8. Taxes are calculated in the system based on the imported data and tax settings. Taxes aren't imported as fixed amounts from the incoming XML file. The results of the calculation can be manually adjusted, if needed.

Successfully imported vendor electronic invoices are shown in the system as pending invoices. To review imported invoices, go to **Accounts payable** > **Invoices** > **Pending vendor invoices**. 

> [!NOTE]
> There are some limitations to this import process:
>  - Import of miscellaneous charges isn;t supported.
>  - Only line-level discounts import is supported.

## Learn more

- [Customer electronic invoices in Denmark](../norway/emea-dnk-e-invoices.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]


