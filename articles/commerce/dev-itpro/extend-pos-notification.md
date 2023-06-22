---
title: Show custom notifications in the POS
description: This article explains how to add custom notifications in the point of sale (POS).
author: josaw1
ms.date: 02/01/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2019-09-2019
ms.dyn365.ops.version: AX 10.0.5
ms.assetid: 
---

# Show custom notifications in the POS

[!include [banner](../includes/banner.md)]

This article explains how to add custom notifications in the point of sale (POS). This article applies to Microsoft Dynamics 365 Finance, Enterprise edition 7.3 and Dynamics 365 for Retail 7.3, and later versions that have the latest binary fix.

You can extend the POS notification framework for these scenarios:

- Show a custom notification so that a store associate can either perform a required action, based on that notification, or perform custom logic.
- Periodically perform some operation in the background. However, this scenario isn't recommended, because it might cause performance issues.

## How custom notifications work

The notification framework in the POS periodically runs for the configured operation in Retail headquarters. (The frequency of the periodic runs can be configured.) It calls the notification service in the Commerce runtime (CRT) and Real time service in Retail headquarters. When the POS makes the call to the notification service in CRT, CRT runs the business logic and determines whether any notification must be sent to the POS for the operation. The operation ID is passed to the request as a parameter. The CRT notification service checks the operation ID and returns the notification details.

If the notification exists, CRT returns the response to the POS and reports that a notification is available. POS parses this notification and shows it in the user interface (UI). When the POS user selects the notification, the relevant operation in POS is run. Notifications are linked to an operation. Inside the operation handler, you write the business logic that must be performed.

When CRT returns the response for the notification, it returns the number of notifications, messages, and action parameters. The POS framework has built-in logic to parse the response to get the POS operation ID and call it when the user selects the notification.

Inside the operation, you can write custom logic to specify what should happen when the POS user selects the notification. Additional parameters can be sent from CRT to the POS by using the action property. Those parameters will then be available inside the operation request in the POS.

### Example

To notify the POS user to prepare orders for pickup, inside CRT, check whether there is an order for pickup. If there is, update the notification response with the relevant parameters. The POS parses the response and shows the notification. When the POS user selects the notification, the POS calls the operation by using the parameter from the notification. (The extension logic determines whether parameters should be sent.) Inside the operation, the POS reads all the pending orders for pickup and shows the orders in the UI so that the POS user can take further action.

## Required steps to make notifications available for a custom operation

1. In Retail headquarters, go to **Retail and Commerce \> Channel Setup \> POS Setup \> POS \> POS operations**, and create an operation.

    > [!NOTE]
    > For custom operations, use an operation ID that is above 5000.

2. Extend the notification service. When the scheduler for the notification service runs, it calls the extension code for both CRT and the Real time transaction service to get the notification message.
3. Extend the POS. In the POS, write logic inside the POS operation to specify what should happen when the POS user selects the notification. For information about how to create a POS operation, see [Add POS operations to POS layouts by using Button grid designer](add-pos-operations.md).
4. In Retail headquarters, configure the notification service with the custom operation. Then, when the scheduler runs the notification service, it includes the custom operation. For information about how to configure notifications in the POS, see [Add POS operations to POS layouts by using Button grid designer](../notifications-pos.md).

    When the POS user selects the notification, the framework calls the correct operation, based on the response that is returned from CRT. The notification service runs for all the notifications that are configured in Retail headquarters, and it returns the response that includes the operation ID and notification details. Therefore, the POS will have the context of the operation ID, and the framework will use this context to call the operation implementation.

> [!NOTE]
> The notification scheduler checks both CRT and Retail headquarters for new notifications. Depending on the scenario, you can extend the Real time transaction service in Retail headquarters or only in CRT. In scenarios where real-time processing is required for notifications, extend the Real-time transaction service method in Retail headquarters. If real-time processing isn't required, extend only CRT.

## Extend the notification service in CRT

To extend the notification service in CRT, override **GetNotificationsExtensionServiceRequest**, and return **GetNotificationsExtensionServiceResponse**.

