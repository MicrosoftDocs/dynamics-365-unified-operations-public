---
# required metadata

title: Show custom notifications in POS
description: This topic explains how to add custom notifications in Point of Sale (POS).
author: mugunthanm
manager: AnnBe
ms.date: 09/17/2019
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
ms.custom: 28021
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2019-09-2019
ms.dyn365.ops.version: AX 10.0.5

---

# Show custom notifications in POS

[!include [banner](../includes/banner.md)]

This topic explains how to add custom notifications in POS. This topic applies to Dynamics 365 for Finance and Operations and Dynamics 365 for Retail 7.3 and higher versions with latest binary fix.

You can extend POS notification framework for these scenarios: 

- Show a custom notifications so that a store associate can perform a required actions based on that notifications or perform any custom logic. 
- Perform some operation periodically in the background. However, this is not recommend because it might cause performance issues.

## How it works

The notification framework in POS runs periodically for the configured operation in Headquarters (the frequency is configurable) and calls the notification service in commerce runtime (CRT) and Real time service in Headquarters. When POS makes the call to the notification service in CRT, CRT runs the business logic and checks if there is any notification to be sent to POS for that particular operation. The operation ID is passed as a parameter to the request and the CRT notification service checks the operation ID and returns the notification details. 

If the notification exists, then the CRT returns the response to POS reporting that there is a notification available. POS parses this notification and shows it in the UI. When the POS user clicks the notification, the relevant operation in POS is executed. Notifications are tied to an operation and inside the operation handler write the business logic to be performed.

When the CRT returns the response for the notification, it returns the number of notifications, messages, and action parameters. The POS framework has built-in logic to parse the response to get the POS operation ID and call it when the user clicks the notification. 

You can write custom logic inside the operation on what should happen when the POS user clicks the notification. Additional parameters from CRT to POS can be sent using the action property, and will be available inside the operation request in POS.

### Example
To notify the POS user to prepare orders for pickup, inside CRT check if there an order for pickup. If so, update the notification response with relevant parameter. POS will parse the response and show the notification. When the POS user clicks the notification, POS calls the operation with the parameter from the notification (it’s up to the extension logic whether to send parameters or not) and inside the operation read all the pending orders for pickup and show it in the UI for the POS user to take further action.

## Steps required to enable notification for custom operation

1. Create a new operation in Headquarters under **Retail and Commerce > Channel Setup > POS Setup > POS > POS operations**.

    > [!NOTE]
    > Use an operation ID greater than 5000 for custom operation.
    
2. Extend the notification service.  When the scheduler for the notification service runs, it calls both the CRT and Real time transaction service extension code to get the notification message.

3.  Extend POS. In POS, write the logic inside the POS operation for what should happen when the user clicks the notification. For instructions on how to create a new POS operation, see [Add POS operations to POS layouts by using Button grid designer](add-pos-operations.md).

4. Configure the notification service in Headquarters with the custom operation. When the scheduler runs it, includes the custom operation. For instructions on to configure notification in POS, see [Add POS operations to POS layouts by using Button grid designer](../notifications-pos.md).

    When the POS user clicks the notification, the framework calls the right operation based on the response returned form the CRT. The notification service runs for all the notifications configured in Headquarters and returns the response with the operation id and notification details. So, POS will have the context of operation ID and the framework will use this to call your operation implementation.

> [!NOTE] 
> The notification scheduler checks both CRT and Headquarters to check if there are any new notifications. Depending on the scenario, extend the real time transaction service in Headquarters or only CRT. Scenarios where real-time processing is required for the notification then extend the Real-time transaction service method in Headquarters if real-time processing is not required the extend only CRT.

## Extend the notification service in CRT

To extend the notification service in CRT override the **GetNotificationsExtensionServiceRequest** and return the **GetNotificationsExtensionServiceResponse**.

There is a sample in the Retail SDK on how to extend the notification service (**RetailSDK\SampleExtensions\CommerceRuntime\Extensions.NotificationSample**).
+ **GetNotificationsExtensionServiceRequest**: Contains the operation ID, staff and channel. Based on the Retail Headquarters configuration, POS runs the notification scheduler for each configured operation.
+ **GetNotificationsExtensionServiceResponse**: In the response return the notification detail entity (**NotificationDetailCollection**), update the **GetNotificationsExtensionServiceResponse** and return all the notifications. Because it is a collection, multiple notifications can be returned.

## Notification details entity contains the below property

