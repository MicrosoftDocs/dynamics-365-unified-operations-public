---
# required metadata

title: Integrated products
description: This topic describes the integration of products data between Finance and Operations and Common Data Service.
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

# Integrated products

[!include [banner](../includes/banner.md)]

[!include [preview](../includes/preview-banner.md)]

With the integration of products, you will be able to synchronize the products from Microsoft Dynamics 365 for Finance and Operations to CDS. The integration will enable you to view and use in Customer Engagement the products originated in Finance and Operations. 
As the concept of products is much richer in Finance and Operations than in Customer Engagement, Finance and Operations will be considered the master of the integration and in Customer Engagement the products originated from the integration will be read-only. 
The richness of the supply chain management related fields to the product will also be available in CDS and all the existing concepts to define the product will also be defined. To harmonize the representation of product between Finance and Operations and Customer Engagement the following model is being introduced:

## Templates

Product information contains all information related to the product and its definition such as the product dimensions or the tracking and storage dimension.  A collection of entity maps are created to synchronize products and its related information, as shown in the following table:

Finance and Operations  | Customer Engagement application
--------------------------|---------------------------------
Released products V2      | Product
Released products V2      | msdyn_sharedproductdetails
CDS released distinct products| Product
CDS released distinct products| msdyn_sharedproductdetails
Product number identified barcode | msdyn_productbarcodes
Default order settings    | msdyn_productdefaultordersettings
Product dimension groups            | msdyn_productdimensiongroups
Storage dimension groups      | msdyn_productstoragedimensiongroups
Sites       | msdyn_operationalsites
Warehouses           | msdyn_inventwarehouses
Colors    | msdyn_productcolors
Sizes          | msdyn_productsizes
Styles         | msdyn_productsytles
Configurations | msdyn_productconfigurations

[!include [banner](../includes/dual-write-symbols.md)]
<!--- the banner above needs to be  https://github.com/MicrosoftDocs/dynamics-365-unified-operations-public/blob/live/articles/dev-itpro/includes/dual-write-symbols.md                 --->

## Integration of products 

With this model the product will be represented by the combination of two different entities in CDS: **Product** and **msdyn_sharedproductdetails**. While the first entity contains the definition of a product (unique identification for the product, product name and description), the second entity contains the fields stored at the product level in Finance and Operations. The combination of these two entities is used to define the product following the Stock Keeping Unit Concept (SKU). 
The representation of the product as an SKU also allows the concepts of distinct products, product masters and product variants from Finance and Operations to be captured in CDS in the following way:
- **Distinct products** (without variants) are products that are defined by themselves, they do not need any dimensions to be defined. For example, a specific book. For these, one record is created in the Product entity and one record in the msdyn_sharedproductdetails. No product family record is created.
- **Product masters** in Finance and Operations are used as generic products to hold the definition and rules to behave in business processes. Based on these definitions, distinct products known as product variants can be generated. For example, a t-shirt would be the product master that could have as dimensions color and size. Different variants could be released with the combination of these dimensions such a small blue t-shirt or a green medium t-shirt. In the integration one record will be created per variant in the product table. This record will contain the variant specific information, such as the different dimensions. [check that this has been done]. The generic information for the product (which in Finance and Operations is hold in the product master) will be kept in the msdyn_sharedproductdetails. Additionally, one product family record is created per product master. The product master information will be synchronized to CDS as soon as the released product master is created (even before variants are released).  

![data model for products](capture.png)

### CDS released distinct products to Product

The product entity contains the fields to define the product. Below the mapping are shown:

Source field | Map type | Destination field
---|---|---
PRODUCTNUMBER | > | productnumber
PRODUCTNAME | > | name
PRODUCTDESCRIPTION | > | description
ITEMNUMBER | >  | msdyn_itemnumber
CURRENCYCODE | > |  transactioncurrencyid.isocurrencycode
SALESUNITSYMBOL | > | msdyn_integrationdefaultuomname
SALESPRICE | > | price
UNITCOST | > | currentcost
[None] | >> | msdyn_integrationdefaultuomschedulename 
PRODUCTTYPE | >> | producttypecode
SALESUNITDECIMALPRECISION | >> | quantitydecimal

### Released products V2 to msdyn_sharedproductdetails

The msdyn_sharedproductdetails entity contains the fields from Finance and Operations that define the product and contain its financial and management information. The mappings are shown in the following table:

