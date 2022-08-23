---
# required metadata

title: Manage attributes and attribute groups
description: This article describes how to use attributes to provide a way to describe a product and its characteristics through user-defined fields. 
author: ashishmsft
ms.date: 08/23/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EcoResCategoryAttribute, EcoResProductEntityAttributeTableFieldAssociation, EcoResCategorySearchList, EcoResAttribute, COODualUseCategories, EcoResAttributeType, EcoResAttributeValue, EcoResCategoryAttributeGroup, EcoResCategoryFriendlyName
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: asharchw
ms.search.validFrom: 2018-03-30
ms.dyn365.ops.version: Application pdate 5, AX 8.0

---

# Manage attributes and attribute groups

[!include [banner](includes/banner.md)]

*Attributes* provide a way to further describe a product and its characteristics through user-defined fields (for example, memory size, hard disk capacity, energy star compliance, etc.). Attributes can be associated with various Commerce entities, such as product categories and channels, and default values can be set for attributes. When attributes are associated with product categories or channels, products then inherit the attributes and their default values. Attribute default values can be overridden at the individual product level, at the channel level, or in a catalog.

For example, a typical television product might have the following attributes.

| Category   | Attribute                | Permissible values          | Default value |
|------------|--------------------------|-----------------------------|---------------|
| TV & Video | Brand                    | Any valid brand value       | None          |
| TV         | Screen Size              | 20–85 inches                | 55 inches     |
|            | Vertical Resolution      | 4K (2160p), Full HD (1080p), HD (720p) | 4K (2160p)|
|            | Screen Refresh Rate      | 60hz, 120hz, or 240hz       | 60hz          |
|            | HDMI Inputs              | 0–10                        | 3             |


## Attributes and attribute types

Attributes are based on *attribute types*. The attribute type identifies the type of data that can be entered for a specific attribute. The following attribute types are supported:

- **Currency** – This type supports a currency value. It can be bounded (that is, it can support a range of values), or it can be left open.
- **DateTime** – This type supports a date and time value. It can be bounded or left open.
- **Decimal** – This type supports a numerical value that includes decimal places. It also supports a unit of measure. It can be bounded or left open.
- **Integer** – This type supports a numerical value. It also supports a unit of measure. It can be bounded or left open.
- **Text** – This type supports a text value. It also supports a predefined set of possible values (that is, an *enumeration*).
- **Boolean** – This type supports a binary value (**true** or **false**).
- **Reference** – This type references other attributes.

### Set up attribute types

1. Sign in to the back-office client as a merchandising manager.
2. Go to **Product information management \> Setup \> Categories and attributes \> Attribute types**.
3. Create two attribute types of the **Text** type, set the **Fixed list** option to **Yes**, and then add a list of values:

    - Name one attribute type **Bag type**, and add the following values: **Satchel, Clutch, Purse, Backpack, Messenger, Wallet**.
    - Name the other attribute type **Sunglass brand**, and add the following values: **Ray ban**, **Aviator**, and **Oakley**.

![Attribute types](media/AttributeType_2022Series.png)

### Set up an attribute

1. Sign in to the back-office client as a merchandising manager.
2. Go to **Product information management \> Setup \> Categories and attributes \> Attributes**.
3. Create an attribute that is named **Bag type**.
4. Set the **Attribute type** field to **Bag type**.

![Attributes](media/Attribute_2022Series.png)

## Attribute metadata

*Attribute metadata* lets you select options to specify how the attributes for each product should behave. For example, you can specify whether attributes are required, whether they can be used for searches, and whether they can be used as a filter.

For products, the attribute metadata settings can be overridden at the channel level. This capability will be discussed later in this article.

An attribute's **Attributes** page includes several options that are related to attribute metadata. For example, under **ATTRIBUTE METADATA FOR COMMERCE CHANNELS**, if you set the **Can be refined** option to **Yes**, that attribute will be displayed for refinement or filtering of products on search results and category browsing pages. The system doesn't allow you to configure an attribute as refinable until you select **Filter settings** on the command bar and confirm the filter settings for the attribute. 

