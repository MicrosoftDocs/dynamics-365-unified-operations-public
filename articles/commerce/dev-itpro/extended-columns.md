---
# required metadata

title: Pre extended column in Channel Database
description: This topic explains how the pre-extended columns in the Channel Database are consumed for extensions.
author: mugunthanm
manager: AnnBe
ms.date: 02/13/2020
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
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2020-02-02
ms.dyn365.ops.version: 10.0.10

---

# Pre extended column in Channel Database

[!include [banner](../../includes/banner.md)]

Some columns in the Channel Database are pre-extended. Pre-extended means that the column length in the Channel Database is greater than the column length in Commerce HQ.

For example, the **INVENTSERIALID** field length in the Commerce HQ database is 20 characters, but in channel database it is 50 characters. The reason for this change is the Channel Database field column length are not extensible, and theses fields are commonly extended, so field lengths are increased out-of-box to support extension scenarios. 

If you need to extend a field that is not already pre-extended, then you must file an extension request or support ticket.

Even though the fields are extended in the Channel Database, your extension must also extend the field in the HQ database using the EDT extension model and extend the corresponding POS or CRT UI.

If the HQ database is not extended, then during the P-Job sync between Channel Database and HQ database will either fail or the extra characters will be truncated. Similarly if the POS UI or CRT is not extended then POS UI or CRT validation will prevent entering more than the default character length. The default length is determined by the base column length in HQ database.

For example, suppose that the **INVENTSERIALID** field length in channel database is 50 characters, but the POS UI accepts serial number only up to 20 characters long. In this scenario, you must extend the field in both the POS UI and HQ database.

As another example, suppose that the **STREET** field length in Channel Database is extended to 400 characters, while validation in CRT prevents accepting more than the default HQ database length. To accommodate this scenario, you must extend both the CRT request handler (**ValidateAddressLengthServiceRequest**) and the HQ database to accept 400 characters for the **STREET** field.

Extending the POS UI or CRT handlers is not required for some fields because they might be read-only fields in POS. For example, **ECORES** product-related fields are read-only because there is no write scenario for products in POS. This is because product creation is not supported in POS.

## Sample code to override the ValidateAddressLengthServiceRequest handler

The following code example overrides the **ValidateAddressLengthServiceRequest** handler.

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

## Pre-extended columns in Channel Database

The columns that are pre-extended are listed in the following table.

| Table                         | Column                                                                        | Length        | Extension in CRT      | Extension in POS                    |
|-------------------------------|-------------------------------------------------------------------------------|---------------|-----------------------|-------------------------------------|
| INVENTSERIAL                  | INVENTSERIALID                                                                | nvarchar(50)  |                       | GetSerialNumberClientRequestHandler |
| LOGISTICSPOSTALADDRESS        | ADDRESS                                                                       | nvarchar(500) | ValidateAddressLength |                                     |
| LOGISTICSPOSTALADDRESS        | STREET                                                                        | nvarchar(400) | ValidateAddressLength |                                     |
| LOGISTICSPOSTALADDRESS        | COUNTY                                                                        | nvarchar(60)  | ValidateAddressLength |                                     |
| LOGISTICSADDRESSCITY          | COUNTYID                                                                      | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSCOUNTY        | COUNTYID                                                                      | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSDISTRICT      | COUNTYID_RU                                                                  | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSZIPCODE       | STREETNAME                                                                    | nvarchar(400) |                       |                                     |
| LOGISTICSADDRESSZIPCODE       | COUNTY                                                                        | nvarchar(60)  |                       |                                     |
| RETAILASYNCADDRESS            | STREET                                                                        | nvarchar(400) |                       |                                     |
| RETAILASYNCADDRESS            | COUNTY                                                                        | nvarchar(60)  |                       |                                     |
| RETAILASYNCCUSTOMER           | STREET                                                                        | nvarchar(400) |                       |                                     |
| RETAILASYNCCUSTOMER           | COUNTY                                                                        | nvarchar(60)  |                       |                                     |
| RETAILFISCALDOCUMENT_BR      | FEADDRESSSTREET                                                               | nvarchar(400) |                       |                                     |
| RETAILFISCALDOCUMENT_BR      | THIRDPARTYADDRESSSTREET                                                       | nvarchar(400) |                       |                                     |
| RETAILTAXFILTERS              | COUNTYID                                                                      | nvarchar(60)  |                       |                                     |
| RETAILTRANSACTIONADDRESSTRANS | STREET                                                                        | nvarchar(400) |                       |                                     |
| RETAILTRANSACTIONADDRESSTRANS | COUNTY                                                                        | nvarchar(60)  |                       |                                     |
| RETAILTRANSACTIONSALESTRANS   | INVENTBATCHID                                                                 | nvarchar(50)  |                       |                                     |
| RETAILTRANSACTIONSALESTRANS   | INVENTSERIALID                                                                | nvarchar(50)  |                       |                                     |
| RETAILTRANSACTIONSALESTRANS   | WAREHOUSELOCATION                                                             | nvarchar(60)  |                       |                                     |
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
| TAXCOMPONENTTABLE_IN         | COMPONENT                                                                     | nvarchar(60)  |                       |                                     |
| WMSLOCATION                   | INPUTLOCATION                                                                 | nvarchar(60)  |                       |                                     |
|                               | WMSLOCATIONID                                                                 | nvarchar(60)  |                       |                                     |
| INVENTLOCATION                | RBODEFAULTWMSLOCATIONID                                                       | nvarchar(60)  |                       |                                     |
|                               | WMSLOCATIONIDDEFAULTISSUE                                                     | nvarchar(60)  |                       |                                     |
|                               | WMSLOCATIONIDDEFAULTRECEIPT                                                   | nvarchar(60)  |                       |                                     |
| PRICEDISCTABLE                | CONSTRAINT I_137462222_1904821809: { "action": "replace-line", "value": "CONSTRAINT [I_PRICEDISCTABLE_RECID] PRIMARY KEY CLUSTERED (  [RECID] )  "CONSTRAINT I_PRICEDISCTABLE_RECID": { "action": "remove-line" }     |               |                       |                                     |
| OMOPERATINGUNIT               | OMOPERATINGUNITNUMBER                                                         | nvarchar(30)  |                       |                                     |
| RETAILPARAMETERS              | USEADVANCEDAUTOCHARGE INT NULL DEFAULT(0)                                     |               |                       |                                     |
|                               | GIFTCARDINQUIRYPRINTHISTORY INT NULL DEFAULT(0)                               |               |                       |                                     |
| RETAILINFOCODETABLE           | PRINTINPUTONFISCALRECEIPT \[int\] NULL DEFAULT (0) PRINTTEXTONFISCALRECEIPT [nvarchar] (50) NULL DEFAULT('')                    |               |                       |                                     |
| RETAILINFORMATIONSUBCODETABLE | PRINTTEXTONFISCALRECEIPT [nvarchar](50) NULL DEFAULT('')                    |               |                       |                                     |

