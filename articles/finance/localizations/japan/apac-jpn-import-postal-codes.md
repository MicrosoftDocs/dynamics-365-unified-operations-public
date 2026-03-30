---
title: Import postal codes for Japan
description: Learn how to import postal codes for Japan, including outlines and step-by-step processes for preparing the ZIP code files and creating data import projects.
author: EricWangChen
ms.author: wangchen
ms.topic: how-to
ms.date: 12/08/2025
ms.custom:
ms.reviewer: johnmichalak 
audience: Application User
ms.search.region: Japan
ms.search.validFrom: 2017-06-30
ms.search.form: DirPartyTable
ms.dyn365.ops.version: July 2017 update
---

# Import postal codes for Japan

[!include [banner](../../includes/banner.md)]

In Japan, the Japan Postal Office provides a ZIP code file that you can import into Dynamics 365 Finance. This article walks you through the process for importing ZIP/postal codes. This example uses the JPMF demo data company.

## Prepare the ZIP code file

To prepare the ZIP code file, follow these steps:

1. Download the comma-separated values (CSV) file from the [Japan Postal Office home page](https://www.post.japanpost.jp/zipcode/download.html).

1. Open the file and convert the file encoding from "Shift-JIS" to "UTF-16 LE" (you can use free software such as Notepad++ for Windows to open the source file and convert the encode to UCS-2 LE BOM).

1. Open the file for editing, and add the following row for the column headings.

    ```Text
    LocalAuthCode,OldZipCode,ZipCode,PrefectureName,KanaCity,KanaStreetName,State,City,StreetName,MoreZipCodeFlag,SmallerAreaFlag,StreetChomeFlag,MoreStreetFlag,UpdateFlag,Reason
    ```

1. In the file, add zeros before any ZIP code that has fewer than seven digits. The system doesn't accept ZIP codes that have fewer than seven digits.

## Create a data import project and import the data

To create a data import project and import the data, follow these steps:

1. Go to **System administration** > **Workspaces** > **Data management**.
1. Select **Import** to create an import project.
1. Enter a name, and select **ZIP Postal Code Japan** as the entity name.
1. Upload the data file.
1. Set the source file format of the importing project to **CSV(Unicode)**.
1. Select **Import**.
1. Validate the results.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
