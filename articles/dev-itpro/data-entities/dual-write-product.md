---
# required metadata

title: Integrated product masters
description: This topic describes the integration of product data between Microsoft Dynamics 365 for Finance and Operations and Common Data Service.
author: benebotg 
manager: AnnBe
ms.date: 08/6/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2019-07-15

---

# Integrated product masters

[!include [banner](../includes/banner.md)]

[!include [preview](../includes/preview-banner.md)]

Integration of products lets you synchronize product data from Microsoft Dynamics 365 for Finance and Operations to Common Data Service. Because of the integration, product data that originates in Finance and Operation can be viewed and used in Dynamics 365 for Customer Engagement.

Because the concept of a product is richer in Finance and Operations than in Customer Engagement, Finance and Operations is considered the master of the integration. In Customer Engagement, the product data from Finance and Operations is read-only.

The richness of the supply chain management related fields to product data is also available in Common Data Service, and all the existing concepts that are used to define the product are also defined.

## Templates

Product information contains all the information that is related to the product and its definition, such as the product dimensions or the tracking and storage dimensions. As the following table shows, a collection of entity maps is created to sync products and related information.

Finance and Operations | Customer Engagement application
-----------------------|--------------------------------
Released products V2 | Product
Released products V2 | msdyn\_sharedproductdetails
CDS released distinct products | Product
CDS released distinct products | msdyn\_sharedproductdetails
Product number identified barcode | msdyn\_productbarcodes
Default order settings | msdyn\_productdefaultordersettings
Product dimension groups | msdyn\_productdimensiongroups
Storage dimension groups | msdyn\_productstoragedimensiongroups
Sites | msdyn\_operationalsites
Warehouses | msdyn\_inventwarehouses
Colors | msdyn\_productcolors
Sizes | msdyn\_productsizes
Styles | msdyn\_productsytles
Configurations | msdyn\_productconfigurations

[!include [banner](../includes/dual-write-symbols.md)]

## Integration of products

In this model, the product is represented by the combination of two entities in Common Data Service: **Product** and **msdyn\_sharedproductdetails**. Whereas the first entity contains the definition of a product (the unique identifier for the product, the product name, and the description), the second entity contains the fields that are stored at the product level in Finance and Operations. The combination of these two entities is used to define the product according to the concept of the stock keeping unit (SKU).

Because the product is represented as an SKU, the concepts of distinct products, product masters, and product variants from Finance and Operations can be captured in Common Data Service in the following way:

- **Distinct products** (without variants) are products that are defined by themselves. No dimensions have to be defined for them. An example is a specific book. For these products, one record is created in the **Product** entity, and one record is created in the **msdyn\_sharedproductdetails** entity. No product family record is created.
- **Product masters** in Finance and Operations are used as generic products that hold the definition and rules to behave in business processes. Based on these definitions, distinct products that are known as product variants can be generated. For example, T-shirt is the product master, and it can have Color and Size as dimensions. Variants can be released that have different combinations of these dimensions, such a small blue T-shirt or a medium green T-shirt. In the integration, one record per variant is created in the product table. This record contains the variant-specific information, such as the different dimensions. The generic information for the product is stored in the **msdyn\_sharedproductdetails** entity. (In Finance and Operations, this generic information is held in the product master.) Additionally, one product family record is created per product master. The product master information is synced to Common Data Service as soon as the released product master is created (but before variants are released).

![Data model for products](media/dual-write-product.png)

### CDS released distinct products to Product

The **Product** entity contains the fields that define the product. The following table shows the mappings.

Source field | Map type | Destination field
---|---|---
PRODUCTNUMBER | \> | productnumber
PRODUCTNAME | \> | name
PRODUCTDESCRIPTION | \> | description
ITEMNUMBER | \> | msdyn\_itemnumber
CURRENCYCODE | \> | transactioncurrencyid.isocurrencycode
SALESUNITSYMBOL | \> | msdyn\_integrationdefaultuomname
SALESPRICE | \> | price
UNITCOST | \> | currentcost
\[None\] | \>\> | msdyn\_integrationdefaultuomschedulename
PRODUCTTYPE | \>\> | producttypecode
SALESUNITDECIMALPRECISION | \>\> | quantitydecimal

### Released products V2 to msdyn\_sharedproductdetails

The **msdyn\_sharedproductdetails** entity contains the fields from Finance and Operations that define the product, and that contain the product's financial and management information. The following table shows the mappings.

