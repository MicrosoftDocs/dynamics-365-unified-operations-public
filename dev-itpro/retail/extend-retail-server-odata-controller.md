---
# required metadata

title: Extend a Retail Server OData controller | Microsoft Docs
description: This article provides code that extends the CustomController class.
author: kfend
manager: AnnBe
ms.date: 2016-02-06 00:48:15
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
ms.custom: 31681
ms.assetid: ec5eac0c-97aa-4702-8ebf-28f12e7775e7
ms.region: Global
# ms.industry: 
ms.author: meeram

---

# Extend a Retail Server OData controller

This article provides code that extends the CustomController class.

A controller is a mapping for a commerce entity that controls create, read, update, and delete (CRUD) behaviors and actions for a commerce entity type. Each commerce entity must have a corresponding controller. You can extend a controller that is included with Microsoft Dynamics AX to add new business actions that meet your business requirement. To extend an existing controller, you must define a new class that extends an existing controller class. In the new class, you use the **ExtendedController** attribute to indicate that the new class extends an existing controller, and to indicate which controller the new class extends. In this example, the new class extends the controller for the **Customer** entity type. Each entity type is associated with only one controller. When you create a new controller that overrides an existing controller, the new controller that has the **ExtendedController** attribute is used instead of the original controller. In the following example, the **ExtendedCustomersController** class extends the **CustomersController** class, and takes the entity type and the key field of the **Customer** entity type as parameters. You can find the sample code from this topic in the Retail software development kit (SDK).

    namespace Microsoft.Dynamics.RetailServer.ExtensionSamples
    {
        using System;
        using System.Collections.Generic;
        using System.Linq;
        using System.Runtime.InteropServices;
        using Microsoft.Dynamics.Commerce.Runtime.DataModel;
        using Microsoft.Dynamics.Retail.StoreServerServiceLibrary;
        using Microsoft.Dynamics.Retail.StoreServerServiceLibrary.ODataControllers;
        [ExtendedController("Customers")]
        [ComVisible(false)]
        public class ExtendedCustomersController : CustomersController
        {
            public override IQueryable<Customer> Get()
            {
                List<Customer> customers = new List<Customer>();
                for (int i = 0; i < 10; i++)
                {
                    var customer = new Customer();
                    customer.AccountNumber = "customer" + i;
                    customer.Name = "Name" + i;
                    customers.Add(customer);
                }
                return customers.AsQueryable();
            }
        }
    }

