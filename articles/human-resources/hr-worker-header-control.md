---
# required metadata

title: Worker header control
description: This article provides information about the personalizable header control in Employee self service, in People hub, and on the Worker page in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 09/06/2022
ms.topic: overview
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

Microsoft Dynamics 365 Human Resources provides a personalizable header control in **Employee self service**, in **People** hub, and on the streamlined **Worker** page. The header contains key information about the worker, and also single-click actions such as emailing, calling, or messaging. The header can be modified by removing fields or adding fields, including custom fields, to show additional information. To use the new header control, go to **Feature management**, and enable the **Worker header control** feature.

## Personalization

One of the key benefits of the worker header control is the ability to personalize information that appears on the header.

In the upper right of the header is a group of three fields that show different data, depending on the status of the employee. This group of fields is referred to as the Spotlight portion of the header. You can personalize the Spotlight portion of the header by removing the current fields or adding fields. The fields that can be added to the Spotlight portion in the header control differ for **Employee self service**, **People** hub, and the **Worker** page.

## Employee self service

The worker header on the **Employee self service** page contains the following information:

- Worker name
- Personnel number
- Position title
- Departments
- Worker type
- Legal entity of employment
- Years of service
- Reports to (manager)
- Position type

The header also contains a single-click action for editing the individual's personal information. Select **Edit personal details** to open the **Personal information** page in **Employee self service**.

## People hub

The worker header in **People** hub (the **People workspace** page) contains the following information:

- Worker name
- Personnel number
- Position title
- Departments
- Worker type
- Legal entity of employment
- Years of service
- Reports to (manager)
- Position type

The header also contains single-click actions such as emailing, calling, or messaging. If a user is viewing their own information on the **People workspace** page, the single-click action section includes the **Edit personal details** button. The user can select this button to open the **Personal information** page in **Employee self service**.

## Streamlined Worker page

The worker header on the streamlined **Worker** page contains the following information:

- Worker name
- Personnel number
- Position title
- Departments
- Worker type
- Legal entity of employment

Depending on the status of the employee, the data on the header might change. For example, if the employee has exited the company, the header control contains an **Exited** badge, the employment end date, and the termination reason.

The table below shows the data that appears on the header for different employee statuses.

| Employee status | Data that is shown | Note |
|-----------------|--------------------|------|
| Pending | <ul><li>Name</li><li>Personnel number</li><li>Position title</li><li>Department</li><li>Worker type</li><li>Legal entity</li><li>Pending badge</li><li>Start date</li><li>Reports to</li><li>Position type</li></ul> | |
| Recent hire | <ul><li>Name</li><li>Personnel number</li><li>Position title</li><li>Department</li><li>Worker type</li><li>Legal entity</li><li>Recent hire badge</li><li>Years of service</li><li>Reports to</li><li>Position type</li></ul> | By default, the **Recent hire** badge is shown for employees who have been hired in the last seven days. To change this setting, on the **Human resources parameters** page, on the **General** tab, in the **Recent hires date range** section, enter a time frame. For example, to view the **Recent hire** badge for employees who were hired in the last 14 days, set the **Period** field to **14** and the **Unit** field to **Days**. |
| Active employee | <ul><li>Name</li><li>Personnel number</li><li>Position title</li><li>Department</li><li>Worker type</li><li>Legal entity</li><li>Start date</li><li>Reports to</li><li>Position type</li></ul> | |
| Exiting | <ul><li>Name</li><li>Personnel number</li><li>Position title</li><li>Department</li><li>Worker type</li><li>Legal entity</li><li>Exiting badge</li><li>Years of service</li><li>Reports to</li><li>Position type</li></ul> | By default, the **Exiting** badge is shown for employees who will leave in the next seven days. To change this setting, on the **Human resources parameters** page, on the **General** tab, in the **Exiting worker date range** section, enter a time frame. For example, to view the **Exiting** badge for employees who are leaving in the next 14 days, set the **Period** field to **14** and the **Unit** field to **Days**. |
| Exited | <ul><li>Exited badge</li><li>Personnel number</li><li>Employment end date</li><li>Reason code</li></ul> | By default, **the Exited** badge is shown for employees who have left in the last seven days. To change this setting, on the **Human resources parameters** page, on the **General** tab, in the **Exited workers date range** section, enter a time frame. For example, to view the **Exited** badge for employees who have left in the last 14 days, set the **Period** field to **14** and the **Unit** field to **Days**. |
