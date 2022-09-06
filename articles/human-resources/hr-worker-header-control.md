---
# required metadata

title: Worker header control overview
description: This article provides a personalizable header control in Employee self service, People hub and worker page in Dynamics 365 Human Resources. 
author: twheeloc  
ms.date: 09/06/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 

ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Worker header control
Dynamics 365 Human Resources provides a personalizable header control in **Employee self service**, **People** hub and the streamlined **Worker** page. The header 
contains key information about the worker, as well as one-click actions such as email, calling, or messaging. The header can also be modified to add or remove fields 
to show additional information including, custom fields. To utilize the new header control, go to **Feature management** and enable the **Worker header control** 
feature.

### Personalization
One of the key benefits of the worker header control is the ability to personalize information that displays in the header.
In the upper right portion of the header, there are three fields that display different data, depending on the status of the employee. This grouping of fields is 
referred to as the Spotlight portion of the header. The Spotlight portion of the header can be personalized to remove the current fields or add fields.    
The fields available for adding to the Spotlight group within the header control will vary between **Employee self service**, the **People** hub, and the **Worker** page.  

### Employee self service
The worker header on the **Employee self service** page contains the following information:  
 - **Worker name** 
 - **Personnel number** 
 - **Position title** 
 - **Departments** 
 - **Worker type** 
 - **Legal entity of employment** 
 - **Years of service** 
 - **Reports to (manager)** 
 - **Position type**  
  
 The header also contains a one-click to edit the individuals personal information. Select the **Edit personal details** button to go to **Personal information** 
 page within ESS.

### People workspace
The worker header in the **People workspace** page contains the following information: 
 - **Worker name** 
 - **Personnel number** 
 - **Position title** 
 - **Departments** 
 - **Worker type** 
 - **Legal entity of employment** 
 - **Years of service** 
 - **Reports to (manager)** 
 - **Position type**   
 
 The header also contains one-click actions such as email, calling, or messaging. If the user is viewing their own information on the **People workspace**, the 
 one-click actions section will display the **Edit personal details** button, and will go to the **Personal information** page within ESS.

### Streamlined employee page

The worker header in the streamlined **Employee** page contains the following information: 
 - **Worker name** 
 - **Personnel number** 
 - **Position title** 
 - **Departments** 
 - **Worker type** 
 - **Legal entity of employment** 
  
  Depending on the status of the employee, the data contained in the header may change. For example, if the employee has exited the company, the header control will 
  contain an **Exited** badge, the employment end date, and the termination reason. 
  
  The table below shows the data that is displayed in the header based on the employee state:

   | Worker state | Data displayed | Additional information |
   | --- | --- | --- |
   | Pending |	•	Name
•	Personnel number
•	Position title
•	Department 
•	Worker type
•	Legal entity
•	Pending badge
•	Start date
•	Reports to
•	Position type	|    |
|Recent hire |•	Name
•	Personnel number
•	Position title
•	Department 
•	Worker type
•	Legal entity
•	Recent hire badge
•	Years of service
•	Reports to | 
• Position type |	By default, the **Recent hire** badge will display for employees who have been hired in the last seven days. To change this setting, on the **Human 
resources parameters** page, on the **General** tab, in the **Recent hires date range** section, enter a time frame. For example, to view the **Recent hire** badge for 
employees who were hired in the last 14 days, set the **Period** field to **14** and the **Unit** field to **Days**. |
|Active employee|	•	Name
•	Personnel number
•	Position title
•	Department 
•	Worker type
•	Legal entity
•	Start date
•	Reports to
•	Position type	|   |
|Exiting| 	•	Name
•	Personnel number
•	Position title
•	Department 
•	Worker type
•	Legal entity
•	Exiting badge
•	Years of service
•	Reports to
•	Position type	| By default, the **Exiting** badge will display for employees who will be leaving in the next seven days. To change this setting, on the **Human 
resources parameters** page, on the **General** tab, in the **Exiting worker date range** section, enter a time frame. For example, to view the **Exiting** badge for 
employees who are leaving in the next 14 days, set the **Period** field to **14** and the **Unit** field to **Days**.|
|Exited	|•	Exited badge
•	Personnel number
•	Employment end date
•	Reason code|	By default, the **Exited** badge will display for employees who have left in the last seven days. To change this setting, on the **Human resources 
parameters** page, on the **General** tab, in the **Exited workers date range** section, enter a time frame. For example, to view the **Exited** badge for employees 
who have left in the last 14 days, set the **Period** field to **14** and the **Unit** field to **Days**.

