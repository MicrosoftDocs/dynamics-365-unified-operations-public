---
title: Support custom pricing attributes for POS
description: Learn how to support custom pricing attributes in POS by implementing a custom request handler
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/28/2025
ms.custom:
- bap-template
---

# Add custom pricing attributes for POS

<!-- KFM: We need to define "POS". Point of sale? Is that part of Commerce? -->

Unified pricing management lets you configure pricing rules that can also consider values of custom pricing attributes for products, customers, sales-lines, and sales-tables. It provides the following two methods <!-- KFM: is it correct to call these "methods"? --> that you can use to implement your own custom request handler and develop your logic: `GetCustomizedPricingPropertiesRequest` and `GetCustomizedPricingPropertiesResponse`.

Custom attributes are marked in `GUPPRICINGATTRIBUTELINK` <!-- KFM: What kind of a thing is `GUPPRICINGATTRIBUTELINK`. A table? Where do we find this? -->using a specific identifier, which indicates that they require special logic in Commerce Scale Unit (CSU) to be supported in POS. To mark a pricing attribute as custom, the `GUPPRICINGATTRIBUTELINK.TypeName` column must be set to `Customization`.

In CSU logic, if a custom pricing attribute is validated as `GUPPRICINGATTRIBUTELINK.TypeName = 'Customization'`, then the system calls the custom request handler.

## Prerequisites

To use the features described in this article, you must be running version 10.0.45 or later of your Microsoft finance and operations apps.

## First steps

<!-- KFM: Introduction is needed here. Explain what we are we about to do and why. -->

1. Implement a custom request handler to process custom pricing attributes. For an example, see [Example custom request handler code](upm-custom-request-handler-example.md)

1. Register the output library in the `CommerceRuntime.Ext.config` file. Here is an example of a custom request handler registration (if the output library were `Contoso.Commerce.Runtime.Services`).

    :::image type="content" source="media/commerce-runtime.png" alt-text="Custom request handler registration." lightbox="media/commerce-runtime.png"::: <!-- KFM: We should provide this as text instead of an image. -->

1. Build the solution and deploy it to your Commerce Scale Unit (CSU).

1. Enable the CSU flight `UPSupportCustomPricingAttributesFlight`. <!-- KFM: We don't normally document features that require flights (because they are usually private previews and we don't document private preview features). Is this a private preview? We don't document how to enable flights. -->

## How to add your custom pricing attributes

<!-- KFM: Introduction is needed here. Explain what we are we about to do and why. -->

