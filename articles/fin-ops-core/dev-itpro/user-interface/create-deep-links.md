---
title: Create shareable, secured URLs (deep links)
description: Learn how to create shareable, secured URLs to forms and records, with overviews on the purpose of shareable URLs, security, and usage.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 07/09/2018
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 3e49f8eb-d9a8-418c-a73d-687da4ca0c96
---

# Create shareable, secured URLs (deep links)

[!include [banner](../includes/banner.md)]

Learn how to create shareable, secured URLs to forms and records.

## Overview

Developers can create shareable and secured URLs (also known as deep links) to specific forms that are root navigable. An optional data context can be passed to the form to display filtered or specific data when the form is opened. The URL Generator enables scenarios such as embedding links in reports, email, and external applications, enabling users to quickly and easily locate the specified forms or data by simply navigating using the generated link.

### Purpose

-   Empower developers to generate URLs that can be used to navigate to root navigable forms in a specified instance.
-   Empower developers to optionally specify a data context that should be displayed when navigating to the specified form.
-   Empower users to share, save, and access the generated URLs from any browser with Internet access.
-   Secure the URLs to prevent unauthorized access to the system, forms, or data.
-   Secure the URLs to prevent exposure of sensitive data or tampering.

## Security
### Site access

Access to the domain/client is controlled through the existing login and SSL mechanism.

### Form access
Access to forms is controlled through Menu items, as Menu items are the entry points where security is enforced. If a user navigates using a URL that contains a Menu item that the user does not have access to, then the Menu item security will prevent the form from opening. The user will receive a message indicating that they do not have the necessary permissions to open the form. Note that deep links will only work for Menu items that allow root navigation.

### Data access

Access to data is controlled through the existing form-level queries. When a form is opened with a generated URL, the form will run its existing form-level queries, which restrict the user's access to data. The data context that is specified in the generated URL is consumed after these form-level queries are applied, and results only in further filtering of the data displayed to the user. In short, a generated URL can, at most, open a form and display all of the data that a form would display to the user based on the form-level queries. A generated URL cannot grant a user access to data that is otherwise inaccessible on the form when not using the generated URL.

## Usage
There are two options for creating deep links for finance and operations apps:
1. **The URL Generator** is a .NET library available for generating deep links from X++ code. This uses the menu item and partition to determine the deep link target for navigation in the client.
2. **System entity navigation** enables generation of the deep link URL outside of X++ code. The developer can construct the URL by providing parameters based on the entity name and record ID of the record to which the deep link URL should navigate.

### URL Generator

The URL Generator is a .NET library that is accessible from X++, under the following namespace.

```xpp
Microsoft.Dynamics.AX.Framework.Utilities.UrlHelper.UrlGenerator
```

#### Requirements

The URL Generator must be used from code running on the AOS, in an active user session or batch process. This requirement ensures that the URL can be secured through encryption specific to the instance that generates the URL. At a minimum, the following information must be specified and passed to the URL Generator in order to generate a working URL.

-   **Host URL**
    -   The URL of the web root for the instance. For example: `https://ax.dynamics.contoso.com/`
-   AOT name of the **Menu Item Display**
    -   The menu item display to be used to open the form.
-   **Partition**
    -   The partition to use for the request.
-   **Company**
    -   The company to use for the request.

#### Example

```xpp
// gets the generator instance
var generator     = new Microsoft.Dynamics.AX.Framework.Utilities.UrlHelper.UrlGenerator();
var currentHost   = new System.Uri(UrlUtility::getUrl());
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

### System entity navigation
Developers can construct a deep link URL dynamically outside of X++ code using the `SysEntityNavigation` action. The developer can construct the URL using the entity name and record ID of the record to which the deep link should navigate. The `SysEntityNavigation` action then navigates to the primary menu item for the defined entity and populates the form with the defined record in finance and operations apps. 

The entities supported for navigation are based on the Dataverse virtual tables for finance and operations apps. See [Enable Microsoft Dataverse virtual entities](../power-platform/enable-virtual-entities.md) for more information on enabling virtual tables for your environment.

#### Parameters

The following are parameters to be specified when constructing the deep link URL:

| Parameter | Description | Data type | Required | 
| --------- | ----------- | --------- | -------- |
| **cmp** | The company ID of the legal entity. In the Dataverse virtual table, this is identified in the **Company Code** column (`mserp_dataareaid`). | String | Optional |
| **entityName** | The plural of the **schema name** of the Dataverse virtual table, as defined in the [Maker Portal](https://make.powerapps.com). For example, `mserp_custcustomerv3entities` is the plural schema name for the **Customers V3 (mserp)** virtual table. | String | Required |
| **entityGuid** | The GUID of the unique identifier property for the selected record in the Dataverse virtual table. For example, the unique identifier column of the **Customers V3 (mserp)** virtual table is `mserp_custcustomerv3entityid` | GUID | Required |

#### URL format

Construct the URL in the following format for deep links using system entity navigation.

```http
https://[Root URL for the environment]/?cmp=[data area ID]&mi=action:SysEntityNavigation&entityName=[entity plural schema name]&entityGuid=[GUID of entity record]

```

#### Example

The following example deep link opens the customer record in finance and operations apps in the **USRT** company for the customer with ID **00004c03-0000-0000-6d28-014105000000** in the **Customers V3 (mserp)** Dataverse virtual table.

```http
https://contoso.operations.dynamics.com/?cmp=usrt&mi=action:SysEntityNavigation&entityName=mserp_custcustomerv3entities&entityGuid=00004c03-0000-0000-6d28-014105000000

```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