Source field | Map type | Destination field
---|---|---
PRODUCTNUMBER | > | msdyn_productnumber
INTRASTATCHARGEPERCENTAGE | > | msdyn_intrastatchargepercentage
ITEMNUMBER | >> | msdyn_itemnumber
APPROXIMATESALESTAXPERCENTAGE | > | msdyn_approximatesalestaxpercentage
ARRIVALHANDLINGTIME | > | msdyn_arrivalhandlingtime
BESTBEFOREPERIODDAYS | > | msdyn_bestbeforeperioddays
CARRYINGCOSTABCCODE | >> | msdyn_carryingcostabccode
CONSTANTSCRAPQUANTITY | > | msdyn_constantscrapquantity
COSTCHARGESQUANTITY | > | msdyn_costchargesquantity
DEFAULTRECEIVINGQUANTITY | > | msdyn_defaultreceivingquantity
FIXEDPURCHASEPRICECHARGES | > | msdyn_fixedpurchasepricecharges
FIXEDSALESPRICECHARGES | > | msdyn_fixedsalespricecharges
GROSSDEPTH | > | msdyn_grossdepth
GROSSPRODUCTHEIGHT | > | msdyn_grossproductheight
GROSSPRODUCTWIDTH | > | msdyn_grossproductwidth
INVENTORYUNITSYMBOL | > | msdyn_inventoryunitsymbol.name
ISDISCOUNTPOSREGISTRATIONPROHIBITED | >> | msdyn_isdiscountposregistrationprohibited
ISEXEMPTFROMAUTOMATICNOTIFICATIONANDCANCELLATION | >> | msdyn_exemptautomaticnotificationcancel
ISINSTALLMENTELIGIBLE | >> | msdyn_isinstallmenteligible
ISINTERCOMPANYPURCHASEUSAGEBLOCKED | >> | msdyn_isintercompanypurchaseusageblocked
ISINTERCOMPANYSALESUSAGEBLOCKED | >> | msdyn_isintercompanysalesusageblocked
ISMANUALDISCOUNTPOSREGISTRATIONPROHIBITED | >> | msdyn_ismanualdiscposregistrationprohibited
ISPHANTOM | >> | msdyn_isphantom
ISPOSREGISTRATIONBLOCKED | >> | msdyn_isposregistrationblocked
ISPOSREGISTRATIONQUANTITYNEGATIVE | >> | msdyn_isposregistrationquantitynegative
ISPURCHASEPRICEAUTOMATICALLYUPDATED | >> | msdyn_ispurchasepriceautomaticallyupdated
ISPURCHASEPRICEINCLUDINGCHARGES | >> | msdyn_ispurchasepriceincludingcharges
ISSALESWITHHOLDINGTAXCALCULATED | >> | msdyn_issaleswithholdingtaxcalculated
ISRESTRICTEDFORCOUPONS | >> | msdyn_isrestrictedforcoupons
ISSALESPRICEADJUSTMENTALLOWED | >> | msdyn_issalespriceadjustmentallowed
ISSALESPRICEINCLUDINGCHARGES | >> | msdyn_issalespriceincludingcharges
ISSCALEPRODUCT | >> | msdyn_isscaleproduct
ISSHIPALONEENABLED | >> | msdyn_isshipaloneenabled
ISUNITCOSTPRODUCTVARIANTSPECIFIC | >> | msdyn_isunitcostproductvariantspecific
ISVARIANTSHELFLABELSPRINTINGENABLED | >> | msdyn_isvariantshelflabelsprintingenabled
ISZEROPRICEPOSREGISTRATIONALLOWED | >> | msdyn_iszeropriceposregistrationallowed
KEYINPRICEREQUIREMENTSATPOSREGISTER | >> | msdyn_keyinpricerequirementsatposregister
KEYINQUANTITYREQUIREMENTSATPOSREGISTER | >> | msdyn_keyinquantityrequirementsatposregister
MARGINABCCODE | >> | msdyn_marginabccode
MAXIMUMPICKQUANTITY | > | msdyn_maximumpickquantity
MUSTKEYINCOMMENTATPOSREGISTER | >> | msdyn_mustkeyincommentatposregister
NECESSARYPRODUCTIONWORKINGTIMESCHEDULINGPROPERTYID | > | msdyn_necessaryproductionworkingtimeschedulingp
NETPRODUCTWEIGHT | > | msdyn_netproductweight
PACKINGDUTYQUANTITY | > | msdyn_packingdutyquantity
POSREGISTRATIONACTIVATIONDATE | > | msdyn_posregistrationactivationdate
POSREGISTRATIONBLOCKEDDATE | > | msdyn_posregistrationblockeddate
POSREGISTRATIONPLANNEDBLOCKEDDATE | > | msdyn_posregistrationplannedblockeddate
POTENCYBASEATTIBUTETARGETVALUE | > | msdyn_potencybaseattibutetargetvalue
POTENCYBASEATTRIBUTEVALUEENTRYEVENT | >> | msdyn_potencybaseattributevalueentryevent
PRODUCTTYPE | >> | msdyn_producttype
PRODUCTIONCONSUMPTIONDENSITYCONVERSIONFACTOR | > | msdyn_productionconsumptiondensityconversion
PRODUCTIONCONSUMPTIONDEPTHCONVERSIONFACTOR | > | msdyn_productionconsumptiondepthconversion
PRODUCTIONCONSUMPTIONHEIGHTCONVERSIONFACTOR | > | msdyn_productionconsumptionheightconversion
PRODUCTIONCONSUMPTIONWIDTHCONVERSIONFACTOR | > | msdyn_productionconsumptionwidthconversion
PRODUCTVOLUME | > | msdyn_productvolume
PURCHASECHARGESQUANTITY | > | msdyn_purchasechargesquantity
PURCHASEOVERDELIVERYPERCENTAGE | > | msdyn_purchaseoverdeliverypercentage
PURCHASEPRICE | > | msdyn_purchaseprice
PURCHASEPRICEDATE | > | msdyn_purchasepricedate
PURCHASEPRICINGPRECISION | > | msdyn_purchasepricingprecision
PURCHASEUNDERDELIVERYPERCENTAGE | > | msdyn_purchaseunderdeliverypercentage
RAWMATERIALPICKINGPRINCIPLE | >> | msdyn_rawmaterialpickingprinciple
SALESCHARGESQUANTITY | > | msdyn_saleschargesquantity
SALESOVERDELIVERYPERCENTAGE | > | msdyn_salesoverdeliverypercentage
SALESPRICE | > | msdyn_salesprice
SALESPRICECALCULATIONCHARGESPERCENTAGE | > | msdyn_salespricecalculationchargespercentage
SALESPRICECALCULATIONCONTRIBUTIONRATIO | > | msdyn_salespricecalculationcontributionratio
SALESPRICECALCULATIONMODEL | >> | msdyn_salespricecalculationmodel
SALESPRICEDATE | > | msdyn_salespricedate
SALESPRICINGPRECISION | > | msdyn_salespricingprecision
SALESUNDERDELIVERYPERCENTAGE | > | msdyn_salesunderdeliverypercentage
SALESUNITSYMBOL | > | msdyn_salesunitsymbol.name
SCALEINDICATOR | >> | msdyn_scaleindicator
SELLSTARTDATE | > | msdyn_sellstartdate
SHELFADVICEPERIODDAYS | > | msdyn_shelfadviceperioddays
SHELFLIFEPERIODDAYS | > | msdyn_shelflifeperioddays
SHIPSTARTDATE | > | msdyn_shipstartdate
TAREPRODUCTWEIGHT | > | msdyn_tareproductweight
TRANSFERORDEROVERDELIVERYPERCENTAGE | > | msdyn_transferorderoverdeliverypercentage
TRANSFERORDERUNDERDELIVERYPERCENTAGE | > | msdyn_transferorderunderdeliverypercentage
UNITCOST | > | msdyn_unitcost
UNITCOSTDATE | > | msdyn_unitcostdate
UNITCOSTQUANTITY | > | msdyn_unitcostquantity
VARIABLESCRAPPERCENTAGE | > | msdyn_variablescrappercentage
WAREHOUSEMOBILEDEVICEDESCRIPTIONLINE1 | > | msdyn_warehousemobiledevicedescriptionline1
WAREHOUSEMOBILEDEVICEDESCRIPTIONLINE2 | > | msdyn_warehousemobiledevicedescriptionline2
WILLINVENTORYISSUEAUTOMATICALLYREPORTASFINISHED | >> | msdyn_willinventoryissueautoreportasfinished
WILLINVENTORYRECEIPTIGNOREFLUSHINGPRINCIPLE | >> | msdyn_willinventoryreceiptignoreflushing
WILLPICKINGWORKBENCHAPPLYBOXINGLOGIC | >> | msdyn_willpickingworkbenchapplyboxinglogic
WILLTOTALPURCHASEDISCOUNTCALCULATIONINCLUDEPRODUCT | >> | msdyn_willtotalpurchdiscountcalcincludeproduct
WILLTOTALSALESDISCOUNTCALCULATIONINCLUDEPRODUCT | >> | msdyn_willtotalsalesdiscountcalcincludeproduct
WILLWORKCENTERPICKINGALLOWNEGATIVEINVENTORY | >> | msdyn_willworkcenterpickingallownegativeinvent
YIELDPERCENTAGE | > | msdyn_yieldpercentage
ISUNITCOSTAUTOMATICALLYUPDATED | >> | msdyn_isunitcostautomaticallyupdated
PURCHASEUNITSYMBOL | > | msdyn_purchaseunitsymbol.name
PURCHASEPRICEQUANTITY | > | msdyn_purchasepricequantity
ISUNITCOSTINCLUDINGCHARGES | >> | msdyn_isunitcostincludingcharges
FIXEDCOSTCHARGES | >> | msdyn_fixedcostcharges
MINIMUMCATCHWEIGHTQUANTITY | >> | msdyn_minimumcatchweightquantity
MAXIMUMCATCHWEIGHTQUANTITY | >> | msdyn_maximumcatchweightquantity
ALTERNATIVEITEMNUMBER | >> | msdyn_alternativeitemnumber.msdyn_itemnumber
BOMUNITSYMBOL | >> | msdyn_bomunitsymbol.name
CATCHWEIGHTUNITSYMBOL | >> | msdyn_catchweightunitsymbol.name
COMPARISONPRICEBASEUNITSYMBOL | >> | msdyn_comparisonpricebaseunitsymbol.name
PRIMARYVENDORACCOUNTNUMBER | >> | msdyn_vendorid.msdyn_vendoraccountnumber
ISCATCHWEIGHTPRODUCT | >> | msdyn_iscatchweight
PRODUCTDIMENSIONGROUPNAME | >> | msdyn_productdimensiongroupid.msdyn_groupname


