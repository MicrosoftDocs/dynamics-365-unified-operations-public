---
title: Extend Customer CDX package to add custom data
description: This topic explains how to add custom data to the customer Commerce Data Exchange (CDX) package in Microsoft Dynamics 365 Commerce.
author: mugunthanm
ms.date: 04/08/2022
ms.topic: article
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 03-30-2022
ms.dyn365.ops.version: AX 10.0.25
---

# Extend customer CDX package to add custom data

[!include [banner](../includes/banner.md)]

This topic explains how extend the customer Commerce Data Exchange (CDX) package to add custom data to in Microsoft Dynamics 365 Commerce.

When point of sale (POS) or any client application calls the Commerce Customer Search API, the API searches for the customer in the channel database. If the customer is not found in the channel database and if remote search is enabled in Commerce headquarters, then the API makes a real time call to headquarters to fetch the data. If the customer data is found in headquarters, then headquarters generates the customer data CDX package and synchronizes it to the channel database. 

If you want to include custom data like **Loyalty**, **Affiliation**, or **Extension** table data as part of the customer data CDX package and synchronize it to the channel database, then you must extend the **RetailTransactionServiceCustomerExtensions** class in headquarters using X++.
 
To add the custom data part of the package, override the **addAdditionalCustomerDataToPackage** method from **RetailTransactionServiceCustomerExtensions** class, add a custom query to read the data from the required tables, and then write the data part of the **RetailCdxDataPackageSerializationHelper** object.

### Prerequisites to adding the X++ extension

- CDX must be extended to synchronize the custom table and fields, and if you are synchronizing extension tables then a Commerce runtime (CRT) extension is required to read the extension table data. If you are using existing entities like **Loyalty**, **Affiliation**, or **Customer**, then no CRT extension is required since the out-of-the-box CRT code will fetch the data. For more information, see [Enable custom Commerce Data Exchange synchronization via extension](cdx-extensibility.md).
- Maintain data integrity between the **Customer** table and the additional data fetched, including the extension tables.
- All the extension and synchronization tables must have write permissions for the CDX framework to write the data to the table.

To create the custom method to add data part of the Customer CDX data package, follow these steps.

1. Start Microsoft Visual Studio.
1. On the **Dynamics 365** menu, select **Model management \> Create model**.
1. In the **Create model** dialog box, enter the following information.
    - **Model name**: Contoso
    - **Model publisher**: Contoso
    - **Version**: 1.0.0.0
    - **Model display name**: Contoso
1. Select **Next**.
1. In the dialog box, select **Select existing package**, and then select **Application Suite** from the drop-down list.
1. Select **Next**.
1. Select **Finish**.
1. In the **New project** dialog box, enter **RetailTransactionServiceCustomerExtensions** as the project name.
1. Select **OK**.
1. Right-click the project and select **Add \> New item**. In the **Add New Item** dialog box, select **Class** and then enter the name of the class as **RetailTransactionServiceCustomerExtensions_Sample_Extension**.
1. Add the **ExtensionOf** attribute to your class and then specify the **RetailTransactionServiceCustomerExtensions** class as the attribute value, as shown in the following example.

    ```X++
    [ExtensionOf(classStr(RetailTransactionServiceCustomerExtensions))]
    public final class RetailTransactionServiceCustomerExtensions_Sample_Extension
    {
    }  
    ```
1. Override the **addAdditionalCustomerDataToPackage** method and fetch data from the required tables.

## Example

In the following example, the data is fetched from the tables below and are included in the package.
- **RetailLoyaltyCard**
- **RetailLoyaltyCardTier**
- **CustTable**
- **ContosoRetailCustPreferredContactHours**

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

## Full sample code

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
