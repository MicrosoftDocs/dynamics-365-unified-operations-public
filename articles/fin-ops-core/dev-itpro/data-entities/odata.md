---
title: Open Data Protocol (OData)
description: Learn about Open Data Protocol (OData) and explains how you can use OData V4 to expose updatable views, including a table that provides webpages for various topics.
author: sumadhey
ms.author: twheeloc
ms.topic: how-to
ms.date: 01/14/2026
ms.reviewer: twheeloc
audience: Developer
ms.assetid: 7137b0a0-1473-4134-b769-ede5e07fd6f5
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
---

# Open Data Protocol (OData)

[!include [banner](../includes/banner.md)]

This article provides information about Open Data Protocol (OData) and explains how you can use OData V4 to expose updatable views.

## What is OData?

OData is a standard protocol for creating and consuming data. The purpose of OData is to provide a protocol that's based on Representational State Transfer (REST) for create, read, update, and delete (CRUD) operations. OData applies web technologies such as HTTP and JavaScript Object Notation (JSON) to provide access to information from various programs. OData provides the following benefits:

- It lets developers interact with data by using RESTful web services.
- It provides a simple and uniform way to share data in a discoverable manner.
- It enables broad integration across products.
- It enables integration by using the HTTP protocol stack.

For more information about OData, see the following webpages.

