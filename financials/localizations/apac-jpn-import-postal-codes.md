---
# required metadata

title: Import postal codes for Japan
description: This topic provides informationa about importing postal codes for Japan.
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

In Japan, the Japan Postal Office provides a ZIP code file that you can import into Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. This procedure walks you through importing ZIP/Postal codes. This procedure was created using demo data company JPMF.

## Prepare the ZIP code file

1. Download CSV file from Japan Postal Office home page (http://www.post.japanpost.jp/zipcode/download.html)
2. Open the file for editng and add a row for column headings to the downloaded file. (LocalAuthCode,OldZipCode,ZipCode,PrefectureName,KanaCity,KanaStreetName,State,City,StreetName,MoreZipCodeFlag,SmallerAreaFlag,StreetChomeFlag,MoreStreetFlag,UpdateFlag,Reason)
3. Add "0" before the zip code if the postal code in the downloaded file is less than 7 digits (zip codes that are less than 7 digits are not accepted)

## Create Data Import project and import the data
1. Go **System administration** > **Workspaces** > **Data management**
2. Click **Import** to create an import project.
3. Enter a name and choose "ZIP Postal Code Japan" as the **Entity name**.
4. Upload the data file.
5. Click **Import**.
6. Verify the results of import process.
