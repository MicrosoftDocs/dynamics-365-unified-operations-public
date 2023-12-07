---
# required metadata

title: Invoice capture custom fields
description: This article provides information about using custom fields in the Invoice capture solution.
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

# Invoice capture solution

[!include [banner](../includes/banner.md)]

This article provides information about using custom fields in the Invoice capture solution.

## Overview  

Invoice capture introduced the standard fields on the header and lines to address processing invoices. However, due to the complexity of the business, customers often have additional fields that need to be 
supported to meet their own business requirements. By introducing the feature "Support custom fields in Invoice capture", customers can tailor the solution on the top of Invoice capture by adding additional 
field with different properties. The value of these fields can be either automatically extracted from the original document or manually entered by the reviewer. 

### Custom fields properties 

Invoice capture has two scopes of the invoice fields: Header and Line.  
Invoice capture has three field groups: **General**, **Tax**, **Charges**. 
**Tax** and **Charges** are used to increase the number of lines in **Tax** and **Charges** panels. **Tax** and **Charges** on the line level are not supported.  

### Data types  

Invoice capture support three data types for custom fields: single line of text, date and time (date only), and currency. 

### Implementation  

To create a new solution and add custom fields, follow these steps: 
1. Go to https://make.powerapps.com/ and select the target environment.
2. Click **Solutions**, click **+ New solution**.
3. Open the solution and add the following tables: 
 - Staging invoice header
 - Staging invoice line
 - User-defined field setting 
4. Select the **Staging invoice header** or **Staging invoice line** table, click **Next**.
5. Click **Add**.
6. Select the table, click **New > Column**.
7. Enter the field name and select the data type, click **Save**.
8. Find the created column and record the logical name. 
9. Select **User defined field setting**, click **Edit**.
10. Click **New row using form**. Enter the value for fields properties and click **Save**. 

To check the details for each field, follow these steps:
a. In Invoice capture, go to **Setup system** > **Manage configuration group**.
b. Select the configuration group and add the fields by clicking **Manage visible fields**.
c. In the side-by-side viewer, the added fields will be displayed to enter values.  

### Map custom fields 

The value of custom fields must be mapped to the corresponding fields in Dynamics 365 Finance using a custom extension.  

Considering an example scenario, in invoice capture, there is a field with logical name “cus_udfdate”. This field will be mapped to the CashDiscountDate field in the invoice header of Dynamics 365 Finance. 
Below is the sample code: 

using Newtonsoft.Json.Linq; 
[ExtensionOf(classStr(VendInvoiceCapInvDataUpdateHandler))] 
internal final class VendInvoiceCapInvDataUpdateHandler _Extension 
{ 
    public static void updateInvoiceHeader(VendorInvoiceHeaderEntity _header, JArray _attributes, CapturedInvoiceType _invoiceType) 
    { 
        next updateInvoiceHeader(_header, _attributes, _invoiceType);   
        // extend logic based on invoice type       
        if (_invoiceType == CapturedInvoiceType::CostInvoice) 
        { 
            System.Collections.IEnumerator iterator = _attributes.GetEnumerator(); 
            while (iterator.MoveNext()) 
            { 
                JObject attribute = iterator.Current; 
                str propName = attribute.GetValue('Key').ToString(); 
                str strValue =  attribute.GetValue('Value').ToString(); 
                switch (propName) 
                { 
                    case "cus_udfdate": 
                        _header.CashDiscountDate = str2Date(strValue, 213); 
                        break; 
                } 
            } 
            _header.update(); 
        } 
    } 
} 

