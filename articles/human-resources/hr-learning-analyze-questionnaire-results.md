--- 
# required metadata 
 
title: Analyzing questionnaire results
description: Questionnaire statistics can be used to calculate averages, totals, and percentages based on a set of demographic data. 
author: twheeloc
ms.date: 06/11/2026
ms.topic: how-to 
 
# optional metadata 
 
ms.search.form: KMQuestionnaireStatistics, KMQuestionnaireStatisticsLine, HcmLearningWorkspace  
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
# Analyzing questionnaire results

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

You can use questionnaire statistics to calculate averages, totals, and percentages based on a set of demographic data. To start this procedure, go to **Questionnaire** > **View and analyze results** > **Questionnaire statistics**. The demo data company used to create this procedure is USMF.

## Create a Questionnaire statistics record

1. Go to **Questionnaire statistics**.
1. Select **New**.
1. In the list, select the row.
1. In the **Statistics** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Questionnaire** field, select the dropdown button to open the lookup.
1. In the list, select the link in the selected row.
1. Select the **General** tab.
    * Select if you want to include anonymous results or results from workers, contacts, and applicants.  
1. Select or clear the **Worker** checkbox.
    * If you'll be viewing the results by seniority or age, specify the intervals that you would like to use for grouping the results.  
    * Entering a five for the age interval groups the results based on five-year age intervals.  
1. In the **Age** field, enter a number.
    * Select if you want to run the calculation against the entire questionnaire, for each result group, for each question, or for each question row.  
    * Select how you want to group the results.  
    * For example, if you calculate the average points per question, you might want to see the questions grouped by Result group.  
    * Select the data to base the calculation on.  
    * For example, if you want to see the average percent received on the questionnaire across your workers versus the average number of points achieved across your workers.  
1. Select the **Range** tab.
    * Use ranges to limit your result set to only those meeting the Range criteria.  
1. Select the **Grouping by** tab.
    * Use Groupings to determine how the results should be displayed.  
    * For example, group the results first by gender, then by age.  
1. In the list, find and select the desired record.
    * Move the groupings into the **Selected** side and place them in the desired order.  

## Execute the statistics calculation

1. Select **Execute**.
    * Select which calculation function you would like to perform on the results.  
    * For example, calculate the average percentages across the questionnaire for the selected groupings or total the points across the result groups for the selected groupings.  
2. Select or clear the **Delete previous searches** check box.
3. Select **OK**.

## View the results of the questionnaire statistics run

1. Select **Result**.
2. Select **Result**.
3. Close the page.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
