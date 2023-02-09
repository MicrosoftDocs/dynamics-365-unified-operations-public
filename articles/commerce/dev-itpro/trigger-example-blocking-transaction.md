---
title: Block transactions by using triggers
description: This article shows how you can use a trigger to block an invoice or credit transaction.
author: josaw1
ms.date: 02/03/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.custom: 65893
ms.assetid: 605f5986-f84f-4b18-b94e-b0912cb367a1
---

# Block transactions by using triggers

[!include [banner](../includes/banner.md)]

This article shows how you can use a trigger to block an invoice or credit transaction.

This article shows how you can block an invoice or credit transaction.

1.  Open Visual Studio as an administrator. Create a new Visual C\# Class Library (Portable) project and name it CRTTriggerExtension. If you get a message that the selection makes this project incompatible with Visual Studio 2010, click **OK**.
2.  In Solution Explorer, rename default class1.cs to GetCustomersServiceRequestTrigger.cs.
3.  Right-click the **Reference** node in the project and add the following references. The location of the references will depend on the deployment topology.
    -   Microsoft.Dynamics.Commerce.Runtime.Entities.dll
    -   Microsoft.Dynamics.Commerce.Runtime.Framework.dll
    -   Microsoft.Dynamics.Commerce.Runtime.Services.Messages.dll

4.  Add the following **using** statement to the GetCustomersServiceRequestTrigger.cs file.

    ```typescript
    using Microsoft.Dynamics.Commerce.Runtime.Messages;
    using Microsoft.Dynamics.Commerce.Runtime.Services.Messages;
    using Microsoft.Dynamics.Commerce.Runtime;
    ```

5.  Rename class1.cs in the code to GetCustomersServiceRequestTrigger and then add the IRequestTrigger interface declaration.

    ```typescript
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using Microsoft.Dynamics.Commerce.Runtime;
    using Microsoft.Dynamics.Commerce.Runtime.Services.Messages;
    using Microsoft.Dynamics.Commerce.Runtime.Messages;

    namespace CRTTriggerExtension
    public class GetCustomersServiceRequestTrigger : IRequestTrigger
    {
    ```

6.  Implement the IRequestTrigger interface trigger. Right-click the IRequestTrigger class, select **Quick Actions**, and then click **Implement Interface**. Visual Studio will implement the interface. You can also place the cursor on IRequestTrigger, press **Ctrl+**, and select **Implement Interface**.
7.  The empty interface members SupportedRequestTypes, OnExecuted, and OnExecuting methods are shown in the following code example.

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

8.  Commerce Scale Unit uses the GetCustomersServiceRequest object to get the customer details from Commerce Runtime (CRT) and uses the GetCustomersServiceRequest object to add the customer to the transaction. Before adding the customer to the transaction you need to check whether the customer is blocked. To do this, implement a post trigger for this request and check whether the customer is blocked. If the customer is blocked, then throw the exception to the Store Commerce app.
9.  In the SupportedRequestTypes method tell the CRT that you are going to add the trigger for GetCustomersServiceRequest. The following code example shows how to add GetCustomersServiceRequest as a supported type.

    ```typescript
    public IEnumerable<Type> SupportedRequestTypes
    {
        get
        {
            return new[] { typeof(GetCustomersServiceRequest) };       
        }
    }
    ```

10. Check if the customer is blocked in the OnExecuted (post trigger) method with the following code.

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

11. Finally, update the OnExecuting method with the following code.

     ```typescript
     public void OnExecuting(Request request) 
     {
        if (request == null)
        {
            throw new ArgumentNullException("request");
        }
     }
     ```
12. Click **Save**.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
