---
# required metadata

title: Mobile workspace X++ APIs
description: These APIs are available to X++ classes that extend SysAppWorkspace.
author: makhabaz
manager: AnnBe
ms.date: 05/10/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 255544
ms.assetid: f5aa0c60-25cc-4453-8df9-efab19b7e272
ms.search.region: Global
# ms.search.industry: 
ms.author: makhabaz
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3

---

# Mobile workspace X++ APIs

These APIs are available to X++ classes that extend **SysAppWorkspace**.

Workspace attribute (SysAppWorkspaceAttribute)
----------------------------------------------

| Attribute parameter | Parameter arguments       | Description                                                                                                                        |
|---------------------|---------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| AppId               | str \_appId               | Specifies the ID of the mobile workspace that the class is associated with.                                                        |
| AppResourceName     | str \_appResourceName     | Specifies the AOT Resource containing the mobile workspace metadata that the class is associated with.                             |
| WorkspaceHidden     | boolean \_workspaceHidden | Determines whether the associated mobile workspace is visible in the workspace designer and thus able to be published/unpublished. |

Workspace lifecycle hooks
-------------------------

| Method               | Arguments         | Returns                 | Description                                                                                                                                    |
|----------------------|-------------------|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| getEnumValues        | EnumName          | List                    | A method you can override to modify the enum values available to the mobile workspace.                                                         |
| getWorkspaceMetadata |                   | SysAppWorkspaceMetadata | A method you can override to modify mobile workspace metadata. Use super() to retrieve the metadata.                                           |
| onBeginAppJob        | SysAppJobRequest  | void                    | A method you can override to modify input data from an action, or data load parameters from a page, before the job is processed by the system. |
| onEndAppJob          | SysAppJobResponse | void                    | A method you can override to modify output data from the processing of an action or page, before the output is returned to the mobile app.     |

Workspace metadata classes
--------------------------

| Method              | Arguments                              | Returns              | Description                                                                                         |
|---------------------|----------------------------------------|----------------------|-----------------------------------------------------------------------------------------------------|
| addConfig           | str \_configName, object \_configValue | void                 | Allows passing custom serializable data contracts to your mobile workspace business logic.          |
| getPage             | str \_pageName                         | SysAppPageMetadata   | Allows getting the metadata for a mobile workspace page. Use super() to retrieve the page metadata. |
| getPageEnumerator   |                                        | MapEnumerator        | Allows enumerating over all page metadata instances.                                                |
| getAction           | str \_actionName                       | SysAppActionMetadata | Allows getting the metadata for a mobile workspace action.                                          |
| getActionEnumerator |                                        | MapEnumerator        | Allows enumerating over all action metadata instances.                                              |

Page metadata class
-------------------

| Method               | Arguments             | Returns               | Description                                                                                                        |
|----------------------|-----------------------|-----------------------|--------------------------------------------------------------------------------------------------------------------|
| getPageName          |                       | str                   | Allows getting a page’s name.                                                                                      |
| pageTitle            | str \_pageTitle       | str                   | The property for the page’s title.                                                                                 |
| pageDescription      | str \_pageDescription | str                   | The property for the page’s description.                                                                           |
| pageHidden           | boolean \_pageHidden  | boolean               | The property for determining whether the page is hidden from the default landing page.                             |
| pageOrder            | int \_pageOrder       | int                   | The property for determining the relative top-to-bottom positioning order of the page on the default landing page. |
| getControl           | str \_controlName     | SysAppControlMetadata | Allows getting metadata for a control on the page.                                                                 |
| getControlEnumerator |                       | MapEnumerator         | Allows enumerating over all control metadata instances on the page.                                                |

Action metadata class
---------------------

| Method               | Arguments              | Returns               | Description                                                                                                                        |
|----------------------|------------------------|-----------------------|------------------------------------------------------------------------------------------------------------------------------------|
| getActionName        |                        | str                   | Allows getting the action’s name.                                                                                                  |
| actionTitle          | str \_actionTitle      | str                   | The property for the action’s title.                                                                                               |
| actionDescription    | str actionDescription  | str                   | The property for the action’s description.                                                                                         |
| actionHidden         | boolean \_actionHidden | boolean               | The property for determining whether the action is hidden from the action bar on its associated page.                              |
| actionOrder          | int \_actionOrder      | int                   | The property for determining the relative top-to-bottom positioning order of the Action on the action bar for its associated Page. |
| getControl           | str \_controlName      | SysAppControlMetadata | Allows getting metadata for a control on the page.                                                                                 |
| getControlEnumerator |                        | MapEnumerator         | Allows enumerating over all control metadata instances on the page.                                                                |

Control metadata class
----------------------

| Method         | Arguments                  | Returns | Description                                                                                                                        |
|----------------|----------------------------|---------|------------------------------------------------------------------------------------------------------------------------------------|
| getControlName |                            | str     | Allows getting the control’s name                                                                                                  |
| controlLabel   | str \_controlLabel         | str     | The property for the control’s label.                                                                                              |
| controlHidden  | boolean \_controlHidden    | boolean | The property for determining whether the control is hidden from the page’s default design.                                         |
| controlOrder   | int \_controlOrder         | int     | The property for determining the relative top-to-bottom positioning order of the control on it’s associated page’s default design. |
| getProperty    | str \_key                  | anytype | Allows getting a property value from the control.                                                                                  |
| setProperty    | str \_key, anytype \_value | void    | Allows setting a property value on the control.                                                                                    |


