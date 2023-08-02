---
# required metadata

title: Create questionnaires
description: This article describes the process for creating a questionnaire. 
author: twheeloc
ms.date: 10/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: KCMCollectionType, KMAnswerCollection, KMCollection, HcmLearningWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: b27e2f12-c7a0-4a54-b8d8-17819f8a1c72
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Create questionnaires


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the process for creating a questionnaire. The first step is to design the questionnaire. When you design a questionnaire, you not only write the questions and answers, but also create the structure that enables answers to be recorded and tabulated. 

A carefully designed questionnaire can help increase the quality of the data that you collect. Through careful design, you can better select the appropriate options at the appropriate time for a questionnaire. The following points can help you plan an effective questionnaire:

-   Clearly define the purpose of the questionnaire to help guarantee that the questions support the purpose.
-   Determine the individual person or the group of people who should complete the questionnaire.
-   Write questions that will appear on the questionnaire, and include answer choices, if applicable.
-   Be sure that the questionnaire flows logically, so that respondents remain engaged.
-   Arrange questions and answers in the order that they should be presented to respondents in.
-   Decide how the results should be evaluated, if applicable.
-   Decide whether you’ll need additional features. For example, determine whether and how results should be categorized, whether a time limit is required, or whether all the questions will be mandatory.

The design phase includes four categories of tasks that you must complete in this order:

1.  Set up prerequisites, as required.
2.  Set up answer groups and answers, if applicable.
3.  Set up questions and their association with the answer groups.
4.  Set up the questionnaire itself, and attach questions to it.

## Prerequisites
Some prerequisites must be in place before you can create questionnaires, answers, and questions. However, not all prerequisites are required for full functionality.

### Required

| Prerequisite        | Description                |
|---------------------|----------------------------|
| Questionnaire types | Categorize questionnaires. |
| Question types      | Categorize questions.      |

### Optional

| Prerequisite             | Description                                                    |
|--------------------------|----------------------------------------------------------------|
| Questionnaire parameters | Modify basic controls and default settings for questionnaires. |

### Questionnaire types

**Questionnaire types** are required and must be assigned when you create a questionnaire. **Questionnaire types** help you manage and classify questionnaires more easily. Use questionnaire types to classify questionnaires and differentiate them from each other. For example, if you have multiple questionnaires to select from, you can filter them by type to help make it easier to find a particular questionnaire. Here are some examples of questionnaire types:

-   Human resource development
-   Customer surveys
-   Review process

### Question types

**Question types** are required and must be assigned when you create a question. 

Use **Question types** to categorize questions for reporting. **Question types** also make it easier to find questions, because you can use types as filters on the **Questions** page. Here are some examples of question types:

-   Human resource
-   Managing business
-   Course evaluation

### Questionnaire parameters

Questionnaire parameters are optional. You might not use them, depending on your company’s requirements. 

Questionnaire parameters define the anonymity, number sequence codes, and reference types of a questionnaire. When an organization distributes a questionnaire, the option to allow respondents to remain anonymous might be of concern. 

The number sequence codes are used to organize questions and answers. Based on these number sequence codes, values are automatically assigned to items. 

You should define all parameters before you begin to create your data. You can modify the questionnaire parameter settings at any time.

## Questionnaire components
Questionnaires comprise three main elements: answer groups that contain the answers for multiple choice questions, questions, and the questionnaire itself. You can optionally group the questions on a questionnaire into result groups. Result groups let you categorize questions and provide further analysis on the questionnaire. 

[![QuestionnaireComponents.](./media/questionnairecomponents-1024x615.png)](./media/questionnairecomponents.png)

### Answer groups and answers

Respondents can answer a question in two ways, depending on the subject of the question:

-   Open-ended questions don’t require responses in a specific format. Respondents can type a response as text, a number, a date, or a time. These questions typically require that the respondents provide subjective information in their answers, such as an opinion, description, evaluation, or estimate.
-   Closed-ended questions require that the respondent select an answer in a list of possible correct answers.

To provide a list of possible answers for closed-ended questions, you can create answers on the **Answer groups** page. 

Answer groups and answers are components that make up the main body of information that questions are created from. After you create an answer group, you can associate the answer group with a question in the **Answer group** field on the **Questions** page. 

An **Answer group** can be used for more than one question on the same questionnaire, and can also be used on more than one questionnaire. 

> [!NOTE]
> If you modify answer text in answer groups that have already been used on completed questionnaires, data can become difficult to evaluate, and questionnaire results might no longer be valid. If you must change an answer group, consider creating a new answer group instead of changing an existing one. You can't delete answer groups that are attached to a question or answer, or that have been answered.

### Questions

A questionnaire must contain questions. Questions can be either open-ended or closed-ended.

-   The responses to open-ended questions aren't controlled, and respondents can type their answers.
-   Closed-ended questions require a list of predefined response options, and the questions can be structured to let a respondent select multiple responses. Questions should be designed to elicit specific information from a respondent and must be linked to an answer group that provides the response options for each closed-ended question. 

    > [!NOTE]
    > Before you can set up closed-ended questions, you must create answer groups and answers.

Questions can be arranged in a conditional question hierarchy, so that secondary questions depend on the answer that the respondent selects for the previous question. You can write the questions first and then arrange them into a hierarchy later.

## Setting up questionnaires

> [!NOTE]
> Before you can set up a questionnaire, you must set up answers, questions, and prerequisites. 

