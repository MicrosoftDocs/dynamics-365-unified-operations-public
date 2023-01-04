---
title: Set up dual-write security roles and permissions
description: This article describes the special security roles and permissions that are required for dual-write to work as expected.
author: ramasri
ms.date: 1/3/2023
ms.topic: article
audience: Developer
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 2023-01-03
ms.dyn365.ops.version: F&O 10.0.30 PU54
ms.custom: "intro-internal"
---

# Set up dual-write security roles and permissions

This article describes the special security roles and permissions that are required for dual-write to work as expected. 

## Assign security roles to Microsoft Dataverse users
All Microsoft Dataverse users should be added to the **dual-write runtime configuration** security role.

## Assign security role to default owning team

In Dataverse, each business unit has a default owning team that uses the same name as the business unit. This team should be assigned to a security role that gives read permissions to all Dataverse tables that are participating in dual-write. To set up the security role, see [Manage the security roles of a team](/power-platform/admin/manage-teams.md#manage-the-security-roles-of-a-team). Global tables are associated to the root business unit. 

To locate the root business unit and default teams, follow these steps.

1. Using a web browser, log on to the Dataverse(CE/CDS/CRM) environment (for example, ```https://???.dynamics.com```).
2. On a different tab, type the following command in the URL: 
   ```https://???.dynamics.com/api/data/v9.0/businessunits?$select=name,businessunitid&$filter=_parentbusinessunitid_value%20eq%20null``` to get a result similar to the following example:

```
{
    "@odata.context": "https://???.dynamics.com/api/data/v9.0/$metadata#businessunits(name,businessunitid)",
    "value": [{
            "@odata.etag": "W/\"...\"",
            "name": "[***]",
            "businessunitid": "????????-????-????-????????"
        }
    ]
}
```
 3. Locate the **businessunitid** and record the value.
 4. On a different tab, type the following command in the URL: ```https://???.dynamics.com/api/data/v9.0/teams?$select=name,teamid&$filter=_businessunitid_value%20eq%20[businessunitid]%20and%20isdefault%20eq%20true```, and replace **[businessunitid]** with the value recorded in step 3 to get a result similar to the following example:

```
{
    "@odata.context": "https://???.dynamics.com/api/data/v9.0/$metadata#teams(name,teamid)",
    "value": [{
            "@odata.etag": "W/\"...\"",
            "name": "[***]",
            "teamid": "...",
            "ownerid": "..."
        }
    ]
}
```
The value of **name** property is the default team of the root business unit and should be used to assign the security role.

## What if you missed the security setup for the default owning team?

When dual-write is invoked to propagate data changes from finance and operations apps to Dataverse, it uses the specific team as the owner of the record 
to be dual-written in Dataverse. If the security role with read permissions isn't assigned, then the Dataverse table will throw an exception similar to the following example: 

```
Unable to write data to table
...
Principal team (Id=***, ..., is missing prvReadcol_*** privilege (Id=***) on OTC=***.
```

If the exception occurs, follow theses steps to assign proper permission to the team to allow dual-write to work as expected.

1. Log on to the Dataverse environment (for example, https://???.dynamics.com) using a web browser.

2. On a different tab, type the following URL. 

```
https://???.crm.dynamics.com/api/data/v9.0/teams?$select=name&$filter=teamid eq [ID]
```

The value of **[ID]** should be the same as the one shown in the error message.

3. Record the **name** of the team.

4. Log on to Microsoft [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/environments).

![Screenshot of Principal Team Security Role1](media/PrincipalTeam-Security-Role-1.png)

5. Locate and then select the Microsoft Power Apps environment that's associated with the Dataverse environment.

6. From the **Access** tab, select **See all** in the **Teams** section.

![Screenshot of Principal Team Security Role2](media/PrincipalTeam-Security-Role-2.png)

7. Select the team name that matches the one recorded at step 3.

8. From the command bar, select **Manage Security Roles**.

![Screenshot of Principal Team Security Role3](media/PrincipalTeam-Security-Role-3.png)

9. From the list of the security roles, select one that has the read privilege to the Dataverse table. Alternatively you can create a custom security role 
with the read permissions to the Dataverse table and select it from the list of security roles.  

![Screenshot of Principal Team Security Role4](media/PrincipalTeam-Security-Role-4.png)

For more information on Dataverse security roles and privileges, see [Configure user security to resources in an environment](/power-platform/admin/database-security.md).





