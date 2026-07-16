--- 
# required metadata 
 
title: Distribute questionnaires using scheduling
description: Questionnaire scheduling allows you to plan and distribute questionnaires to multiple respondents. 
author: twheeloc
ms.date: 06/25/2026
ms.reviewer: twheeloc
ms.topic: how-to 
 
# optional metadata 
 
ms.search.form: KMKnowledgeCollectorPlanningTable, KMKnowledgeCollectorPlanningMulti, SysQueryForm, HcmPersonLookup, KMKnowledgeCollectorPlanning, HcmLearningWorkspace
audience: Application User 
# ms.devlang:  

# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---

# Distribute questionnaires using scheduling



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Questionnaire scheduling enables you to plan and distribute questionnaires to multiple respondents. The demo data company used to create this procedure is USMF.

## Create a questionnaire schedule

1. Go to **Questionnaire** > **Distribute** > **Questionnaire schedules**.
1. Select **New**.
1. In the **Scheduling** field, enter a value.
1. In the **Description** field, enter a value.
    * Set the schedule to **Anonymous** if you want to record the responses without names associated to the response.  
    * To allow anonymous results, set up the HR parameters first.  
1. In the **Type** field, select the planning type. In this example, use the **Satisfaction** type.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Date** field, enter a date.
1. Expand the **Email for employee self service** section.
1. In the **Subject** field, enter a value.

    * Example: Questionnaire available  

1. In the **Text** field, enter the body of your email message. Use the variable to substitute values in the system.

    * Example: Dear %P%, Please sign-in to Employee Self Service to complete the Workforce Health questionnaire.  Contoso  

1. Select **Save**.

## Use the Setup details to select the questionnaires to answer and any queries to use to select respondents.

1. Select **Setup details**.
1. In the list, select a query to use to search the system for respondents for the questionnaire. For example, Workers.  
1. Select **View or modify query** to select specific people or adjust the query to find people who match specific criteria.

    * All respondents must also be users in the system.  

1. In the list, mark the row for Person.
1. In the **Criteria** field, enter or select a value. Select Julia Funderburk.  
1. In the list, select Julia Funderburk.
1. Select **OK**.
1. Select the **Questionnaires** tab.
1. In the tree, expand the node for the questionnaire type **Satisfaction Survey**.
1. In the tree, check **Workforce Health Assessment**.
1. Select **OK**.
1. Select **Planned answer session**.
    * The system creates **Planned answer sessions** for each selected or queried user.  

1. Close the page.

## Start the questionnaire schedule to make the questionnaire available for respondents to complete.

1. Select **Functions**.
1. Select **Start**.
1. Select **OK**.

## Send the email to inform respondents of the available questionnaire.

1. Select **Functions**.
1. Select **Send email**.
1. Select **Cancel**.

## Use Planned answer sessions to monitor who needs to complete the questionnaire.

1. Select **Planned answer session**.
    * Delete any remaining planned answer session when you're ready to end the scheduled session.  

1. Select **Delete**.
1. Select **Yes**.
1. Close the page.

## End the schedule when all respondents complete the questionnaire and you delete all remaining Planned answer sessions.

1. Select **Functions**.
1. Select **End**.
1. Select **OK**.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
