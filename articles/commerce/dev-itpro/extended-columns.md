---
title: Pre-extended columns in the channel database
description: This article explains how the pre-extended columns in the channel database are consumed for extensions.
author: josaw1
ms.date: 01/12/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2020-02-02
ms.dyn365.ops.version: 10.0.10
ms.custom: 
ms.assetid: 
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

| Table                         | Column                             | Length        | Extension in CRT      | Extension in POS  |
|-------------------------------|------------------------------------|---------------|-----------------------|-------------------|
| INVENTSERIAL                  | INVENTSERIALID | nvarchar(50)  |                       | GetSerialNumberClientRequestHandler |
| LOGISTICSPOSTALADDRESS        | ADDRESS        | nvarchar(500) | ValidateAddressLength |                                     |
| LOGISTICSPOSTALADDRESS        | STREET         | nvarchar(400) | ValidateAddressLength |                                     |
| LOGISTICSPOSTALADDRESS        | COUNTY         | nvarchar(60)  | ValidateAddressLength |                                     |
| LOGISTICSPOSTALADDRESS        | STATE          | nvarchar(60)  | ValidateAddressLength |                                     |
| LOGISTICSPOSTALADDRESS        | ZIPCODE        | nvarchar(60)  | ValidateAddressLength |                                     |
| LOGISTICSADDRESSCITY          | COUNTYID       | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSCITY          | STATEID        | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSCITY          | NAME           | nvarchar(120)  |                       |                                     |
| LOGISTICSADDRESSCOUNTY        | COUNTYID       | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSCOUNTY        | NAME           | nvarchar(120)  |                       |                                     |
| LOGISTICSADDRESSDISTRICT      | COUNTYID\_RU   | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSDISTRICT      | STATEID\_RU    | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSDISTRICT      | NAME           | nvarchar(120)  |                       |                                     |
| LOGISTICSADDRESSZIPCODE       | STREETNAME     | nvarchar(400) |                       |                                     |
| LOGISTICSADDRESSZIPCODE       | COUNTY         | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSZIPCODE       | STATE          | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSZIPCODE       | ZIPCODE        | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSSTATE        | STATEID         | nvarchar(60)  |                       |                                     |
| LOGISTICSADDRESSSTATE        | NAME            | nvarchar(120)  |                       |                                     |
| LOGISTICSELECTRONICADDRESS   | COUNTRYREGIONCODE | nvarchar(10)  |   ValidateElectronicAddressServiceRequest |                                     |
| RETAILASYNCADDRESS            | STREET         | nvarchar(400) |                       |                                     |
| RETAILASYNCADDRESS            | COUNTY         | nvarchar(60)  |                       |                                     |
| RETAILASYNCADDRESS            | CUSTNAME       | nvarchar(300)  |                       |                                     |
| RETAILASYNCADDRESS            | STATE          | nvarchar(60)  |                       |                                     |
| RETAILASYNCADDRESS            | ZIP            | nvarchar(60)  |                       |                                     |
| RETAILASYNCCUSTOMER           | STREET         | nvarchar(400) |                       |                                     |
| RETAILASYNCCUSTOMER           | COUNTY         | nvarchar(60)  |                       |                                     |
| RETAILASYNCCUSTOMER           | CUSTNAME       | nvarchar(300)  |                       |                                     |
| RETAILASYNCCUSTOMER           | FIRSTNAME      | nvarchar(100)  |                       |                                     |
| RETAILASYNCCUSTOMER           | LASTNAME       | nvarchar(100)  |                       |                                     |
| RETAILASYNCCUSTOMER           | MIDDLENAME     | nvarchar(100)  |                       |                                     |
| RETAILASYNCCUSTOMER           | CUSTGROUP      | nvarchar(25)  |                       |                                     |
| CUSTTABLE           | CUSTGROUP                | nvarchar(25) |                       |                                     |
| CUSTTABLE           | INVENTLOCATION           | nvarchar(25) |                       |                                     |
| CUSTOMERTABLETYPE_V2           | FIRSTNAME     | nvarchar(100)  | ValidateCustomerNameLengthServiceRequest |                                     |
| CUSTOMERTABLETYPE_V2          | MIDDLENAME     | nvarchar(100)  | ValidateCustomerNameLengthServiceRequest |                                     |
| CUSTOMERTABLETYPE_V2           | LASTNAME      | nvarchar(100)  |  ValidateCustomerNameLengthServiceRequest |                                     |
| RETAILFISCALDOCUMENT\_BR      | FEADDRESSSTREET | nvarchar(400) |                       |                                     |
| RETAILFISCALDOCUMENT\_BR      | THIRDPARTYADDRESSSTREET | nvarchar(400) |                       |                                     |
| RETAILTAXFILTERS              | COUNTYID       | nvarchar(60)  |                       |                                     |
| RETAILTRANSACTIONADDRESSTRANS | STREET         | nvarchar(400) |                       |                                     |
| RETAILTRANSACTIONADDRESSTRANS | STATE          | nvarchar(60)  |                       |                                     |
| RETAILTRANSACTIONADDRESSTRANS | ZIPCODE        | nvarchar(60) |                       |                                     |
| RETAILTRANSACTIONADDRESSTRANS | COUNTY         | nvarchar(60)  |                       |                                     |
| RETAILTRANSACTIONSALESTRANS   | INVENTBATCHID  | nvarchar(50)  |                       |                                     |
| RETAILTRANSACTIONSALESTRANS   | INVENTSERIALID | nvarchar(50)  |                       |                                     |
| RETAILTRANSACTIONSALESTRANS   | WAREHOUSELOCATION | nvarchar(60)  |                       |                                     |
| RETAILTRANSACTIONSALESTRANS   | ITEMID         | nvarchar(100)  |                       |                                     |
| RETAILTRANSACTIONSALESTRANS   | INVENTLOCATIONID | nvarchar(25)  |                       |                                     |
| RETAILTRANSACTIONSALESTRANS   | UNIT           | nvarchar(20)  |                       |                                     |
| RETAILTRANSACTIONSALESTRANS   | ORIGINALTAXITEMGROUP | nvarchar(100)  |                       |                                     |
| RETAILTRANSACTIONSALESTRANS   | TAXITEMGROUP   | nvarchar(100)  |                       |                                     |
| RETAILDLVMODEADDRESSEXPLODED  | STATE         | nvarchar(60)  |                       |                                     |
| INVENTDIM                     | INVENTBATCHID  | nvarchar(50)  |                       |                                     |
| INVENTDIM                     | INVENTSERIALID | nvarchar(50)  |                       |                                     |
| INVENTDIM                     | CONFIGID       | nvarchar(60)  |                       |                                     |
| INVENTDIM                     | INVENTCOLORID  | nvarchar(60)  |                       |                                     |
| INVENTDIM                     | INVENTSIZEID   | nvarchar(60)  |                       |                                     |
| INVENTDIM                     | INVENTSTYLEID  | nvarchar(60)  |                       |                                     |
| INVENTDIM                     | WMSLOCATIONID  | nvarchar(60)  |                       |                                     |
| INVENTDIM                     | INVENTLOCATIONID | nvarchar(25)  |                       |                                     |
| ECORESCOLOR                   | NAME           | nvarchar(60)  |                       |                                     |
| ECORESSTYLE                   | NAME           | nvarchar(60)  |                       |                                     |
| ECORESCONFIGURATION           | NAME           | nvarchar(60)  |                       |                                     |
| ECORESSIZE                    | NAME           | nvarchar(60)  |                       |                                     |
| RETAILTABLEFIELDID            | TABLENAME      | nvarchar(81)  |                       |                                     |
| RETAILTABLEFIELDID            | FIELDNAME      | nvarchar(81)  |                       |                                     |
| RETAILTRANSACTIONTAXTRANSGTE  | TAXCOMPONENT   | nvarchar(60)  |                       |                                     |
| TAXCOMPONENTTABLE\_IN         | COMPONENT      | nvarchar(60)  |                       |                                     |
| WMSLOCATION                   | INPUTLOCATION  | nvarchar(60)  |                       |                                     |
| WMSLOCATION                   | WMSLOCATIONID    | nvarchar(60)  |                       |                                     |
| WMSLOCATION                   | INVENTLOCATIONID | nvarchar(25)  |                       |                                     |
| INVENTLOCATION                | RBODEFAULTWMSLOCATIONID | nvarchar(60)  |                       |                                     |
| INVENTLOCATION                | WMSLOCATIONIDDEFAULTISSUE | nvarchar(60)  |                       |                                     |
| INVENTLOCATION                | WMSLOCATIONIDDEFAULTRECEIPT | nvarchar(60)  |                       |                                     |
| INVENTLOCATION                | NAME | nvarchar(120)  |                       |                                     |
| INVENTLOCATION                | INVENTLOCATIONID | nvarchar(25)  |                       |                                     |
| PRICEDISCTABLE                | CONSTRAINT I_137462222_1904821809 |  |  |  |
| PRICEDISCTABLE                | CONSTRAINT I_PRICEDISCTABLE_RECID |  |  |  |
| PRICEDISCTABLE                | UNITID | nvarchar(20) |  |  |
| PRICEDISCTABLE                | ITEMRELATION | nvarchar(100) |  |  |
| OMOPERATINGUNIT               | OMOPERATINGUNITNUMBER | nvarchar(30)  |  |  |
| RETAILPARAMETERS              | USEADVANCEDAUTOCHARGE | INT DEFAULT(0) |  |  |
| RETAILPARAMETERS              | GIFTCARDINQUIRYPRINTHISTORY | INT DEFAULT(0) |  |  |
| RETAILINFOCODETABLE           | PRINTINPUTONFISCALRECEIPT | int DEFAULT(0) |  | 
| RETAILINFOCODETABLE           | PRINTTEXTONFISCALRECEIPT | nvarchar(50) |  | 
| RETAILINFOCODETABLE           | PROMPT |  nvarchar(350) |  |   |
| RETAILINFOCODETABLE           | DESCRIPTION |  nvarchar(150) |  |   |
| RETAILINFORMATIONSUBCODETABLE | PRINTTEXTONFISCALRECEIPT | nvarchar(50) |  |  |
| RETAILINFOCODETRANSLATION     | PROMPT | nvarchar(350) |  |  |
| DIRPERSONNAME                 | FIRSTNAME | nvarchar(100)  |                       |                                     |
| DIRPERSONNAME               | LASTNAME | nvarchar(100)  |                       |                                     |
| DIRPERSONNAME               | MIDDLENAME | nvarchar(100)  |                       |                                     |
| DIRPARTYTABLE               | NAME      | nvarchar(300)  |                       |                                     |
| DIRPARTYTABLE               | NAMEALIAS | nvarchar(150)  |                       |                                     |
| INVENTTABLE               | NAMEALIAS   | nvarchar(120)  |                       |                                     |
| INVENTTABLE               | ITEMID      | nvarchar(100)  |                       |                                     |
| INVENTTABLE               | ALTITEMID   | nvarchar(100)  |                       |                                     |
| ECORESPRODUCT               | SEARCHNAME | nvarchar(150)  |                       |                                     |
| ECORESPRODUCT               | DISPLAYPRODUCTNUMBER | nvarchar(190)  |                       |                                     |
| TAXSUBSTITUTIONCODETABLE\_BR               | ITEMID | nvarchar(100)  |                       |                                     |
| INVENTITEMBARCODE               | ITEMID            | nvarchar(100)  |                       |                                     |
| INVENTTABLEMODULE               | ITEMID            | nvarchar(100)  |                       |                                     |
| INVENTTABLEMODULE               | UNITID            | nvarchar(20)  |                       |                                     |
| RETAILINVENTTABLE               | ITEMID            | nvarchar(100)  |                       |                                     |
| RETAILINVENTTABLE               | BASECOMPARISONUNITCODE | nvarchar(20)  |                       |                                     |
| RETAILITEMONHANDQUANTITY               | ITEMID | nvarchar(100)  |                       |                                     |
| TAXBENEFITCODESETUPDATA_BR               | ITEMRELATION | nvarchar(100)  |                       |                                     |
| INVENTITEMGTIN               | ITEMID | nvarchar(100)  |                       |                                     |
| INVENTITEMGTIN               | UNITID | nvarchar(20)  |                       |                                     |
| INVENTITEMGTIN               | GLOBALTRADEITEMNUMBER | nvarchar(16)  |                       |                                     |
| INVENTITEMGROUPITEM               | ITEMID | nvarchar(100)  |                       |                                     |
| INVENTDIMCOMBINATION               | ITEMID | nvarchar(100)  |                       |                                     |
| INVENTDIMCOMBINATION               | RETAILVARIANTID | nvarchar(20)  |                       |                                     |
| TMPASSORTEDPRODUCTS               | ITEMID | nvarchar(100)  |                       |                                     |
| INVENTORYINBOUNDOUTBOUNDSOURCEDOCUMENTLINE               | ITEMID | nvarchar(100)  |                       |                                     |
| INVENTITEMSALESSETUP               | ITEMID | nvarchar(100)  |                       |                                     |
| RETAILINVENTLINKEDITEM               | ITEMID | nvarchar(100)  |                       |                                     |
| RETAILINVENTLINKEDITEM               | LINKEDITEMID | nvarchar(100)  |                       |                                     |
| RETAILINVENTLINKEDITEM               | UNIT | nvarchar(20)  |                       |                                     |
| RETAILSTORETENDERTYPETABLE               | GIFTCARDITEMID | nvarchar(100)  |                       |                                     |
| RETAILSTORETENDERTYPETABLE               | NAME | nvarchar(120)  |                       |                                     |
| WARRANTYINVENTTABLE               | ITEMID | nvarchar(100)  |                       |                                     |
| INVENTORYINBOUNDOUTBOUNDDOCUMENTLINE               | ITEMID | nvarchar(100)  |                       |                                     |
| TAXBURDEN\_BR               | ITEMID | nvarchar(100)  |                       |                                     |
| RETAILFISCALDOCUMENTLINE_BR               | ITEMID | nvarchar(100)  |                       |                                     |
| RETAILFISCALDOCUMENTLINE_BR               | UNIT | nvarchar(20)  |                       |                                     |
| RETAILFISCALDOCUMENTLINE_BR               | GLOBALTRADEITEMNUMBER | nvarchar(16)  |                       |                                     |
| ECORESTRACKINGDIMENSIONGROUPITEM               | ITEMID | nvarchar(100)  |                       |                                     |
| RETAILTRANSACTIONKITSDISASSEMBLYTRANS               | ITEMID | nvarchar(100)  |                       |                                     |
| RETAILDLVMODEPRODUCTEXPLODED               | ITEMID | nvarchar(100)  |                       |                                     |
| ECORESSTORAGEDIMENSIONGROUPITEM               | ITEMID | nvarchar(100)  |                       |                                     |
| CUSTPACKINGSLIPTRANS               | ITEMID | nvarchar(100)  |                       |                                     |
| ECORESPRODUCTTRANSLATION               | NAME | nvarchar(250)  |                       |                                     |
| RETAILFISCALDOCUMENT\_BR                | FEADDRESSSTREET | nvarchar(400)  |                       |                                     |
| RETAILFISCALDOCUMENT\_BR                | THIRDPARTYADDRESSSTREET | nvarchar(400)  |                       |                                     |
| RETAILFISCALDOCUMENTREFERENCE\_BR                | REFRECEIPTNUMBER | nvarchar(40)  |                       |                                     |
| RETAILFISCALDOCUMENT\_BR                | THIRDPARTYADDRESSSTREET | nvarchar(400)  |                       |                                     |
| INVENTMODELGROUPITEM               | ITEMID | nvarchar(100)  |                       |                                     |
| RETAILLABELCHANGEJOURNALTRANS               | ITEMID | nvarchar(100)  |                       |                                     |
| RETAILFISCALDOCUMENTMODEL2LINE\_BR               | ITEMID | nvarchar(100)  |                       |                                     |
| RETAILFISCALDOCUMENTMODEL2LINE\_BR                | UNIT  | nvarchar(20)  |                       |                                     |
| RETAILFISCALRECEIPTLINE\_BR               | ITEMID        | nvarchar(100)  |                       |                                     |
| RETAILFISCALRECEIPTLINE\_BR               | UNIT          | nvarchar(20)  |                       |                                     |
| RETAILINCOMEEXPENSEACCOUNTTABLE               | NAMEALIAS | nvarchar(120)  |                       |                                     |
| RETAILINCOMEEXPENSEACCOUNTTABLE               | NAME      | nvarchar(120)  |                       |                                     |
| ECORESATTRIBUTE               | NAME                      | nvarchar(120)  |                       |                                     |
| ECORESATTRIBUTETYPE               | NAME                  | nvarchar(120)  |                       |                                     |
| ERSOLUTIONVERSIONTABLE               | NAME               | nvarchar(120)  |                       |                                     |
| RETAILTHEMEPALLET               | NAME                    | nvarchar(120)  |                       |                                     |
| KEYVAULTCERTIFICATETABLE               | NAME             | nvarchar(120)  |                       |                                     |
| CUSTHIERARCHY               | NAME                        | nvarchar(120)  |                       |                                     |
| FISCALESTABLISHMENT_BR               | NAME               | nvarchar(120)  |                       |                                     |
| INVENTITEMGROUP               | NAME                      | nvarchar(120)  |                       |                                     |
| LEDGER               | NAME                               | nvarchar(120)  |                       |                                     |
| INVENTSITE               | NAME                           | nvarchar(120)  |                       |                                     |
| TAXINFORMATION_IN               | NAME                    | nvarchar(120)  |                       |                                     |
| TAXRUNTIMEDOCMODELATTR               | NAME               | nvarchar(120)  |                       |                                     |
| DOCUREF               | NAME                              | nvarchar(120)  |                       |                                     |
| ERTEXTFORMATVERSIONTABLE               | NAME             | nvarchar(120)  |                       |                                     |
| FISCALESTABLISHMENTGROUP_BR               | NAME          | nvarchar(120)  |                       |                                     |
| RETAILHARDWAREPROFILE               | NAME                | nvarchar(120)  |                       |                                     |
| ACCOUNTANT_BR               | NAME                        | nvarchar(120)  |                       |                                     |
| RETAILCHANNELPROFILE               | NAME                 | nvarchar(120)  |                       |                                     |
| TAXRUNTIMEDOCCOMPONENTMEASURE               | NAME        | nvarchar(120)  |                       |                                     |
| TAXRUNTIMEMODELATTR               | NAME                  | nvarchar(120)  |                       |                                     |
| TAXRATETYPE               | NAME                          | nvarchar(120)  |                       |                                     |
| ECORESTRACKINGDIMENSIONGROUP               | NAME         | nvarchar(120)  |                       |                                     |
| RETAILUSERDEFINEDCERTIFICATEPROFILE               | NAME  | nvarchar(120)  |                       |                                     |
| TAXRUNTIMECOMPONENT               | NAME                  | nvarchar(120)  |                       |                                     |
| RETAILSHAREDCONFIGURATIONPARAMETERS               | NAME  | nvarchar(120)  |                       |                                     |
| TAXSOLUTIONSCOPE               | NAME                     | nvarchar(120)  |                       |                                     |
| TAXRUNTIMEREFERENCEMODELATTR               | NAME         | nvarchar(120)  |                       |                                     |
| TAXRUNTIMELOOKUPSTRUCTURE               | NAME            | nvarchar(120)  |                       |                                     |
| RETAILTILLLAYOUT               | NAME                     | nvarchar(120)  |                       |                                     |
| ECORESPRODUCTRELATIONTYPE               | NAME            | nvarchar(120)  |                       |                                     |
| SYSTASKRECORDERFRAMEWORK               | NAME             | nvarchar(120)  |                       |                                     |
| CUSTGROUP               | NAME                            | nvarchar(120)  |                       |                                     |
| CUSTGROUP               | CUSTGROUP                       | nvarchar(25)  |                       |                                     |
| SYSTASKRECORDERINDUSTRY               | NAME              | nvarchar(120)  |                       |                                     |
| FISCALDOCUMENTSOURCETEXT\_BR               | NAME         | nvarchar(120)  |                       |                                     |
| RETAILTHEMEACCENT               | NAME                    | nvarchar(120)  |                       |                                     |
| ECORESATTRIBUTEGROUP               | NAME                 | nvarchar(120)  |                       |                                     |
| TAXRUNTIMELOOKUPSTRUCTUREFIELDBINDING  | NAME   | nvarchar(120)  |          |           |  
| TAXRUNTIMEPOSTINGTYPE     		    | NAME   | nvarchar(120)  |           |           |  
| RETAILVISUALPROFILE                    | NAME| nvarchar(120)      |          |           |  
| TAXRUNTIMELOOKUP		  	    | NAME| nvarchar(120)      |          |          | 
| TAXRUNTIMEDOCMODELROWMEASURE		   | NAME| nvarchar(120)      |          |          |  
| TAXRUNTIMEMEASURE		    | NAME| nvarchar(120)      |          |          |  
| PRICEDISCGROUP		    | NAME| nvarchar(120)      |          |          |  
| SYSSERVICECONFIGURATIONSETTING | NAME| nvarchar(120)      |          |          |  
| RETAILKEYBOARDBUTTONCONTROL	 | NAME| nvarchar(120)      |          |          |  
| RETAILDISCOUNTVALIDATIONPERIOD | NAME| nvarchar(120)      |          |          |  
| ERFORMATMAPPINGVERSIONTABLE		    | NAME| nvarchar(120)      |          |          |  
| EXCHANGERATETYPE		    | NAME| nvarchar(120)      |          |          |  
| TAXRUNTIMEDOCCOMPONENT		    | NAME| nvarchar(120)      |          |          |  
| ERFORMATMAPPINGTABLE		    | NAME| nvarchar(120)      |          |          |  
| RETAILBUTTONGRID		    | NAME| nvarchar(120)      |          |          |  
| ERSOLUTIONTABLE		    | NAME| nvarchar(120)      |          |          |  
| RETAILTRANSACTIONATTRIBUTETRANS	| NAME| nvarchar(120)      |          |          |  
| TAXRUNTIMEDOCCONTEXT		    | NAME| nvarchar(120)      |          |          |  
| TAXRUNTIMECOMPONENTMEASURE		    | NAME| nvarchar(120)      |          |          |  
| INVENTMODELGROUP		    | NAME| nvarchar(120)      |          |          |  
| RETAILPERIODICDISCOUNT		    | NAME| nvarchar(120)      |          |          |  
| DIRADDRESSBOOK		    | NAME| nvarchar(120)      |          |          |  
| RETAILFUNCTIONALITYPROFILE		    | NAME| nvarchar(120)      |          |          |  
| RETAILIDENTITYPROVIDER		    | NAME| nvarchar(120)      |          |          |  
| TAXRUNTIMEDOCTAXTYPE		    | NAME| nvarchar(120)      |          |          |  
| TAXRUNTIMEREFERENCEMODELROW		    | NAME| nvarchar(120)      |          |          |  
| RETAILPOSPERMISSIONGROUP		    | NAME| nvarchar(120)      |          |          |  
| TAXRUNTIMEDEFCONTEXT		    | NAME| nvarchar(120)      |          |          |  
| COMMISSIONSALESGROUP		    | NAME| nvarchar(120)      |          |          |  
| LOGISTICSLOCATIONROLE		    | NAME| nvarchar(120)      |          |          |  
| RETAILPOSTHEME		    | NAME| nvarchar(120)      |          |          |  
| TAXRUNTIMELOOKUPSTRUCTUREFIELD	| NAME| nvarchar(120)      |          |          |  
| WHSINVENTSTATUS		    | NAME| nvarchar(120)      |          |          |  
| ERDATAMODELTABLE		    | NAME| nvarchar(120)      |          |          |  
| RETAILTERMINALTABLE		    | NAME| nvarchar(120)      |          |          |  
| RETAILFISCALINTEGRATIONDOCUMENTPROVIDERTABLE | NAME| nvarchar(120)      |      |          |  
| TAXRUNTIMEMODEL		    | NAME| nvarchar(120)      |          |          |  
| TAXRUNTIMEDOCCOMPONENTPOSTINGPROFILEDET	| NAME| nvarchar(120)      |          |          |  
| ERTEXTFORMATTABLE	| NAME| nvarchar(120)      |          |          |  
| RETAILTENDERTYPETABLE	| NAME| nvarchar(120)      |          |          |  
| TAXPERIODHEADER	| NAME| nvarchar(120)      |          |          |  
| RETAILTABLEIDTABLE		    | NAME| nvarchar(120)      |          |          |  
| RETAILPERIODICDISCOUNTLINE		    | NAME| nvarchar(120)      |          |          |  
| RETAILCONNDATABASEPROFILE		    | NAME| nvarchar(120)      |          |          |  
| RETAILSTORETENDERTYPECARDTABLE	| NAME| nvarchar(120)      |          |          |  
| RETAILAFFILIATION		    | NAME| nvarchar(120)      |          |          |  
| RETAILONLINECHANNELFUNCTIONALITYPROFILETABLE| NAME| nvarchar(120)      |        |          |  
| TAXRUNTIMEREFERENCEMODEL		    | NAME| nvarchar(120)      |          |          |  
| RETAILTENDERTYPECARDTABLE		    | NAME| nvarchar(120)      |          |          |  
| ERVENDORTABLE		    | NAME| nvarchar(120)      |          |          |  
| ERMODELMAPPINGTABLE		    | NAME| nvarchar(120)      |          |          |  
| RETAILDRAWERPOOLDEVICE		    | NAME| nvarchar(120)      |          |          |  
| RETAILDRAWERPOOL		    | NAME| nvarchar(120)      |          |          |  
| RETAILCONFIGURATIONPARAMETERS	| NAME| nvarchar(120)      |          |          |  
| TAXENGINESQLDICTIONARY		    | NAME| nvarchar(120)      |          |          |  
| LOGISTICSADDRESSFORMATHEADING	| NAME| nvarchar(120)      |          |          |  
| TAXRUNTIMEDOCMODELROW		    | NAME| nvarchar(120)      |          |          |  
| RETAILCDXDATAGROUP		    | NAME| nvarchar(120)      |          |          |  
| ECORESPRODUCTMASTERDIMVALUETRANSLATION	| NAME| nvarchar(120)      |          |          |  
| TAXRUNTIMELOOKUPSTRUCTUREBINDING	| NAME| nvarchar(120)      |          |          |  
| RETAILTRANSACTIONSERVICEPROFILE	| NAME| nvarchar(120)      |          |          |  
| RETAILSTORESAFE		    | NAME| nvarchar(120)      |          |          |  
| TAXRUNTIMETAXTYPE		    | NAME| nvarchar(120)      |          |          |  
| RETAILTERMINALCUSTOMFIELD		    | NAME| nvarchar(120)      |          |          |  
| RETAILFISCALINTEGRATIONCONNECTORTABLE	| NAME| nvarchar(120)      |          |          |  
| TAXRUNTIMEMODELROW		    | NAME| nvarchar(120)      |          |          |  
| ERDATAMODELVERSIONTABLE		    | NAME| nvarchar(120)      |          |          |  
| TAXRUNTIMEDOCCOMPONENTPOSTINGPROFILE | NAME| nvarchar(120)      |          |          |  
| TAXRUNTIMEDOCMODEL		    | NAME| nvarchar(120)      |          |          |  
| RETAILPOSITIONPOSPERMISSION		    | NAME| nvarchar(120)      |          |          |  
| RETAILTENDERDISCOUNT		    | NAME| nvarchar(120)      |          |          |  
| RETAILDLVMODEADDRESSEXPLODED | STATE | nvarchar(60)      |          |          |  
| INVENTLOCATIONDEFAULTLOCATION | INVENTLOCATIONID | nvarchar(25)     |   |          |  
| RETAILRETURNPOLICYLINE	| INVENTLOCATIONID | nvarchar(25)      |          |          |  
| RETAILRETURNINFOCODEPOLICYLINE	    | INVENTLOCATIONID | nvarchar(25)      |     |       |  
| RETAILRETURNREASONCODEPOLICYLINE |	INVENTLOCATIONID | nvarchar(25)      |          |        |  
| RETAILPRODUCTWAREHOUSEINVENTORY	| INVENTLOCATIONID | nvarchar(25)      |        |       |  
| RETAILPUBRETAILSTORETABLE	| INVENTLOCATIONIDFORCUSTOMERORDER | nvarchar(25)   |    |      |  
| RETAILSTORETABLE | INVENTLOCATIONIDFORCUSTOMERORDER | nvarchar(25)      |      |          |  
| RETAILSTORELOCATORGROUPMEMBER | INVENTLOCATIONID | nvarchar(25)      |          |          |  
| RETAILTRANSACTIONORDERINVOICETRANS	   | INVOICEID | nvarchar(40)      |          |          |  
| RETAILTRANSACTIONTABLE	   | INVENTLOCATIONID | nvarchar(25)      |          |          |  
| RETAILTRANSACTIONTABLE	   | CUSTOMERNAME | nvarchar(300)      |          |          |  
| RETAILCHANNELTABLE		   | INVENTLOCATION | nvarchar(25)      |          |          |  
| RETAILPUBRETAILCHANNELTABLE	 | INVENTLOCATION | nvarchar(25)      |          |          |  
| UNITOFMEASURE		    | SYMBOL | nvarchar(20)      |          |          |  
| RETAILPRODUCTLISTLINEUPDATE	    | UNITOFMEASURE | nvarchar(20)      |          |          |  
| RETAILUNIT		    | UNITID | nvarchar(20)      |          |          |  
| LOGISTICSELECTRONICADDRESS	  | COUNTRYREGIONCODE | nvarchar(10)      |          |          |  
| REQITEMTABLE		    | ITEMID | nvarchar(100)      |          |          |  
| GUPITEMBASEPRICE		    | ITEMID | nvarchar(100)      |          |          |  
| AGREEMENTLINE		    | ITEMID | nvarchar(100)      |          |          |  
| MARKUPAUTOTABLE		    | ITEMRELATION | nvarchar(100)      |          |          |  
| MARKUPAUTOLINE		    | TAXITEMGROUP | nvarchar(100)      |          |          |
| MARKUPTABLE		    | TAXITEMGROUP | nvarchar(100)      |          |          |



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
