---
# required metadata

title: Invoice capture financial dimensions
description: This article provides information about using financial dimensions in invoice capture.
author: sunfzam
ms.date: 12/07/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Invoice capture financial dimensions

[!include [banner](../includes/banner.md)]

This article provides information about using financial dimensions in invoice capture.

## Background 

Financial dimensions play a crucial role in optimizing the invoice processing workflow for cost invoices. This ensures the invoices can be redirected to the appropriate individuals for approval within Dynamics
365 Finance. Financial dimensions can be specified at either the invoice header or line level. When financial dimension values aren't provided in Invoice capture, defaulting logic is used to transfer invoices from Invoice capture to Dynamics 365 Finance. 
 

This article provides information about financial dimensions within Invoice capture. It provides guidance about extending the solution to support financial dimensions that align with specific business requirements in the Dynamics 365 Finance. 

## Standard fields

Invoice capture contains three financial dimension fields on the header that determines the right person for approval: 
 - Business unit
 - Department
 - Cost center 

To make these fields visible in the side-by-side viewer: **Select configuration group** > select the **Cost invoice** type > Click **Manage visible fields**.

The financial dimension fields are available on the invoice header in the side-by-side viewer. During manual reviews, AP clerks can enter the financial dimension value from the lookup lists.  

>[!Note]
> When the feature **Integration of custom prebuilt model** is released, values can be automatically captured from the document and assigned to the corresponding field.  


During the invoice transfer, the default financial dimension fields from invoice capture are automatically mapped to the relevant fields in the invoice header in Dynamics 365 Finance. The financial dimensions
are automatically serialized to accommodate the financial dimension setting within Dynamics 365 fields.  

When invoices are created using a **Vendor invoice**, the transferred financial dimension values can be viewed going to: **Pending vendor invoice** > **Invoice header** > **Financial dimensions**.  

When invoices are created using the **Invoice journal**, the transferred financial dimension values can be viewed in the **Invoice journal detailed**. 

>[!Note]
>Starting in Dynamics 365 Finance version 10.0.39, standard financial dimension field mapping and serialization logic is available in Dynamics 365 Finance. Customers on earlier versions will have to implement their own logic in their own extension.  

### Extension  

Go to **Financial dimension configuration for integration** application, customers can update to the financial dimension setting to meet business needs by incorporating additional fields and adjusting their
order. To accommodate the flexible settings of financial dimensions, two extensions are required for a vendor invoice automation solution for cost invoices. 

 
### Add financial dimension fields in Invoice capture

The definitions of financial dimension fields aren't different from the invoice header or line within the Invoice capture. 

### Financial dimension serialization 
Before importing the financial dimensions into the corresponding vendor invoice entities, the financial dimensions have to be serialized. In Dynamics 365 Finance version 10.0.39, serialization logic is available. 

### Example

For example, a customer wants to transfer three dimension fields from invoice capture to Dynamics 365 Finance on pending invoice lines. The logical field names of the three dimension fields are “vis_businessunit”,”vis_costcenter” and ”vis_department”. In version 10.0.39, the VendInvoiceCapInvDataUpdateHandler class is available for customers to make extension. Four methods are provided in the
class to update header and lines for pending invoice and invoice journal. 

using Newtonsoft.Json.Linq; 

public class VendInvoiceCapInvDataUpdateHandler 

{ 

```    public static void updateInvoiceHeader(VendorInvoiceHeaderEntity _header, JArray _attributes, CapturedInvoiceType _invoiceType) 

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

Customers need to use the chain of command to extend their own logic. Example code segments to extend functionality to update pending invoice lines are below: 

 using Newtonsoft.Json.Linq; 

[ExtensionOf(classStr(VendInvoiceCapInvDataUpdateHandler))] 

internal final class VendInvoiceCapInvPendingVendorInvoiceProcessor_Extension 

{ 

```    public static void updateInvoiceLine(VendorInvoiceLineEntity _line, JArray _attributes, CapturedInvoiceType _invoiceType) 

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

 Below is the logic how to serialize the financial dimension set to a string: 

```     str displayValue; 

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
