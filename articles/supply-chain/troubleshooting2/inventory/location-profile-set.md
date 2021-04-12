---
# required metadata

title: Location profile setting "Allow negative inventory" set to No is still allowing negative inventory in the On-hand Inventory form.
description: Location profile setting "Allow negative inventory" set to No is still allowing negative inventory in the On-hand Inventory form.
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSLocationProfile
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: shawan@microsoft.com

---

# Location profile setting "Allow negative inventory" set to No is still allowing negative inventory in the On-hand Inventory form.

KB Number: 4613622

The system needs to be able to go negative in order for government-regulated transactions to book losses. The plan was for the item to be able to go negative but only in designated locations such as tanks. A thorough test shows that if an item model group allows negative inventory then it does not matter if the location is set to allow negative.  If the item is set-up to not allow negative inventory then it doesn't matter how the location profile is set-up.


## Resolution
This works as expected. The 'Allow negative' from location profile is only working for warehouse processing such as picking process.  Item model group to allow negative inventory will impact all the issue process from inventory and warehouse module, and the allow negative physical inventory from model group won't be overridden by this setting from location profile. Customer can disable 'allow negative physical inventory' on item model group and enable 'allow negative physical inventory' from location profile.


