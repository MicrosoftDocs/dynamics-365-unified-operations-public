---
# required metadata

title: Pre-extended columns in the channel database
description: This topic explains how the pre-extended columns in the channel database are consumed for extensions.
author: mugunthanm
ms.date: 06/04/2020
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
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2020-02-02
ms.dyn365.ops.version: 10.0.10

---

# Pre-extended columns in the channel database

[!include [banner](../../includes/banner.md)]

Some columns in the channel database are *pre-extended*. In other words, the column length in the channel database exceeds the column length in Microsoft Dynamics 365 Commerce Headquarters. For example, the length of the **INVENTSERIALID** field is 20 characters in the Commerce Headquarters database but 50 characters in the channel database.

Although fields in the channel database are often extended, column lengths for those fields aren't extensible. Therefore, out-of-box column lengths have been increased to support extension scenarios.

> [!NOTE]
> If you must extend a field that isn't already pre-extended, you must file an extension request in Lifecycle Services (LCS). For more information, see [Extensibility requests](../../fin-ops-core/dev-itpro/extensibility/extensibility-requests.md).

Although the fields are extended in the channel database, your extension must also extend the field in the Commerce Headquarters database by using the extended data type (EDT) extension model. Additionally, you must extend the corresponding point of sale (POS) or Commerce runtime (CRT) user interface (UI).

If the Commerce Headquarters database isn't extended, either synchronization between the channel database and the Commerce Headquarters database will fail during the P-job or the extra characters will be truncated. Likewise, if the corresponding point of sale (POS) user interface (UI) or the Commerce runtime (CRT) isn't extended, validation will prevent more than the default character length from being entered. The default length is determined by the base column length in the Commerce Headquarters database.

Here are some examples:

- The length of the **INVENTSERIALID** field in the channel database is 50 characters, but the POS UI accepts serial numbers that are a maximum of only 20 characters long. In this case, you must extend the field in both the POS UI and the Commerce Headquarters database.
- The length of the **STREET** field in the channel database is extended to 400 characters, but validation in CRT prevents more than the default length in the Commerce Headquarters database from being accepted. In this case, you must extend both the CRT request handler (**ValidateAddressLengthServiceRequest**) and the Commerce Headquarters database, so that 400 characters are accepted for the **STREET** field.

Extension of the POS UI or CRT handlers isn't required for some fields, because they might be read-only fields in POS. For example, **ECORES** product-related fields are read-only. Because product creation isn't supported in POS, there is no write scenario for products in POS.

## Sample code to override the ValidateAddressLengthServiceRequest handler

The following example shows how to override the **ValidateAddressLengthServiceRequest** handler.

```C#
namespace Contoso
{
    namespace Commerce.Runtime.ReceiptsSample
    {
        using System;
        using System.Collections.Generic;
        using Microsoft.Dynamics.Commerce.Runtime;
        using Microsoft.Dynamics.Commerce.Runtime.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.Services.Messages;

        public class ValidateAddressLengthServiceRequestExt : IRequestHandler
        {
            private static int maxDefaultFullAddressColumnLength = 250;
            private static int maxDefaultStreetColumnLength = 250;
            private static int maxDefaultCountyColumnLength = 10;

            /// <summary>
            /// Gets the collection of supported request types by this handler.
            /// </summary>
            public IEnumerable<Type> SupportedRequestTypes
            {
                get
                {
                    return new[]
                    {
                        typeof(ValidateAddressLengthServiceRequest),
                    };
                }
            }

            public Response Execute(Request request)
            {
                if (request == null)
                {
                    return null;
                }

                ValidateAddressLengthServiceRequest validateAddressLengthServiceRequest = (ValidateAddressLengthServiceRequest)request;

                var validationFailures = new List<DataValidationFailure>();

                // Add custom logic to check your desired length.

                if (!string.IsNullOrEmpty(validateAddressLengthServiceRequest?.Address?.FullAddress) 
                && validateAddressLengthServiceRequest.Address.FullAddress.Length > maxDefaultFullAddressColumnLength)
                {
                    validationFailures.Add(new DataValidationFailure(
                        DataValidationErrors.Microsoft_Dynamics_Commerce_Runtime_AddressLengthExceeded,
                        string.Format("The full address exceeds the maximum number of {0} characters allowed.",
                        maxDefaultFullAddressColumnLength))
                    {
                        LocalizedMessageParameters = new object[] { maxDefaultFullAddressColumnLength }
                    });
                }

                // Add custom logic to check your desired length.

                if (!string.IsNullOrEmpty(validateAddressLengthServiceRequest?.Address?.Street) 
                && validateAddressLengthServiceRequest.Address.Street.Length > maxDefaultStreetColumnLength)
                {
                    validationFailures.Add(new DataValidationFailure(
                        DataValidationErrors.Microsoft_Dynamics_Commerce_Runtime_StreetLengthExceeded,
                        string.Format("The street exceeds the maximum number of {0} characters allowed.", maxDefaultStreetColumnLength))
                    {
                        LocalizedMessageParameters = new object[] { maxDefaultStreetColumnLength }
                    });
                }

                // Add custom logic to check your desired length.

                if (!string.IsNullOrEmpty(validateAddressLengthServiceRequest?.Address?.County) 
                && validateAddressLengthServiceRequest.Address.County.Length > maxDefaultCountyColumnLength)
                {
                    validationFailures.Add(new DataValidationFailure(
                        DataValidationErrors.Microsoft_Dynamics_Commerce_Runtime_CountyLengthExceeded,
                        string.Format("The county exceeds the maximum number of {0} characters allowed.", maxDefaultCountyColumnLength))
                    {
                        LocalizedMessageParameters = new object[] { maxDefaultCountyColumnLength }
                    });
                }

                if (validationFailures.Count > 0)
                {
                    throw new DataValidationException(DataValidationErrors.Microsoft_Dynamics_Commerce_Runtime_AggregateValidationError,
                    validationFailures, "An error occurred when validating the address.");
                }

                return new NullResponse();
            }
        }
    }
}
```

