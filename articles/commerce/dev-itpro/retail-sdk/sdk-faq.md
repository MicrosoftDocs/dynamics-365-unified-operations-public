---
# required metadata

title: Retail SDK FAQ
description: This topic summarizes answers to questions that are frequently asked by users of the Retail SDK.
author: mugunthanm 
manager: AnnBe
ms.date: 06/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2020-06-10
ms.dyn365.ops.version: 10.0.9
---

# Retail SDK FAQ

[!include [banner](../../includes/banner.md)]

This topic summarizes answers to questions that are frequently asked by users of the Retail SDK.


## How do I handle a runtime error thrown when using ISupportedTypesAware in SDK version (10.0.420.10003~10.0.420.10033)?

This error might occur when you use **ISupportedTypesAware**.

*Exception: System.MissingMethodException: Method not found: \'System.Collections.Generic.IEnumerable`1<System.Type> 
Microsoft.Dynamics.Commerce.Runtime.ISupportedTypesAware.get_SupportedRequestTypes()\'*

When extending or implementing CRT handlers, use **IRequestHandlerAsync** instead of **ISupportedTypesAware**. **ISupportedTypesAware** is not supported and if used in extension it may cause this runtime error. Additionally, don't use explicit implementations. 


The following example shows the recommended approach using **IRequestHandlerAsync**.

```csharp

public class MyHandler : IRequestHandlerAsync
{
    public IEnumerable<Type> SupportedRequestTypes
    {
        get
        {
            return new[]
            {
                typeof(MyRequest)
            };
        }
    }

    public Task<Response> Execute(Request request)
    {
        // Return response.
    }
}
```

The following examples, which is not recommended, uses **ISupportedTypesAware**.

```csharp
// NOT RECOMMENDED
public class MyHandler : IRequestHandlerAsync, ISupportedTypesAware
{
    public IEnumerable<Type> SupportedRequestTypes
    {
        get
        {
            return new[]
            {
                typeof(MyRequest)
            };
        }
    }

    Task<Response> IRequestHandlerAsync.Execute(Request request)
    {
        return null;
    }
}
```

## ReadOnly CartValidationException - in SDK version (10.0.0 and later)

This error will occur if the below read-only properties are updated in SDK version 10.0.9 or lesser, these properties are made read-only in SDK version  10.0.0 to avoid some miscalculations in the cart total:

- ExtendedPrice
- TaxAmount
- ItemTaxGroupId
- TaxAmountExclusive
- TaxAmountInclusive
- TotalAmount
- NetAmountWithoutTax
- IsInvoiceLine
- InvoiceId
- InvoiceAmount

To mitigate this issue, remove the code in client/server setting this value and OOB code will calculate these values or keep the logic in the read-only fields by following the below approach but later should modify the code according to the best practice (this option is not recommended) :

In HQ Commerce parameters > Configuration parameters > create a new config with the a name/value like the following pattern:

**RetailReadOnlyExempt_[EntityName] : [ColumnName]**

For instance, in the error at the top of this page, ITEMTAXGROUPID is the read-only property with the error. You can search to see this is part of CartLine and CartLineData. So our configuration name/value pair would look like this:

**RetailReadOnlyExempt_CartLineData : ITEMTAXGROUPID**  **Note:** The ITEMTAXGROUPID is the column name of the property not the actual property name.

After adding the config **run job 1110 to push this change**.

