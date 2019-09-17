---
# required metadata

title: Show custom notification in POS
description: This topic explains how to add custom notification in POS.
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

# Show custom notification in POS

[!include [banner](../includes/banner.md)]

This topic explains how to add custom notification in POS. This topic is applicable for Dynamics 365 for Finance and Operations or Dynamics 365 for Retail 7.3 and higher versions with latest binary fix.

For custom scenario if you want to show notification in POS or if you want POS to do something periodically then you can extend the notification framework to show notification and store associates can perform necessary action based on that notifications or do any custom logic.

**How it works:**

In POS we build a notification framework which runs periodically for the configured operation in Retail headquarters (frequency is configurable in Retail headquarters) and call the notification service in commerce runtime (CRT) and Real time service in Retail headquarters. When POS makes the call to the notification service in CRT, CRT runs the business logic and check if there any notification need to be send to POS for that particular operation (operation id is passed as parameter to the request and in the CRT notification service we will check the operation id and return the notification details), if notification exists then CRT returns the response to POS saying there is a notification available. POS parses this notification and show it in the UI. When the cashier clicks the notification the relevant operation in POS is executed because each notification is tied to an operation and inside the operation you can write further logic to do additional steps.

When CRT returns the response for notification it returns the number of notifications, messages and action parameters. The POS framework has built in logic to parse the response and get the POS operation id and call it when the user clicks the notification. You can write custom logic inside the operation on what should happen when the user clicks the notification, as mentioned earlier you can send additional parameter from CRT to POS using the action property it will also available for you inside the operation request in POS.

Ex: If you want to notify the user to prepare few orders for pickup, then inside CRT you will check is there any order for pickup if so update the notification response with relevant parameter. POS will parse the response and show the notification. When the user clicks the notification, POS will call the operation with the parameter from the notification (it’s up to the extension logic whether to send parameters or not) and inside the operation you can read all the pending orders for pickup for that user and show it in the UI and the user can take further action.

**Steps required to enable notification for custom operation:**

1.  Create a new operation in Retail headquarters. Under Retail > Channel Setup > POS Setup > POS > POS operations.

    Note: When you create new operation use operation id greater than 4000.

2.  Extend Notification service – When the scheduler for the notification service runs, it will call both CRT and Real time transaction service extension code to get the notification message.

3.  Extend POS – In POS write the logic for what should happen when the user clicks the notification. You need to create an operation in POS, check this link for how to create a new pos operation:

    <https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/add-pos-operations>

4.  Configure the Notification service in Retail Headquarters with your custom operation. So that when the scheduler runs it will include your operation too. Check the below topic on how to configure notification in POS:

<https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/notifications-pos>.

When the user clicks the notification, the framework will call the right operation based on the response returned form the CRT. The notification service runs for all the notification configured in retail headquarters and returns the response with the operation id and notification details. So, POS will have the context of operation id and the framework will use this to call your operation implementation.

**Note:** Our schedule will check both CRT and Retail headquarters to check if there any new extension. You can extend both CRT and Retail headquarters to send notification. It depends on our scenario whether you want to extend the real time transaction service in retail headquarters or CRT. If you have any scenario where you want to check something in Retail headquarters and show notification, then you can call your custom Real time transaction service method form CRT directly instead of extending our Real time service notification class in Retail headquarters.

**How to extend the notification service in CRT:**

To extend the notification service in CRT you should override the GetNotificationsExtensionServiceRequest and return the GetNotificationsExtensionServiceResponse.

There is also a sample available in Retail SDK on how to extend the notification service (RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.NotificationSample).

**GetNotificationsExtensionServiceRequest** – Contains the operation id, staff and channel. Based on your Retail headquarters configuration POS runs the notification scheduler for each configured operation.

**GetNotificationsExtensionServiceResponse** – In the response you should return the notification detail entity, update the GetNotificationsExtensionServiceResponse(NotificationDetailCollection) and return all the notifications. Since its collection you can return multiple notifications.

**Notification details entity contains the below property:**

| **Property name**      | **Data type**  | **Description**                                                                 |
|------------------------|----------------|---------------------------------------------------------------------------------|
| ActionProperty         | string         | Custom property to send to POS operation.                                       |
| DisplayText            | string         | Notification display text                                                       |
| IsLiveContentOnly      | bool           | Indicator whether the notification is only for live content                     |
| IsNew                  | bool           | Indicator whether the notification is new or not                                |
| IsSuccess              | bool           | Indicator whether the notification was success or not                           |
| ItemCount              | long           | Number of notification                                                          |
| LastUpdatedDateTime    | DateTimeOffset | The last updated date time of the item in the action property                   |
| LastUpdatedDateTimeStr | string         | The last updated date time of the item in the action property in string format. |

**Detailed steps:**

1.  Open the Runtime.Extensions.NotificationSample.proj from Retail SDK (RetailSDK\\ SampleExtensions\\CommerceRuntime\\Extensions.NotificationSample)

2.  Rename the project according to your naming convention.

3.  Inside the project there is a class file called NotificationExtensionService.cs, open the file.

4.  If you check that class, we have overridden the GetNotificationsExtensionServiceRequest. To add custom notification, you should override the GetNotificationsExtensionServiceRequest and return the GetNotificationsExtensionServiceResponse.

5.  Either you can create a new class and override the GetNotificationsExtensionServiceRequest or use our sample template. Below steps assume you are using our template:

6.  In the NotificationExtensionService class, there is a method called Process, inside the method we will be checking the operation id and based on the operation id create notification details object and add the notification if any. So, you will check if it's my custom operation id then write your logic to check is there any notification if so create a notification object with the details and return it with the response. Then POS will parse the response and show the notification.

    **Note:** You can remove the sample implementation inside the process method and just keep your custom logic.

    Ex:
```C#
 /**

 * SAMPLE CODE NOTICE
 *
 * THIS SAMPLE CODE IS MADE AVAILABLE AS IS. MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,

 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.

* THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.

* NO TECHNICAL SUPPORT IS PROVIDED. YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.

 */

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
7.  Once you are done with the changes build the project and drop the output library in

    \RetailServer\webroot\bin\Ext

8.  Register your output library in CommerceRuntime.Ext.config.

9.  Next step is to create a new operation in POS with the same operation id used in the CRT extension in this case its “*5000*”. You can use any operation id greater than 4000.

 When the user clicks the notification tile, the POS framework will call the operation handler for the operation id you used, inside the handler you can add required logic on what should happen when the user clicks the notification. Check this link for how to create a operation request, response and handler for POS: <https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/add-pos-operations>

 **Note:** The action property in the Notification detail entity will be sent to your POS operation request, use that action property if you want to pass any custom information from the notification service to POS.
10.  Configure the notification scheduler by following the steps in the below link:
     <https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/notifications-pos>

**Validate your customization:**

<!-- -->

1.  Launch the Cloud POS or Modern POS (where you have deployed your POS customization)

2.  POS should trigger the notification service based on your notification scheduler configuration.

3.  You can debug the CRT code by attaching the CRT project to w3wp.exe. The breakpoint should hit whenever the notification service is called from POS.

4.  When you receive the notification in POS, click the notification it should then call the POS operation handler and inside the handler you can write the required logic.
