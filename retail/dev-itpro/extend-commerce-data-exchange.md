---
# required metadata

title: Extend Commerce Data Exchange - Real-time Service
description: This article explains how you can extend Commerce Data Exchange -  Real-time service by adding extension methods to the RetailTransactionServiceEx class. Real-time Service enables retail clients to interact with retail functionality in real time.
author: josaw1
manager: AnnBe
ms.date: 2016-03-17 21 - 39 - 38
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 68673
ms.assetid: 72a63836-2908-45fa-b1a6-3b1c499a19a2
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Extend Commerce Data Exchange - Real-time Service

This article explains how you can extend Commerce Data Exchange -  Real-time service by adding extension methods to the RetailTransactionServiceEx class. Real-time Service enables retail clients to interact with retail functionality in real time.

To extend Commerce Data Exchange: Real-time Service, you create a new method in the **RetailTransactionServiceEx** class. This method must meet the following criteria:

-   The method must be a public static method.
-   The return value must be a container that has a length of 2 or more. The first two elements must be a Boolean value that indicates whether the method call was successful, and a string value that you can use for a comment or error message. The other items in the container can be of any type, and they can even be nested containers.
-   The method parameters must be one of the following primitive types:
    -   Boolean
    -   date
    -   int
    -   int64
    -   str
    -   guid
    -   Real

## Create and call a new extension method
1.  Start Microsoft Visual Studio.
2.  On the **Dynamics 365 **menu, click **Model management** &gt; **Create model**.
3.  In the **Create model** dialog box, enter the following details.
    -   **Model name**: Contoso
    -   **Model publisher**: Contoso
    -   **Layer**: USR (Select the relevant layer)
    -   **Version**: 1.0.0.0
    -   **Model display name**: Contoso

4.  Click **Next**.
5.  In the dialog, select **Select existing package**, and then select **Application Suite** in the list.
6.  Click **Next**.
7.  Click **Finish**.
8.  In the **New project** dialog box, enter **ContosoRetailTransactionServiceEx** as the project name.
9.  Click **OK**.
10. In Application Explorer, expand the **Code** node, and select **Classes**.
11. Right-click the **RetailTransactionServiceEx** class, and then click **Customize**.
12. In the code editor, add the following code.

        public static container SerialCheck(str _serialNum)
            {
                boolean             success = true;
                str                 errorMessage;
                container           serialNumResult;
                if (_serialNum)
                {
                // check whether the serial number exists
                    errorMessage = "Serial number found";
                }
                else
                {
                    success = false;
                    errorMessage = "Serial number not found";
                }

                return [success, errorMessage, "Serial number found"];
        }

13. In Solution Explorer, right-click the project, and then click **Build**.

After you've finished building your new extension methods, the project will be deployed.

## Call the new method from the CRT
1.  In your commerce runtime (CRT), add a reference to the Microsoft.Dynamics.Commerce.Runtime.TransactionService.dll, if it hasn't already been added.
2.  Use the following sample code to call the new method.

        TransactionServiceClient transactionService = new TransactionServiceClient(request.RequestContext);
        ReadOnlyCollection serviceResponse = transactionService.InvokeExtensionMethod("SerialCheck", "123");

3.  From the serviceResponse object, you can read the response values from Real-time Service.

**Note:** The **InvokeExtensionMethod** method takes two parameters. One parameter is the Real-time Service method name, and the other is the list of parameters that should be used. The method name that is passed should be the same as the method name that you created in the **RetailTransactionServiceEx** class.

