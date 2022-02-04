---
# required metadata

title: Extensibility in Attract
description: This topic describes how you can extend Microsoft Dynamics 365 Talent - Attract by using the Microsoft Power platform.
author: andreabichsel
ms.date: 03/18/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-10-15
ms.dyn365.ops.version: Talent October 2018 update

---

# Extensibility in Attract

[!include [banner](includes/banner.md)]



Microsoft Dynamics 365 Talent is built on top of Dataverse, and can be extended in various ways by using the Microsoft Power Platform and the capabilities that Dataverse offers. Therefore, you can configure and personalize the system by using Microsoft Power Apps and Microsoft Power Automate. You can also get additional analytics about people by using Microsoft Power BI. Furthermore, new custom activities, such as the Power Apps and Web content (iframe) activities, make the hiring process more adaptable than ever. By using these activities, you can tailor the hiring process to your business needs and processes, and can make sure that both the hiring team and candidates have a seamless, customized experience.

## Extending Choice columns in Attract

A **Choice** column (picklist) is a type of column that can be included in an table. It defines a set of options. When a Choice column is displayed in a form it uses a drop-down list control.  In Attract there are multiple columns that are Choice columns.  We are beginning to introduce the capability to extend the Choice columns, beginning with the Rejection reason column, Employment type column, and Seniority type column.   Also, you can add localized display labels for the options that you add. For more information, see [Customize labels to support multiple languages](/powerapps/developer/common-data-service/customize-labels-support-multiple-languages).

> [!NOTE]
> The job posting to LinkedIn functionality requires the use of the **Employment type** and **Seniority type** column on the **Job details** page. The default values in these columns are supported by LinkedIn and are displayed when the job is posted. Therefore, if you are posting jobs to LinkedIn and you modify the existing Choice values for these columns, the job will still post, but LinkedIn will not display the custom **Employment type** and **Seniority type** values.  

Listed below are the steps to update the **Rejection reason** column with values that are specific to your business.  

1. To extend the **Rejection reason** column, navigate to the [Power Apps Admin website](https://admin.powerapps.com).
2. You might be prompted to sign into your account. Provide your userID and password credentials that you use to sign into Dynamics365 and/or Office365, and then click **Next**.
3. On the **Environments** tab, select the environment that you want to manage, and double-click to get to the **Details** tab.
4. On the **Details** tab, select **Dynamics 365 Administration Center**.
5. Select the instance that you want to modify and select **Open**.
6. Navigate to **Settings**, and then **Customizations**, and choose **Customize the system**.
7. Find the table that you want to expand the Choices for by selecting **Tables** and expanding the group. In this example, it will be the **Job application table**.
8. Go to the column that you want to extend the Choices for by selecting the **Fields** option. In this example, it will be the **msdyn_rejectionreason**. Double-click the column.
9. In the **Option Set** column, choose **Edit**.
10. Select the **+** icon.
11. Enter a **Label**.  (This must be a unique value – no duplicates).
12. Select **Save**.
13. Select **Publish** at the top of the page.

## Take advantage of the Microsoft Power Platform 

Because all the data from Attract resides in Dataverse, you can use tools from the Microsoft Power Platform to incorporate your unique business needs into Attract.

### Power Apps

You can use Power Apps to easily build apps that connect to your Attract data, and that use expressions like the expressions in Microsoft Excel to add logic. Apps that you build by using Power Apps can run on the web, and on Apple iOS and Google Android devices.

For example, you can make university career fairs easier for recruiters by building a lightweight app that lets them scan resumes and feed candidates to a position in Attract. Alternatively, you can build an app that helps meet your organization's compliance needs. For more information about Power Apps and how to use it to build apps, see [Integrate data into Dataverse](/powerapps).

### Microsoft Power Automate 

You can use Microsoft Power Automate to create automated workflows that run on top of Attract data. You can easily connect to hundreds of popular apps and services without having to write code. By building flows that interact with the Attract Job, Candidate, and Application Tables in Dataverse, you can automate various actions. For example, when a candidate accepts an offer, a notification can be sent to an onboarding team, or the news can be announced on Twitter. For more information about flows, see the [Microsoft Power Automate documentation](/flow/).

### Power BI

Power BI lets you build and view custom reports and dashboards that give you deeper insight into your Attract data. For more information about Power BI and how to build interactive reports and dashboards, see the [Power BI documentation](/power-bi/).

### Custom activities 

You can add custom activities, such as the Power Apps apps and Web content (iframe) activities, at the level of the job process template or while you're creating a new job. These activities let you customize the hiring process and bring business logic that is unique to your organization into Attract.

#### Power Apps activity 

The Power Apps activity lets the creator of a job or job process template embed a Power Apps app in the hiring flow. After you create and publish the app, you can enter its app ID in the activity configurations. By using a Power Apps app, you can read and write data into Dataverse. You can even link the app to a flow. For example, you have an app that recruiters use to fill in a form while they conduct phone interviews. In this case, you can link the app to a flow that evaluates whether an applicant can be advanced further in the job application process. This type of activity can be viewed only by members of the hiring team. For more information about how to configure the Power Apps activity, see [Activities in hiring processes](./activities-attract.md).

> [!NOTE]
> The Power Apps activity is available only with the Comprehensive hiring add-on.

#### Web content (iframe) activity

The Web content (iframe) activity lets you embed a custom web solution that you've built in the hiring process or the Candidate portal. You can read and write data directly from Dataverse. You can also customize the solution so that it triggers flows or takes advantage of Microsoft Azure functions. For more information about how to configure the Web content activity, see [Activities in hiring processes](./activities-attract.md).

> [!NOTE]
> The Web content activity is available only with the Comprehensive hiring add-on.


[!INCLUDE[footer-include](../includes/footer-banner.md)]