## Filter settings for attributes

Filter settings for attributes let you define how the filters for attributes are shown in the POS. To access the filter settings for an attribute, on the **Attributes** page, select the attribute, and then, on the Action Pane, select **Filter settings**.

The **Filter display preferences** page includes the following fields:

- **Name** – By default, this field is set to the name of the attribute. However, you can change the value.
- **Display option** – The following options are available:

    - **Single value** – 
        - This option is available for the following attribute types: **Boolean**, **Currency**, **Decimal**, **Integer**, and **Text**. 
        - This option only allows single value selection for refiners on product list pages such as category browsing and product search results.
    
    - **Multi value** – 
        - This option is available for the following attribute types: **Currency**, **Decimal**, **Integer**, and **Text**. 
        - This option enables multi-value selection for this attribute in the client for refinement.
      
- **Display control** – The following options are available:

    - **List** – This option is available for the all attribute types.
    - **Range** – This option is available for the following attribute types: **Currency**, **Decimal**, and **Integer**.
    - **Slider** – This option is available for the following attribute types: **Currency**, **Decimal**, and **Integer**.
    - **Slider with bars** – This option is available for the following attribute types: **Currency**, **Decimal**, and **Integer**.

- **Threshold value** – This setting is required if you selected **Range** as the display control type. You can define values by using a semicolon (;) as a delimiter.

    For example, for the filter like **Bag Volume**, a threshold value can be **10; 20; 50; 100; 200; 500; 1000; 5000**. In this case, the POS will show the following ranges. Any ranges that don't have any products in the result set will appear dimmed.

    - Less than 10
    - 10 – 20
    - 20 – 50
    - 50 – 100
    - 100 – 200
    - 200 – 500
    - 500 or more

![Attribute filter settings](media/AttributeFilterSettings_2022Series.png)


> [!NOTE]
> - Filter settings for attributes are only applicable for 'Product attributes' and can be used for refining product search and category browsing results. These filter settings do not apply to Customer search or Order search, although same attributes could be used for enriching customer or order information. 
> - Among default eCommerce modules, there is no out-of-box support available for filter settings with 'Display control' as 'Range' or 'Slider' or 'Slider with bars'. 'Range' and 'Slider' continue to be supported for Point-of-sale solution, whereas 'Slider with Bars' was applicable for legacy 'SharePoint' online storefront and continues to be available for 3rd party integration and custom scenarios. 
> - It is ideally recommended for refinable attributes to have an attribute of type 'fixed-list', but along with that our recommendations is to keep the list manageable and have upto 100-200 unique values and certainly not consider 'fixed-list' type if the unique values for the refiner are going to be in 1000s to 10000s unique values. In that case, best-suited attribute type is 'Text' and not 'Fixed-list'
> - Translations are critical for attribute names and their values. For attribute of type fixed-list, you can define translations on 'attribute-type' for its values whereas for every other attribute you are able to define translations on the forms where you may define the values for attributes. e.g., For attribute of type 'text' one can define translations for 'default' value on the 'attribute', whereas if you were to override default value at a product level, then you can define translations for it on the 'product attributes' form for the product. 
> - Once an attribute has been marked as refinable for a channel, then you should not update the 'Attribute type' as it would impact the publishing of product data to search index. It is recommended to create a new attribute for new type of refiner and retire previous attribute by removing from other attribute groups. 
> - Search by attributes is supported, whereas it only fetches result for exact match of search words. e.g., if you were to have an attribute 'Fabric' with value as 'Cashmere cotton' then if a shopper were to search for 'Cash' then product with 'Fabric = Cashmere cotton' shall not be retrieved, whereas if user were to search for 'Cashmere' or 'Cotton' or 'Cashmere Cotton' then this product will be retrieved among the search results. 

### Additional options for attribute *(applicable for legacy SharePoint online storefront and external integrations)*

These are the remaining attribute metadata options on the **Attributes** page:

- **Searchable**
- **Retrievable**
- **Can be queried**
- **Sortable**
- **Ignore case and format**
- **Complete match**

