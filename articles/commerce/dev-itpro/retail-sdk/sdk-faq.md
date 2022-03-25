---
# required metadata

title: Retail SDK FAQ
description: This topic summarizes answers to questions that are frequently asked by users of the Retail SDK.
author: mugunthanm 
ms.date: 06/30/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
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

The following example, which is not recommended, uses **ISupportedTypesAware**.

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

## How do I handle a ReadOnly CartValidationException error in SDK version (10.0.0 and later)?

This error will occur if the following read-only properties are updated in SDK version 10.0.9 or earlier. These properties are made read only in SDK version 10.0.0 to avoid miscalculations in the cart total:

- ExtendedPrice
- TaxAmount
- ItemTaxGroupId
- TaxAmountExclusive
- TaxAmountInclusive
- TotalAmount
- NetAmountWithoutTax
- IsInvoiceLine
- InvoiceAmount

To resolve this issue, remove the code in the client/server. Setting this value and OOB code will calculate these values or keep the logic in the read-only fields. You can follow the example shown below, however be sure to modify the code according to the best practice, as this option is not recommended.

In **HQ Commerce parameters > Configuration parameters > Create a new config** with a name/value like the following pattern:

**RetailReadOnlyExempt_[EntityName] : [ColumnName]**

For example, in the error at the top of this page, ITEMTAXGROUPID is the read-only property with the error. You can search to see this is part of CartLine and CartLineData. The configuration name/value pair would look like this:

**RetailReadOnlyExempt_CartLineData : ITEMTAXGROUPID**  

Additionally, to exempt more than one column for a given entity, use a comma as the separator for column names. The configuration name/value pair in this case would look like this:

**RetailReadOnlyExempt_CartLineData : TAXAMOUNT,TOTALAMOUNT, ExtendedPrice, ItemTaxGroupId, TaxAmountExclusive, TaxAmountInclusive, TotalAmount, NetAmountWithoutTax, IsInvoiceLine, InvoiceAmount**

> [!NOTE]
> ITEMTAXGROUPID, TAXAMOUNT, TOTALAMOUNT are the column names of the properties in the examples above, not the actual property names. The entity name for the CartLine is CartLineData.

After adding the config run job 1110 to push this change.

## Deployment failed with error - Could not load file or assembly Microsoft.Dynamics.Commerce.RetailServer.Extensibility.Contracts

**Deployment of the new retail deployable package fails with the message:**

*An unhandled exception occurred during the execution of the current web request. Please review the stack trace for more information about the error and where it originated in the code. 
Could not load file or assembly "Microsoft.Dynamics.Commerce.RetailServer.Extensibility.Contracts, Version=7.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" or one of its dependencies. The system cannot find the file specified.*

This error may occur if the extension project upgraded from Retail SDK version 10.0.10 or 10.0.11 to Retail SDK version 10.0.12 or later, and there are extension projects referencing Microsoft.Dynamics.Commerce.RetailServer.Extensibility.Contracts.

To fix this issue, remove the reference to Microsoft.Dynamics.Commerce.RetailServer.Extensibility.Contracts in the extension project and regenerate the package and deploy again. Removing this reference library will not impact extension code/functionality because it’s not needed for extension solutions. Starting in version 10.0.11, extensions can refer to Microsoft.Dynamics.Commerce.Hosting.Contracts for Retail server APIs.

## MSbuild in SDK version 10.0.19 and 10.0.20 fails while checking Visual Studio 2017 dependencies

In Retail SDK version 10.0.19 and 10.0.20, the MSBuild command fails while checking for Visual Studio 2017 dependencies. During MSBuild, the script checks if all the prerequisites are installed, if not, the script will try to install the prerequisites but will fail and display one of the following errors:

- Error RetailSDK\dirs.proj(14,9): Error MSB3073: The command "powershell -NoProfile -NonInteractive .\BuildTools\checkVS2017Dependencies.ps1" exited with code -1.
- Error MSB3073: The command "powershell -NoProfile -NonInteractive .\BuildTools\checkVS2017Dependencies.ps1" exited with code -1.
- EXEC : An error occurred: Microsoft.VisualStudio.Product.Professional (15.9.28307.1440) vsconfig export fail! [K:\10.0.
19\RetailSDK\Code\dirs.proj]

To this resolve issue, run msbuild with the parameter **msbuild /p:CheckVSDependencies=False**. If prerequisites are missing, install everything by manually by following the [Retail software development kit (SDK) prerequisites](/dynamics365/commerce/dev-itpro/retail-sdk/retail-sdk-overview#prerequisites).

In the Azure DevOps pipeline, pass the parameter -p:CheckVSDependencies=False in the MSBuild argument.

## Retail SDK MSbuild fails with missing .NET Framework 4.5.1 or 4.6.2 or Web deploy components error

If the Retail SDK msbuild fails with an error noting that the .NET Framework 4.5.1 or 4.6.2 or Web deploy components are missing, then install the following components:

- .NET Developer Pack:
    +  [.NET Framework 4.5.1](https://dotnet.microsoft.com/download/dotnet-framework/thank-you/net451-developer-pack-offline-installer)
    +  [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/thank-you/net451-developer-pack-offline-installer)
    
- [Web Deploy v3.6 ](https://www.microsoft.com/download/confirmation.aspx?id=43717)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
