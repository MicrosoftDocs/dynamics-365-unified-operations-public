---
# required metadata

title: Extensibility in Attract
description: This topic provides information about extending the Attract application by using the Power platform.
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

Built on top of the Common Data Service (CDS) for Apps platform, Dynamics 365 for Talent can be extended in a variety of ways by using the Power Platform and the capabilities offered by CDS for Apps. This enables you to configure and personalize the system by using PowerApps and Power Flow, and to get additional people analytics using Power BI. The hiring process is more adaptable than ever with the addition of custom activities such as PowerApps and Web content (iframe). You can tailor the hiring process to suit your business needs and processes with these new types of activities and ensure that both the hiring team and candidates have a seamless, customized experience.

## Leveraging the Power platform 

Because all of the data from Attract resides in CDS for Apps, you can now use tools from the Power platform to incorporate your unique business needs into Attract.

### PowerApps

You can use PowerApps to build and run apps that easily connect to your Attract data, use Excel-like expressions to add logic, and run on the web, iOS, and Android devices. You can make university career fairs easier for recruiters by building a lightweight app to allow them to scan resumes and feed candidates to a position within Attract, or build an app to meet your organization’s compliance needs. For more information about PowerApps and how to build them, see [Integrate data into Common Data Service for Apps](https://docs.microsoft.com/en-us/powerapps).

### Microsoft Flow 

Using Flows, you can create automated workflows that run on top of Attract data. You can connect to hundreds of popular apps and services easily and without writing code. You can automate actions such as sending a notification to an onboarding team when a candidate accepts an offer or announcing the news on Twitter by building Flows that interact with the Attract’s Job, Candidate, and Application entities in CDS for Apps. To learn more about Flows, see the [Microsoft Flow Documentation](https://docs.microsoft.com/en-us/flow/).

### Power BI

Power BI allows you to build and view custom reports and dashboards that provide you with a deeper insight into your Attract data. Learn more about Power BI and how to build interactive reports and dashboards, see the [Power BI documentation](https://docs.microsoft.com/en-us/power-bi/).

### Custom Activities 

You can add custom activities such as PowerApps and Web content (iframe) both at a job process template level and while creating a new job. Such activities allow you to customize the hiring process and bring any business logic unique to your organization into Attract.

### PowerApp activity 

This type of activity allows the creator of a job or job process template to embed a PowerApp into the hiring flow. After you create and publish a PowerApp, you can enter the PowerApp’s App ID in the activity configurations. Using a PowerApp, you will be able to read/write data into CDS for Apps and if needed, you can tie the PowerApp with a Flow. For example, you may want to have a PowerApp that recruiters use to fill in a form while performing a phone interview which will evaluate whether an applicant can be advanced further in the job application process. This type of activity can only be viewed by members of the hiring team. To learn more about how to configure this activity, see [Activities in Attract](./activities-attract.md).

> [!NOTE]
> The PowerApps activity is only available with the Comprehensive Hiring Add-On.

### Web content (iframe)

The web content (iframe) activity allows you to embed a custom web solution that you built into the hiring process or in the candidate portal. You have the ability to read/write data directly from CDS for Apps and can tailor such a solution to trigger Flows or leverage Azure functions. To learn more about how to configure this activity, see [Activities in Attract](./activities-attract.md).

> [!NOTE]
> The Web content activity is only available with the Comprehensive Hiring Add-On.