These options were originally intended to improve the search functionality for the legacy online storefront that was SharePoint based and do not necessarily apply to Dynamics 365 Commerce e-commerce websites or point-of-sale (POS). We continue to support headless integration and thus, these properties continue to be available to export this metadata for attributes using the Commerce software development kit (SDK). Customers can use the Commerce SDK to put products into an external search index of their choice. In that way, they can build an optimal index to make sure that they index only attributes that, *in their opinion*, should be indexed.

> [!NOTE]
> For information about the purpose of these remaining options, see [Overview of the search schema in SharePoint Server 2013](/SharePoint/search/search-schema-overview).

## Attribute groups

An *attribute group* is used to group the individual attributes for a component or subcomponent in a product configuration model. An attribute can be included in more than one attribute group. Attribute groups can help users configure products, because the various selections are arranged in a specific context. Attribute groups can be assigned to categories or channels.You can also set default values for attributes that are included in an attribute group. 

![Attribute groups.](media/AttributeGroup_2022Series.png)

### Create an attribute group

1. Sign in to the back-office client as a merchandising manager.
2. Go to **Product information management \> Setup \> Categories and attributes \> Attribute groups**.
3. Create an attribute group that is named **Fashion Sunglasses**.
4. Add the following attributes: **Lens shape** and **Sunglass brand**.

### Assign attribute groups to categories

One or more attribute groups can be associated with category nodes in the following types of category hierarchies: Commerce product hierarchy, Channel navigation category hierarchy, and Supplemental product category hierarchy. Then, when products are categorized, they inherit the attributes that are included in the attribute groups.

![Product hierarchy – Product attribute groups.](media/AGRetailProdHierarchy_2022Series.png)

Follow these steps to assign attribute groups to categories in the Commerce product hierarchy.

1. Sign in to the back-office client as a merchandising manager.
2. Go to **Retail and Commerce \> Category and product management \> Commerce product hierarchy**.
3. Select **Fashion navigation hierarchy**.
4. Under **Menswear**, select the **Pants** category, and then, on the **Product attribute groups** FastTab, add an attribute group that is named **Men's belt**. 
5. Select the **Fashion sunglasses** category, and verify the new attributes in the **Fashion Sunglasses** attribute group by selecting **View attributes**. The attribute group should show the new **Lens shape** and **Sunglass brand** attributes.
6. Under **Menswear**, select the **Pants** category, and verify the attributes for the **Men's belt** attribute group by selecting **View attributes**. The attribute group should show the **Men's belt brand**, **Belt fabric**, and **Belt size** attributes.

> [!NOTE]
> This procedure can also be used to assign attribute groups to categories in the Channel navigation category hierarchy and the Supplemental product category hierarchy. In step 2, use the following navigation paths:
>
> - Retail and Commerce &gt; Category and product management &gt; Channel navigation categories
> - Retail and Commerce &gt; Category and product management &gt; Supplemental product categories
> 
> Additionally, you must ensure that you are only associating attribute groups in category hierarchy to **Product attribute groups** fast-tab and *not **Category attribute groups***. If you see attributes showing up in fast-tab **Category attribute values**, please switch the view to category management - where you are able to add or remove category nodes by selecting **Edit category hierarchy** from the top-ribbon (Note : There are two edit options on the category page, please select 'Edit category hierarchy' only) and then locate fast-tab **Category attribute groups** and remove it. There's no support available to fetch attributes by category through Cloud-scale unit.  

## Identify viewable and refinable attributes for Commerce channels for default product collection

As you have associated various attribute groups to categories in various hierarchies (Commerce product hierarchy or Channel navigation categories) and defined those attribute values for each product based on the category association. For those attributes to be viewable in a specific channel, you will have to set "Show attribute on Channel" flag. 

This flag can be located at *Channel categories and product attributes > Set attribute metadata > Select your category from Navigation hierarchy > Channel **Product** attributes (not **Category attributes**) and mark the flag for 'Show attribute on channel' as 'Yes'* for the attribute you intend to be viewable only. And if you intend to have this attribute be 'refinable' as well then you must also check **'Can be refined'**.     

