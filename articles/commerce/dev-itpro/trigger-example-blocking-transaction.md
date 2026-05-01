---
title: Block transactions by using triggers
description: Learn how you can use a trigger to block an invoice or credit transaction in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 02/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.assetid: 605f5986-f84f-4b18-b94e-b0912cb367a1
ms.custom: 
  - bap-template
---

# Block transactions by using triggers

[!include [banner](../includes/banner.md)]

This article explains how you can use a trigger to block an invoice or credit transaction in Microsoft Dynamics 365 Commerce.

To block an invoice or credit transaction, follow these steps:

1. Open Visual Studio as an administrator. Create a new Visual C\# Class Library (Portable) project and name it CRTTriggerExtension. If you get a message that the selection makes this project incompatible with Visual Studio 2010, select **OK**.
1. In Solution Explorer, rename default class1.cs to GetCustomersServiceRequestTrigger.cs.
1. Right-click the **Reference** node in the project and add the following references. The location of the references depends on the deployment topology.
    - Microsoft.Dynamics.Commerce.Runtime.Entities.dll
    - Microsoft.Dynamics.Commerce.Runtime.Framework.dll
    - Microsoft.Dynamics.Commerce.Runtime.Services.Messages.dll

1. Add the following **using** statement to the GetCustomersServiceRequestTrigger.cs file.

    ```typescript
    using Microsoft.Dynamics.Commerce.Runtime.Messages;
    using Microsoft.Dynamics.Commerce.Runtime.Services.Messages;
    using Microsoft.Dynamics.Commerce.Runtime;
    ```

1. Rename class1.cs in the code to GetCustomersServiceRequestTrigger and then add the IRequestTrigger interface declaration.

    ```typescript
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using Microsoft.Dynamics.Commerce.Runtime;
    using Microsoft.Dynamics.Commerce.Runtime.Services.Messages;
    using Microsoft.Dynamics.Commerce.Runtime.Messages;

    namespace CRTTriggerExtension
    public class GetCustomersServiceRequestTrigger : IRequestTrigger
    ```

1. Implement the IRequestTrigger interface trigger. Right-click the IRequestTrigger class, select **Quick Actions**, and then select **Implement Interface**. Visual Studio implements the interface. You can also place the cursor on IRequestTrigger, press **Ctrl+**, and select **Implement Interface**.
1. The empty interface members SupportedRequestTypes, OnExecuted, and OnExecuting methods are shown in the following code example.

    ```typescript
    public class GetCustomersServiceRequestTrigger : IRequestTrigger
    {
        public IEnumerable<Type> SupportedRequestTypes
        {
            get
            {
                throw new NotImplementedException();
            }
        }

        public void OnExecuted(Request request, Response response)
        {
            throw new NotImplementedException();
        }

        public void OnExecuting(Request request)
        {
            throw new NotImplementedException();
        } 
    }
    ```

1. Commerce Scale Unit uses the GetCustomersServiceRequest object to get the customer details from Commerce Runtime (CRT) and uses the GetCustomersServiceRequest object to add the customer to the transaction. Before adding the customer to the transaction, you need to check whether the customer is blocked. To check whether the customer is blocked, implement a post trigger for this request and check whether the customer is blocked. If the customer is blocked, throw the exception to the Store Commerce app.
1. In the SupportedRequestTypes method, tell the CRT that you're going to add the trigger for GetCustomersServiceRequest. The following code example shows how to add GetCustomersServiceRequest as a supported type.

    ```typescript
    public IEnumerable<Type> SupportedRequestTypes
    {
        get
        {
            return new[] { typeof(GetCustomersServiceRequest) };       
        }
    }
    ```

1. Check if the customer is blocked in the OnExecuted (post trigger) method with the following code.

     ```typescript
     public void OnExecuted(Request request, Response response)
     {
        if (response == null)
        {
        throw new ArgumentNullException("request");
        }

        var getCustomersServiceResponse = (GetCustomersServiceResponse)response;
        if(getCustomersServiceResponse.Customers.FirstOrDefault().Blocked == true)
        {
            string message = string.Format("Failed to add customer '{0}' to cart. Blocked customers are not allowed for transactions.",
                getCustomersServiceResponse.Customers.FirstOrDefault().AccountNumber);
            throw new CartValidationException(DataValidationErrors.Microsoft_Dynamics_Commerce_Runtime_CustomerAccountIsBlocked, message);
        }
     }
     ```

1. Finally, update the OnExecuting method with the following code.

     ```typescript
     public void OnExecuting(Request request) 
     {
        if (request == null)
        {
            throw new ArgumentNullException("request");
        }
     }
     ```
1. Select **Save**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