| Property name          | Data type      | Description                                                                 |
|------------------------|----------------|---------------------------------------------------------------------------------|
| ActionProperty         | string         | Custom property to send to POS operation.                                       |
| DisplayText            | string         | Notification display text.                                                       |
| IsLiveContentOnly      | bool           | Indicator whether the notification is only for live content.                    |
| IsNew                  | bool           | Indicator whether the notification is new or not.                                |
| IsSuccess              | bool           | Indicator whether the notification was success or not.                           |
| ItemCount              | long           | Number of notification.                                                          |
| LastUpdatedDateTime    | DateTimeOffset | The last updated date time of the item in the action property.                   |
| LastUpdatedDateTimeStr | string         | The last updated date time of the item in the action property in string format. |

## Detailed steps

1. Open **Runtime.Extensions.NotificationSample.proj** from the Retail SDK (**RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.NotificationSample**).
2. Rename the project according to standard naming convention.
3. Inside the project there is a class file called **NotificationExtensionService.cs**. Open the file.
4. **GetNotificationsExtensionServiceRequest** class is overridden to add custom notification. Override the **GetNotificationsExtensionServiceRequest** and return the **GetNotificationsExtensionServiceResponse**.
5. Either create a new class and override the **GetNotificationsExtensionServiceRequest** or use the sample template. The following steps assume that the template is used:
6. In the **NotificationExtensionService** class, there is a method names **Process**. Inside the method the code checks the operation ID and based on the operation ID it creates notification details object and adds any notifications. Check if it's custom operation ID and then write logic to check is there are any notification. If so, then create a notification object with the details and return it with the response. Then POS will parse the response and show the notification.
    > [!NOTE]
    > Remove the sample implementation inside the process method and just keep the custom logic.

    ```csharp
    namespace Contoso
    {
        namespace Commerce.Runtime.NotificationSample
        {
            using System;
            using Microsoft.Dynamics.Commerce.Runtime;
            using Microsoft.Dynamics.Commerce.Runtime.DataModel;
            using Microsoft.Dynamics.Commerce.Runtime.Services.Messages;
            /// <summary>
            /// Service class responsible executing the service requests.
            /// </summary>
            public class NotificationExtensionService : SingleRequestHandler<GetNotificationsExtensionServiceRequest, GetNotificationsExtensionServiceResponse>
            {
                /// <summary>
                /// The handler for the <c>GetNotificationsExtensionServiceRequest</c> request.
                /// </summary>
                /// <param name="request">The request with the operation.</param>
                /// <returns>The notification details for the operation.</returns>
                protected override GetNotificationsExtensionServiceResponse Process(GetNotificationsExtensionServiceRequest request)
                {
                    ThrowIf.Null(request, "request");
                    NotificationDetailCollection details = new NotificationDetailCollection();
                    DateTimeOffset lastNotificationDateTime = DateTimeOffset.Now;
                    string myOperationId = "5000";
                    // do the actual work here
                    if ((request.SubscribedOperation).ToString() == myOperationId)
                    {
                        NotificationDetail detail = new NotificationDetail()
                        {
                        // Text which will display for the notification detail in the POS notification center
                        DisplayText = "Custom notification",
                        // Number of notifications found
                        ItemCount = 1,
                        // Timestamp of creation of latest notification item (Used to determine whether notification is new)
                        LastUpdatedDateTime = lastNotificationDateTime,
                        // Boolean value representing whether the attempt to get notifications for the given operation was successful
                        IsSuccess = true,
                        // If you would like POS to navigate to a specific action property for the given operation
                        // when the notification tile is clicked, define the action property as well.
                        ActionProperty = "1"
                        };
                    details.Add(detail);
                    }
                    var serviceResponse = new GetNotificationsExtensionServiceResponse(details);
                    return serviceResponse;
                }
            }
        }
    }
    ```
7. Once done with the changes build the project and drop the output library in **\RetailServer\webroot\bin\Ext**.
8. Register the output library in **CommerceRuntime.Ext.config**.
9. Create a new operation in POS with the same operation ID used in the CRT extension. In this example, it is **5000**. Use any operation ID greater than 5000.
    When the user clicks the notification tile, the POS framework calls the operation handler for the operation id used. Inside the handler, add required logic for what should happen when the POS user clicks the notification. For instructions on how to create a POS  operation request, response, and handler, see [Show order notifications in the point of sale (POS)](add-POS-operations.md).
    > [!NOTE]
    > The action property in the Notification detail entity will be sent to the POS operation request, use that action property to pass any custom information from the notification service to POS.
10. Configure the notification scheduler according to the instructions in [Show order notifications in the point of sale (POS)](../notifications-pos.md).

## Validate the customization

1. Launch the extended Cloud POS or Modern POS.
2. POS triggers the notification service based on your notification scheduler configuration.
3. Debug the CRT code by attaching the CRT project to w3wp.exe. The breakpoint should hit whenever the notification service is called from POS.
4. When the notification received in POS, click the notification. It should call the POS operation handler and execute the custom logic written inside the handler.
