---
# required metadata

title: OData
description: This article provides information about Open Data Protocol (OData) and explains how you can use OData V4 to expose updatable views.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 24841
ms.assetid: 7137b0a0-1473-4134-b769-ede5e07fd6f5
ms.search.region: Global
# ms.search.industry: 
ms.author: kuntalme
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# OData

[!include[banner](../includes/banner.md)]


This article provides information about Open Data Protocol (OData) and explains how you can use OData V4 to expose updatable views.

You can expose updatable views by using Open Data Protocol (OData) V4.

## What is OData?
OData is a standard protocol for creating and consuming data. The purpose of OData is to provide a Representational State Transfer (REST)–based protocol for Create, Read, Update, and Delete (CRUD)–style operations. OData applies web technologies such as HTTP and JavaScript Object Notation (JSON) to provide access to information from various programs. OData provides the following benefits:

-   It lets developers interact with data by using RESTful web services.
-   It provides a simple and uniform way to share data in a discoverable fashion.
-   It enables broad integration across products.
-   It enables integration by using the HTTP protocol stack.

For more information about OData, see the following webpages.

| To learn about this topic                                                        | See this webpage                                        |
|----------------------------------------------------------------------------------|---------------------------------------------------------|
| Open Data Protocol Standards                                                     | <http://www.odata.org/documentation/>  |
| Open Data Protocol: Data access for the web, the cloud, mobile devices, and more | <http://msdn.microsoft.com/en-us/data/hh237663.aspx>    |
| Open Data Protocol by example                                                    | <http://msdn.microsoft.com/en-us/library/ff478141.aspx> |

The public OData service endpoint that enables access to data in a consistent way across a broad range of clients. To see a list of all the entities that are exposed, open the OData service root URL. The URL for the service root on your system has the following format: `[Your Organization Root URL]/data`.

## Addressing
The following table describes the resources and the corresponding URLs in the Fleet Management sample.

| Resource            | URL                                                                   | Description                                                    |
|---------------------|-----------------------------------------------------------------------|----------------------------------------------------------------|
| Service endpoint    | \[Your Organization Root URL\]/data/                                  | The root service endpoint for OData entities                   |
| Entity collection   | \[Your Organization Root URL\]/data/Customers                         | The collection of all customers                                |
| Entity              | \[Your Organization Root URL\]/data/Customers(“\[key\]”)              | A single entity from the entity collection                     |
| Navigation property | \[Your Organization Root URL\]/data/Customers(“\[key\]”)/Reservations | The navigation from a customer to that customer's reservations |
| Property            | \[Your Organization Root URL\]/data/Customers(“\[key\]”)/FirstName    | The customer’s first name                                      |

## Exposing OData entities
OData entities are based on the concept of an updatable view. When the **IsPublic** property for an updatable view is set to **TRUE**, that view is exposed as a top-level OData entity.

## Setting navigation properties between OData entities
Links between OData entities are described by a navigation property. Navigation properties describe the navigation from one end of an association to the other end.

## Adding actions on OData entities
Actions provide a way to inject behaviors into the data model. To add actions, add a method to the updatable view, and decorate that method with specific attributes. Here is an example.

    [SysODataActionAttribute("CalcMaintenanceDuration", true)]
    public int CalculateMaintenanceDuration()
    {
        //do something
        return 0;
    }

In this example, the **SysODataActionAttribute** class decorates the **CalculateMaintenanceDuration** method that is exposed as an action. The first argument of the attribute is the publicly exposed name of the action, and the second argument indicates whether this action is always available. Methods that are exposed as actions can return any primitive type or another public updatable view. After this method is exposed, it appears in the OData $metadata. Here is an example.[![1\_Odata](./media/1_odata.png)](./media/1_odata.png) The following example of an OData action takes in a parameter and returns a list.

    [SysODataActionAttribute("GetColors", true),
     SysODataCollectionAttribute("return", Types::Record, "CarColor")]
    public List GetColorsByAvailability(boolean onlyAvailableVehicles)
    {
        List returnList = new List(Types::Record);
        // do something
        return returnList;
    }

In this example, the **SysODataCollectionAttribute** class enables OData to expose strongly typed collections from X++. This class takes in three parameters:

-   The name of the parameter that is a list (use **return** for the return value of the method)
-   The X++ type for the members of this list
-   The public name of the OData resource that is contained in the collection

After these actions are exposed, they can be invoked from the service root URL. To learn more about OData actions, see [Action in OData](http://odata.org/blog/actions-in-odata/).

## Querying or browsing an OData endpoint
OData enables an SQL-like language for creating rich queries against the database to include only those data items that you want in the results. To create a query, append criteria to the resource path. For example, you can query the **Customers** entity collection by appending the following query options in your browser.

| URL                                                                      | Description                                                                                   |
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| \[Your Organization Root URL\]/data/Customers                            | List all the customers.                                                                       |
| \[Your Organization Root URL\]/data/Customers?$top=3                     | List the first three records.                                                                 |
| \[Your Organization Root URL\]/data/Customers?$select=FirstName,LastName | List all the customers, but show only the first name and last name properties.                |
| \[Your Organization Root URL\]/data/Customers?$format=json               | List all the customers in a JSON format that can be used to interact with JavaScript clients. |

The OData protocol supports many similar filtering and querying options on entities. For the full set of query options, see [Windows Communication Foundation](http://msdn.microsoft.com/en-us/library/ff478141.aspx).

## Authentication
OData sits on the same authentication stack as the server. For more information about the authentication, see [Service endpoints](services-home-page.md).




