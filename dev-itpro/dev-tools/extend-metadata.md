---
# required metadata

title: Extend the metadata | Microsoft Docs
description: This article provides code to extend the CommerceModelFactory class.
author: kfend
manager: AnnBe
ms.date: 2016-02-06 00:46:00
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 31641
ms.assetid: c2734f79-aa93-40b2-a500-a687ca3d9607
ms.region: Global
# ms.industry: 
ms.author: meeram

---

# Extend the metadata

This article provides code to extend the CommerceModelFactory class.

When you use OData together with Microsoft Dynamics AX for Retail, metadata defines the contract between a client and server. The metadata exposes entity definitions and action definitions, so that when you make a change on the server side, you can use a tool on the client side to generate proxy code. Therefore, the maintenance effort for developers is reduced. To consume new or changed entities and actions, you must extend the metadata. Retail Server has a default metadata controller that is named **CommerceModelFactory**. To extend the default controller, you create a new class that uses the **Export** attribute together with the **IEdmModelFactory** interface. You can then add and override existing code. For example, you can add new entity sets, new actions, new complex types, or new exception types. In the following example, the **ExtendedEdmModelFactory** class extends the **CommerceModelFactory** metadata controller and creates a new action that is named **NewAction** and a new entity set that is named **NewEntities**. You can find the sample code from this topic in the Retail software development kit (SDK).

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

