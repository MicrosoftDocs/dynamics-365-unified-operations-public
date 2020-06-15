## Product categories to msdyn_productcategories

This template synchronizes data between Finance and Operations apps and Common Data Service.

Finance and Operations field | Map type | Other Dynamics 365 field | Default value
---|---|---|---
PRODUCTCATEGORYHIERARCHYNAME | = | msdyn_hierarchy.msdyn_name | 
ISCATEGORYINHERITINGPARENTPRODUCTATTRIBUTES | >< | msdyn_isinheritingparentproductattributes | 
PROJECTCATEGORYNAME | = | msdyn_projectcategoryname | 
ISTANGIBLEPRODUCT | >< | msdyn_istangibleproduct | 
ISCATEGORYINHERITINGPARENTCATEGORYATTRIBUTES | >< | msdyn_isinheritingparentcategoryattributes | 
CATEGORYCODE | = | msdyn_code | 
CATEGORYDESCRIPTION | = | msdyn_description | 
CATEGORYKEYWORDS | = | msdyn_keywords | 
CATEGORYNAME | = | msdyn_name | 
FRIENDLYCATEGORYNAME | = | msdyn_friendlycategoryname | 
PARENTPRODUCTCATEGORYNAME | = | msdyn_parentproductcategory.msdyn_name | 
PRODUCTCATEGORYHIERARCHYNAME | >> | msdyn_parentproductcategory.msdyn_hierarchy.msdyn_name | 
