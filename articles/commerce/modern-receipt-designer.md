---
title: Modern receipt designer in Commerce headquarters
description: Learn how to use the modern receipt designer in Microsoft Dynamics 365 Commerce headquarters to create receipt formats with tables and rich text.
author: anush6121
ms.author: anvenkat
ms.topic: how-to
ms.date: 11/05/2026
ms.reviewer: mirao
ms.search.form: RetailFormLayout
ms.custom:
  - bap-template
---

# Modern receipt designer in Commerce headquarters

[!INCLUDE [banner](includes/banner.md)]

The modern receipt designer provides a React-based design experience for Commerce receipt formats directly from Commerce headquarters. It replaces the legacy **ClickOnce** designer launch experience with a browser-based designer that you can open from the **Receipt formats** page. The designer includes a visual canvas, template selection, reusable templates, localized field labels and preview data, custom receipt fields, validation, and preview support.

In Commerce version 10.0.50, the designer also supports fixed and repeating tables and rich-text formatting for document receipts. You can use these capabilities for detailed invoices, order summaries, tax breakdowns, and other B2B and trade-counter scenarios.

The modern designer saves structured receipt layout data for the new receipt format path. Store Commerce can use the structured receipt format path when you enable the modern receipt designer feature and the Commerce Scale Unit supports structured receipts.

## Prerequisites

- Update Commerce headquarters, Commerce Scale Unit, Store Commerce, and Hardware Station to compatible versions before you use tables or document typography.
- Enable the modern receipt designer feature in **Feature management** before using the structured receipt path in Store Commerce.
- Configure existing receipt profiles, printers, and hardware profiles for registers where receipts are printed.

> [!IMPORTANT]
>
> - Enable the modern receipt designer feature only after updating the Commerce Scale Unit or Retail Server to a version that supports structured receipts. When you enable the feature, Store Commerce uses the structured receipt endpoint for supported receipt flows. If the endpoint isn't available, receipt preview or printing can fail.
>
> - Commerce version 10.0.50 migrates supported legacy receipt layouts to the modern designer JSON format. Review migrated formats in the modern designer and test them with representative transaction data before deploying them to stores.

## Open the modern receipt designer

To open the modern receipt designer, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS** > **Receipt formats**.
1. Create a receipt format, or select an existing receipt format.
1. Select **Designer**.
1. If the receipt format doesn't already have a modern design, select a template from the template gallery or start from a blank template.
1. Select **Edit format** to open the full designer canvas.

> [!NOTE]
> The template gallery appears only when a receipt format doesn't already have a modern design, such as when you create a new receipt format or open an existing format before it has been saved in the modern designer. After a modern design exists for the receipt format, the gallery isn't shown again for that format.

:::image type="content" source="media/modern-receipt-designer-template-gallery.png" alt-text="Screenshot of the modern receipt designer template gallery embedded on the Receipt formats page." lightbox="media/modern-receipt-designer-template-gallery.png":::

## Design a receipt format

The modern designer canvas shows the receipt layout with separate receipt sections and fields. The field palette lists standard receipt fields and custom fields. Use the palette and property editor to add fields, position fields, and edit properties.

To design a receipt format, follow these steps:

1. Open the modern receipt designer from the receipt format.
1. Use the field palette to find the field to add. Standard fields and custom fields are grouped separately.
1. Drag the field to the receipt canvas.
1. Select a field on the canvas to edit its properties.
1. Update applicable properties, such as position, length, alignment, font weight, prefix, or text.
1. Resolve any validation errors that appear in the designer.
1. Select **Save**.

:::image type="content" source="media/modern-receipt-designer-canvas.png" alt-text="Screenshot of the modern receipt designer canvas with receipt fields and the field palette." lightbox="media/modern-receipt-designer-canvas.png":::

### Custom fields and localized labels

In Commerce version 10.0.49, the modern receipt designer supports user-defined receipt custom fields. Custom fields appear in the field palette with their configured captions. If a translated caption is available for the current legal entity and language, the designer shows the localized caption. If a translation isn't available, the designer falls back to the field name.

Standard field labels and sample preview data are also localized in version 10.0.49. This behavior helps implementers design receipt layouts in the same language context that store users see.

## Add tables

Commerce version 10.0.50 supports the following table types:

- **Fixed table**: Contains rows that you add and arrange in the designer. Cells can contain static text or receipt fields.
- **Repeating table**: Defines a row that Commerce repeats for each matching record. Repeating tables support item lines, invoice lines, tenders, tax summaries, loyalty earn lines, and loyalty redeem lines. You can add repeating tables only to the **Lines** section.

> [!IMPORTANT]
> For physical printing, fixed and repeating tables and document typography are supported only through the Windows printer path in Windows Hardware Station. OPOS, Epson, Star, and Adyen printer paths reject layouts that contain these capabilities instead of producing partial or lossy output. Previews and modern HTML email receipts support tables independently of the physical printer path.

To add and configure a table, follow these steps:

1. In the field palette, add a fixed or repeating table to the canvas.
1. For a repeating table, select the applicable **Line type**.
1. Add, remove, resize, move, or reorder rows, columns, and cells.
1. Add static text, standard receipt fields, or eligible custom fields to the cells.
1. Configure column headings, borders, banded rows, alignment, and text formatting as required.
1. Resolve validation errors, and then select **Save**.

You can position multiple tables and ordinary fields on the same receipt line when enough space is available. Repeating fields can be blank when a value isn't available for a record. Preview and test the format with representative transactions, including transactions with no matching records and transactions with long or multiline values.

