--- 
# required metadata 
 
title: Create a product configuration model
description: This procedure shows how to create a product configuration model and enter basic information such as attributes and subcomponents. 
author: t-benebo
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, EcoResProductVariantMaintainWorkspace, PCProductConfigurationModelListPage, PCCreateProductConfigurationModel, PCProductConfigurationModelDetails, PCBOMLineDetails   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a product configuration model

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a product configuration model and enter basic information such as attributes and subcomponents. The demo data company used to create this procedure is USMF.


## Create a product model

1. Go to **Product information management \> Products \> Product configuration models**.
1. Select **New**.
1. In the **Name** field, type a value.
1. In the **Description** field, type a value.
1. In the **Solver strategy** field, select an option.
    * The solver strategy determines how the constraints in a constraint-based product configuration model are processed. This selection can have an impact on the performance of the product configuration model.  
1. In the **Name** field, type a value.
    * The root component represents the product configuration model, but it can also be used in other product models.  
1. Select **OK**.
1. In the **Reuse configurations** field, select an option.
    * If the reuse configurations parameter is set to Yes, the system will check for identical configurations after each configuration session and reuse if an exact match is found.  

## Add attributes

1. Expand the **Attributes** section.
2. Select **Add**.
3. In the list, mark the selected row.
4. In the **Name** field, type a value.
5. In the **Solver name** field, type a value.
    * The solver name is used by the constraint solver of the product configurator. It must not include spaces or special characters except _ (underscore).  
6. In the **Description** field, type a value.
    * The description text is displayed to the configuration user and can therefore serve as help in selecting the right attribute value.  
7. In the **Attribute type** field, enter or select a value.
    * The attribute type determines which values are available for the attribute.  
8. Select the **Include in reuse** check box.
    * This option is only available when the Reuse configurations option is selected. Including the attribute in the reuse check box means that this attribute will be considered when the system is looking for an exact match.  

## Add subcomponents

1. Expand the **Subcomponents** section.
2. Select **Add**.
3. In the list, mark the selected row.
4. In the **Name** field, type a value.
5. In the **Solver name** field, type a value.
6. In the **Description** field, type a value.
7. In the **Component** field, enter or select a value.
    * Each subcomponent must reference a component definition. This design supports reusable components and ensures that once a component has been defined it can be used in many product models.  
8. Select **Save**.
9. Select **BOM line details**.
    * The BOM line details form enables the user to select the required properties for the subcomponent. Each property can be given a fixed value or mapped to an attribute. Mapping to an attribute will result in the BOM line property getting different values depending on the configuration selection.  
10. In the **Item number** field, enter or select a value.
    * Each subcomponent represents a configurable product master with constraint-based configuration technology. The reference is made through the item number.  
11. Select the **Set** check box.
12. Select **Yes** in the **Calculation** field.
    * Setting the calculation option ensures that the product will be included when running a cost calculation for the product.  
13. Select the **Setup** tab.
14. Select the **Set** check box.
15. In the **Quantity** field, enter a number.
    * The quantity field determines how much of this product will be consumed in the configured product.  
16. Select the **Set** check box.
17. In the **Per series** field, enter a number.
18. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]