Source field | Map type | Destination field
---|---|---
PRODUCTNUMBER | \> | msdyn\_productnumber
INTRASTATCHARGEPERCENTAGE | \> | msdyn\_intrastatchargepercentage
ITEMNUMBER | \>\> | msdyn\_itemnumber
APPROXIMATESALESTAXPERCENTAGE | \> | msdyn\_approximatesalestaxpercentage
ARRIVALHANDLINGTIME | \> | msdyn\_arrivalhandlingtime
BESTBEFOREPERIODDAYS | \> | msdyn\_bestbeforeperioddays
CARRYINGCOSTABCCODE | \>\> | msdyn\_carryingcostabccode
CONSTANTSCRAPQUANTITY | \> | msdyn\_constantscrapquantity
COSTCHARGESQUANTITY | \> | msdyn\_costchargesquantity
DEFAULTRECEIVINGQUANTITY | \> | msdyn\_defaultreceivingquantity
FIXEDPURCHASEPRICECHARGES | \> | msdyn\_fixedpurchasepricecharges
FIXEDSALESPRICECHARGES | \> | msdyn\_fixedsalespricecharges
GROSSDEPTH | \> | msdyn\_grossdepth
GROSSPRODUCTHEIGHT | \> | msdyn\_grossproductheight
GROSSPRODUCTWIDTH | \> | msdyn\_grossproductwidth
INVENTORYUNITSYMBOL | \> | msdyn\_inventoryunitsymbol.name
ISDISCOUNTPOSREGISTRATIONPROHIBITED | \>\> | msdyn\_isdiscountposregistrationprohibited
ISEXEMPTFROMAUTOMATICNOTIFICATIONANDCANCELLATION | \>\> | msdyn\_exemptautomaticnotificationcancel
ISINSTALLMENTELIGIBLE | \>\> | msdyn\_isinstallmenteligible
ISINTERCOMPANYPURCHASEUSAGEBLOCKED | \>\> | msdyn\_isintercompanypurchaseusageblocked
ISINTERCOMPANYSALESUSAGEBLOCKED | \>\> | msdyn\_isintercompanysalesusageblocked
ISMANUALDISCOUNTPOSREGISTRATIONPROHIBITED | \>\> | msdyn\_ismanualdiscposregistrationprohibited
ISPHANTOM | \>\> | msdyn\_isphantom
ISPOSREGISTRATIONBLOCKED | \>\> | msdyn\_isposregistrationblocked
ISPOSREGISTRATIONQUANTITYNEGATIVE | \>\> | msdyn\_isposregistrationquantitynegative
ISPURCHASEPRICEAUTOMATICALLYUPDATED | \>\> | msdyn\_ispurchasepriceautomaticallyupdated
ISPURCHASEPRICEINCLUDINGCHARGES | \>\> | msdyn\_ispurchasepriceincludingcharges
ISSALESWITHHOLDINGTAXCALCULATED | \>\> | msdyn\_issaleswithholdingtaxcalculated
ISRESTRICTEDFORCOUPONS | \>\> | msdyn\_isrestrictedforcoupons
ISSALESPRICEADJUSTMENTALLOWED | \>\> | msdyn\_issalespriceadjustmentallowed
ISSALESPRICEINCLUDINGCHARGES | \>\> | msdyn\_issalespriceincludingcharges
ISSCALEPRODUCT | \>\> | msdyn\_isscaleproduct
ISSHIPALONEENABLED | \>\> | msdyn\_isshipaloneenabled
ISUNITCOSTPRODUCTVARIANTSPECIFIC | \>\> | msdyn\_isunitcostproductvariantspecific
ISVARIANTSHELFLABELSPRINTINGENABLED | \>\> | msdyn\_isvariantshelflabelsprintingenabled
ISZEROPRICEPOSREGISTRATIONALLOWED | \>\> | msdyn\_iszeropriceposregistrationallowed
KEYINPRICEREQUIREMENTSATPOSREGISTER | \>\> | msdyn\_keyinpricerequirementsatposregister
KEYINQUANTITYREQUIREMENTSATPOSREGISTER | \>\> | msdyn\_keyinquantityrequirementsatposregister
MARGINABCCODE | \>\> | msdyn\_marginabccode
MAXIMUMPICKQUANTITY | \> | msdyn\_maximumpickquantity
MUSTKEYINCOMMENTATPOSREGISTER | \>\> | msdyn\_mustkeyincommentatposregister
NECESSARYPRODUCTIONWORKINGTIMESCHEDULINGPROPERTYID | \> | msdyn\_necessaryproductionworkingtimeschedulingp
NETPRODUCTWEIGHT | \> | msdyn\_netproductweight
PACKINGDUTYQUANTITY | \> | msdyn\_packingdutyquantity
POSREGISTRATIONACTIVATIONDATE | \> | msdyn\_posregistrationactivationdate
POSREGISTRATIONBLOCKEDDATE | \> | msdyn\_posregistrationblockeddate
POSREGISTRATIONPLANNEDBLOCKEDDATE | \> | msdyn\_posregistrationplannedblockeddate
POTENCYBASEATTIBUTETARGETVALUE | \> | msdyn\_potencybaseattibutetargetvalue
POTENCYBASEATTRIBUTEVALUEENTRYEVENT | \>\> | msdyn\_potencybaseattributevalueentryevent
PRODUCTTYPE | \>\> | msdyn\_producttype
PRODUCTIONCONSUMPTIONDENSITYCONVERSIONFACTOR | \> | msdyn\_productionconsumptiondensityconversion
PRODUCTIONCONSUMPTIONDEPTHCONVERSIONFACTOR | \> | msdyn\_productionconsumptiondepthconversion
PRODUCTIONCONSUMPTIONHEIGHTCONVERSIONFACTOR | \> | msdyn\_productionconsumptionheightconversion
PRODUCTIONCONSUMPTIONWIDTHCONVERSIONFACTOR | \> | msdyn\_productionconsumptionwidthconversion
PRODUCTVOLUME | \> | msdyn\_productvolume
PURCHASECHARGESQUANTITY | \> | msdyn\_purchasechargesquantity
PURCHASEOVERDELIVERYPERCENTAGE | \> | msdyn\_purchaseoverdeliverypercentage
PURCHASEPRICE | \> | msdyn\_purchaseprice
PURCHASEPRICEDATE | \> | msdyn\_purchasepricedate
PURCHASEPRICINGPRECISION | \> | msdyn\_purchasepricingprecision
PURCHASEUNDERDELIVERYPERCENTAGE | \> | msdyn\_purchaseunderdeliverypercentage
RAWMATERIALPICKINGPRINCIPLE | \>\> | msdyn\_rawmaterialpickingprinciple
SALESCHARGESQUANTITY | \> | msdyn\_saleschargesquantity
SALESOVERDELIVERYPERCENTAGE | \> | msdyn\_salesoverdeliverypercentage
SALESPRICE | \> | msdyn\_salesprice
SALESPRICECALCULATIONCHARGESPERCENTAGE | \> | msdyn\_salespricecalculationchargespercentage
SALESPRICECALCULATIONCONTRIBUTIONRATIO | \> | msdyn\_salespricecalculationcontributionratio
SALESPRICECALCULATIONMODEL | \>\> | msdyn\_salespricecalculationmodel
SALESPRICEDATE | \> | msdyn\_salespricedate
SALESPRICINGPRECISION | \> | msdyn\_salespricingprecision
SALESUNDERDELIVERYPERCENTAGE | \> | msdyn\_salesunderdeliverypercentage
SALESUNITSYMBOL | \> | msdyn\_salesunitsymbol.name
SCALEINDICATOR | \>\> | msdyn\_scaleindicator
SELLSTARTDATE | \> | msdyn\_sellstartdate
SHELFADVICEPERIODDAYS | \> | msdyn\_shelfadviceperioddays
SHELFLIFEPERIODDAYS | \> | msdyn\_shelflifeperioddays
SHIPSTARTDATE | \> | msdyn\_shipstartdate
TAREPRODUCTWEIGHT | \> | msdyn\_tareproductweight
TRANSFERORDEROVERDELIVERYPERCENTAGE | \> | msdyn\_transferorderoverdeliverypercentage
TRANSFERORDERUNDERDELIVERYPERCENTAGE | \> | msdyn\_transferorderunderdeliverypercentage
UNITCOST | \> | msdyn\_unitcost
UNITCOSTDATE | \> | msdyn\_unitcostdate
UNITCOSTQUANTITY | \> | msdyn\_unitcostquantity
VARIABLESCRAPPERCENTAGE | \> | msdyn\_variablescrappercentage
WAREHOUSEMOBILEDEVICEDESCRIPTIONLINE1 | \> | msdyn\_warehousemobiledevicedescriptionline1
WAREHOUSEMOBILEDEVICEDESCRIPTIONLINE2 | \> | msdyn\_warehousemobiledevicedescriptionline2
WILLINVENTORYISSUEAUTOMATICALLYREPORTASFINISHED | \>\> | msdyn\_willinventoryissueautoreportasfinished
WILLINVENTORYRECEIPTIGNOREFLUSHINGPRINCIPLE | \>\> | msdyn\_willinventoryreceiptignoreflushing
WILLPICKINGWORKBENCHAPPLYBOXINGLOGIC | \>\> | msdyn\_willpickingworkbenchapplyboxinglogic
WILLTOTALPURCHASEDISCOUNTCALCULATIONINCLUDEPRODUCT | \>\> | msdyn\_willtotalpurchdiscountcalcincludeproduct
WILLTOTALSALESDISCOUNTCALCULATIONINCLUDEPRODUCT | \>\> | msdyn\_willtotalsalesdiscountcalcincludeproduct
WILLWORKCENTERPICKINGALLOWNEGATIVEINVENTORY | \>\> | msdyn\_willworkcenterpickingallownegativeinvent
YIELDPERCENTAGE | \> | msdyn\_yieldpercentage
ISUNITCOSTAUTOMATICALLYUPDATED | \>\> | msdyn\_isunitcostautomaticallyupdated
PURCHASEUNITSYMBOL | \> | msdyn\_purchaseunitsymbol.name
PURCHASEPRICEQUANTITY | \> | msdyn\_purchasepricequantity
ISUNITCOSTINCLUDINGCHARGES | \>\> | msdyn\_isunitcostincludingcharges
FIXEDCOSTCHARGES | \>\> | msdyn\_fixedcostcharges
MINIMUMCATCHWEIGHTQUANTITY | \>\> | msdyn\_minimumcatchweightquantity
MAXIMUMCATCHWEIGHTQUANTITY | \>\> | msdyn\_maximumcatchweightquantity
ALTERNATIVEITEMNUMBER | \>\> | msdyn\_alternativeitemnumber.msdyn\_itemnumber
BOMUNITSYMBOL | \>\> | msdyn\_bomunitsymbol.name
CATCHWEIGHTUNITSYMBOL | \>\> | msdyn\_catchweightunitsymbol.name
COMPARISONPRICEBASEUNITSYMBOL | \>\> | msdyn\_comparisonpricebaseunitsymbol.name
PRIMARYVENDORACCOUNTNUMBER | \>\> | msdyn\_vendorid.msdyn\_vendoraccountnumber
ISCATCHWEIGHTPRODUCT | \>\> | msdyn\_iscatchweight
PRODUCTDIMENSIONGROUPNAME | \>\> | msdyn\_productdimensiongroupid.msdyn\_groupname

