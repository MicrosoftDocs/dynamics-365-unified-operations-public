---
# required metadata

title: Manager self service overview
description: This article provides an overview of the Manager self service workspace.
author: twheeloc
ms.date: 03/06/2023
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

# Manager self service overview


[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article provides an overview of the **Manager self service** workspace.

**Manager self service** allows people managers access to their direct reports’ personnel data such as leave, time-off, performance, learning, and many more. Having these 
capabilities allows managers to perform limited HR tasks, maintain compliance reporting, access real-time data, and save time while reducing HR administrative tasks.  

**Manager self service** is the same navigation as **Employee self service** with the addition of **My team** tab next to **My information**. **My team** is only 
visible and accessible to managers.   

## Configure Employee self service 

Go to **Human resources > Employee self service**.
You can configure the following options for managers to make changes or add leave requests on behalf of their direct reports: 
 - **Certificates** 
 - **Courses**
 - **Loan items**
 - **Project experience** 
 - **Skills**
 - **Leave and absence requests** 

## Configure Manager self service
Go to **Human resources > Manager self service**.

On the **Manager self service** workspace, managers can set up, view, and access the following information:  
 - View emergency contacts 
    - None (default) 
    - Direct reports only
    - Extended reports (includes direct reports and extended reports) 
 - View expiring records option 
    - None
    - Direct reports only 
    - Extended reports (includes direct reports and extended reports) 
 - Open positions
    - Direct reports only 
    - Extended reports 
    - Both 
    - None 
 - Exiting workers
    - None 
    - Direct reports only 
    - Extended reports 

### Configure personnel actions 

Go to **Human resources shared parameters > Personnel actions**. 
Enable worker actions will display the following:
 - Request new employee 
 - Request new contractor 
 - Request worker reassignment 
 - Request termination 
 - Request compensation change 

Enable position actions will display the following: 
 - Request new position 
 - Request change to position details 

**My team** is separated into two sections, **Summary** and **My team information**.  

### Summary 

Information in the **Summary** section depends on the options that are selected in **Human resources parameters** page. On the **Manager self service** tab of the **Human
resources parameters** page, you can configure options for displaying expiring records and open positions. Enabling these options determines what managers can see in 
the **Summary** section. 

You can configure the following tiles for managers: 
 - **Certificates expiring for my team**
 - **Identification numbers expiring for my team** 
 - **Probations expiring for my team** 
 - **Screenings expiring for my team**
 - **Tests expiring for my team**
 - **Open positions for direct and/or extended reports**
 - **Pending time off requests for my team** 
 - **Team skills assessment** 
 - **Skill gap analysis**
 - **Team performance journals**
 - **Team performance goals** 
 - **Team performance reviews**
 - **Exiting workers** 

### My team information 

My team allows managers to view and update direct and extended reports. To access extended reports, select the employee who has directs, and then choose **View team** 
on the tile. All of the same options apply to extended reports as direct reports. 

### Summary tab 

The **Summary** tab provides a quick view of your direct reports. If a direct report also has workers reporting to them, the card displays the number of direct reports
in the upper section, along with a **View team** button. Options above each tile apply to the selected employee. For example, if you want to enter a leave request on 
behalf of an employee, you select the employee and then choose **Request time off**. 

If you select **Details** after selecting an employee, the following options display: 
 - **Certificates**
 - **Compensation**
 - **Courses**
 - **Reviews**
 - **Time off**
 - **Loaned items**
 - **Performance goals**
 - **Project experience**
 - **Skills** 
 - **Send feedback**
 - **Signing limits** 

Depending on your organization's settings, you can either make changes or view only. 

### Position tab 

The **Position** tab provides a summary view of employees in their primary position. **Name**, **Title**, and **Department** displays in the heading area of each tile. 
This tile includes: 
 - **Seniority date** - Displayed from the worker summary section of the **Worker** page.
 - **Years of service** - Calculated based on the employee's employment start date. 
 - **Number of previous positions** - Based on position history, selecting this number opens the detailed view of all previously held positions.
 - **Birth date** - The month and day of the employee's birth date. 
 You can view position data for both direct and extended reports. 

### Compensation tab 

The **Compensation** tab displays the employee's annual salary. A company identifier displays under the salary amount. If an employee has more than one employment and 
is getting paid from multiple legal entities, the employee will have multiple compensation plans. To see all compensation plans across legal entities without switching 
companies, you must enable cross compensation under **Human resources > Shared parameters > Advanced access > Enable cross company compensation**. 

To view compensation history, select the **Salary amount** to open the **Details** page. Only current and historical fixed and variable compensation records display on 
the **Compensation** page. If an employee has more than one employment, you can switch between companies to view compensation history in each company or enable cross 
company compensation in **Human resources shared parameters** to view all compensation plans. 

You can view compensation for both direct and extended reports. 

### Leave and absence tab 

The **Leave and absence** tab displays the top balances for employees that have activity. To take action or view a full list of activities, select **Details** and then 
select **Time off**. On the **Time off** page, you can view balances, requests, approved time off, and forecast balances to help employees better manage time. Depending
on your organization's settings, you can also request time off for your directs and extended reports. 

### Performance goals tab 

The **Performance goals** tab summarizes performance goals by status. Select a number for a status or select performance goals from the **Details** to see all goals for 
an employee. Managers and employees can update goals as needed over the duration of the goal. 

Managers can see all goals for their team through the **Team performance goals** tile in the **Summary** section of **My team**. 

### Reviews tab 

The **Reviews** tab summarizes the reviews the employee has in each state: **In progress**, **Ready for review**, and **Final review**. To access an employee's review, 
select **Details** and then select reviews to collaborate on. Based on where a review is within the workflow process, you can see if the review is available for 
updating. 

You can see all reviews for your team through the **Team performance reviews** tile in the **Summary** section of **My team**. 

### Learning tab 

The **Learning** tab provides an overview of courses assigned employees categorized by **All assigned courses**, **Overdue**, and **Due soon**. Click on the **Course ID**
to drill into all the details of the course.   

Managers can assign a course to their employee by clicking **Assign course**. The manager will have the option to create a new course or simply find a course previously
created and assign to the employee. This helps managers drive a culture of continuous learning and development which can drive employee engagement, retention, and 
business success. 