For each questionnaire, you can specify the following information:

-   The total time or time limit to answer mandatory questions.
-   Whether all questions are mandatory.
-   Whether to calculate points on a questionnaire.
-   How to categorize results.
-   Whether the questionnaire will be available to a restricted set of respondents.
-   Whether a form template should be displayed as a background behind each page of the questionnaire.
-   Whether additional notes are required in order to clarify the intent of the questionnaire for the respondents.
-   Whether to display questions in a fixed order or randomly select them from a pool.
-   Whether questions will be asked only if specific responses are given for previous answers.

### Set up a questionnaire

The primary page that you use to set up a questionnaire is the **Questionnaires** page. To set up a questionnaire, complete the following tasks in order:

1.  Create a questionnaire.
2.  Follow one of these steps to attach questions to the questionnaire:
    -   If you're using result groups, you can attach questions to a questionnaire by using result groups. First set up the result groups for the questionnaire, and then add questions to the result groups.
    -   If you aren't using result groups, you can attach questions directly to the questionnaire.

3.  Set up a conditional question hierarchy, if it's required.
4.  Test the questionnaire.

On the **Questionnaires** page, click **Validate** to test whether the questionnaire is assembled correctly. However, it's also a good idea to complete the questionnaire and test it yourself before you distribute it.

### Modify a questionnaire

You can complete the following tasks on the **Questionnaires** page:

-   Modify information in the questionnaire, such as the result groups and questions.
-   Delete and add questions.
-   Make changes in the result groups and sequence number. 

> [!CAUTION]
> Be careful when you change questionnaires that have already been answered. Changes can reduce the accuracy of statistics and therefore make them a poor basis for evaluation. Consider creating a new question instead of changing a question that has already been answered.

In a questionnaire, you can't delete the following types of questions:

-   Questions that are attached to a questionnaire
-   Questions that have already been answered and therefore appear in the **Answers** dialog box.

### Result groups

**Result groups** are optional when you attach questions to a questionnaire. 

A result group is used to calculate points and categorize the results of a questionnaire. If you use result groups, you can perform the following tasks:

-   Evaluate questionnaire results, based on point statistics.
-   Evaluate a respondent’s score for each result group that you set up.
-   Generate statistics for each result group to help you analyze results.
-   Print a report that shows results for each result group, and also optional points/texts that are based on points that are earned in each result group.

> [!NOTE]
> Before you can set up result groups, you must complete the following tasks:

-   Set up closed-ended questions. For a closed-ended question, the input type on the **Questions** page must be **Check box**, **Alternative button**, or **Combo box**.
-   Define points for answers in the answer groups that are assigned to each question.
-   Set up a questionnaire.

To attach questions to a questionnaire by using result groups, first set up the result groups for the questionnaire, and then add questions to the result groups. If you don't use result groups, you can attach questions directly to a questionnaire. 

You can set up multiple result groups to evaluate the points that a respondent earns in each category. After a questionnaire is completed, you can view the points that have been achieved for each result group. 

> [!TIP]
> To evaluate a questionnaire by using points but not separate categories, you can add all questions to a single result group. 

For each result group, you can also set up one or more point-based messages that respondents receive after they complete a questionnaire. The text that is shown can vary, depending on the score that a respondent achieves in a result group. To use point-based messages, you must define point intervals and a description of each interval. When a respondent achieves a score in a specific interval, the text for that interval is included on the results report. 

Because a result group is related to the points that are associated with specific sets of questions on a questionnaire, you can use only a specific result group for a questionnaire.

#### Example: Points/texts for result group 3

You're using a questionnaire for a leadership test that has 15 questions in three categories. You create three result groups and add five questions to each result group. Points are then totaled in the three groups. The three result groups are as follows:

-   Creative abilities
-   Leadership abilities
-   Technical abilities

To use point-based messages, you set up text intervals for each result group. Each question is assigned two points. Therefore, the maximum point total in each result group is 10. 

The following table shows the point-based messages that you define for the “leadership abilities” result group.

| Point interval | Text                                       |
|----------------|--------------------------------------------|
| 1 to 3         | You have average leadership abilities.     |
| 4 to 7         | You have good leadership abilities.        |
| 8 to 10        | You have outstanding leadership abilities. |

You can set up point intervals and texts for each result group on a questionnaire. Texts that correspond to each respondent’s score are displayed for each result group. 

> [!NOTE]
> You can change intervals and texts. However, if a questionnaire has been completed, changes might cause differences between previous and new result reports.

### Conditional question hierarchies

Conditional question hierarchies are optional when you set up a questionnaire. 

> [!NOTE]
> Before you can set up a conditional question hierarchy, you must attach questions that have assigned answer groups to the questionnaire. 

To use conditional questions to create a question hierarchy in a questionnaire, you can make the sequence that questions are presented in depend on the answer that a respondent selects for each question. By basing the question sequence on a respondent’s answer, you can modify the questionnaire as the respondent completes it.

#### Examples

A legal entity offers both items and services to its customers. As typically occurs in such cases, some customers purchase only items, some purchase only services, and some purchase both items and services. Therefore, when the legal entity distributes a customer satisfaction survey, it applies a conditional structure to the questionnaire, so that customers who purchase only services don't have to answer questions about items. 

Alternatively, you set up a questionnaire so that if a respondent selects answer A for question 1, question 2 is next in the question sequence. However, if the respondent selects answer B for question 1, question 5 is next.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
