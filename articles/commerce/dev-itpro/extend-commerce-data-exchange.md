---
title: Extend Commerce Data Exchange - Real-time Service
description: This article explains how you can extend Commerce Data Exchange - Real-time service by adding extension methods to the RetailTransactionServiceEx class.
author: josaw1
ms.date: 08/31/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.assetid: 72a63836-2908-45fa-b1a6-3b1c499a19a2
---

# Extend Commerce Data Exchange - Real-time Service

[!Include [banner](../includes/banner.md)]

This article explains how you can extend Commerce Data Exchange (CDX) - Real-time service by adding extension methods to the RetailTransactionServiceEx class. Real-time Service enables clients to interact with Commerce functionality in real time. Finance and Operation databases and classes can’t be accessed directly from Retail server. You should access them through the CDX class extension using the finance and operations and Commerce Runtime extension.

To extend Commerce Data Exchange - Real-time Service, you create a new method in the **RetailTransactionServiceEx** class. This method must meet the following criteria:

-   The method must be a public static method.
-   The return value must be a container that has a length of 2 or more. The first element must be a Boolean value that indicates whether the method call was successful, and a string value that you can use for a comment or error message. The other items in the container can be of any type, and they can even be nested containers.
-   The method parameters must be one of the following primitive types:
    -   Boolean
    -   date
    -   int
    -   int64
    -   str
    -   guid
    -   Real

## Create and call a new extension method
1. Start Microsoft Visual Studio.
2. On the **Dynamics 365** menu, select **Model management > Create model**.
3. In the **Create model** dialog box, enter the following details.
   -   **Model name** - Contoso
   -   **Model publisher** - Contoso
   -   **Layer** - USR (Select the relevant layer)
   -   **Version** - 1.0.0.0
   -   **Model display name** - Contoso

4. Select **Next**.
5. In the dialog box, select **Create new package \> Next**, select **Select referenced packages**, and then in the list select the **Application Suite** and **Application Platform** checkboxes.
6. Select **Next**.
7. Select **Finish**.
8. In the **New project** dialog box, enter **ContosoRetailTransactionServiceEx** as the project name.
9. Select **OK**.
10. Right-click the project and select **Add > New item**. In the **Add New Item** window, select **Class** and enter the name of the class as **ContosoRetailTransactionServiceSample**.

    To consume the CDX method in Commerce runtime (CRT) you must add the ExtensionOf attribute to your class, such as ExtensionOf(classStr(RetailTransactionServiceEx). This addition means that the class is extending from the RetailTransactionServiceEx.

11. In the code editor, add the following code. 

    ```X++
    [ExtensionOf(classStr(RetailTransactionServiceEx))]
    final class ContosoRetailTransactionServiceSample
    {
    }
    ``` 

12. Inside the class, add a new method to do your custom logic. This method is what you will call from CRT to do the custom logic.

    ```X++
    [ExtensionOf(classStr(RetailTransactionServiceEx))]
    final class ContosoRetailTransactionServiceSample_Extension
    {
        public static container SerialCheck(str _serialNum)
        {
            boolean success = false;
            str errorMessage;
            int fromLine;
            
            try
            {
                if (_serialNum)
                {
                     ttsbegin;
                   // check whether the serial number exists

                    // Add your custom logic

                    errorMessage = "Serial number found";
                    ttscommit;
                }
                else
                {
                    // Add your custom logic
                    success = false;
                    errorMessage = "Serial number not found";
                }
            }
            catch (Exception::Error)
            {
                ttsAbort;
                errorMessage = RetailTransactionServiceUtilities::getInfologMessages(fromLine);
            }

            // Return sanitized error code.
            errorMessage = RetailTransactionServiceUtilities::getErrorCode(errorMessage);

            return [success, errorMessage, "Custom values"];
        }
    }
    ```
13. In Solution Explorer, right-click the project, and then click **Build**.

After you've finished building your new extension methods, the project will be deployed.

## Call the new method from the CRT
1.  In your commerce runtime (CRT) extension, include the Microsoft.Dynamics.Commerce.Runtime.RealtimeServices.Messages nuget package, if it hasn't already been added.
2.  Use the following sample code to call the new method.

    ```C#
        
            InvokeExtensionMethodRealtimeRequest extensionRequest = new InvokeExtensionMethodRealtimeRequest("SerialCheck", "123");
            InvokeExtensionMethodRealtimeResponse response = await request.RequestContext.ExecuteAsync<InvokeExtensionMethodRealtimeResponse>   (extensionRequest).ConfigureAwait(false);
                ReadOnlyCollection<object> results = response.Result;
                
                string resValue = (string)results[0];       
    ```

3.  From the results object, you can read the response values from Real-time Service.
4.  The CRT framework code will check the success/failure state and provide an error message based on the values returned from the CDX methods. If required, the extension code can catch this and provide more logic.  

    > [!NOTE]
    > The **InvokeExtensionMethodRealtimeRequest** method takes two parameters. One parameter is the Real-time Service method name, and the other is the list of parameters that should be used. The method name that is passed should be the same as the method name that you created in the **ContosoRetailTransactionServiceSample** class.
    
 ```
  public InvokeExtensionMethodRealtimeRequest(string methodName, params object[] parameters)
            : base(methodName, parameters)
        {
        }
 ```

## CDX offline

When there is no connectivity to the HQ, client/Retail Server will not be able to call the CDX method. In this case, the extension code should follow the best practice mentioned below:

-   Check before calling the CDX method  to determine if CRT is connected to the online (Retail server) or the offline (local) database. This can be done both in POS and CRT.

### How to check the connection status

**POS**

Use the **GetConnectionStatusClientRequest** POS API.

**CRT**

```C#
if(request.RequestContext.Runtime.Configuration.IsMasterDatabaseConnectionString)
{ }
```

-   If the connection to the CDX method failed, an error message might display saying that the operation cannot be performed if there is no connectivity to HQ or that you need to have mitigation logic if this operation needs to work if there is no connectivity to the CDX method.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

