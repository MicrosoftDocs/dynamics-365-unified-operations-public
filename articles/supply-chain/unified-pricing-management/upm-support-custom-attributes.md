---
title: Add custom pricing attributes for Dynamics 365 Commerce Point of Sale
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

# Add custom pricing attributes for Dynamics 365 Commerce Point of Sale

[!INCLUDE [banner](../includes/banner.md)]

Unified pricing management lets you configure pricing rules that can also consider values of custom pricing attributes for products, customers, orders, and order lines.

To use a custom pricing attribute in Dynamics 365 Commerce Point of Sale (POS), you must make the attribute available in Microsoft finance and operations apps and Commerce Scale Unit (CSU). You must also implement a custom request handler that uses `GetCustomizedPricingPropertiesRequest` and `GetCustomizedPricingPropertiesResponse`.

Custom attributes are marked in the `GUPPRICINGATTRIBUTELINK` table using a specific identifier, which indicates that they require special logic in CSU to be supported in POS. To mark a pricing attribute as custom, the `GUPPRICINGATTRIBUTELINK.TypeName` column must be set to `Customization`.

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

## Create the pricing attribute in finance and operations apps

To implement custom pricing attributes for products, customers, orders, and order lines, follow these steps:

Create a class for each custom pricing attribute. The class must extend the appropriate class that derives from `GUPAbstractPricingAttribute` and must implement `GUPIPricingAttribute`.

Implement methods such as `getValueOfAttribute()`, `getName()`, and `getDataType()`. Apply the following discovery attributes to the class:

- `GUPPricingMetadataDiscovery` identifies the class as pricing attribute metadata.
- `GUPPricingAttributeSourceDiscovery` identifies the pricing attribute source and source level.
- `GUPPricingAttributeFieldsDiscovery` identifies the related table and field.

#### Example: Create a header-level customer attribute

The following example creates a header-level customer pricing attribute for the existing `CustTable.StatisticsGroup` field.

```X++
/// <summary>
/// Pricing attribute for the StatisticsGroup field on CustTable.
/// </summary>
[GUPPricingMetadataDiscovery]
[GUPPricingAttributeSourceDiscovery(GUPPricingAttributeSource::Customer, GUPPricingAttributeSourceLevel::Header)]
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
        return typeName;
    }
}
```

#### Example: Create a line-level sales attribute

The following example creates a line-level pricing attribute for the existing `SalesLine.LineNum` field.

```X++
/// <summary>
/// Pricing attribute for the LineNum field on SalesLine.
/// </summary>
[GUPPricingMetadataDiscovery]
[GUPPricingAttributeSourceDiscovery(GUPPricingAttributeSource::SalesLine, GUPPricingAttributeSourceLevel::Line)]
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
        return typeName;
    }
}
```

## Add an attribute that doesn't exist in finance and operations apps

Skip this section if the source field already exists on a finance and operations table.

To create a completely new pricing attribute, complete the following steps:

1. Create an extended data type for the attribute, if an appropriate extended data type doesn't already exist.
     An extended data type defines the type and maximum length of a field. The following sample creates a text field that can contain up to 50 characters.

   ```XML
   <?xml version="1.0" encoding="utf-8"?>
   <AxEdt xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns=""
       i:type="AxEdtString">
       <Name>PricingGroup_EMP</Name>
       <Label>PricingGroup_EMP</Label>
       <ArrayElements />
       <Relations />
       <TableReferences />
       <StringSize>50</StringSize>
   </AxEdt>
   ```
