---
title: Invoice capture custom fields
description: Learn about how to use custom fields in the Invoice capture solution, including an overview on custom field properties and data types.
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

# Invoice capture custom fields

[!include [banner](../includes/banner.md)]

This article explains how to use custom fields in the Invoice capture solution.

Invoice capture introduced standard fields on the header and lines to address the processing of invoices. However, customers often have additional fields that must be supported to meet business requirements. The **Support custom fields in Invoice capture** feature can create additional fields that have different properties. The value of these fields can be either automatically extracted from the original document or manually entered by the reviewer.

## Custom field properties

Invoice capture has two scopes for the invoice fields: Header and Line.

Invoice capture has three field groups: **General**, **Tax**, and **Charges**. **Tax** and **Charges** are used to increase the number of lines in the **Tax** and **Charges** panes. **Tax** and **Charges** aren't supported at the line level.

## Data types

Invoice capture support three data types for custom fields:

- Single line of text
- Date and time (date only)
- Currency 

## Implementation

To create a new solution and add custom fields, follow these steps.

1. Sign in to the [Power Apps maker portal](https://make.powerapps.com/), and select the target environment.
2. Select **Solutions**, and then select **New solution**.
3. Open the solution, and add the following tables:

    - Staging invoice header
    - Staging invoice line
    - User-defined field setting

4. Select the **Staging invoice header** or **Staging invoice line** table, and then select **Next**.
5. Select **Add**.
6. Select the table, and then select **New** \> **Column**.
7. Enter the field name, select the data type, and then select **Save**.
8. Find the column that you just created, and make a note of the logical name.
9. Select **User defined field setting**, and then select **Edit**.
10. Select **New row using form**, enter the value for field properties, and then select **Save**.

To review the details for each field, follow these steps.

1. In Invoice capture, go to **Setup system** \> **Manage configuration group**.
2. Select the configuration group, and then select **Manage visible fields** to add the fields.
3. The side-by-side viewer shows the added fields, and you can enter values.

## Map custom fields

The value of custom fields must be mapped to the corresponding fields in Microsoft Dynamics 365 Finance. You must use a custom extension to do this mapping.

For example, in Invoice capture, there's a field that has the logical name **cus\_udfdate**. This field will be mapped to the **CashDiscountDate** field in the invoice header of Dynamics 365 Finance.

Here's the sample code.

```
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
```
