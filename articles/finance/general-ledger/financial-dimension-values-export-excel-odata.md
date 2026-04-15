---
title: Exporting and editing dimensions data in Excel via OData plug-in
description: Learn how to export and edit financial dimension values using the Open in Excel button, the Financial dimension values entity, and DMF.
author: ethanrimes
ms.author: ethankallett
ms.topic: article
ms.date: 04/09/2026
ms.custom: evergreen
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2018-10-31
ms.search.form: DimensionDetails, DimensionValueDetails
ms.dyn365.ops.version: 8.1
---

# Export and edit dimension data in Excel by using the OData plug-in

[!include [banner](../includes/banner.md)]

The Excel button on the **Financial dimension values** page opens a dropdown with two distinct sections: **Open in Excel** and **Export to Excel**. These sections differ in data scope and interactivity.

![The Excel button on the Financial dimension values page, showing the Open in Excel and Export to Excel sections.](media/odata-add-in-click.png)

## Open in Excel (OData plug-in)

The workbooks listed under **Open in Excel** - **Financial dimension values**, **Financial dimension value legal entity overrides**, and **Financial dimension value translations** - connect to Finance through the OData plug-in. The workbook stays live, and you can publish any edits back to Finance directly from Excel.

> [!IMPORTANT]
> Because these workbooks use the **Financial dimension values entity**, they follow the same scope as Data Management Framework (DMF) exports. Custom dimension values are always exported. However, for entity-backed dimensions, only values that you use as dimensions or values that you explicitly modify properties for are returned. Unused entity-backed values don't appear.
>
> Used values include those you enter in transactions (such as ledger accounts, non-ledger accounts, or default dimensions) or values for which you modify properties (such as Active from/Active to dates, Suspended status, and other overrides).
>
> For dimensions sourced from other records in the system (such as customers, departments, or cost centers), not all values are exported - only those that you use as described earlier.

## Export to Excel

The options listed under **Export to Excel** - such as **Custom list financial dimension** - perform a one-time static export of the data currently visible in the grid. Unlike the OData workbooks, these exports include all dimension values regardless of whether you use them. However, the exported file is read-only; you can't publish changes back to Finance.

If a value is visible on the **Financial dimension values** page but missing from an **Open in Excel** workbook or a Data Management Framework (DMF) export, use **Export to Excel** > **Custom list financial dimension** to retrieve the full list.

## Make values available through the OData add-in or Data Management Framework (DMF)

If a dimension value doesn't appear in OData add-in workbooks or DMF exports, it's because you didn't set a property for it. To make the value available, set any property on it, such as an *Active from* date or a *Suspended* status. Set properties directly on the **Financial dimension values** page by selecting the value and updating its properties. Or, set properties in bulk by importing overrides through the **Financial dimension values entity** via DMF. When you set a property, the value appears in subsequent OData add-in workbooks and DMF exports.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