### Control visibility of dimension-based refiners Size, Style and Color

As you may know, there are product dimensions like Size, Style and Color and that they are the most commonly used refiner(s). To make these product dimensions available as refiners, you would be expected to associate an Attribute group at channel level, which is supposed to be composed of reference attribute type inheriting values automatically from product dimension values. 

Next, you would identify intended product dimensions to be viewable and refinable by updating flags located at *Channel categories and product attributes > Set attribute metadata > Select **root-node** from Navigation hierarchy > Channel **Product** attributes (not **Category attributes**) and mark the flag for 'Show attribute on channel' as 'Yes'* for the associated attributes to *Size, Style, Color* dimensions if you intend to make them viewable only. And if you intend to have this attribute be 'refinable' as well then you must also check **'Can be refined'**. 

![Associate product dimension refiners based attribute group to channel](./media/ProductDimensionRefinersAttributeGroup_2022Series.png)

![Set attribute metadata for dimension refiners](./media/ProductDimensionRefinersMetadataSetup_2022Series.png)

![Example of product dimension based attribute setup](./media/ProductDimensionRefinersAttributeSetup_2022Series.png)

Example of steps to enable the attributes so that they are available in the demo-data based Houston channel:

1. Navigate to **Channel categories and product attributes form**
2. Select **Houston**
3. On the Action Pane, select **Set attribute metadata**.
4. Select the **Fashion** category node, and then, on the **Channel product attributes** FastTab, select **Include attribute** for each attribute.
5. Select the **Fashion Accessories** category node, select the **Fashion Sunglasses** category, and then, on the **Channel product attributes** FastTab, select **Include attribute** for each attribute.
6. Select the **Menswear** category node, select the **Pants** category, and then, on the **Channel product attributes** FastTab, select **Include attribute** for each attribute.
7. Ensure upon updating the attribute metadata for your intended attributes and refiners, ensure that you save and 'Publish channel updates' and following to publishing you must run following jobs - 1070 (Channel configuration), 1040 (Products), and 1150 (Catalog). 

