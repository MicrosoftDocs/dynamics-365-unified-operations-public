---
# required metadata

title: Extensible EDTs
description: This article extensible EDTs.
author: mfp
manager: AnnBe
ms.date: 09/09/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 


# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfp
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---

# Extended data types

Extended Data Types have a rich extension model, giving extenders control to change certain behavior.  

To provide an extensible solution keep this in mind: 

| Property | Considerations|
|---------|----------|
|Label / Help text|These properties can be changed by an extension. Naturally only one value can win.  The assumption is that if multiple solutions would change the label of the same extended data type, then they would be functionally mutual exclusive, i.e. no one would install both on the same system.
|String size|This can only be defined on root extended data types.  The system will use the largest value defined across the extended data type and its extensions.
String size cannot be changed by an extension for derived extended data types, as it would break the IS-A relationship between the extended data types. 
Assignments to string extended data types will truncate the string to match the defined string size.|
|Extends|This property cannot be changed by an extension; and changing it after released is a breaking change; hence ensure it is set correctly initially. 
By setting this property, you forfeit the ability to change string size in the future - both by you and extenders.
Avoid unnecessary dependencies, like extending generic extended data types, like Name and Description.|
|No Of Decimals is Extensible [sic]|This property cannot be changed by an extension.
Setting this to True will allow extenders to change the number of decimals. 
While setting this to True, you must guarantee that:
+ All truncation logic would honor the number of decimals specified on the Extended Data Type .i.e. no implicit or hard coded rounding would occur.
+ The value is not assigned to other incompatible extended data types without proper handling of rounding.|
