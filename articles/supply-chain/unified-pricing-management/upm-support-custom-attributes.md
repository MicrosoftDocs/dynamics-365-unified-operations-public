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
       <Name>PricingGroup_Custom</Name>
       <Label>PricingGroup_Custom</Label>
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

## Make the attribute available in CSU

Skip this section if the source field already exists in CSU. These steps must be followed if 1) the field is new to both finance and operations apps and CSU, or 2) the field exists in finance and operations apps but not in CSU.

1. In headquarters, open the **Commerce channel schema** page.
1. Select the Commerce channel that you want to update.
1. On the **Channel database extension SQL script** tab, select **Generate SQL script**.
1. Apply the generated script to the Channel database.

   Don't add the field directly to the standard table in the `ax` schema. The generated script creates or updates an extension table in the `ext` schema. For example, an extension for `CustTable` is added to `ext.CustTableExt`.

   For more information, see [Channel database extensions](../../commerce/dev-itpro/channel-db-extensions.md).

1. Add the field to Commerce Data Exchange synchronization.

   Commerce Data Exchange (CDX) copies data from headquarters to CSU.

   The following example copies `CustTable.SalesDistrictId` to `ext.CustTableExt`. Replace `SalesDistrictId` with your field name. Add another `Field` element if you need to copy more than one field.


   ```XML
   <RetailCdxSeedData ChannelDBMajorVersion="7" ChannelDBSchema="ext" Name="AX7">
      <Subjobs>
       <Subjob Id="CustTable" TargetTableName="CustTableExt" TargetTableSchema="ext" OverrideTarget="false">
           <AxFields>
               <Field Name="SalesDistrictId" />
           </AxFields>
       </Subjob>
      </Subjobs>
   </RetailCdxSeedData>
   ```

1. Register the CDX file.

   Add the following event handler so that Commerce uses the custom CDX file when it creates the synchronization setup.

   ```XML
   <?xml version="1.0" encoding="utf-8"?>
   <AxClass xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
       <Name>RetailCDXSeedDataAX7EventHandler_Custom</Name>
       <SourceCode>
           <Declaration><![CDATA[
   /// <summary>
   /// Event handler that registers the custom CDX seed data resource for CDX seed data generation.
   /// </summary>
   internal class RetailCDXSeedDataAX7EventHandler_Custom
   {
   }
   ]]></Declaration>
           <Methods>
               <Method>
                   <Name>RetailCDXSeedDataBase_registerCDXSeedDataExtension</Name>
                   <Source><![CDATA[
       /// <summary>
       /// Registers the extension CDX seed data resource to be used during CDX seed data generation.
       /// </summary>
       /// <param name="originalCDXSeedDataResource">The original CDX seed data resource name.</param>
       /// <param name="resources">The list of resources to extend.</param>
       [SubscribesTo(classStr(RetailCDXSeedDataBase), delegateStr(RetailCDXSeedDataBase, registerCDXSeedDataExtension))]
       public static void RetailCDXSeedDataBase_registerCDXSeedDataExtension(str originalCDXSeedDataResource, List resources)
       {
           if (originalCDXSeedDataResource == resourceStr(RetailCDXSeedDataAX7))
           {
               resources.addEnd(resourceStr(RetailCDXSeedDataAX7_Custom));
           }
       }

   ]]></Source>
               </Method>
           </Methods>
       </SourceCode>
   </AxClass>
   ```

   For more information, see [Enable custom Commerce Data Exchange synchronization via extension](../../commerce/dev-itpro/cdx-extensibility.md).

1. Build and deploy the solution.
1. In headquarters, run **Initialize commerce scheduler**.
1. Open the scheduler subjob mapping for the source table and verify that the new field appears.

## Identify the attribute as a customization

The `TypeName` column of the attribute's `GUPPRICINGATTRIBUTELINK` record must be set to `Customization`.

#### Set TypeName for a new pricing attribute

For a new pricing attribute class, extend `GUPPricingAttributeRepository.toPriceAttributeLink()` and set `TypeName` when the pricing attribute link is created.

```X++
[ExtensionOf(classStr(GUPPricingAttributeRepository))]
public static final class GUPPricingAttributeRepository_Extension
{
    public static GUPPricingAttributeLink toPriceAttributeLink(
        GUPIPricingAttribute _pricingAttr)
    {
        GUPPricingAttributeLink link =
            next toPriceAttributeLink(_pricingAttr);

        if (link.AttributeName == fieldPName(
            CustTable,
            StatisticsGroup))
        {
            link.TypeName =
                (_pricingAttr
                    as GUPPricingAttributeCustTableStatisticsGroup)
                    .getAttributeType();
        }

        return link;
    }
}
```

#### Set TypeName for an existing pricing attribute link

If the `GUPPRICINGATTRIBUTELINK` record already exists, update its `TypeName` value to `Customization`. The following SQL statement is an example.

```SQL
update dbo.GUPPRICINGATTRIBUTELINK
set TYPENAME = 'Customization'
where ATTRIBUTENAME = 'Custom attribute name'
```

The following image shows how entries marked as custom appear in the `GUPPRICINGATTRIBUTELINK` table.

:::image type="content" source="media/ssms-customization.png" alt-text="Custom pricing attributes in the GUPPRICINGATTRIBUTELINK table in SQL Server Management Studio." lightbox="media/ssms-customization.png":::


## Build and configure the attribute

After you create the pricing attribute and any required table or CDX extensions, follow these steps:

1. Build the relevant extension models and the Global Unified Pricing model.
1. Restart Internet Information Services (IIS), and then clear the cache for the finance and operations environment.
1. Go to **Pricing management** > **Setup** > **Price attribute groups** > **Price attribute groups**.
1. Select the price attribute group that you want to update.
1. On the **Attributes** FastTab, add the custom pricing attribute.
1. Repeat these steps for each price attribute group that should use the custom attribute.


## Synchronize and test the attribute

To synchronize and test the custom pricing attribute, follow these steps:

1. Go to **Retail and Commerce** > **Retail and Commerce IT** > **Distribution schedule**.
1. Run the **1210 Pricing management** job.
1. Confirm that `GUPPRICINGATTRIBUTELINK.TypeName` is set to `Customization` for the custom attribute.
1. Configure test data:

   - For a `Customer` or `Product` attribute, set a value on a record and create a trade agreement journal that uses the attribute and value.
   - For a `SalesTable` or `SalesLine` attribute, create an auto charge that uses the attribute and value.

1. Run the **9999 All jobs** job.
1. If you extended the Channel database, verify that the field value was synchronized to the extension table in the `ext` schema.
1. In POS, create a transaction that uses the configured record.
1. Verify that the expected price or auto charge is applied.



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
