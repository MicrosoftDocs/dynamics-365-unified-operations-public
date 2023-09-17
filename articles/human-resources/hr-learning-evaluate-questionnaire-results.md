---
# required metadata

title: View and evaluate the results of questionnaires
description: This article explains how you can view and evaluate the results of questionnaires that respondents complete. 
author: twheeloc
ms.date: 10/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: KMCollection, KMKnowledgeCollectorCollection, KMKnowledgeCollectorUserResults, HcmLearningWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 6570206a-b2c4-4025-8715-432fe6652b78
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# View and evaluate the results of questionnaires


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article explains how you can view and evaluate the results of questionnaires that respondents complete. 

After respondents complete a questionnaire, you can view and evaluate the questionnaire results in the following ways:

-   **Completed answer sessions** – View details about the questionnaires that respondents have completed, and generate reports to summarize answers and any points that were earned.
-   **Result groups** – View result group details and statistics for questionnaires. Result group statistics can be generated for either a single answer session of a questionnaire or all answer sessions.
-   **Questionnaire statistics** – Specify criteria to calculate statistics for a specific group of respondents.

You can also generate various reports to view results that are sorted by person, answer session, or result group. The following reports that are related to completed questionnaires are available:

-   Answers
-   Answers per questionnaire
-   Answers per person
-   Feedback analysis

## Answer session results

After respondents complete a questionnaire, you can view the results of the completed answer sessions. An answer session is one user’s response to a questionnaire. You can view details about completed answer sessions on the **Answers** page. The answer sessions that are included on the **Answers** page are filtered in various ways, depending on how you open the page:

-   All questionnaires
-   A specific questionnaire
-   A specific person

From the **Answers** page, you can view details about answers, points that were earned, a respondent’s responses in each result group, and the question hierarchy that was used on the selected questionnaire, if a question hierarchy was used. You can also generate and print the following reports:

-   **Results report** – This report shows a graphical representation of the points that were earned per result group for the selected answer session.
-   **Answer report** – This report shows the answers that the respondent selected for each question on the questionnaire.
-   **Incorrect answers** – This report shows information that is related to the incorrect answers that the respondent selected.

> [!NOTE]
> The **Results** report is available only if you use results groups on the questionnaire, and if you selected **Results page** on the **Questionnaires** page. The **Answer** report and the **Incorrect answers** report are available only if you selected **Answer report** on the **Questionnaires** page.

## Questionnaire statistics

You can use questionnaire statistics to analyze the results of a completed questionnaire, based on calculations that you define. To define calculations, you must complete the following tasks:

-   Select criteria to calculate and display the statistics.
    -   You can show statistics by questionnaire, questions, question rows, or results groups.
    -   Select the type of chart that will be used when you view results.
    -   Select the types of people from the network, such as employees, contact persons, or applicants, to include answers for. You can also include answers from questionnaires that were completed anonymously.
    -   Set up intervals that are based on age or seniority to analyze results.
-   Select or verify settings that refine the subject of the statistics. For example, by selecting a ZIP Code or postal code, you can analyze results for all respondents within a specific geographic area.
-   Select or verify criteria to analyze results by respondent or questionnaire characteristics. For example, by selecting **ZIP/postal code**, you can analyze the correlation between a respondent’s location and correct answers.

The settings that you define are saved and can be used to periodically recalculate results.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
