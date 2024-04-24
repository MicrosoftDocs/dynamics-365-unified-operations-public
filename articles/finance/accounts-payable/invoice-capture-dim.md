---
title: Invoice capture financial dimensions
description: Learn about how to use financial dimensions in Invoice capture, including overviews on standard fields and extensions, with code examples.
author: sunfzam
ms.author: zezhangzhao
ms.topic: overview
ms.date: 12/07/2023
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-09-28
ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
ms.dyn365.ops.version: 
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
---

# Invoice capture financial dimensions

[!include [banner](../includes/banner.md)]

This article provides information about financial dimensions in Invoice capture and explains how to use them. It provides guidance for extending the solution to support financial dimensions that are aligned with specific business requirements in Microsoft Dynamics 365 Finance.

Financial dimensions play a crucial role in optimizing the invoice processing workflow for cost invoices. This optimization ensures that the invoices can be redirected to the appropriate individuals for approval in Dynamics 365 Finance. Financial dimensions can be specified at either the invoice header level or the line level. If financial dimension values aren't provided in Invoice capture, defaulting logic is used to transfer invoices from Invoice capture to Dynamics 365 Finance.

## Standard fields

In Invoice capture, three financial dimension fields on the header are used to determine the correct person for approval:

- Business unit
- Department
- Cost center

To make these fields available on the invoice header in the side-by-side viewer, select a configuration group, select the **Cost invoice** type, and then select **Manage visible fields**.

During manual reviews, Accounts payable (AP) clerks can enter the financial dimension values from the lookup lists.

> [!NOTE]
> When the **Integration of custom prebuilt model** feature is released, values can be automatically captured from the document and assigned to the corresponding field.

During the invoice transfer, the default financial dimension fields from Invoice capture are automatically mapped to the relevant fields on the invoice header in Dynamics 365 Finance. The financial dimensions are automatically serialized to accommodate the financial dimension settings in Dynamics 365 fields.

When invoices are created by using a vendor invoice, you can view the transferred financial dimension values by going to **Pending vendor invoice** \> **Invoice header** \> **Financial dimensions**. When invoices are created by using the invoice journal, you can view the transferred financial dimension values in **Invoice journal detailed**.

> [!NOTE]
> As of Dynamics 365 Finance version 10.0.39, standard financial dimension field mapping and serialization logic is available. Customers who use earlier versions must implement their own logic in their own extension.

## Extension

In the Financial dimension configuration for integration application, customers can update the financial dimension settings to meet their business needs by incorporating additional fields and adjusting their order. To accommodate the flexible settings of financial dimensions, two extensions are required for a vendor invoice automation solution for cost invoices.

### Add financial dimension fields in Invoice capture

The definitions of financial dimension fields don't differ from the invoice header or line in Invoice capture.

### Financial dimension serialization

Before you import the financial dimensions into the corresponding vendor invoice entities, the financial dimensions must be serialized. In Dynamics 365 Finance version 10.0.39, serialization logic is available.

### Example

For example, a customer wants to transfer three dimension fields from Invoice capture to Dynamics 365 Finance on pending invoice lines. The logical field names of the three dimension fields are **vis\_businessunit**, **vis\_costcenter**, and **vis\_department**. In version 10.0.39, customers can use the `VendInvoiceCapInvDataUpdateHandler` class to make an extension. This class provides four methods for updating the header and lines for the pending invoice and invoice journal.

```
using Newtonsoft.Json.Linq; 
public class VendInvoiceCapInvDataUpdateHandler 
{ 
    public static void updateInvoiceHeader(VendorInvoiceHeaderEntity _header, JArray _attributes, CapturedInvoiceType _invoiceType) 
    { 
    } 
    public static void updateInvoiceLine(VendorInvoiceLineEntity _line, JArray _attributes, CapturedInvoiceType _invoiceType) 
    {
    } 
    public static void updateInvoiceJournalHeader(VendInvoiceJournalHeaderEntity _journalHeader, JArray _attributes) 
    { 
    } 
    public static void updateInvoiceJournalLine(VendInvoiceJournalLineEntity _journalLine, JArray _attributes) 
    { 
    }
}
```

Customers must use the chain of command to extend their own logic. The following example code segments show how to extend functionality to update pending invoice lines.

```
using Newtonsoft.Json.Linq; 
[ExtensionOf(classStr(VendInvoiceCapInvDataUpdateHandler))]
internal final class VendInvoiceCapInvPendingVendorInvoiceProcessor_Extension 
{ 
    public static void updateInvoiceLine(VendorInvoiceLineEntity _line, JArray _attributes, CapturedInvoiceType _invoiceType) 
    { 
        next updateInvoiceLine(_line, _attributes, _invoiceType); 
        Map dimensionMap = new Map(Types::String, Types::String); 
        System.Collections.IEnumerator iterator = _attributes.GetEnumerator(); 
        while (iterator.MoveNext()) 
        { 
            JObject attribute = iterator.Current; 
            str propName = attribute.GetValue('Key').ToString(); 
            switch (propName) 
            { 
                case "vis_businessunit": 
                    dimensionMap.insert("BusinessUnit", attribute.GetValue('Value').ToString()); 
                    break; 
                case "vis_costcenter": 
                    dimensionMap.insert("CostCenter", attribute.GetValue('Value').ToString()); 
                    break; 
                case "vis_department": 
                    dimensionMap.insert("Department", attribute.GetValue('Value').ToString()); 
                    break; 
            } 
        }
```

The following example shows the logic for serializing the financial dimension set to a string.

```
        str displayValue; 
        str dimensionSegmentDelimiter = DimensionParameters::getDimensionSegmentDelimiter(); 
        DefaultDimensionIntegrationStructureDisplay dimensionAttributesFormat = DimensionHierarchy::getDisplayStringDimensionIntegrationStructure(DimensionDataEntityStructureType::DataEntityDefaultDimensionFormat); 
        List dimensionNames = DimensionResolver::splitByDimensionIntegrationDelimiter(dimensionAttributesFormat); 
        ListEnumerator listEnum = dimensionNames.getEnumerator(); 
        while (listEnum.moveNext()) 
        { 
            str dimensionName = listEnum.current(); 
            str segmentValue; 
            if(dimensionMap.exists(dimensionName)) 
            { 
                segmentValue = any2Str(dimensionMap.lookup(dimensionName)); 
            } 
            displayValue += ((displayValue == "")? segmentValue : (dimensionSegmentDelimiter + segmentValue)); 
        } 
        _line.DimensionDisplayValue = displayValue; 
        _line.update(); 
    } 
}
```
