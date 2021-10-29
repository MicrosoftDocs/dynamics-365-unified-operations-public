---
# required metadata

title: Import postal codes for Japan
description: This topic explains how to import postal codes for Japan.
author: EricWangChen
ms.date: 11/22/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: DirPartyTable
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Japan
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update

---

# Import postal codes for Japan

[!include [banner](../includes/banner.md)]

In Japan, the Japan Postal Office provides a ZIP code file that you can import into Dynamics 365 Finance. This topic walks you through the process for importing ZIP/postal codes. This example uses the JPMF demo data company.

## Prepare the ZIP code file

1. Download the comma-separated values (CSV) file from the [Japan Postal Office home page](https://www.post.japanpost.jp/zipcode/download.html).

2. Open the file and convert the file encoding from “Shift-JIS” to “UTF-16 LE” (you can use free software such as Notepad++ for Windows to open the source file and convert the encode to UCS-2 LE BOM.)

3. Open the file for editing, and add the following row for the column headings.

    ```Text
    LocalAuthCode,OldZipCode,ZipCode,PrefectureName,KanaCity,KanaStreetName,State,City,StreetName,MoreZipCodeFlag,SmallerAreaFlag,StreetChomeFlag,MoreStreetFlag,UpdateFlag,Reason
    ```
    
4. In the file, add zeros before any ZIP code that has fewer than seven digits. ZIP codes that have fewer than seven digits won't be accepted.)

## Create a data import project and import the data
1. Go **System administration** > **Workspaces** > **Data management**.
2. Click **Import** to create an import project.
3. Enter a name, and select **ZIP Postal Code Japan** as the entity name.
4. Upload the data file.
5. Set the source file format of the importing project to “CSV(Unicode)”.
6. Click **Import**.
7. Validate the results.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
