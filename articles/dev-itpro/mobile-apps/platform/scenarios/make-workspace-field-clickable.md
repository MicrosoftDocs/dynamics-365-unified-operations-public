---
# required metadata

title: Set up clickable fields
description: This topic explains how to customize the fields on a mobile app page so that they are shown as email addresses, phone numbers, or URLs.
author: makhabaz
manager: AnnBe
ms.date: 07/01/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 255544
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: makhabaz
ms.search.validFrom: 2017-07-20
ms.dyn365.ops.version: Platform update 3

---

# Set up clickable fields

The fields on a mobile app page can be customized so that they are shown as email addresses, phone numbers, or URLs.

## Email field
You can mark a field as an email address field by using business logic. Then, when a user clicks the field, the default mobile email app starts, and the field value appears as the email address in the app.

## Phone field
You can mark a field as a phone number field by using business logic. Then, when a user clicks the field, the mobile dialer app starts, and the field value appears as the phone number in the app.

> [!NOTE]
> On iOS, if the phone number isn't valid, it might not trigger the mobile dialer app.

## URL field
You can mark a field as a URL field by using business logic. Then, when a user clicks the field, the URL opens in the default mobile browser, and the field value appears in the address bar.

> [!NOTE]
> On iOS, you must provide a complete URL (that is, a URL that starts with a protocol, such as **http**). Otherwise, the URL isn't opened in the browser. A URL such as www.microsoft.com doesn't work. Instead, the URL must be specified as `http://www.microsoft.com`.

## Example
This example shows how to configure the customer email address and phone number fields so that they can clicked and opened in the appropriate iOS apps.

Before the fields are customized, they can't be clicked, as shown in the following image.

![Customer details page before the changes are made](media/workspace-api/FieldAsURLOriginal.png)

Follow these steps to specify that a field is a link.

1. Add the following lines to the **appInit** method. You call the **configureControl** method, and pass in the page name and control name. You then supply the **LinkType** value for the control. The following values are supported: **Telephone**, **Email**, and **Url**.

    ```
    metadataService.configureControl('PageName', 'ControlName', { LinkType: 'Telephone' });
    metadataService.configureControl('PageName', ' ControlName ', { LinkType: 'Email' });
    metadataService.configureControl('PageName', ' ControlName ', { LinkType: 'Url' });
    ```

2. Upload the updated business logic file by using the mobile app designer.
3. Update the workspace metadata in the mobile client.

The fields now appear as links.

![Customer details page after the changes](media/workspace-api/FieldAsURLFinal.png)
