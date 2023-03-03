---
# required metadata

title: Business events example
description: This article provides an example of Business events.
author: twheeloc
ms.date: 03/03/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HRMParameters, EssWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: ["51941", "intro-internal"]
ms.assetid: 2cfb061a-a616-4bf9-9d98-9cde00039eec
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-03-19
ms.dyn365.ops.version: Human Resources

---

#  Business events example


[!INCLUDE [PEAP](../includes/peap-2.md)]

Flow setup - Assigned task notification  

Sign in to Power apps maker portal.  

Select an existing environment where you have the permissions needed to create a Power Automate resource. The default environment is open to all companies.  

Create a new solution. Inside a Solution create a new Automated flow.  

Graphical user interface, application

Description automatically generated  

Search for Dynamics 365 Finance and select the connector. You will notice a trigger named When a Business Event occurs. Select this trigger.  

Graphical user interface, application

Description automatically generated  

Select your environment instance,   

category = Human Resources,   

Business event = Business Event Name. (Example: Assigned task)  

Legal entity  

Select the +New step button to add a new action. Search for the Parse JSON data operation. This step is needed to parse the message with the schema of the data 
contract. Select the content field of Parse Json action, then the Body output from the earlier step should appear as an option. Now, Select body.  

Graphical user interface, application

Description automatically generated  

  

Go to the FnO instance.   

Select System Administration > Business events > Business events catalog  

Select a business event. For Example: we have selected “Assigned task” in below screen.   

Click on Download schema link. This will download a text file. Open the text file and copy the content.  

Graphical user interface, text, application, email

Description automatically generated  

  

Go Back to Power Automate (Step 7) and select the Generate from sample to generate schema.   

  

Paste the text file content (copied from step 8) and select Done.  

  

Graphical user interface, text, application, email

Description automatically generated  

On click of done, the content look like as below.  

Graphical user interface, text, application

Description automatically generated  

  

Add a new action and use the ‘Get a record’ connector to fetch more details using the relevant entity record. This will open a window to supply instance, Entity name 
and Object id.  

Graphical user interface, application

Description automatically generated 

 

Provide the information as below  

Instance: Select environment instance.  

Entity name: Select the entity name that has the field you want to add.  

Object id: Object id refers to the key values for the record as strings and separated by a comma. For Example: for Assigned task business event - we need Personnel 
number of worker (AssignedWorkerPersonnelNumber) and Id of the assigned task(BusinessProcessTaskId). Because values can only be given in the form of strings and the 
task id format is GUID. To obtain the exact Task ID, we used the substring expression. Similarly, depending on the format of field, the value must be converted to 
String. This conversion is not required if the format of the field is already a string. For example: the format of AssignedWorkerPersonnelNumber is String so we have 
directly used the field.  

substring(body('Read_business_event')?['BusinessProcessTaskId'], 1, sub(length(body('Read_business_event')?['BusinessProcessTaskId']),2)),   

  

Graphical user interface, text, application, email

Description automatically generated  

  

Graphical user interface, text, application

Description automatically generatedUse the Outlook (or Teams) connector to send notifications. Select Add dynamic content button to supply dynamic content to the 
notification.   

  

Graphical user interface, text, application

Description automatically generatedFor Example: To add Email Id – we have selected AssignedWorkerEmail.  

  

Add the information as below  

 

To: Add Email ID. you can use specific field which gives value of email id. For example: In case of Assigned tasks, you can use Assigned worker email.  

 

Subject: You can provide any text along with specific information from entity. For example: In case of Assigned tasks, you can use Task Name.   

 

Body: You can enter the content you want to send as a notification along with dynamic content. The content can be formatted. For example, in the case of Assigned tasks,
we wanted to send a notification to the worker to whom the task was assigned, including all task details and the due date. As a result, we have supplied the assigned 
worker's name, description, instructions, and due date information in Body area.  

Graphical user interface, application, Teams

Description automatically generated  

  

Alternatively, to receive responses back from the notification sent ‘Send email with options’ connector can be used. Using this will pause the flow until it receives a 
response back, which can then be accessed via the ‘SelectedOption’ field, available on the dynamic content dialog, to add further logic to your flow. Additionally, 
this connector allows formatting emails with HTML (Hyper Text Markup Language) tags.   

Graphical user interface, text, application, email

Description automatically generated  

Graphical user interface, text, application

Description automatically generated  

  

Once the flow is ready, click Save.  

Graphical user interface, application

Description automatically generated  

Go to System Administration > Setup > Business Events. Select Endpoints. Verify that a new endpoint has been created with a GUID.  

Graphical user interface, text, application, email

Description automatically generated  

On the same form, verify that the event is activated in the Active business events tab.  

When an event occurs, it will trigger the flow and a notification should be sent based on the configuration above. For Example: with the Assigned task example mentioned
with above steps, if any new task is assigned to a worker, then this would trigger the flow which will send the notifications to the assigned worker.  

  

Recommended content  

  

Business events and Microsoft Power Automate - Finance and Operations | Dynamics 365  

Business events in Microsoft Power Automate - Finance and Operations | Dynamics 365  
