---
# required metadata

title: Extensibility in Attract
description: This topic describes how you can extend the Microsoft Dynamics 365 for Talent - Attract application by using the Microsoft Power platform.
author: 
manager: AnnBe
ms.date: 10/15/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: rschloma
ms.search.validFrom: 2018-10-15
ms.dyn365.ops.version: Talent October 2018 update

---

# Extensibility in Attract

[!include[banner](../includes/banner.md)]

Microsoft Dynamics 365 for Talent is built on top of the Common Data Service (CDS) for Apps platform, and can be extended in various ways by using the Microsoft Power Platform and the capabilities that Common Data Service for Apps offers. Therefore, you can configure and personalize the system by using Microsoft PowerApps and Microsoft Flow. You can also get additional people analytics by using Microsoft Power BI. Furthermore, new custom activities, such as the PowerApps and Web content (iframe) activities, make the hiring process more adaptable than ever. By using these activities, you can tailor the hiring process to your business needs and processes, and can make sure that both the hiring team and candidates have a seamless, customized experience.

## Take advantage of the Microsoft Power platform 

Because all the data from Attract resides in Common Data Service for Apps, you can use tools from the Microsoft Power platform to incorporate your unique business needs into Attract.

### PowerApps

You can use PowerApps to easily build apps that connect to your Attract data, and that use expressions like the expressions in Microsoft Excel to add logic. Apps that you build by using PowerApps can run on the web, and on Apple iOS and Google Android devices.

For example, you can make university career fairs easier for recruiters by building a lightweight app that lets them scan resumes and feed candidates to a position in Attract. Alternatively, you can build an app that helps meet your organization's compliance needs. For more information about PowerApps and how to use it to build apps, see [Integrate data into Common Data Service for Apps](https://docs.microsoft.com/en-us/powerapps).

### Microsoft Flow 

You can use Microsoft Flow to create automated workflows that run on top of Attract data. You can easily connect to hundreds of popular apps and services without having to write code. By building flows that interact with the Attract Job, Candidate, and Application entities in Common Data Service for Apps, you can automate various actions. For example, when a candidate accepts an offer, a notification can be sent to an onboarding team, or the news can be announced on Twitter. For more information about flows, see the [Microsoft Flow documentation](https://docs.microsoft.com/en-us/flow/).

### Power BI

Power BI lets you build and view custom reports and dashboards that give you deeper insight into your Attract data. For more information about Power BI and how to build interactive reports and dashboards, see the [Power BI documentation](https://docs.microsoft.com/en-us/power-bi/).

### Custom activities 

You can add custom activities, such as the PowerApps apps and Web content (iframe) activities, at the level of the job process template or while you're creating a new job. These activities let you customize the hiring process and bring business logic that is unique to your organization into Attract.

#### PowerApps activity 

The PowerApps activity lets the creator of a job or job process template embed a PowerApps app in the hiring flow. After you create and publish the app, you can enter its app ID in the activity configurations. By using a PowerApps app, you can read and write data into Common Data Service for Apps. You can even link the app to a flow. For example, you have an app that recruiters use to fill in a form while they conduct phone interviews. In this case, you can link the app to a flow that evaluates whether an applicant can be advanced further in the job application process. This type of activity can be viewed only by members of the hiring team. For more information about how to configure the PowerApps activity, see [Activities in Attract](./activities-attract.md).

> [!NOTE]
> The PowerApps activity is available only with the Comprehensive hiring add-on.

#### Web content (iframe) activity

The Web content (iframe) activity lets you embed a custom web solution that you've built in the hiring process or the Candidate portal. You can read and write data directly from Common Data Service for Apps. You can also customize the solution so that it triggers flows or takes advantage of Microsoft Azure functions. For more information about how to configure the Web content activity, see [Activities in Attract](./activities-attract.md).

> [!NOTE]
> The Web content activity is available only with the Comprehensive hiring add-on.
