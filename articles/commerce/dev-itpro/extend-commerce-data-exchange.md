---
# required metadata

title: Extend Commerce Data Exchange - Real-time Service
description: This topic explains how you can extend Commerce Data Exchange - Real-time service by adding extension methods to the RetailTransactionServiceEx class.
author: mugunthanm
manager: AnnBe
ms.date: 07/16/2020
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
ms.custom: 68673
ms.assetid: 72a63836-2908-45fa-b1a6-3b1c499a19a2
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Extend Commerce Data Exchange - Real-time Service

[!include [banner](../includes/banner.md)]

This topic explains how you can extend Commerce Data Exchange (CDX) - Real-time service by adding extension methods to the RetailTransactionServiceEx class. Real-time Service enables clients to interact with Commerce functionality in real time.

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
2. On the **Dynamics 365** menu, click **Model management > Create model**.
3. In the **Create model** dialog box, enter the following details.
   -   **Model name** - Contoso
   -   **Model publisher** - Contoso
   -   **Layer** - USR (Select the relevant layer)
   -   **Version** - 1.0.0.0
   -   **Model display name** - Contoso

4. Click **Next**.
5. In the dialog box, select **Select existing package**, and then select **Application Suite** in the list.
6. Click **Next**.
7. Click **Finish**.
8. In the **New project** dialog box, enter **ContosoRetailTransactionServiceEx** as the project name.
9. Click **OK**.
10. Right-click the project and select **Add > New item**. In the **Add New Item** window, select **Class** and enter the name of the class as **ContosoRetailTransactionServiceSample**.

    To consume the CDX method in Commerce runtime (CRT) you must add the ExtensionOf attribute to your class, such as ExtensionOf(classStr(RetailTransactionServiceEx). This means that the class is extending from the RetailTransactionServiceEx.

11. In the code editor, add the following code. 

    ```C#
    [ExtensionOf(classStr(RetailTransactionServiceEx))]
    final class ContosoRetailTransactionServiceSample
    {
    }
    ``` 

12. Inside the class, add a new method to do your custom logic. This is the method that you will call from CRT to do the custom logic.

    ```C#
    [ExtensionOf(classStr(RetailTransactionServiceEx))]
    final class ContosoRetailTransactionServiceSample
    {
        public static container SerialCheck(str _serialNum)
        {
            boolean success = false;
            str errorMessage;
            int fromLine;

            ttsbegin;

            try
            {
                if (_serialNum)
                {
                    // check whether the serial number exists

                    // Add your custom logic

                    errorMessage = "Serial number found";
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
                error = RetailTransactionServiceUtilities::getInfologMessages(fromLine);
            }

            ttscommit;

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
                
                bool success = Convert.ToBoolean(results[0]);

                if (!success)
                {
                    string error = Convert.ToString(results[1]);
                    Console.WriteLine(error);
                    throw new CommerceException(error, "Failed to validate serial number.");
                }
       
    ```

3.  From the results object, you can read the response values from Real-time Service.

    > [!NOTE]
    > The **InvokeExtensionMethodRealtimeRequest** method takes two parameters. One parameter is the Real-time Service method name, and the other is the list of parameters that should be used. The method name that is passed should be the same as the method name that you created in the **ContosoRetailTransactionServiceSample** class.
    
 ```
  public InvokeExtensionMethodRealtimeRequest(string methodName, params object[] parameters)
            : base(methodName, parameters)
        {
        }
 ```


