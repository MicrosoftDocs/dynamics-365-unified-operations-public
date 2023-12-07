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

This article provides information about about using financial dimensions in invoice capture.

## Background 

Financial dimensions play a crucial role in optimizing the invoice processing workflow for cost invoices. This ensures the invoices can be redirected to the appropriate individuals for approval within Dynamics
365 Finance. Financial dimensions can be specified at either the invoice header or line level. When financial dimension value is not provided in Invoice capture, defaulting logic comes into play during the 
transfer of the invoice from Invoice capture to Dynamics 365 Finance. 

 

This article provides insights into the support for financial dimensions within Invoice capture. Additionally, it guides customers on extending the solution to cater to the dynamic financial dimension settings 
that align with their specific business requirements in the Dynamics 365 Finance. 

## Standard field

In the standard field definition for cost invoices, Invoice capture offers three default financial dimension fields on the header level that are commonly utilized to determine the right person for approval: 
 - Business unit
 - Department
 - Cost center 

Customers can make these fields visible in SBS viewer under the configuration group > Select configuration group > Choose "Cost invoice” type > Click “Manage visible fields”. 

Then the financial dimension fields will be available on the invoice header panel in SBS viewer. During manual reviews, AP clerks can enter the financial dimension value from the lookup lists.  

>[!Note]
> When the feature “Integration of custom prebuilt model” is ready, the value can be automatically captured from the document and assigned to the corresponding fields.  


During the invoice transfer, the default financial dimension fields from invoice capture will be automatically mapped to the relevant fields in the invoice header in Dynamics 365 Finance. The financial dimension
set will be automatically serialized to accommodate the financial dimension setting within Dynamics 365 fields.  

In case the invoice is created within the "Vendor Invoice" framework, the transferred financial dimensions value can be found within Pending Vendor Invoice > Invoice Header > Financial Dimensions.  

In case the invoice is created within the "Invoice journal" framework, the transferred financial dimension value can be found under the offset account field in the invoice journal detailed form. 

Note: 

Before release 10.0.39, the standard financial dimension field mapping and serialization logic are not available in the Dynamics 365 Finance. This means that customers have to implement their own logic to cover
both in their own extension.  

### Extension  

Under "Financial dimension configuration for integration application", customers can cater to the financial dimension setting to meet their own business need by incorporating additional fields and adjusting their
order. To accommodate the flexible settings of financial dimensions, two extensions are required to build such an end-to-end vendor invoice automation solution for cost invoices. 

 
### Add financial dimension fields in Invoice capture

The definitions of financial dimension fields have no difference from the ones on invoice header or line within the Invoice capture. For detailed guidance, please refer to the chapter "Support custom fields in 
Invoice capture". 

### Financial dimension serialization 

To successfully import the financial dimensions value set into Dynamics 365 Finance, the financial dimension set has to be serialized to a string before importing the value into corresponding vendor invoice 
entities.  

Following the 10.0.39 update, a standardized serialization logic will be provided. Customers will then only require focusing on the definition of the mapping between Invoice Capture and Dynamics 365 Finance 
fields. 

Taking the scenario below as an extension example: customers want to transfer three dimension fields from invoice capture to F&O on pending invoice lines. The logical field names of those three dimension fields
are “vis_businessunit”,”vis_costcenter” and ”vis_department”. Following the 10.0. 39 update, we will expose a class  VendInvoiceCapInvDataUpdateHandler for customer to make extension, we provide 4 methods in the
class to update header and lines for pending invoice and invoice journal. 

 

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


Customers need to use COC(chain of command) to extend their own logic, example code segment to extend the functionality to update pending invoice lines as below: 

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

        // Below is the logic how to serialize the financial dimension set to a string 

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