1. Create an extension for the source table.
1. Add the new field to the table extension. The following sample adds four customer pricing fields.
     ```XML
   <?xml version="1.0" encoding="utf-8"?>
   <AxTableExtension xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
       <Name>CustTable.GUPExtend</Name>
       <FieldGroupExtensions />
       <FieldGroups>
           <AxTableFieldGroup>
               <Name>PricelistGroup_Custom</Name>
               <Label>PricelistGroup_Custom</Label>
               <Fields>
                   <AxTableFieldGroupField>
                       <DataField>PricelistGroup_Custom</DataField>
                   </AxTableFieldGroupField>
               </Fields>
           </AxTableFieldGroup>
           <AxTableFieldGroup>
               <Name>MemberGroup_Custom</Name>
               <Label>MemberGroup_Custom</Label>
               <Fields>
                   <AxTableFieldGroupField>
                       <DataField>MemberGroup_Custom</DataField>
                   </AxTableFieldGroupField>
               </Fields>
           </AxTableFieldGroup>
           <AxTableFieldGroup>
               <Name>PricingGroup_Custom</Name>
               <Label>PricingGroup_Custom</Label>
               <Fields>
                   <AxTableFieldGroupField>
                       <DataField>PricingGroup_Custom</DataField>
                   </AxTableFieldGroupField>
               </Fields>
           </AxTableFieldGroup>
           <AxTableFieldGroup>
               <Name>PromoGroup_Custom</Name>
               <Label>PromoGroup_Custom</Label>
               <Fields>
                   <AxTableFieldGroupField>
                       <DataField>PromoGroup_Custom</DataField>
                   </AxTableFieldGroupField>
               </Fields>
           </AxTableFieldGroup>
       </FieldGroups>
       <FieldModifications />
       <Fields>
           <AxTableField xmlns="" i:type="AxTableFieldString">
               <Name>PricelistGroup_Custom</Name>
               <ExtendedDataType>PricelistGroup_Custom</ExtendedDataType>
               <IgnoreEDTRelation>Yes</IgnoreEDTRelation>
           </AxTableField>
           <AxTableField xmlns="" i:type="AxTableFieldString">
               <Name>MemberGroup_Custom</Name>
               <ExtendedDataType>MemberGroup_Custom</ExtendedDataType>
               <IgnoreEDTRelation>Yes</IgnoreEDTRelation>
           </AxTableField>
           <AxTableField xmlns="" i:type="AxTableFieldString">
               <Name>PricingGroup_Custom</Name>
               <ExtendedDataType>PricingGroup_Custom</ExtendedDataType>
               <IgnoreEDTRelation>Yes</IgnoreEDTRelation>
           </AxTableField>
           <AxTableField xmlns="" i:type="AxTableFieldString">
               <Name>PromoGroup_Custom</Name>
               <ExtendedDataType>PromoGroup_Custom</ExtendedDataType>
               <IgnoreEDTRelation>Yes</IgnoreEDTRelation>
           </AxTableField>
       </Fields>
       <FullTextIndexes />
       <Indexes />
       <Mappings />
       <PropertyModifications />
       <RelationExtensions />
       <RelationModifications />
       <Relations />
   </AxTableExtension>
   ```

1. Create the pricing attribute class as described in [Create the pricing attribute in finance and operations apps](#create-the-pricing-attribute-in-finance-and-operations-apps).







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
1. Open your Microsoft finance and operations app and go to **Pricing management** > **Setup** > **Price attribute groups** > **Price attribute groups**. Select the price attribute group that you want to customize and then use the **Attributes** FastTab to add your custom pricing attributes to it. Update each group as needed.
1. Go to **Retail and Commerce** > **Retail and Commerce IT** > **Distribution Schedule** and run the *1210 Pricing management* job to sync changes to the Channel database.
1. For *existing* custom pricing attributes, manually set the `TypeName` column of the `GUPPRICINGATTRIBUTELINK` table to `Customization` in SQL Server Management Studio (SSMS). Here's an example of how to set the `Customization` identifier:

    ```SQL
    update dbo.GUPPRICINGATTRIBUTELINK
    set TYPENAME = 'Customization'
    where ATTRIBUTENAME = 'Custom attribute name'
    ```

    The following image shows an example of how entries marked as custom are shown in the `GUPPRICINGATTRIBUTELINK` table.

    :::image type="content" source="media/ssms-customization.png" alt-text="SSMS customization." lightbox="media/ssms-customization.png":::

1. For `Customer` or `Product`, create a trade agreement journal that tests the new custom pricing attribute. For `SalesTable` or `SalesLine`, create an auto charge that tests the new custom pricing attribute. In both cases, make sure to set a specific value.
1. Go to **Retail and Commerce** > **Retail and Commerce IT** > **Distribution Schedule**  and run the *9999 All jobs* job to sync changes to the Channel database.
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
