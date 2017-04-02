---
# required metadata

title: License sizing estimator (AX 2012)
description: This article provides information about License sizing estimator in Microsoft Dynamics Lifecycle Services (LCS). The License sizing estimator tool helps you estimate the number of licenses that an organization will require for Microsoft Dynamics AX. The article also explains how to enter data and generate a report so that you can start using the tool.
author: kfend
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 13381
ms.assetid: 6f5723b9-a2f5-40e1-9a95-2fd5f6b9fd84
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# License sizing estimator (AX 2012)

This article provides information about License sizing estimator in Microsoft Dynamics Lifecycle Services (LCS). The License sizing estimator tool helps you estimate the number of licenses that an organization will require for Microsoft Dynamics AX. The article also explains how to enter data and generate a report so that you can start using the tool.

In Microsoft Dynamics Lifecycle Services (LCS), License sizing estimator helps you estimate the number of licenses that an organization will require for Microsoft Dynamics AX. It provides a shared workspace that you can use to model default and customized roles, and then automatically calculate the required client access licenses (CALs). License sizing estimator provides information that you can use in the following circumstances:

-   Before a customer purchases Microsoft Dynamics AX
-   Before you expand your existing Microsoft Dynamics AX implementation
-   Before you upgrade to a newer version of Microsoft Dynamics AX

You can define roles and their associated duties in several ways. License sizing estimator provides the default roles that are included in Microsoft Dynamics AX. You can use any of these predefined roles if they adequately describe the roles in the customer organization. If a predefined role doesn't meet the organization’s requirements, you can add duties or remove duties to model a custom role. You can also model a new role from the list of available duties. **Important:** The roles that you define in License sizing estimator can't be exported to Microsoft Dynamics AX. To implement custom roles in Microsoft Dynamics AX, see [Set up user security in Microsoft Dynamics AX](http://technet.microsoft.com/library/a9eea83b-60bf-4690-8442-a459de3c2001(AX.60).aspx). After you define the roles in the organization, you can view a report that summarizes the information that you entered. This report automatically estimates the number and types of licenses that the organization requires. The estimate is based on the CAL levels that are required to perform the duties that are included in each role, and the number of people in each role. The estimate is also based on the way that users access Microsoft Dynamics AX. Users can access Microsoft Dynamics AX either as named users or through a licensed device.

## Prerequisites
None

## Getting started
To use License sizing estimator, you enter data and generate reports. **Important:** This tool assumes that each user performs a single role. If you enter the same person in multiple roles, that person will be counted as multiple separate users on the report. For example, a person who has three roles will be counted as three users.

### Enter data

1.  [Go to Lifecycle Services](https://lcs.dynamics.com).
2.  In a project, click **License sizing estimator**.
3.  On the **Edit overview** page, enter information about the number of employees and vendor users, and select whether you're creating an estimate for a new or existing implementation.
4.  Click **Add department** to select departments to add.
5.  On the **License sizing estimator** page, enter details about the roles in the customer organization. **Note:** The **License sizing estimator** page is a panorama page. To see all the information on this page, scroll to the right by using your mouse wheel or the lower scrollbar in your browser.

### Generate a report

On the **License sizing estimator** page, click **Generate report**. The report summarizes the data that you’ve entered, and provides estimated licensing information in the form of a table and a pie chart.