> [!NOTE]
> You can't save a layout that contains a table when content extends beyond the selected paper width. Export remains available so that an implementer can correct the layout outside the designer.

## Apply rich-text formatting

For compatible document formats, you can apply the following rich-text formatting to ordinary fields, table cells, and table headings:

- Font family.
- Font size from 11 through 96 pixels.
- Normal, light, semibold, or bold font weight.
- Italic, underline, and strike-through.
- Text alignment.

Windows uses the nearest available weight when the selected font doesn't contain the exact authored weight. If the selected font or size isn't available, Windows Hardware Station uses the configured Windows printer font and size.

Thermal and mobile receipt formats continue to use their existing regular and large font sizes. The document font family and pixel-size settings don't change thermal formatting.

## Validate receipt lines

The modern designer validates line-level issues while you edit the receipt format. Validation helps prevent field placement and line-type issues before the format is used in Store Commerce.

Validation can detect problems such as:

- Fields that conflict with the line type.
- Fields that overlap in the same line.
- Line types that need to be inferred or corrected after fields are moved.

If validation errors appear, select the affected field or line, correct the placement or field selection, and save the format again.

## Save a receipt format as a template

Templates let you reuse a receipt design across formats. You can save a completed design as a template and select it later when another receipt format needs the same layout pattern.

To save a receipt format as a template, follow these steps:

1. Open the receipt format in the modern receipt designer.
1. Make the required layout changes.
1. Select **Save as Template**.
1. Enter a template name and description.
1. Select **Save as Template**.

To use a saved template:

1. Create a new receipt format or open a receipt format that doesn't already have a modern design.
1. Select the template from the gallery.
1. Open the designer to make any receipt-specific changes.

You can't apply saved templates from the gallery after a receipt format already has a modern design.

## Preview the receipt format

After you save a modern receipt design, the **Receipt formats** page shows an embedded preview. The preview helps you confirm the layout before testing the format in Store Commerce.

To preview a receipt format, follow these steps:

1. In Commerce headquarters, open the receipt format.
1. Review the embedded preview on the **Receipt formats** page.
1. If you need to make any changes, select **Edit format**.
1. Save the changes and return to the receipt format page. The preview refreshes after the save.

:::image type="content" source="media/modern-receipt-designer-preview.png" alt-text="Screenshot of the embedded modern receipt preview on the Receipt formats page." lightbox="media/modern-receipt-designer-preview.png":::

## Use modern receipt formats in Store Commerce

When you enable the modern receipt designer feature, Store Commerce uses the structured receipt path for supported receipt scenarios. Structured receipts include a device-agnostic receipt document that Store Commerce and Retail hardware station use for preview and printing.

Supported receipt flows include:

- Post-sale receipt print and gift receipt print or email.
- Show journal receipt preview, print, print all, quick email, gift receipts, and document-based preview.
- Customer Transactions receipt preview and print.
- Cash management receipts, such as bank drop, safe drop, tender removal, starting amount, tender declaration, open drawer, void transaction, suspend transaction, and gift card inquiry receipts.

> [!NOTE]
> Changes saved in the modern receipt designer aren't saved back to the legacy designer format. If the modern receipt designer feature is later disabled, changes made only in the modern designer won't appear in the legacy designer. The modern changes are available again if you re-enable the feature.

## Print and preview behavior

The structured receipt path aligns preview, print, print-all, email, and gift receipt behavior with the legacy path. Store Commerce uses receipt print behavior settings, such as **Always print**, **Prompt user**, and **Do not print**, when deciding which receipts to print.

If you configure the receipt with **Prompt user**, Store Commerce prompts at checkout and prints the selected structured receipt through the configured printer. If a receipt can't be printed because the receipt or printer configuration doesn't allow printing, Store Commerce shows the same type of availability message used by the legacy receipt path.

### Output support for tables and document formatting

The following outputs support the table and document-formatting capabilities that were added in Commerce version 10.0.50:

| Output | Support |
| ------ | ------- |
| Modern designer and Commerce headquarters preview | Fixed and repeating tables, table formatting, and document typography. |
| Store Commerce receipt preview, Show journal, and Customer transactions | Fixed and repeating tables, table formatting, and document typography. |
| Windows printer through Windows Hardware Station | Fixed and repeating tables, table formatting, document typography, images, and barcodes |
| Modern receipt email composed by Commerce Scale Unit | HTML tables and document typography. |

For physical printing, tables and document typography require the Windows printer path. OPOS, Epson, Star, and Adyen printer paths don't support these capabilities and reject the layout instead of producing partial or lossy output. Table-free receipts without document typography continue to use the existing printer paths.

Windows Hardware Station keeps a table row together during pagination when possible. For document layouts from 99 through 140 columns, pagination also respects the configured document margins and the printer driver's printable area.

Modern email receipts preserve tables and formatting when Commerce Scale Unit composes the receipt from the modern JSON layout. Email client font availability and CSS support can affect the final appearance. Older headquarters-composed email workflows retain their existing plain-text behavior.

## Close the designer with unsaved changes

If you change a receipt design and try to leave the page before saving, the designer reports the dirty state to the Commerce headquarters host. Commerce headquarters can then prompt before closing or navigating away, helping prevent accidental loss of receipt layout changes.

## Learn more

- [Set up and design receipt formats](receipt-templates-printing.md)
- [Send email receipts from Store Commerce](email-receipts.md)
- [Configure and manage receipt numbers](reset_receipt_number_sequence.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