> [!NOTE]
> 1. If your business requires to frequently add or remove products in the navigation hierarchy (including updating display orders or adding new categories or adding new attribute groups to categories in navigation hierarchy) or refiner setup. It's recommended to have 'Publish channel updates' configured as a batch job to run frequently or manually trigger 'Publish channel updates' followed by CDX jobs - 1070 (Channel configuration), 1040 (Products), and 1150 (Catalog). 
>
> 1. An inherit option lets you specify that this channel should inherit the attribute groups from its parent channel in the hierarchy. If you set the **Inherit** option to **Yes**, the child channel node inherits all the attribute groups and all the attributes in those attribute groups.
> 
> 1. If you notice that 'Set attribute metadata' is greyed-out, then you must ensure that 'Navigation hierarchy' is associated with your channel under 'General' fast-tab. 
> 
> You must not associate any other attribute groups at a channel level ('Attribute groups' on 'Channel categories and product attributes' form) other than dimension based attribute group. (e.g. with Demo Data, you would see there's an attribute group named 'Default dimensions group for refiners' is only valid attribute group to associate in this place). 
> 
> Starting 10.0.27, with introduction of support for 'Customer specific catalogs' (aka B2B catalogs), you are expected to identify the 'refiner' and 'attribute' setup for each B2B catalog in the same manner as described here. 
> ![Catalog – Product attribute and refiner settings - step 1](media/CatalogAttributeRefinerSetup1_2022Series.png)
> ![Catalog – Product attribute and refiner settings - step 2](media/CatalogAttributeRefinerSetup2_2022Series.png)

## Overriding attribute values

The default values of attributes can be overridden for individual products at the product level. Default values can also be overridden for individual products in specific catalogs that are targeted at specific channels.

### Override the attribute values of an individual product

1. Sign in to the back-office client as a merchandising manager.
2. Go to **Retail and Commerce \> Category and product management \> Released products by category**.
3. Select the **Fashion \> Fashion Accessories \> Fashion Sunglasses** category node.
4. Select the required product in the grid. Then, on the Action Pane, on the **Product** tab, in the **Set up** group, select **Product attributes**.
5. Select an attribute in the left pane, and then update its value in the right pane.

![Product details page – Product attribute groups.](media/ProdDetailsProdAttrValues_2022Series.png)

### Override the attribute values of products in a catalog

1. Sign in to the back-office client as a merchandising manager.
2. Go to **Retail and Commerce \> Catalog management \> All catalogs**.
3. Select the **Fabrikam Base Catalog** catalog.
4. Select the **Fashion \> Fashion Accessories \> Fashion Sunglasses** category node.
5. On the **Products** FastTab, select the required product, and then select **Attributes** above the product grid.
6. On the following FastTabs, update the values of the required attributes

### Override the attribute values of products in a channel

1. Sign in to the back-office client as a merchandising manager.
2. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**.
3. Select the **Houston** channel.
4. On the **Products** FastTab, select the required product, and then select **Attributes** above the product grid.
5. If no products are available, add products by selecting **Add** on the **Products** FastTab and then selecting the required products in the **Add products** dialog box.
6. On the following FastTabs, update the values of the required attributes:
    - Shared product media
    - Shared product attributes
    - Channel media
    - Channel product attributes

### Define variant specific attribute values and define multiple values for product attributes

1. Sign in to the back-office client as a merchandising manager.
2. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**.
3. Select the **Houston** channel.
4. On the **Products** FastTab, select the required product variant, and then select **Attributes** above the product grid.
5. If no products are available, add products by selecting **Add** on the **Products** FastTab and then selecting the required product variants in the **Add products** dialog box.
6. On the following FastTabs, update the values of the required attributes:
    - Shared product media
    - Shared product attributes
    - Channel media
    - Channel product attributes
    
7. Example – 
		
    P001 is a ‘Multi-activity Shoe’ and it has 3 variants – _Running, Walking, Trekking_. And for each variant you want to define ‘Activity’ attribute value uniquely – which can be done through ‘Channel categories and product attributes’ form, from 'Products' fast-tab for your channel and 

    - P001-Master : Activity – Sports 
    - P001-1 : Activity - Running
    - P001-2 : Activity – Walking 
    - P001-3 : Activity – Trekking

Now, when a user were to search for ‘Shoe’ – it would certainly list P001 among search results and if you had chosen ‘Activity’ to be refinable as well then ‘Activity’ refiner would ONLY list ‘Sports’ as a refinable value, considering that’s defined for ‘Activity’ attribute at ‘P001-Master’

Then, what about the attributes that are defined at a variant level? How can those values show up among refiners? 

Default experience – variant-level attribute are only intended for PDP (Product details page) – as you select a specific variant, product specifications are updated for that specific product variant. 
 
But, for refiners to show values defined at a product variant level – You would need to define an attribute at a product master level with **‘Allow multiple values’** checked on attribute definition of type ‘TEXT’. 
 
Next, you would need to determine all possible values for your product variants. To continue with the example of ‘Activity’ – there shall be following possible values for the attribute : Running, Walking, Hiking, Trekking, Camping, Watersports, Snowsports, etc. 
 
Once you have determined those values – you can define that on a Product master level with a pipe-separated-value.  In the above example – ‘Activity’ on product master would have to be defined as following – ‘Running|Walking|Hiking|Trekking|Camping|Watersports|Snowsports’

Mark this attribute as refinable 

And now on each variant you can either define values for this attribute to be either pipe-separated or single values. In the above example – ‘Activity’ on individual product variant could be – ‘Running|Walking|Hiking’ or ‘Running’ or ‘Running|Hiking|Watersports’ etc. 
 
‘Publish channel updates’ from ‘Channel categories and product attributes’ and run 1150, 1040 and 1070 jobs. 

Upon successful completion of the job and updates to the ‘search index’ – all expected values will show among the search results and category browsing results. 



[!INCLUDE[footer-include](../includes/footer-banner.md)]
