---
# required metadata

title: Create and use deep links | Microsoft Docs
description: Learn how to create shareable, secured URLs to forms and records.
author: RobinARH
manager: AnnBe
ms.date: 2015-12-11 23:54:59
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 24321
ms.assetid: 2e3f4305-1466-440f-b29e-2d1845fdb669
ms.region: Global
# ms.industry: 
ms.author: shshabazz

---

# Create and use deep links

Learn how to create shareable, secured URLs to forms and records.

Overview
--------

The URL Generator enables developers to create shareable and secured URLs (a.k.a. deep links) to specific forms. An optional data context can be passed to the form to display filtered or specific data when the form is opened. The URL Generator enables scenarios such as embedding links in reports, emails, and external applications, enabling users to quickly and easily locate the specified forms or data by simply navigating using the generated link.

### Purpose

-   Empower developers to generate URLs that can be used to navigate to forms in a specified instance.
-   Empower developers to optionally specify a data context that should be displayed when navigating to the specified form.
-   Empower users to share, save, and access the generated URLs from any browser with Internet access.
-   Secure the URLs to prevent unauthorized access to the system, forms, or data.
-   Secure the URLs to prevent exposure of sensitive data or tampering.

## Security
### Site access

Access to the domain/client is controlled through the existing login and SSL mechanism.

### Form access

Access to the form is controlled through the specified Menu Item, and the accompanying Menu Item security system. If a user navigates using a URL which contains a Menu Item that the user does not have access to, then the Menu Item security will prevent the form from opening. The user will receive message which says that they do not have the necessary permissions to open the form.

### Data access

Access to data is controlled through the existing form-level queries. When a form is opened with a generated URL, the form will run its existing form-level queries, which restrict the user's access to data. The data context that is specified in the generated URL is consumed after these form-level queries are applied, and results only in further filtering of the data displayed to the user. In short, a generated URL can, at most, open a form and display all of the data that a form would display to the user based on the form-level queries. A generated URL cannot grant a user access to data that is otherwise inaccessible on the form when not using the generated URL.

## Usage
The URL Generator is a .NET library that is accessible from X++, under the following namespace.

    Microsoft.Dynamics.AX.Framework.Utilities.UrlHelper.UrlGenerator

#### Requirements

The URL Generator must used from code running on the AOS, in an active user session or batch process. This requirement ensures that the URL can be secured through encryption specific to the instance that generates the URL. At a minimum, the following information must be specified and passed to the URL Generator in order to generate a working URL.

-   **Host URL**
    -   The URL of the web root for the instance. For example: https://ax.dynamics.contoso.com/
-   AOT name of the **Menu Item Display**
    -   The menu item display to be used to open the form.
-   **Partition**
    -   The partition to use for the request.
-   **Company**
    -   The company to use for the request.

#### Example

```
// gets the generator instance
var generator     = new Microsoft.Dynamics.AX.Framework.Utilities.UrlHelper.UrlGenerator();
var currentHost   = new System.Uri(UrlUtility::getUrl());
generator.HostUrl = currentHost.GetLeftPart(System.UriPartial::Authority);
generator.Company = curext();
generator.MenuItemName = <menu item name>;
generator.Partition = getCurrentPartition(); 

// repeat this segment for each datasource to filter
var requestQueryParameterCollection = generator.RequestQueryParameterCollection;
requestQueryParameterCollection.AddRequestQueryParameter(
    <datasource name>,
    <field1>, <value1>,
    <field2>, <value2>,
    <field3>, <value3>,
    <field4>, <value4>,
    <field5>, <value5>
);

System.Uri fullURI = generator.GenerateFullUrl();

// to get the encoded URI, use the following code
fullURI.AbsoluteUri
```

