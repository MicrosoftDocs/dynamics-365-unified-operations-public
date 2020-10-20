---
# required metadata

title: Create your own Excel sheet to edit retail transactions
description: This topic describes the feature to create your own Excel sheet to edit retail transactions in Dynamics 365 Commerce.
author: josaw1
manager: AnnBe
ms.date: 10/20/2020
ms.topic: index-page
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2018-11-15
ms.dyn365.ops.version: 

---
# Create your own Excel sheet to edit retail transactions

[!include [banner](includes/banner.md)]

While there is a pre-defined Excel template that customers can leverage from different parts of the system to edit & audit retail transactions, customers also have a choice to handcraft their own Excel sheet for this purpose. The same can be achieved by following the below steps:

1.	Open Excel & create a blank spreadsheet
2.	Click on the **Insert** tab and click on **My add-ins**
3.	Click on **Add server information** link on the side pane 
4.	Specify the server URL and click **OK**
5.	If you get the following error message **No applet registrations found**, follow the below steps to resolve the issue
    - Navigate to **System administration > Setup > Office app parameters**
    - In the App parameters fast tab, click **Initialize app parameters** button
    - In the confirmation dialog box, click **OK**
    - In the Registered applets fast tab, click **Initialize applet registration button**
    - Repeat Steps 2-4   
6.	Click on **Design** and then click on **Add table**
7.	Based on the data that needs to be modified, select the entities that needs to be added to the Excel sheet for editing using the below table as a reference:
    
    | Transaction type | Data entities to use|
    |------------------|---------------------|
    | Cash and carry transactions / Online orders / Async customer orders / Async customer quotes | Transaction (auditable), Sales transaction (auditable), Payment transactions (auditable), Tax transactions (auditable), Discount transactions (auditable), Charge transactions (auditable) |
    | Bank drop | Transaction (auditable), Banked tender transactions (auditable) |
    | Safe drop |	Transaction (auditable), Safe tender transactions (auditable) |
    | Tender declaration | Transaction (auditable), Tender declaration transactions (auditable) |
    | Income / Expense | Transaction (auditable), Income/Expense transactions (auditable), Payment transactions (auditable) |
    | Declare starting amount / Tender removal / Float entry / Change tender / Invoice payment / Customer deposit | Transaction (auditable), Payment transactions (auditable) |

8.	It is important to add only one entity to each Excel spreadsheet. Also, all fields that are indicated with key icon needs to be added to the relevant spreadsheet
9.	Once the spreadsheets are designed, apply the required filters. Make sure to apply the same filters to all the spreadsheets in the file. Avoid loading huge amounts of data to the Excel file as this can cause your system & Excel to perform super slow   . It is recommended to always use Company + Statement Number or Transaction Number as filters on the file
10.	After the filter is composed, click on **Refresh** and the data will be loaded
11.	Edit the required data and then publish the data. If the Publish button is disabled, it is probably because not all key fields were added to the Excel sheet