The Retail software development kit (SDK) includes a sample that shows how to extend the notification service (**RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.NotificationSample**).

+ **GetNotificationsExtensionServiceRequest** – This class contains the operation ID, staff, and channel. Based on the configuration of Retail headquarters, the POS runs the notification scheduler for each configured operation.
+ **GetNotificationsExtensionServiceResponse** – In the response, return the notification detail entity (**NotificationDetailCollection**), update **GetNotificationsExtensionServiceResponse**, and return all the notifications. Because the response is a collection, multiple notifications can be returned.

## Properties of the notification detail entity

The notification detail entity has the following properties. Some of these properties can be configured in the Retail essentials button grid designer and in Commerce headquarters.

| Property               | Data type      | Description                                                                            |
|------------------------|----------------|----------------------------------------------------------------------------------------|
| ActionProperty         | string         | A custom property to send to the POS operation. (This property can be configured using the **Operation parameter** field in the button grid designer.)         |
| DisplayText            | string         | The display text of the notification.                                                  |
| IsLiveContentOnly      | bool           | A value that indicates whether the notification is only for live content.              |
| IsNew                  | bool           | A value that indicates whether the notification is new.                                |
| IsSuccess              | bool           | A value that indicates whether the notification was successful.                        |
| ItemCount              | long           | The number of notifications.                                                           |
| LastUpdatedDateTime    | DateTimeOffset | The date/time when the item in the action property was last updated.                   |
| LastUpdatedDateTimeStr | string         | The date/time when the item in the action property was last updated, in string format. |

## Detailed steps

1. Open **Runtime.Extensions.NotificationSample.proj** from the Retail SDK (**RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.NotificationSample**).
2. Rename the project according to the standard naming convention.
3. Inside the project, there is a class file that is named **NotificationExtensionService.cs**. Open this file.
4. The **GetNotificationsExtensionServiceRequest** class is overridden to add a custom notification. Override **GetNotificationsExtensionServiceRequest**, and return **GetNotificationsExtensionServiceResponse**.
5. Either create a new class and override **GetNotificationsExtensionServiceRequest**, or use the sample template. 
6. In the **NotificationExtensionService** class, there is a method that is named **Process**. The code inside that method checks the operation ID and then, based on the operation ID, creates a notification details object and adds any notifications. Check whether the operation ID is custom operation ID, and then write logic to check whether there are any notifications. If there are, create a notification object that contains the details, and return it together with the response. The POS will then parse the response and show the notification. The following code example is based on the template.

> [!NOTE]
> The action property in the notification detail entity will be sent to the POS operation request. Use the action property to pass any custom information from the notification service to the POS. The **ActionProperty** can be configured using the **Operation parameter** field of the button grid designer, and the **ActionProperty** value should be equal to the input of the **Operation** parameter in the button grid designer.

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
                        // when the notification tile is selected, define the action property as well.
                        // This property can be configured using the Operation parameter field of the button grid designer and passed to the CRT code.
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

7. After you've completed your changes, build the project, and drop the output library into **\\RetailServer\\webroot\\bin\\Ext**.
8. Register the output library in the **CommerceRuntime.Ext.config** file.
9. In the POS, create a new operation that has the same operation ID that is used in the CRT extension. In this example, the operation ID is **5000**. You can use any operation ID that is above 5000.
10. When the POS user selects the notification tile, the POS framework calls the operation handler for the operation ID that is used. Inside the handler, add the required logic to specify what should happen when the POS user selects the notification. For information about how to create a POS operation request, response, and handler, see [Show order notifications in the point of sale (POS)](add-POS-operations.md).
 
11. Configure the notification scheduler according to the instructions in [Show order notifications in the point of sale (POS)](../notifications-pos.md).

## Validate the customization

1. Open the extended Store Commerce application.

    The POS triggers the notification service, based on your notification scheduler configuration.

3. Debug the CRT code by attaching the CRT project to w3wp.exe. The breakpoint should be hit whenever the notification service is called from the POS.
4. When the notification is received in the POS, select it. The notification should call the POS operation handler and run the custom logic that is written inside it.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
