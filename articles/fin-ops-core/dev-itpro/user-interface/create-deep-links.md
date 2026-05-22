---
title: Create shareable, secured URLs (deep links)
description: Learn how to create shareable, secured URLs to forms and records, with overviews on the purpose of shareable URLs, security, and usage.
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/12/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 3e49f8eb-d9a8-418c-a73d-687da4ca0c96
---

# Create shareable, secure URLs (deep links)

[!include [banner](../includes/banner.md)]

Learn how to create shareable, secure URLs to forms and records.

## Overview

Developers can create shareable and secure URLs (also known as deep links) to specific forms that are root navigable. You can pass an optional data context to the form to display filtered or specific data when the form opens. By using the URL Generator, you can embed links in reports, email, and external applications. By using the URL Generator, users can quickly and easily locate the specified forms or data by navigating through the generated link.

### Purpose

- Empower developers to generate URLs that navigate to root navigable forms in a specified instance.
- Empower developers to optionally specify a data context that displays when navigating to the specified form.
- Empower users to share, save, and access the generated URLs from any browser with internet access.
- Secure the URLs to prevent unauthorized access to the system, forms, or data.
- Secure the URLs to prevent exposure of sensitive data or tampering.

## Security

### Site access

You control access to the domain or client through the existing authentication and SSL mechanism.

### Form access

You control access to forms through Menu items. The system enforces security at these entry points. If a user tries to access a form by using a URL that contains a Menu item they don't have access to, the Menu item security stops the form from opening. The user sees a message that says they don't have permission to open the form.

> [!NOTE]
> Deep links only work for Menu items that allow root navigation.

### Data access

You control access to data through existing form-level queries. When you open a form by using a generated URL, the form runs its existing form-level queries. These queries restrict the user's access to data. The data context specified in the generated URL is applied after these form-level queries, and it only further filters the data displayed to the user. In short, a generated URL can, at most, open a form and display all of the data that a form would display to the user based on the form-level queries. A generated URL can't grant a user access to data that is otherwise inaccessible on the form when not using the generated URL.

## Usage

You can create deep links for finance and operations apps by using either of the following options:

- **URL Generator**: A .NET library you can use to generate deep links from X++ code. It uses the menu item and partition to determine the deep link target for navigation in the client.
- **System entity navigation**: A method you can use to generate the deep link URL outside of X++ code. Developers can construct the URL by providing parameters based on the entity name and record ID of the record to which the deep link URL should navigate.

### URL Generator

The URL Generator is a .NET library that you can access from X++ under the following namespace.

```xpp
Microsoft.Dynamics.AX.Framework.Utilities.UrlHelper.UrlGenerator
```

#### Requirements

Use the URL Generator from code running on the AOS, in an active user session or batch process. This requirement ensures that the URL can be secured through encryption specific to the instance that generates the URL. At a minimum, specify and pass the following information to the URL Generator to generate a working URL.

- **Host URL**
  - The URL of the web root for the instance. For example: `https://ax.dynamics.contoso.com/`
- AOT name of the **Menu Item Display**
  - The menu item display to use to open the form.
- **Partition**
  - The partition to use for the request.
- **Company**
  - The company to use for the request.

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

You can dynamically create a deep link URL outside of X++ code by using the `SysEntityNavigation` action. Construct the URL by using the entity name and record ID for the record you want the deep link to go to. The `SysEntityNavigation` action goes to the primary menu item for the entity you define and fills the form with the record you specify in finance and operations apps.

The entities you can navigate to are based on the Dataverse virtual tables for finance and operations apps. For more information about enabling virtual tables for your environment, see [Enable Microsoft Dataverse virtual entities](../power-platform/enable-virtual-entities.md).

#### Parameters

Specify the following parameters when you construct the deep link URL:

| Parameter | Description | Data type | Required |
| --------- | ----------- | --------- | -------- |
| **cmp** | The company ID of the legal entity. In the Dataverse virtual table, the **Company Code** column (`mserp_dataareaid`) identifies this value. | String | Optional |
| **entityName** | The plural of the **schema name** of the Dataverse virtual table, as defined in the [Maker Portal](https://make.powerapps.com). For example, `mserp_custcustomerv3entities` is the plural schema name for the **Customers V3 (mserp)** virtual table. | String | Required |
| **entityGuid** | The GUID of the unique identifier property for the selected record in the Dataverse virtual table. For example, the unique identifier column of the **Customers V3 (mserp)** virtual table is `mserp_custcustomerv3entityid`. | GUID | Required |

#### URL format

Construct the URL in the following format for deep links that use system entity navigation.

```http
https://[Root URL for the environment]/?cmp=[data area ID]&mi=action:SysEntityNavigation&entityName=[entity plural schema name]&entityGuid=[GUID of entity record]

```

#### Example

The following example deep link opens the customer record in finance and operations apps in the **USRT** company for the customer with ID **00004c03-0000-0000-6d28-014105000000** in the **Customers V3 (mserp)** Dataverse virtual table.

```http
https://contoso.operations.dynamics.com/?cmp=usrt&mi=action:SysEntityNavigation&entityName=mserp_custcustomerv3entities&entityGuid=00004c03-0000-0000-6d28-014105000000

```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
