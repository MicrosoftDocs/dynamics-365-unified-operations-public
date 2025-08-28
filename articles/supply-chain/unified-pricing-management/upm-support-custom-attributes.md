---
title: Add custom pricing attributes for Dynamics 365 Commerce Point of Sale (preview)
description: Learn how to support custom pricing attributes in Dynamics 365 Commerce Point of Sale (POS) by implementing a custom request handler
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/24/2025
ms.custom:
- bap-template
---

# Add custom pricing attributes for Dynamics 365 Commerce Point of Sale (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

<!-- KFM: Preview until 10.0.46 GA -->

Unified pricing management lets you configure pricing rules that can also consider values of custom pricing attributes for products, customers, orders, and order lines. It provides the following two components that you can use to implement your own custom request handler and develop your logic: `GetCustomizedPricingPropertiesRequest` and `GetCustomizedPricingPropertiesResponse`.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Custom attributes are marked in the `GUPPRICINGATTRIBUTELINK` table using a specific identifier, which indicates that they require special logic in Commerce Scale Unit (CSU) to be supported in Dynamics 365 Commerce Point of Sale (POS). To mark a pricing attribute as custom, the `GUPPRICINGATTRIBUTELINK.TypeName` column must be set to `Customization`.

In CSU logic, if a custom pricing attribute is validated as `GUPPRICINGATTRIBUTELINK.TypeName = 'Customization'`, then the system calls the custom request handler.

## Prerequisites

To use the features described in this article, you must be running version 10.0.46 or later of your Microsoft finance and operations apps.

## First steps

Start by setting up your environment to implement custom pricing attributes, as described in the following procedure:

1. Implement a custom request handler to process custom pricing attributes. Learn more in [Example custom request handler code](upm-custom-request-handler-example.md).
1. Register the output library in the `CommerceRuntime.Ext.config` file. Here's an example of a custom request handler registration (if the output library were `Contoso.Commerce.Runtime.Services`).

   ```XML
   <add source="assembly" value="Contoso.Commerce.Runtime.Services" />
   ```

1. Build the solution and deploy it to your CSU.

## Add custom pricing attributes

To implement custom pricing attributes for products, customers, orders, and order lines, follow these steps:

1. Create a class to represent each new custom pricing attribute. The class should extend `GUPAbstractPricingAttribute` and implement `GUPIPricingAttribute`. Some methods should also be overwritten, such as `getValueOfAttribute()`, `getName()`, and `getDataType()`. Describe this class with three system attributes:

    - [`GUPPricingMetadataDiscovery`] – Describe all pricing attributes.
    - [`GUPPricingAttributeSourceDiscovery(, )`] – Identify the attribute source this attribute applies to.
    - [`GUPPricingAttributeFieldsDiscovery(fieldStr(, ))`] – Identify the table and field this attribute is related to.

   You must add a new class for each custom pricing attribute you want to add.

    - Here's an example of code that creates a header-level custom pricing attribute (for `Customer` `GUPPricingAttributeSource`):

        ```X++
        /// <summary>
        /// PricingAttribute of table <c>CustTable</c> field StatisticsGroup.
        /// </summary>
        [GUPPricingMetadataDiscovery][GUPPricingAttributeSourceDiscovery(GUPPricingAttributeSource::Customer, GUPPricingAttributeSourceLevel::Header)]
        [GUPPricingAttributeFieldsDiscovery(fieldStr(CustTable, StatisticsGroup))]
        internal class GUPPricingAttributeCustTableStatisticsGroup extends GUPPricingAttributeCustTable implements GUPIPricingAttribute
        {
            private Name typeName = 'Customization';
            
            public anytype getValueOfAttribute(Common _pricingObject)
            {
                return this.getTableRecord(_pricingObject).StatisticsGroup;
            }
        
            public str getName()
            {
                return this.getNameFromField();
            }
        
            public AttributeDataType getDataType()
            {
                return AttributeDataType::Text;
            }
        
            public Name getAttributeType()
            {
                return this.typeName;
            }
        
        }
        ```

    - Here's an example of code that creates a line-level custom pricing attribute (for `SalesLine` `GUPPricingAttributeSource`):

        ```X++
        /// <summary>
        /// PricingAttribute of table <c>SalesLine</c> field LineNum.
        /// </summary>
        [GUPPricingMetadataDiscovery][GUPPricingAttributeSourceDiscovery(GUPPricingAttributeSource::SalesLine, GUPPricingAttributeSourceLevel::Line)]
        [GUPPricingAttributeFieldsDiscovery(fieldStr(SalesLine, LineNum))]
        internal final class GUPPricingAttributeSalesLineLineNum extends GUPPricingAttributeSalesLine implements GUPIPricingAttribute
        {
            private Name typeName = 'Customization';
        
            public anytype getValueOfAttribute(Common _pricingObject)
            {
                return this.getTableRecord(_pricingObject).LineNum;
            }
        
            public str getName()
            {
                return this.getNameFromField();
            }
        
            public AttributeDataType getDataType()
            {
                return AttributeDataType::Integer;
            }
        
            public FieldId getField()
            {
                return fieldNum(SalesLine, LineNum);
            }
        
            public Name getAttributeType()
            {
                return this.typeName;
            }
        
        }
        ```

