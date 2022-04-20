---
title: Extend the customer CDX package to add custom data
description: This topic explains how to add custom data to the customer Commerce Data Exchange (CDX) package in Microsoft Dynamics 365 Commerce.
author: mugunthanm
ms.date: 04/21/2022
ms.topic: article
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 03-30-2022
ms.dyn365.ops.version: AX 10.0.25
---

# Extend the customer CDX package to add custom data

[!include [banner](../includes/banner.md)]

This topic explains how to extend the customer Commerce Data Exchange (CDX) package to add custom data in Microsoft Dynamics 365 Commerce.

When point of sale (POS) or any client application calls the Commerce Customer Search application programming interface (API), the API searches for the customer in the channel database. If the customer isn't found in the channel database, and if remote search is enabled in Commerce headquarters, the API makes a real-time call to Commerce headquarters to fetch the data. If the customer data is found in Commerce headquarters, Commerce headquarters generates the customer data CDX package and synchronizes it to the channel database.

If you want to include custom data (for example, **Loyalty**, **Affiliation**, or **Extension** table data) as part of the customer data CDX package and synchronize it to the channel database, you must use X++ to extend the **RetailTransactionServiceCustomerExtensions** class in Commerce headquarters.

To add the custom data part of the package, override the **addAdditionalCustomerDataToPackage** method from the **RetailTransactionServiceCustomerExtensions** class, add a custom query to read the data from the required tables, and then write the data part of the **RetailCdxDataPackageSerializationHelper** object.

## Prerequisites for adding the X++ extension

- CDX must be extended to synchronize the custom table and fields. If you're synchronizing extension tables, a Commerce runtime (CRT) extension is required to read the extension table data. If you're using existing entities (for example, **Loyalty**, **Affiliation**, or **Customer**), no CRT extension is required, because the out-of-box CRT code will fetch the data. For more information, see [Enable custom Commerce Data Exchange synchronization via extension](cdx-extensibility.md).
- Maintain data integrity between the **Customer** table and the additional data that is fetched. This additional data includes the extension tables.
- All the extension and synchronization tables must have write permissions for the CDX framework to write the data to the table.

To create the custom method to add the data part of the Customer CDX data package, follow these steps.

1. Open Microsoft Visual Studio.
1. On the **Dynamics 365** menu, select **Model management \> Create model**.
1. In the **Create model** dialog box, enter the following information:

    - **Model name:** Contoso
    - **Model publisher:** Contoso
    - **Version:** 1.0.0.0
    - **Model display name:** Contoso

1. Select **Next**.
1. Select **Select existing package**, and then select **Application Suite** in the drop-down list.
1. Select **Next**.
1. Select **Finish**.
1. In the **New project** dialog box, enter **RetailTransactionServiceCustomerExtensions** as the project name.
1. Select **OK**.
1. Select and hold (or right-click) the project, and then select **Add \> New item**.
1. In the **Add New Item** dialog box, select **Class**, and then enter **RetailTransactionServiceCustomerExtensions_Sample_Extension** as the class name.
1. Add the **ExtensionOf** attribute to your class, and then specify the **RetailTransactionServiceCustomerExtensions** class as the attribute value, as shown in the following example.

    ```X++
    [ExtensionOf(classStr(RetailTransactionServiceCustomerExtensions))]
    public final class RetailTransactionServiceCustomerExtensions_Sample_Extension
    {
    }
    ```

1. Override the **addAdditionalCustomerDataToPackage** method, and fetch data from the required tables.

## Example

In this example, the data is fetched from the following tables and included in the package:

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
