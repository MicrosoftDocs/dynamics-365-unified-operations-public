---
title: Extend Customer CDX package to add custom data
description: This topic explains how to add custom data to the Customer Commerce Data Exchange (CDX) package.
author: mugunthanm
ms.date: 03/30/2022
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 03-30-2022
ms.dyn365.ops.version: AX 10.0.25
---

# Extend Customer CDX package to add custom data

[!include [banner](../includes/banner.md)]


## Extend Customer CDX package to add custom data

This topic explains how to extend RetailTransactionServiceCustomerExtensions class to add custom data to the Customer Commerce Data Exchange (CDX) package.
Scenario:
When POS or any Client application calls the Commerce Customer Search API, the API searches for the customer in the channel database, if the customer is not found in the channel database and if remote search is enabled in HQ, then the API makes real time call to the Commerce Headquarters to fetch the data. If the Customer data is found in HQ, then HQ generates the Customer data CDX package and sync it to the channel database. 
If you want to include custom data like Loyalty, Affiliation or Extension table data part of the Customer data CDX package and sync it to the channel database, then extend RetailTransactionServiceCustomerExtensions class in Commerce HQ (X++) to add your custom data part of the package.
To add the custom data part of the package, override the addAdditionalCustomerDataToPackage method from RetailTransactionServiceCustomerExtensions class, and add custom query to read the data from the required tables and then write the data part of the RetailCdxDataPackageSerializationHelper object.
### Before adding the x++ extension:
- [CDX must be extended to sync the custom table and fields](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/cdx-extensibility) and if you are syncing extension tables then CRT extension is required to read the extension table data, if its existing entity like Loyalty, Affiliations for Customers then the out of the box CRT code will fetch the data, no CRT extension is required. 
- Maintain data integrity between the Customer table and the additional data fetched including the extension tables.
- All the extension and sync table must have the write permission for the CDX framework to write the data to the table.

**Steps to Create the Custom method to add data part of the Customer CDX data package:**
1.	Start Microsoft Visual Studio.
2.	On the Dynamics 365 menu, click Model management > Create model.
3.	In the Create model dialog box, enter the following details.
    - Model name - Contoso
    - Model publisher - Contoso
    - Version - 1.0.0.0
    - Model display name - Contoso
4.	Click Next.
5.	In the dialog box, select Select existing package, and then select Application Suite in the list.
6.	Click Next.
7.	Click Finish.
8.	In the New project dialog box, enter RetailTransactionServiceCustomerExtensions as the project name.
9.	Click OK.
10.	Right-click the project and select Add > New item. In the Add New Item window, select Class and enter the name of the class as RetailTransactionServiceCustomerExtensions_Sample_Extension
11.	Add the ExtensionOf attribute to your class and specify the RetailTransactionServiceCustomerExtensions class as the attribute value.
Ex:  
```X++
[ExtensionOf(classStr(RetailTransactionServiceCustomerExtensions))]
public final class RetailTransactionServiceCustomerExtensions_Sample_Extension
{
}  
```
12.	Override the addAdditionalCustomerDataToPackage method and fetch data from the required tables.
Ex: In this example, the data is fetched from the tables below and included in the package:
- RetailLoyaltyCard
- RetailLoyaltyCardTier
- CustTable
- ContosoRetailCustPreferredContactHours


```X++
		 /// <summary>
    /// Extension method to add additional data to customer data package.
    /// </summary>
    /// <param name = "serializer">The CDX data package serializer.</param>
    /// <param name = "customerRecord">The <see cref="CustTable" /> record for which related information needs to be added.</param>
    public static void addAdditionalCustomerDataToPackage(RetailCdxDataPackageSerializationHelper serializer, CustTable customerRecord)
    {
        RetailLoyaltyCard loyaltyCard;
        RetailLoyaltyCardTier loyaltyCardTier;
        CustTable extensionCustTable;
        ContosoRetailCustPreferredContactHours contactHoursTable;

        while select loyaltyCard
            where loyaltyCard.Party == customerRecord.Party
        {
            serializer.writeRecord(loyaltyCard);
            loyaltyCardTableAddedToPackage = true;

            while select loyaltyCardTier
                where loyaltyCardTier.LoyaltyCard == loyaltyCard.RecId
            {
                serializer.writeRecord(loyaltyCardTier);
                loyaltyCardTierTableAddedToPackage = true;
            }
        }

        while select contactHoursTable
        {
            serializer.writeRecord(contactHoursTable);
            extensionTableAddedToPackage = true;
        }
    }


```

**Full sample code:**

```X++
	/// <summary>
/// Extension sample for RetailTransactionServiceCustomerExtensions::addAdditionalCustomerDataToPackage() method.
/// </summary>
[ExtensionOf(classStr(RetailTransactionServiceCustomerExtensions))]
public final class RetailTransactionServiceCustomerExtensions_Sample_Extension
{
    // These fields are added for unit testing only and are not needed for extension functionality.
    public static boolean loyaltyCardTableAddedToPackage;
    public static boolean loyaltyCardTierTableAddedToPackage;
    public static boolean extensionTableAddedToPackage;


    /// <summary>
    /// Extension method to add additional data to customer data package.
    /// </summary>
    /// <param name = "serializer">The CDX data package serializer.</param>
    /// <param name = "customerRecord">The <see cref="CustTable" /> record for which related information needs to be added.</param>
    public static void addAdditionalCustomerDataToPackage(RetailCdxDataPackageSerializationHelper serializer, CustTable customerRecord)
    {
        RetailLoyaltyCard loyaltyCard;
        RetailLoyaltyCardTier loyaltyCardTier;
        CustTable extensionCustTable;
        ContosoRetailCustPreferredContactHours contactHoursTable;

        while select loyaltyCard
            where loyaltyCard.Party == customerRecord.Party
        {
            serializer.writeRecord(loyaltyCard);
            loyaltyCardTableAddedToPackage = true;

            while select loyaltyCardTier
                where loyaltyCardTier.LoyaltyCard == loyaltyCard.RecId
            {
                serializer.writeRecord(loyaltyCardTier);
                loyaltyCardTierTableAddedToPackage = true;
            }
        }

        while select contactHoursTable
        {
            serializer.writeRecord(contactHoursTable);
            extensionTableAddedToPackage = true;
        }
    }
}
```