1. In AppSuite repo <!-- KFM: What is this? Where do I find it? -->, create new custom pricing attributes according to: [How to add a new pricing attribute](https://eng.ms/docs/cloud-ai-platform/business-and-industry-copilot/bic-bis-ai-erp-smb/aierp-finance/d365-finance-application-core-services/dynamics-365-ai-erp/domainknowledge/scm/pricingmanagement/howto/howtoaddanewpricingattribute). <!-- KFM: This link requires a VPN; I think it's internal (not public). Our customers won't be able to open it. Do we have public link for this info? --> You must add a new class for each custom pricing attribute you want to add.

    - Here is an example of code that creates a header-level custom pricing attribute (for `Customer`): <!-- KFM: What is the text in parentheses? A table name? Should we say "for" or maybe "in"? Also,what language is this example? -->

        ```text
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

    - Here is an example of code that creates a line-level custom pricing attribute (for `SalesLine`): <!-- KFM: What is the text in parentheses? A table name? Should we say "for" or maybe "in"? Also,what language is this example? -->

        ```text
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

1. For **new** <!-- KFM: How much of this procedure applies just for **new** groups? Just this step, or everything up to the step where we mention **existing** groups? --> custom pricing attributes, you must programmatically set the `TypeName` column of the `GUPPRICINGATTRIBUTELINK` table to `Customization`. In AppSuite repo,  create an extension to [GUPPricingAttributeRepository.xml](https://msdyneng.visualstudio.com/FinOps/_git/ApplicationSuite?path=/Source/Metadata/GlobalUnifiedPricing/GlobalUnifiedPricing/AxClass/GUPPricingAttributeRepository.xml&version=GBmaster&line=271&lineEnd=271&lineStartColumn=45&lineEndColumn=65&lineStyle=plain&_a=contents) <!-- KFM: Will customers be able to open this link? --> and add a statement to the `toPriceAttributeLink()` method that programmatically sets the `TypeName` column for each new custom pricing attribute. Here is an example of how to do this: <!-- what language is this example? -->

    ```text
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

1. Build the relevant models (GUP or extension) <!-- KFM: Spell out "GUP". What do these values in parentheses mean? -->, restart Internet Information Services (IIS), and clear the cache using a URL such as `<https://usnconeboxax1aos.cloud.onebox.dynamics.com/?cmp=usrt&mi=SysClassRunner&cls=SysFlushAOD>`. <!-- KFM: Can we give a more generic URL for this? We maybe shouldn't expose our internal server names. -->

1. Sign in to your Microsoft finance and operations app and go to **Pricing management** \> **Setup** \> **Price attribute groups** \> **Price attribute groups**. Select the price attribute group that you want to customize and then use the **Attributes** FastTab to add your custom pricing attributes to it. Update each group as needed.

1. Run the 1210 (Pricing management) job and sync changes to Channel database. <!-- KFM: I'm not familiar with any of this. More detail and instructions are probably needed. How/where do we do this? What is the "Channel database"? -->

1. For **existing** custom pricing attributes, manually set the `TypeName` column of the `GUPPRICINGATTRIBUTELINK` table to `Customization` in SSMS. <!-- KFM: Spell out "SSMS". -->. Here's an example of how to set the `Customization` identifier: <!-- KFM: What coding language is this?. -->

    ```text
    update dbo.GUPPRICINGATTRIBUTELINK
    set TYPENAME = 'Customization'
    where ATTRIBUTENAME = 'Custom attribute name'
    ```

    <!-- KFM: We should add some text here that introduces this image. What are we showing here? -->

    :::image type="content" source="media/ssms-customization.png" alt-text="SSMS customization." lightbox="media/ssms-customization.png":::

1. For `Customer` or `Product`, create a trade agreement journal that tests the new custom pricing attribute. For `SalesTable` or `SalesLine`, create an auto charge that tests the new custom pricing attribute. In both cases, make sure to set a specific value.

1. Run the 9999 (full sync) and sync to Channel database. <!-- KFM: I'm not familiar with any of this. More detail and instructions are probably needed. How/where do we do this? What is the "Channel database"? -->

1. In POS <!-- KFM: What is this? -->, you should see the value configured in the trade agreement journal or that an auto charge was correctly applied.

## Troubleshooting

### You receive a POS notification that a custom request handler is not implemented

[<img src="media/request-handler-custom.png" alt="Custom request handler" title="Custom request handler" width="360" />](media/request-handler-custom.png#lightbox)

1. Verify that a custom request handler is implemented and included in the build.

1. Ensure that the custom request handler is correctly registered in the CommerceRuntime.Ext.config file. Keep in mind that this registration can be overwritten during the build process, so it is important for the customer to confirm the registration after build completion.

### You receive a POS notification that custom pricing attributes are detected among out-of-box attributes

[<img src="media/custom-customer-attribute.png" alt="Custom customer attribute" title="Custom customer attribute" width="360" />](media/custom-customer-attribute.png#lightbox) [<img src="media/custom-product-attribute.png" alt="Custom product attribute" title="Custom product attribute" width="360" />](media/custom-product-attribute.png#lightbox)

1. Verify that the CSU flight UPSupportCustomPricingAttributesFlight is enabled.

1. Confirm that the new custom pricing attributes are identified as custom. The GUPPRICINGATTRIBUTELINK.TypeName column should be set to 'Customization' for all custom pricing attributes.

### Further troubleshooting

1. It is possible to find more details on errors or exceptions in our AzureDataExplorer dashboards.

    - Useful dashboards (Must access with PME account):
        - CSU logs: <https://dataexplorer.azure.com/dashboards/db50f9f4-9a19-4a4c-9993-17e0861444d1>
        - POS logs: <https://dataexplorer.azure.com/dashboards/8ad7df1a-a343-459b-beeb-5f4cafabe91c>
        - Drill MPOS - CPOS - CSU - RSSU sessions logs: <https://dataexplorer.azure.com/dashboards/32491967-1eff-4b22-b161-f4bb8db6e550>

1. Given the app session id, user session id, or activity id, it is possible to trace AppInsights. (AppInsights PROD stores all Commerce customer logs.)

    Troubleshooting through telemetry wiki: <https://msazure.visualstudio.com/D365/_wiki/wikis/D365.wiki/9342/Troubleshooting-Through-Telemetry>

   [<img src="media/telemetry-troubleshooting.png" alt="Telemetry troubleshooting" title="Telemetry troubleshooting" width="720" />](media/telemetry-troubleshooting.png#lightbox)

    - Starting query template for CSU logs:

    ```
    traces
    | where customDimensions.UserSessionId == "UserSessionId"
    ```

    ```
    traces
    | where customDimensions.AppSessionId == "AppSessionId"
    ```

    ```
    traces
    | where customDimensions.ActivityId == "ActivityId"
    ```

    - Example of locating full database error in CSU logs:

        [<img src="media/retail-server-logs.png" alt="Retail server logs" title="Retail server logs" width="720" />](media/retail-server-logs.png#lightbox)
