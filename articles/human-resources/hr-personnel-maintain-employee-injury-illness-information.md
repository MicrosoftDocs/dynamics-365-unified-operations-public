--- 
# required metadata 
 
title: Maintain employee injury and illness information
description: This task describes how to create an injury or illness case.
author: twheeloc
ms.date: 11/03/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: HRMInjuryIncident, HcmWorkerLookUp, HcmPersonnelManagementWorkspace
audience: Application User 
# ms.devlang:  

# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Maintain employee injury and illness information


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



It is recommended to complete the 'Setup injury and illness' task guide first, as some of the setup information is used here. 



This task recording describes the basic steps for creating an injury or illness case. In addition to the details of the injury or illness, a case status is tracked. By default, cases have a status of **Open**. You can manage the status by using the **Case status** menu item at the top of the page.

1. Go to **Human resources \> Workers \> Injury and illness \> Injury or illness incidents**.
2. Select **New**.
3. In the **Case description** field, enter a value (for example, **Wrist injury**).
4. In the **Worker** field, enter or select a value (for example, **Ana Bowman**).
5. In the **Date and time of incident** field, enter a date and time (for example, January 20, 2016, at 10:00 AM).
6. In the **Injury or illness type** field, enter or select a value (for example, **Fracture**).
7. In the **Body part** field, enter or select a value (for example, **Wrist**).
8. In the **Outcome type** field, enter or select a value (for example, **Therapy**).
9. In the **Date and time reported** field, enter a date and time.

    The reported date and time must be later than the date and time of the incident.

10. In the **Person who reported case** field, enter or select a value (for example, **Ana Bowman**).

    The specified person might be the employee or another witness to the incident.

11. In the **Incident** section, in the **Where incident occurred** field, enter a value (for example, **Warehouse**).
12. In the **On work premises** field, select **Yes** if the incident occurred on the work premises.
13. In the **Date and time began work** field, enter the date and time when the affected individual started to work before the incident occurred.
14. In the **Employee job or task** field, enter the job or task that the worker was performing when the incident occurred (for example, **Loading boxes**). 
15. In the **Cause of incident** field, enter the cause of the incident (for example, **Slipped on wet floor**).
16. In the **Severity level** field, enter or select a value.
17. In the **Action to be taken** field, enter a value (for example, **Clean up spills promptly**).
18. In the **Expected days away from work** field, enter the number of days that the individual is expected to be away from work.

    After the individual returns to work, update the **Days away from work** field with the actual number of days that the individual was away.

19. In the **Injury or illness costs** section, select **Add**.
20. In the **Date** field, enter a date.
21. In the **Cost type** field, enter or select a value (for example, **Therapy**).

    You can also enter an amount and attach any supporting documentation to the cost (for example, invoices or doctor's notes).

22. Select **Add**.
23. In the **Date** field, enter a date.
24. In the **Cost type** field, enter or select a value (for example, **Doctor**).
25. In the **Injury or illness treatments** section, select **Add**.
26. In the **Treatment date** field, enter a date and time.
27. In the **Treatment type** field, enter or select a value (for example, **Splint**).
28. Optional: Set the **Emergency room hospital visit** section to **Yes**.
29. In the **Treatment comments** field, enter a value (for example, **Splint for 2 weeks**).
30. In the **Physician name** field, enter a value (for example, **Dr. Anderson**).
31. In the **Treatment facility and location** field, enter a value (for example, **Elm St. Emergency**).
32. In the **Treatment details** field, enter a value (for example, **X-ray confirms fracture, wear splint**).
33. Select **Save**.

The case status can be updated at any time. If the processing of the injury or illness is in progress, set the status to **In process**. After you close the incident, you can only add or remove costs, treatments, or filings that are related to the incident. To change other information, you must reopen the case.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