| Topic                                                               | Webpage                                                 |
|---------------------------------------------------------------------|---------------------------------------------------------|
| OData standards                                                     | [OData Version 4.01 documentation](https://www.odata.org/documentation/) |
| OData: Data access for the web, the cloud, mobile devices, and more | [OData in ASP.NET Web API](/aspnet/web-api/overview/odata-support-in-aspnet-web-api/) |

The public OData service endpoint enables access to data in a consistent manner across a broad range of clients. To see a list of all the entities that are exposed, open the OData service root URL. The URL for the service root on your system has the following format: **\[Your organization's root URL\]/data**

> [!NOTE]
> OData actions added through extensions aren't currently supported.

## Addressing

The following table describes the resources and the corresponding URLs in the Fleet Management sample.

| Resource            | URL                                                                     | Description                                                    |
|---------------------|-------------------------------------------------------------------------|----------------------------------------------------------------|
| Service endpoint    | \[Your organization's root URL\]/data/                                  | The root service endpoint for OData entities                   |
| Entity collection   | \[Your organization's root URL\]/data/Customers                         | The collection of all customers                                |
| Entity              | \[Your organization's root URL\]/data/Customers("\[key\]")              | A single entity from the entity collection                     |
| Navigation property | \[Your organization's root URL\]/data/Customers("\[key\]")/Reservations | The navigation from a customer to that customer's reservations |
| Property            | \[Your organization's root URL\]/data/Customers("\[key\]")/FirstName    | The customer's first name                                      |

## OData services

The product provides an OData REST endpoint. This endpoint exposes all the data entities that you mark as **IsPublic** in the Application Object Tree (AOT). It supports complete CRUD (create, retrieve, update, and delete) functionality that you can use to insert and retrieve data from the system. Detailed labs for this feature are on the LCS methodology.

> [!NOTE]
> When working with data entities by using OData, you must provide all fields in the entity key to make a successful OData call.

Code examples for consuming OData services are available in the [Microsoft Dynamics AX Integration GitHub repository](https://github.com/Microsoft/Dynamics-AX-Integration/tree/master/ServiceSamples/ODataConsoleApplication).

### Supported features from the OData specification

The following high-level features are enabled for the OData service, per the [OData specification](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html).

- CRUD support works through HTTP verb support for POST, PATCH, PUT, and DELETE.
- Available query options are:

  - $filter
  - $count
  - $orderby
  - $skip
  - $top
  - $expand (only first-level expansion is supported)
  - $select

- The OData service supports serving driven paging with a maximum page size of 10,000.

For more information, see: [OData actions that are bound to entities](https://docs.oasis-open.org/odata/odata/v4.0/errata02/os/complete/part1-protocol/odata-v4.0-errata02-os-part1-protocol-complete.html#_Toc406398355).

#### Filter details

The $filter option has built-in operators:

- Equals (eq)
- Not equals (ne)
- Greater than (gt)
- Greater than or equal (ge)
- Less than (lt)
- Less than or equal (le)
- And
- Or
- Not
- Addition (add)
- Subtraction (sub)
- Multiplication (mul)
- Division (div)
- Decimal division (divby)
- Modulo (mod)
- Precedence grouping ({ })

You can also use the **Contains** option with $filter requests. It's implemented as a wildcard character. For example: `http://host/service/EntitySet?$filter=StringField eq '*retail*'`

The operators `has` and `in` aren't supported.

For more information, see [OData operators](https://docs.oasis-open.org/odata/odata/v4.0/errata02/os/complete/part2-url-conventions/odata-v4.0-errata02-os-part2-url-conventions-complete.html#_Toc406398096).

#### Batch requests

The OData service supports batch requests. For more information, see [OData batch requests](https://docs.oasis-open.org/odata/odata/v4.0/errata02/os/complete/part1-protocol/odata-v4.0-errata02-os-part1-protocol-complete.html#_Toc406398359).

#### Metadata annotations

The `/data/$metadata` endpoint provides annotations. The `$metadata` supports `EnumType`.

:::image type="content" source="./media/metadata.png" alt-text="Screenshot of EnumType metadata.":::

### Cross-company behavior

By default, OData returns only data that belongs to the user's default company. To see data from outside the user's default company, specify the **?cross-company=true** query option. This option returns data from all companies that the user has access to.

**Example:** `http://[baseURI]/data/FleetCustomers?cross-company=true`

To filter by a particular company that isn't your default company, use the following syntax:

`http://[baseURI]/data/FleetCustomers?$filter=dataAreaId eq 'usrt'&cross-company=true`

### Validate methods

The following table summarizes the validate methods that the OData stack implicitly calls on the corresponding data entity.

| OData | Methods (listed in the order in which they're called) |
|-------|---------------------------------------------------------|
| Create | <ol><li><strong>Clear()</strong></li><li><strong>Initvalue()</strong></li><li><strong>PropertyInfo.SetValue()</strong> for all specified fields in the request</li><li><strong>Validatefield()</strong></li><li><strong>Defaultrow</strong></li><li><strong>Validatewrite()</strong></li><li><strong>Write()</strong></li></ol> |
| Update | <ol><li><strong>Forupdate()</strong></li><li><strong>Reread()</strong></li><li><strong>Clear()</strong></li><li><strong>Initvalue()</strong></li><li><strong>PropertyInfo.SetValue()</strong> for all specified fields in the request</li><li><strong>Validatefield()</strong></li><li><strong>Defaultrow()</strong></li><li><strong>Validatewrite()</strong></li><li><strong>Write()</strong></li></ol> |
| Delete | <ol><li><strong>Forupdate()</strong></li><li><strong>Reread()</strong></li><li><strong>checkRestrictedDeleteActions()</strong></li><li><strong>Validatedelete()</strong></li><li><strong>Delete()</strong></li></ol> |

## Exposing OData entities

OData entities are based on the concept of an updatable view. When you set the **IsPublic** property for an updatable view to **TRUE**, you expose that view as a top-level OData entity.

## Setting navigation properties between OData entities

A navigation property describes links between OData entities. Navigation properties describe the navigation from one end of an association to the other end.

#### Adding actions on OData entities

Actions let you inject behaviors into the data model. To add actions, add a method to the updatable view, and decorate that method with specific attributes. Here's an example.

```xpp
[SysODataActionAttribute("CalcMaintenanceDuration", true)]
public int CalculateMaintenanceDuration()
{
    //do something
    return 0;
}
```

In this example, the **SysODataActionAttribute** class decorates the **CalculateMaintenanceDuration** method that the action exposes. The first argument of the attribute is the publicly exposed name of the action, and the second argument indicates whether this action is always available. Methods that the action exposes can return any primitive type or another public updatable view. After you expose this method, it appears in the OData $metadata. Here's an example.

```xml
<Action Name="CalcMaintenanceDuration" IsBound="true">
    <Parameter Name="ViewMaintenance" Type="Microsoft.Dynamics.AX.Resources.ViewMaintenance"/>
    <ReturnType Type="Edm.String" />
</Action>
```

The following example of an OData action takes in a parameter and returns a list.

```xpp
[SysODataActionAttribute("GetColors", true),
    SysODataCollectionAttribute("return", Types::Record, "CarColor")]
public List GetColorsByAvailability(boolean onlyAvailableVehicles)
{
    List returnList = new List(Types::Record);
    // do something
    return returnList;
}
```

In this example, the **SysODataCollectionAttribute** class enables OData to expose strongly typed collections from X++. This class takes in three parameters:

- The name of the parameter that is a list (Use **return** for the return value of the method.)
- The X++ type of the members of this list
- The public name of the OData resource that is contained in the collection

After you expose these actions, you can invoke them from the service root URL.

You can find actions that are defined on data entities by searching for the **SysODataActionAttribute** attribute in the source code.

## Querying or browsing an OData endpoint

OData provides an SQL-like language that you can use to create rich queries against the database. You can filter the results so they include only the data items that you want. To create a query, append criteria to the resource path. For example, you can query the **Customers** entity collection by appending the following query options in your browser.

| URL                                                                        | Description |
|----------------------------------------------------------------------------|-------------|
| \[Your organization's root URL\]/data/Customers                            | List all the customers. |
| \[Your organization's root URL\]/data/Customers?$top=3                     | List the first three records. |
| \[Your organization's root URL\]/data/Customers?$select=FirstName,LastName | List all the customers, but show only the first name and last name properties. |
| \[Your organization's root URL\]/data/Customers?$format=json               | List all the customers in a JSON format that JavaScript clients can use. |

The OData protocol supports many similar filtering and querying options on entities. For the full set of query options, see [Windows Communication Foundation](/dotnet/framework/wcf/).

## Using enums

Enums are under the namespace **Microsoft.Dynamics.DataEntities**. To include enums in an OData query, use the following syntax.

`Microsoft.Dynamics.DataEntities.Gender'Unknown'`

`Microsoft.Dynamics.DataEntities.NoYes'Yes'`

The following example query uses the above enum values.

`https://environment.cloud.onebox.dynamics.com/data/CustomersV3?\$filter=PersonGender eq Microsoft.Dynamics.DataEntities.Gender'Unknown'`

`https://environment.cloud.onebox.dynamics.com/data/Currencies?\$filter=ReferenceCurrencyForTriangulation eq Microsoft.Dynamics.DataEntities.NoYes'No'`

The operations that enums support are **eq** and **ne**.

## Authentication

OData uses the same authentication stack as the server. For more information about authentication, see [Service endpoints overview](services-home-page.md).

## Tips and tricks

### Run multiple requests in a single transaction

The OData batch framework uses *changesets*. Each changeset contains a list of requests that the framework treats as a single atomic unit. In other words, either all the requests run successfully or, if any request fails, none of the requests run. The following example shows how to send a batch request that has a list of requests in a single changeset.

The **SaveChangesOptions.BatchWithSingleChangeset** option in **SaveChanges()** helps guarantee that all requests are bundled into a single changeset.

```xpp
public static void CreateProductColors(Resources context)
{
    var productColorsCollection = new DataServiceCollection<ProductColor>(context);

    var color1 = new ProductColor();
    productColorsCollection.Add(color);
    color1.ColorId = "New Color1"; // set any other properties needed

    var color2 = new ProductColor();
    productColorsCollection.Add(color1);
    color2.ColorId = "New Color2"; // set any other properties needed

    context.SaveChanges(SaveChangesOptions.BatchWithSingleChangeset);
}
```

### Prevent unset records from being posted when you use an OData client

When you create a new record by using an OData client, as shown in example 1, the client includes properties that you don't set in the body of the request and assigns default values to them. To prevent this behavior and post only properties that you set explicitly, use the **SaveChangesOptions.PostOnlySetProperties** option in **SaveChanges()**, as shown in example 2.

**Example 1**

```xpp
public static void CreateVendor(Resources context)
{
    var vendorCollection = new DataServiceCollection<Vendor>(context);
    var vendor = new Vendor();
    vendorCollection.Add(vendor);
    // set properties
    context.SaveChanges();
}
```

**Example 2**

```xpp
public static void CreateVendor(Resources context)
{
    var vendorCollection = new DataServiceCollection<Vendor>(context);
    var vendor = new Vendor();
    vendorCollection.Add(vendor);
    // set properties

    // Save specifying PostOnlySetProperties flag
    context.SaveChanges(SaveChangesOptions.PostOnlySetProperties);
}
```

### Handling duplicate names between enums and entities in metadata

Enums and entities sometimes share the same name. This name duplication results in OData client code generation errors. To recover from this error, use the [helper code in GitHub](https://github.com/Microsoft/Dynamics-AX-Integration/blob/master/ServiceSamples/ODataConsoleApplication/MetadataDocumentValidator.cs) to identify duplicate name instances that you must remove. You can use the generated metadata document for further processing of the OData logic on the client side.

### Array fields

OData doesn't support array fields in entities. Consider this limitation when you design entities for use with OData.

### After restarting AOS, the first OData call might take a long time to process

The first OData call that an AOS processes after you restart it might take a long time because the metadata isn't cached. You can avoid this latency by warming up OData when AOS starts. For more information, see [Build OData metadata cache when the AOS starts](../sysadmin/odata-warmup.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
