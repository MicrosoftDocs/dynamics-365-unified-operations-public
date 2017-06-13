---
# required metadata

title: Import postal codes for Japan
description: This topic explains how to import postal codes for Japan.
author: RichardLuan
manager: AnnBe
ms.date: 05/29/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Japan
# ms.search.industry: 
ms.author: riluan
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Enterprise edition, July 2017 update

---

# Import postal codes for Japan

In Japan, the Japan Postal Office provides a ZIP code file that you can import into Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. This topic walks you through the process for importing ZIP/postal codes. This example uses the JPMF demo data company.

## Prepare the ZIP code file

1. Download the comma-separated values (CSV) file from the Japan Postal Office home page: <http://www.post.japanpost.jp/zipcode/download.html>
2. Open the file for editing, and add the following row for column headings.

        LocalAuthCode,OldZipCode,ZipCode,PrefectureName,KanaCity,KanaStreetName,State,City,StreetName,MoreZipCodeFlag,SmallerAreaFlag,StreetChomeFlag,MoreStreetFlag,UpdateFlag,Reason

3. In the file, add zeros before any ZIP code that has fewer than seven digits. (ZIP codes that have fewer than seven digits won't be accepted.)

## Create a data import project and import the data
1. Go **System administration** > **Workspaces** > **Data management**.
2. Click **Import** to create an import project.
3. Enter a name, and select **ZIP Postal Code Japan** as the entity name.
4. Upload the data file.
5. Click **Import**.
6. Validate the results of the import process.
