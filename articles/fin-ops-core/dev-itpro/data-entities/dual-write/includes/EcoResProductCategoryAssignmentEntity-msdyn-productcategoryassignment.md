## Product category assignments to msdyn_productcategoryassignments

This template synchronizes data between Finance and Operations apps and Dataverse.

Finance and Operations field | Map type | Customer engagement field | Default value
---|---|---|---
PRODUCTNUMBER | = | msdyn_globalproduct.msdyn_productnumber | 
PRODUCTCATEGORYNAME | = | msdyn_productcategory.msdyn_name | 
PRODUCTCATEGORYHIERARCHYNAME | = | msdyn_productcategory.msdyn_hierarchy.msdyn_name | 
PRODUCTNUMBER | >> | msdyn_name | 