## Product dimensions and product dimension group

Product dimensions are characteristics that serve to identify a product variant. The four product dimensions - **Color**, **Size**, **Style** and **Configuration** - are also mapped to CDS to define the product variant. 

### Colors

All the available colors present in Finance and Operations are available in CDS thanks to the following mappings:

Source field | Map type | Destination field
---|---|---
COLORID | >> | msdyn_name
COLORID | >> | msdyn_productcolorname

### Sizes

All the possible sizes in Finance and Operations are available in CDS using the mappings:

Source field | Map type | Destination field
---|---|---
SIZEID | >> | msdyn_productsize
SIZEID | >> | msdyn_name

### Styles

All the possible styles in Finance and Operations are available in CDS using the mappings:

Source field | Map type | Destination field
---|---|---
STYLEID | >> | msdyn_productstyle
STYLEID | >> | msdyn_name

### Configurations

All the possible configurations in Finance and Operations are available in CDS using the mappings:

Source field | Map type | Destination field
---|---|---
CONFIGURATIONID | >> | msdyn_name
CONFIGURATIONID | >> | msdyn_productconfiguration
CONFIGURATIONID | >> | msdyn_name
CONFIGURATIONID | >> | msdyn_productconfiguration


## Product number identified barcode

To uniquely identify products the product barcodes are used. These product barcodes will be available in CDS using the following mappings:

Source field | Map type | Destination field
---|---|---
PRODUCTNUMBER | > | msdyn_productnumberid.productnumber
BARCODE | > | msdyn_name
BARCODE | > | msdyn_barcode
PRODUCTQUANTITY | > | msdyn_productquantity
PRODUCTDESCRIPTION | > | msdyn_productdescription
BARCODESETUPID | > | msdyn_barcodesetupid
PRODUCTQUANTITYUNITSYMBOL | > | msdyn_unitofmeasureid.name
ISDEFAULTSCANNEDBARCODE | >> | msdyn_isdefaultscannedbarcode
ISDEFAULTPRINTEDBARCODE | >> | msdyn_isdefaultprintedbarcode
ISDEFAULTDISPLAYEDBARCODE | >> | msdyn_isdefaultdisplayedbarcode
