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

This article provides an example of a business event. 

[!INCLUDE [PEAP](../includes/peap-2.md)]

## Set up flow - Assigned task notification  
1. Sign in to Power apps maker portal.  
2. Select an existing environment where you have the permissions needed to create a Power Automate resource. The default environment is open to all companies.  
3. Create a new solution. Inside a solution, create a new Automated flow.  

![View new automated flow.](./media/solution1.png)

4. Search and select the **Dynamics 365 Finance** connector. Select the **When a Business event occurs** trigger.  
5. Select your environment instance: 
 - Category = Human Resources
 - Business event = Business Event Name. (Example: Assigned task)  
 - Legal entity  

6. Select **+New step** to add a new action. Search for the Parse JSON data operation. This step is needed to parse the message with the schema of the data 
contract. Select the content field of **Parse Json** action, and select **Body**.  

![Select JSON.](./media/Select-option2.png)

7. Go to the FnO instance.
 - Go to **System Administration > Business events > Business events catalog**.
 - Select a business event. 
 - Click **Download schema**, this will download a text file. Open the text file and copy the content.  

![Download schema.](./media/Downschema3.png)

8. Go back to Power Automate (Step 7) and select **Generate from sample** to generate schema.   
9. Paste the text file content (copied from step 8) and select **Done**. 
10. Add a new action and use the ‘Get a record’ connector to fetch more details using the relevant entity record. This will open a window to supply instance, Entity name and Object ID.  
11. Provide the information below:
 - **Instance**: Select environment instance.  
 - **Entity name**: Select the entity name that has the field you want to add.  
 - **Object id**: Object id refers to the key values for the record as strings and separated by a comma. For example: in the **Assigned task business event** - the Personnel number of worker (AssignedWorkerPersonnelNumber) and ID of the assigned task(BusinessProcessTaskId) is needed. Values are given in the form of strings and the task ID format is GUID. To obtain the exact Task ID, the substring expression is used. Similarly, depending on the format of field, the value must be converted to **String**. This conversion isn't required if the format of the field is already a **String**. 
For example: the format of AssignedWorkerPersonnelNumber is **String** so the field is used.  

substring(body('Read_business_event')?['BusinessProcessTaskId'], 1, sub(length(body('Read_business_event')?['BusinessProcessTaskId']),2)),   

![Get a record](./media/get-record4.png)

![Send an email](./media/Send-email5.png)

12. Use the Outlook (or Teams) connector to send notifications. Select **Add dynamic content** to supply dynamic content to the notification.   
13. Add the information below:  
 - **To**: Add Email ID. you can use specific field, which gives value of email ID. For example, in **Assigned tasks**, use **Assigned worker email**.  
 - **Subject**: You can provide any text along with specific information from entity. For example, in **Assigned tasks**, use **Task name**.
 - **Body**: You can enter the content you want to send as a notification along with dynamic content. The content can be formatted. For example, in the **Assigned tasks**, we wanted to send a notification to the worker to whom the task was assigned, including all task details and the due date. As a result, the assigned worker's name, description, instructions, and due date information has been provided in the body area.  

![Fill in information in email](./media/Send-notification6.png)

 - Alternatively, to receive responses back from the notification sent **Send email with options** connector can be used. Using this will pause the flow until it receives a response back, which can then be accessed via the **SelectedOption** field, available on the dynamic content dialog, to add further logic to your flow. Additionally, this connector allows formatting emails with HTML (Hyper Text Markup Language) tags.   

14. Once the flow is ready, click **Save**.  
15. Go to **System Administration > Setup > Business events**. Select **Endpoints** and verify that a new endpoint has been created with a GUID.  



16. On the same form, verify that the event is activated in the **Active business events** tab. 
17. When an event occurs, it will trigger the flow and a notification should be sent based on the configuration above. 

For example, in the Assigned task example mentioned above, if any new task is assigned to a worker, this would trigger the flow, and will send the notifications to the assigned worker.  