## Product dimensions and product dimension group

Product dimensions are characteristics that identify a product variant. The four product dimensions (Color, Size, Style, and Configuration) are also mapped to Common Data Service to define the product variants. The following illustration shows the data model.

![Data model for products](media/dual-write-product-2.png)

### Colors

All the possible colors in Finance and Operations are available in Common Data Service through the following mappings.

Source field | Map type | Destination field
---|---|---
COLORID | \>\> | msdyn\_name
COLORID | \>\> | msdyn\_productcolorname

### Sizes

All the possible sizes in Finance and Operations are available in Common Data Service through the following mappings.

Source field | Map type | Destination field
---|---|---
SIZEID | \>\> | msdyn\_productsize
SIZEID | \>\> | msdyn\_name

### Styles

All the possible styles in Finance and Operations are available in Common Data Service through the following mappings.

Source field | Map type | Destination field
---|---|---
STYLEID | \>\> | msdyn\_productstyle
STYLEID | \>\> | msdyn\_name

### Configurations

All the possible configurations in Finance and Operations are available in Common Data Service through the following mappings.

Source field | Map type | Destination field
---|---|---
CONFIGURATIONID | \>\> | msdyn\_name
CONFIGURATIONID | \>\> | msdyn\_productconfiguration
CONFIGURATIONID | \>\> | msdyn\_name
CONFIGURATIONID | \>\> | msdyn\_productconfiguration