## Pre-extended columns in the channel database

The following table lists the columns that are pre-extended.

| Table                         | Column                                                                        | Length        | Extension in CRT      | Extension in POS                    |
|-------------------------------|-------------------------------------------------------------------------------|---------------|-----------------------|-------------------------------------|
| INVENTSERIAL                  | INVENTSERIALID                                                                | nvarchar(50)  |                       | GetSerialNumberClientRequestHandler |
| LOGISTICSPOSTALADDRESS        | ADDRESS                                                                       | nvarchar(500) | ValidateAddressLength |                                     |
| LOGISTICSPOSTALADDRESS        | STREET                                                                        | nvarchar(400) | ValidateAddressLength |                                     |
| LOGISTICSPOSTALADDRESS        | COUNTY                                                                        | nvarchar(60)  | ValidateAddressLength |                                     |
| LOGISTICSADDRESSCITY          | COUNTYID                                                                      | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSCITY          | STATEID                                                                      | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSCOUNTY        | COUNTYID                                                                      | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSDISTRICT      | COUNTYID\_RU                                                                  | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSDISTRICT      | STATEID\_RU                                                                  | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSZIPCODE       | STREETNAME                                                                    | nvarchar(400) |                       |                                     |
| LOGISTICSADDRESSZIPCODE       | COUNTY                                                                        | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSZIPCODE       | STATE                                                                        | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSZIPCODE       | ZIPCODE                                                                        | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSSTATE        | STATEID                                                                        | nvarchar(60)  |                       |                                     |
| LOGISTICSELECTRONICADDRESS   | COUNTRYREGIONCODE                                                              | nvarchar(10)  |   ValidateElectronicAddressServiceRequest                    |                                     |
| RETAILASYNCADDRESS            | STREET                                                                        | nvarchar(400) |                       |                                     |
| RETAILASYNCADDRESS            | COUNTY                                                                        | nvarchar(60)  |                       |                                     |
| RETAILASYNCCUSTOMER           | STREET                                                                        | nvarchar(400) |                       |                                     |
| RETAILASYNCCUSTOMER           | COUNTY                                                                        | nvarchar(60)  |                       |                                     |
| CUSTOMERTABLETYPE_V2           | FIRSTNAME                                                                        | nvarchar(100)  | ValidateCustomerNameLengthServiceRequest                     |                                     |
| CUSTOMERTABLETYPE_V2          | MIDDLENAME                                                                        | nvarchar(100)  | ValidateCustomerNameLengthServiceRequest                       |                                     |
| CUSTOMERTABLETYPE_V2           | LASTNAME                                                                        | nvarchar(100)  |  ValidateCustomerNameLengthServiceRequest                      |                                     |
| RETAILFISCALDOCUMENT\_BR      | FEADDRESSSTREET                                                               | nvarchar(400) |                       |                                     |
| RETAILFISCALDOCUMENT\_BR      | THIRDPARTYADDRESSSTREET                                                       | nvarchar(400) |                       |                                     |
| RETAILTAXFILTERS              | COUNTYID                                                                      | nvarchar(60)  |                       |                                     |
| RETAILTRANSACTIONADDRESSTRANS | STREET                                                                        | nvarchar(400) |                       |                                     |
| RETAILTRANSACTIONADDRESSTRANS | COUNTY                                                                        | nvarchar(60)  |                       |                                     |
| RETAILTRANSACTIONSALESTRANS   | INVENTBATCHID                                                                 | nvarchar(50)  |                       |                                     |
| RETAILTRANSACTIONSALESTRANS   | INVENTSERIALID                                                                | nvarchar(50)  |                       |                                     |
| RETAILTRANSACTIONSALESTRANS   | WAREHOUSELOCATION                                                             | nvarchar(60)  |                       |                                     |
| RETAILDLVMODEADDRESSEXPLODED   | STATE                                                                        | nvarchar(60)  |                       |                                     |
| INVENTDIM                     | INVENTBATCHID                                                                 | nvarchar(50)  |                       |                                     |
| INVENTDIM                     | INVENTSERIALID                                                                | nvarchar(50)  |                       |                                     |
| INVENTDIM                     | CONFIGID                                                                      | nvarchar(60)  |                       |                                     |
| INVENTDIM                     | INVENTCOLORID                                                                 | nvarchar(60)  |                       |                                     |
| INVENTDIM                     | INVENTSIZEID                                                                  | nvarchar(60)  |                       |                                     |
| INVENTDIM                     | INVENTSTYLEID                                                                 | nvarchar(60)  |                       |                                     |
| INVENTDIM                     | WMSLOCATIONID                                                                 | nvarchar(60)  |                       |                                     |
| ECORESCOLOR                   | NAME                                                                          | nvarchar(60)  |                       |                                     |
| ECORESSTYLE                   | NAME                                                                          | nvarchar(60)  |                       |                                     |
| ECORESCONFIGURATION           | NAME                                                                          | nvarchar(60)  |                       |                                     |
| ECORESSIZE                    | NAME                                                                          | nvarchar(60)  |                       |                                     |
| RETAILTABLEFIELDID            | TABLENAME                                                                     | nvarchar(81)  |                       |                                     |
|                               | FIELDNAME                                                                     | nvarchar(81)  |                       |                                     |
| RETAILTRANSACTIONTAXTRANSGTE  | TAXCOMPONENT                                                                  | nvarchar(60)  |                       |                                     |
| TAXCOMPONENTTABLE\_IN         | COMPONENT                                                                     | nvarchar(60)  |                       |                                     |
| WMSLOCATION                   | INPUTLOCATION                                                                 | nvarchar(60)  |                       |                                     |
|                               | WMSLOCATIONID                                                                 | nvarchar(60)  |                       |                                     |
| INVENTLOCATION                | RBODEFAULTWMSLOCATIONID                                                       | nvarchar(60)  |                       |                                     |
|                               | WMSLOCATIONIDDEFAULTISSUE                                                     | nvarchar(60)  |                       |                                     |
|                               | WMSLOCATIONIDDEFAULTRECEIPT                                                   | nvarchar(60)  |                       |                                     |
| PRICEDISCTABLE                | CONSTRAINT I\_137462222\_1904821809: { "action": "replace-line", "value": "CONSTRAINT \[I\_PRICEDISCTABLE\_RECID\] PRIMARY KEY CLUSTERED ( \[RECID\] ) "CONSTRAINT I\_PRICEDISCTABLE\_RECID": { "action": "remove-line" } |               |                       |                                     |
| OMOPERATINGUNIT               | OMOPERATINGUNITNUMBER                                                         | nvarchar(30)  |                       |                                     |
| RETAILPARAMETERS              | USEADVANCEDAUTOCHARGE INT NULL DEFAULT(0)                                     |               |                       |                                     |
|                               | GIFTCARDINQUIRYPRINTHISTORY INT NULL DEFAULT(0)                               |               |                       |                                     |
| RETAILINFOCODETABLE           | PRINTINPUTONFISCALRECEIPT \[int\] NULL DEFAULT (0) PRINTTEXTONFISCALRECEIPT \[nvarchar\] (50) NULL DEFAULT('') |               |                       |                                     |
| RETAILINFORMATIONSUBCODETABLE | PRINTTEXTONFISCALRECEIPT \[nvarchar\](50) NULL DEFAULT('')                    |               |                       |                                     |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
