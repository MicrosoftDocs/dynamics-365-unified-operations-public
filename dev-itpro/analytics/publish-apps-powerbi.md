---
# required metadata

title: Publish analytical applications on Power BI 
description:  As an administrator, part of your responsibilities include deploying Analytical applications authored within the
organization to Dynamics Lifecycle Services (LCS) as an implementation asset.
author: sericks007
manager: AnnBe
ms.date: 07/26/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Platform, UnifiedOperations, AX Platform
# ms.tgt_pltfrm: 
ms.custom: 265864
ms.assetid: e253a57a-979b-4ca5-8e09-2bfce97395a5
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Publish analytical applications on Power BI 

[!include[banner](../includes/banner.md)]


The steps outlined in this article require administrative privileges in theDynamics 365 for Finance and Operations, Enterprise edition 
subscription. As an administrator, part of your responsibilities include deploying Analytical applications authored within the
organization to Dynamics Lifecycle Services (LCS) as an implementation asset.

Once the reports have been uploaded to an LCS project they can be published to production environments. This represents the 
Application Lifecycle Management process for transitioning Analytical applications from developer environments into production.

## Publishing Analytical Applications on PowerBI.com

Before continuing, make sure that have you've verified and packaged your Analytical Applications into a PBIX file using Power BI Desktop. See details
here for details on creating Analytical Applications using the local Entity Store database. Once you're ready to promote your solution, 
use the following steps as a guide for publishing Analytical Applications to PowerBI.com.

**Step 1** Upload reports to Dynamics Lifecycle Services

Dynamics Lifecycle Services (LCS) is the tool used to migrate development artifacts from developer to production environments. LCS 
supports migrating PBIX files between environments.


1.  Launch LCS (http://lcs.dynamics.com) from the developer environment.

>   If you haven’t created a project in the LCS environment, create a project.
>   Scroll to the right and select the **Asset library** icon.

Notice that the Asset library lets you add **Power BI report models** (PBIX > files) as implementation artifacts to a project.

[LCS asset library.png](media/asset-library.PNG)

2.  Select the **+** icon to add a new asset

3.  Provide a file name and description

4.  Select the **Upload** button and locate the file that you saved in the earlier step.

![Upload new file](media/upload.PNG)

5.  After successful upload, select **Confirm**.

Notice that the selected file is uploaded into LCS as an implementation asset. LCS supports managing versions and releases for Power BI 
reports. You can maintain several versions and publish reports to other environments as you would in case of any other implementation 
artifact. Because you added the PBIX files as an asset within an LCS project, Finance and Operations environments deployed using that
project have access to this report.

Optionally, you can publish this report so that all your projects can access the shared assets. If you are a Microsoft partner or an ISV,
and want to share this report with your customers, you can share it to your global library and enable your customers to import the asset
into their respective LCS projects. To do this, select the **Save to my library** option.

## Step 2 Deploy the report into production

Your administrator should associate your environment with an LCS project so that Dynamics 365 for Finance and Operations is able to 
consume assets within the project. It’s very likely that this step has already been performed in your production environment.
Launch the client from the environment that you want to deploy the Power BI reports. Typically, this is the test or a production 
instance where you want to see your report with a different set of data than the ones you worked with as a business analyst. 

Go to the\*\* System parameters\*\* form. Select the **Help** tab. Using the **Lifecycle Services help configuration** list box, 
select the LCS project that you uploaded the PBIX file. Select the **Save** button. 

> [!NOTE] 
> This page will only show the LCS projects where the current user has access to. If this step is being performed by an 
administrator, either the administrator needs to have access to the project, or the PBIX artifacts need to be imported into a project 
that the administrator has access to.

1.  On the client, select **System Administration** \> **Setup** \> **Deploy     Power BI**. You will see the file that you uploaded 
into LCS.

[Deploy Power BI](media/deploy.PNG)

2.  Select the **Sales Report** file, and then select the **Deploy Power BI files** option on the menu.

> [!NOTE] 
> You may be asked to consent publishing to PowerBI.com service.
Click the link to provide consent.

3.  When consent is complete, you need to go back to the original browser window and select the **Close** button.

After successful publishing, the Power BI report will appear in your own PowerBI.com subscription. You will notice that the report 
now points to the Entity store in the production environment.

## Distribute Analytical Applications as Solution Assets

This walk-through describes the process for using LCS to migrate Analytical Applications from a developer environment into production. 
Because Power BI reports captured as PBIX files are recognized as implementation assets within LCS, you can bundle the reports with 
other solution assets. For those interested in making custom solutions available to others, this technique offers the
following opportunities:

-   Amaze customers with rich, interactive reports that are shipped as part of a custom solution

-   Create Analytical Applications using Power BI that includes semantic models, sample data, and custom visualizations

-   With Power BI reports available as a stand-alone implementation asset, reports can be delivered “out of band” to customers without 
disrupting services. This facilitates an iterative creation process enabling individuals within an organization to author and enhance 
reports without requiring a Developer

-   You can also build and share customized Power BI reports for specific customers