When a product has different product dimensions (for example, a product master has Size and Color as product dimensions), each distinct product (that is, each product variant) is defined as a combination of those product dimensions. For example, product number B0001 is an extra-small black T-shirt, and product number B0002 is a small black T-shirt. In this case, the existing combinations of product dimensions are defined. For example, the T-shirt from the preceding example can be extra-small and black, small and black, medium and black, or large and black, but it can't be extra-large and black. In other words, the product dimensions that a product master can take are specified, and variants can be released based on these values.

To keep track of the product dimensions that a product master can take, the following entities are created and mapped in Common Data Service for each product dimension. For more information about products in Finance and Operations, see [Product information overview](https://docs.microsoft.com/dynamics365/unified-operations/supply-chain/pim/product-information).

### Shared product color

The **Shared product color** entity indicates the colors that a specific product master of Finance and Operations can have. This concept is migrated to Common Data Service to keep data consistent. The following table shows the mappings.

Source field | Map type | Destination field
---|---|---
PRODUCTCOLORID | \>\> | msdyn\_productcolorintegration
PRODUCTCOLORID | \>\> | msdyn\_productcolorid.msdyn\_productcolorname
PRODUCTMASTERNUMBER | \>\> | msdyn\_sharedproductnumberintegration
PRODUCTMASTERNUMBER | \>\> | msdyn\_sharedproductdetailid.msdyn\_itemnumber
REPLENISHMENTWEIGHT | \>\> | msdyn\_replenishmentweight
DISPLAYSEQUENCENUMBER | \>\> | msdyn\_retaildisplayorder

### Shared product size

The **Shared product size** entity indicates the sizes that a specific product master of Finance and Operations can have. This concept is migrated to Common Data Service to keep data consistent. The following table shows the mappings.

Source field | Map type | Destination field
---|---|---
PRODUCTMASTERNUMBER | \>\> | msdyn\_sharedproductnumberintegration
PRODUCTMASTERNUMBER | \>\> | msdyn\_sharedproductdetailid.msdyn\_itemnumber
PRODUCTSIZEID | \>\> | msdyn\_productsizeid.msdyn\_productsize
PRODUCTSIZEID | \>\> | msdyn\_productsizeintegration
REPLENISHMENTWEIGHT | \>\> | msdyn\_replenishmentweight
DISPLAYSEQUENCENUMBER | \>\> | msdyn\_displaysequencenumber

### Shared product style

The **Shared product style** entity indicates the styles that a specific product master of Finance and Operations can have. This concept is migrated to Common Data Service to keep data consistent. The following table shows the mappings.

Source field | Map type | Destination field
---|---|---
PRODUCTMASTERNUMBER | \>\> | msdyn\_sharedproductdetailintegration
PRODUCTMASTERNUMBER | \>\> | msdyn\_sharedproductdetailsid.msdyn\_itemnumber
PRODUCTSTYLEID | \>\> | msdyn\_productstyleintegration
PRODUCTSTYLEID | \>\> | msdyn\_productstyleid.msdyn\_productstyle
REPLENISHMENTWEIGHT | \>\> | msdyn\_replenishmentweight
DISPLAYSEQUENCENUMBER | \>\> | msdyn\_displaysequencenumber

### Shared product configuration

The **Shared product configuration** entity indicates the configurations that a specific product master of Finance and Operations can have. This concept is migrated to Common Data Service to keep data consistent. The following table shows the mappings.

Source field | Map type | Destination field
---|---|---
CONTAINERUNITSYMBOL | \>\> | msdyn\_containerunitsymbol
PRODUCTCONFIGURATIONID | \>\> | msdyn\_configurationintegration
PRODUCTCONFIGURATIONID | \>\> | msdyn\_productconfigurationid.msdyn\_productconfiguration
PRODUCTMASTERNUMBER | \>\> | msdyn\_sharedproductnumberintegration
PRODUCTMASTERNUMBER | \>\> | msdyn\_sharedproductdetailid.msdyn\_itemnumber
REPLENISHMENTWEIGHT | \>\> | msdyn\_replenishmentweight
DISPLAYSEQUENCENUMBER | \>\> | msdyn\_displaysequencenumber

## Product number identifier bar codes

Product bar codes are used to uniquely identify products. The following mappings are used to make these product bar codes available in Common Data Service.

Source field | Map type | Destination field
---|---|---
PRODUCTNUMBER | \> | msdyn\_productnumberid.productnumber
BARCODE | \> | msdyn\_name
BARCODE | \> | msdyn\_barcode
PRODUCTQUANTITY | \> | msdyn\_productquantity
PRODUCTDESCRIPTION | \> | msdyn\_productdescription
BARCODESETUPID | \> | msdyn\_barcodesetupid
PRODUCTQUANTITYUNITSYMBOL | \> | msdyn\_unitofmeasureid.name
ISDEFAULTSCANNEDBARCODE | \>\> | msdyn\_isdefaultscannedbarcode
ISDEFAULTPRINTEDBARCODE | \>\> | msdyn\_isdefaultprintedbarcode
ISDEFAULTDISPLAYEDBARCODE | \>\> | msdyn\_isdefaultdisplayedbarcode