1. For *new* custom pricing attributes, you must programmatically set the `TypeName` column of the `GUPPRICINGATTRIBUTELINK` table to `Customization`. Create an extension to `GUPPricingAttributeRepository` and add a statement to the `toPriceAttributeLink()` method that programmatically sets the `TypeName` column for each new custom pricing attribute. Here's an example of how to do this:

    ```X++
    [ExtensionOf(classStr(GUPPricingAttributeRepository))]
    public static final class GUPPricingAttributeRepository_Extension
    {
        public static GUPPricingAttributeLink toPriceAttributeLink(GUPIPricingAttribute _pricingAttr)
        {
            GUPPricingAttributeLink link = next toPriceAttributeLink(_pricingAttr);
    
            if (link.AttributeName == "StatisticsGroup")
            {
                link.TypeName = (_pricingAttr as GUPPricingAttributeCustTableStatisticsGroup).getAttributeType();
            }
    
            return link;
        }
    
    }
    ```

1. Build the relevant models, Global Unified Pricing (GUP) or extension, and restart Internet Information Services (IIS). Then, clear the cache for your Microsoft finance and operations apps.
1. Open your Microsoft finance and operations app and go to **Pricing management** \> **Setup** \> **Price attribute groups** \> **Price attribute groups**. Select the price attribute group that you want to customize and then use the **Attributes** FastTab to add your custom pricing attributes to it. Update each group as needed.
1. Go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution Schedule** and run the *1210 Pricing management* job to sync changes to the Channel database.
1. For *existing* custom pricing attributes, manually set the `TypeName` column of the `GUPPRICINGATTRIBUTELINK` table to `Customization` in SQL Server Management Studio (SSMS). Here's an example of how to set the `Customization` identifier:

    ```SQL
    update dbo.GUPPRICINGATTRIBUTELINK
    set TYPENAME = 'Customization'
    where ATTRIBUTENAME = 'Custom attribute name'
    ```

    The following image shows an example of how entries marked as custom are shown in the `GUPPRICINGATTRIBUTELINK` table.

    :::image type="content" source="media/ssms-customization.png" alt-text="SSMS customization." lightbox="media/ssms-customization.png":::

1. For `Customer` or `Product`, create a trade agreement journal that tests the new custom pricing attribute. For `SalesTable` or `SalesLine`, create an auto charge that tests the new custom pricing attribute. In both cases, make sure to set a specific value.
1. Go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution Schedule**  and run the *9999 All jobs* job to sync changes to the Channel database.
1. In POS, you should see the value configured in the trade agreement journal or that an auto charge was correctly applied.

## Troubleshooting

### You receive a POS notification that a custom request handler isn't implemented

While creating a transaction in POS that is associated with one or more custom pricing attributes, you might receive an error message similar to the following message:

> The request GetCustomizedPricingPropertiesRequest is not implemented in customized code. Please contact your system administrator.

To address this issue, follow these steps:

1. Verify that a custom request handler is implemented and included in the build.
1. Ensure that the custom request handler is correctly registered in the `CommerceRuntime.Ext.config` file. Keep in mind that this registration can be overwritten during the build process, so it's important for you to confirm the registration after the build completes.

### You receive a POS notification that custom pricing attributes are detected among out-of-box attributes

While creating a transaction in POS that is associated with one or more custom pricing attributes, you might receive one of the following error messages:

> A custom product pricing attribute has been detected. Please contact your system administrator to verify the setup of custom attributes.

Or:

> A custom customer pricing attribute has been detected. Please contact your system administrator to verify the setup of custom attributes.

To address this issue, follow these steps:

1. Verify that the CSU flight `UPSupportCustomPricingAttributesFlight` is enabled.
1. Confirm that the new custom pricing attributes are identified as custom. The `GUPPRICINGATTRIBUTELINK.TypeName` column should be set to `Customization` for all custom pricing attributes.

### Further troubleshooting

To find more information about errors or exceptions, or to review CSU and POS logs, contact Microsoft Support and open a support ticket.
