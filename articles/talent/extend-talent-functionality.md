---
# required metadata

title: Extend the functionality of Microsoft Dynamics 365 for Talent
description: If you’ve created any Microsoft PowerApps, you can start those applications from links within Microsoft Dynamics 365 for Talent. 
author: rschloma
manager: AnnBe
ms.date: 11/28/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: Talent
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 17271
ms.assetid: ba1ad49d-8232-400e-b11f-525423506a3f
ms.search.region: Global
# ms.search.industry: 
ms.author: rschloma
ms.search.validFrom: 2017-11-28
ms.dyn365.ops.version: Talent July 2017 update

---
# Extend the functionality of Microsoft Dynamics 365 for Talent
If you’ve created any Microsoft PowerApps, you can start those applications from links within Microsoft Dynamics 365 for Talent. To set up access to your applications, you’ll need to set up some information in Talent on a configuration page that you can open from the **System administration** workspace.

## Configuring embedded PowerApps within Talent
Use the **Set embedded Microsoft PowerApps** page to configure Talent pages to start PowerApps applications. To open the **Set embedded Microsoft PowerApps** page, open the **System administration** workspace and then open the **Links** tab. Select **Microsoft PowerApps** from the **Setup** group. 

The following information is entered or set on this page: 

> -	A descriptive name or identifier for each PowerApps application.
> -	A unique identifier (GUID) for each application that you add to a Talent page. The app ID is available on the PowerApps site, [powerapps.com](http://powerapps.com/). 
> -	The page from which users can open an application or report. Not all Talent pages support embedded PowerApps and Power BI reports. 

 > [!NOTE]
 >  Enter the internal name of the page, rather than the display name that appears at the top of the page. To find the internal name, open the page that you need the internal name of, and right-click anywhere on the page. When the menu opens, hover over the **Form information** item. The internal form name is displayed next to the **Form information** item in the menu.
 
> -	Specify the form control from which the application can retrieve context data. For example, an application might use data about a worker. If you enter the **Worker** page in the **Context** field, the **Worker** page will open when you start the application. An entry in the **Context field** is optional. 
> -	Set the size of the dialog box on which the PowerApps application will run. The dialog boxes are designated as “small” or “large” to optimize the user interface when your application for running on a phone or a larger device, respectively. 

You can also specify which legal entities an application will be available for, or you can make it available to all your legal entities. By default, your PowerApps applications are available to all legal entities.

## Opening an application
When you’ve configured embedded PowerApps applications, llinks to the applications that you specified will be added to the pages within Talent. Click a link to open an application. 


