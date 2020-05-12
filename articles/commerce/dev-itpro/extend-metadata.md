---
# required metadata

title: Extend the default Cloud Scale Unit metadata controller
description: This article provides code to extend the CommerceModelFactory class.
author: kfend
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 31641
ms.assetid: 6e25b63e-be1e-42fc-b1bd-c91585cd624d
ms.search.region: Global
# ms.search.industry: 
ms.author: meeram
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Extend the default Cloud Scale Unit metadata controller

[!include [banner](../includes/banner.md)]

This article provides code to extend the CommerceModelFactory class.

When you use OData together with Microsoft Dynamics 365 Commerce, metadata defines the contract between a client and server. The metadata exposes entity definitions and action definitions, so that when you make a change on the server side, you can use a tool on the client side to generate proxy code. Therefore, the maintenance effort for developers is reduced. To consume new or changed entities and actions, you must extend the metadata. 

Commerce Scale Unit has a default metadata controller that is named **CommerceModelFactory**. To extend the default controller, you create a new class that uses the **Export** attribute together with the **IEdmModelFactory** interface. You can then add and override existing code. For example, you can add new entity sets, new actions, new complex types, or new exception types. In the following example, the **ExtendedEdmModelFactory** class extends the **CommerceModelFactory** metadata controller and creates a new action that is named **NewAction** and a new entity set that is named **NewEntities**. You can find the sample code from this topic in the Retail software development kit (SDK).

```xpp
namespace Microsoft.Dynamics.RetailServer.Samples.Extensions
{
    using System.ComponentModel.Composition;
    using Microsoft.Dynamics.Retail.StoreServerServiceLibrary;
    [Export(typeof(IEdmModelFactory))]
    public class ExtendedEdmModelFactory : CommerceModelFactory
    {
        protected override void BuildNonBindableActions()
        {
            base.BuildNonBindableActions();
            var NewAction = BindAction("NewAction");
            NewAction.Returns<string>();
        }
        protected override void BuildEntitySets()
        {
            base.BuildEntitySets();
            BuildEntitySet<NewEntity>("NewEntities");
        }
    }
}
```


