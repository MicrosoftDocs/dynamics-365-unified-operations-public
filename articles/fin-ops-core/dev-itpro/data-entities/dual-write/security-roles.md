---
title: Dual-write Security Roles and Permissions
description: This article describes the security role permissions setup required to complete the dual-write setup.
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

# Setup Security Roles and Permissions

Special security roles and permissions are required for dual-write to work as expected. This article talks about it.

## Assign security roles to Dataverse users
All Dataverse users should be added to "dual-write runtime configuration" security role.

## Assign security role to default owning team

In Dataverse, each business unit has a default owning team and it has the same name as the business unit. This team should be assigned to a security role that gives read permissions to all Dataverse tables participating in dual-write. Follow [manage security roles guidance](https://learn.microsoft.com/en-us/power-platform/admin/manage-teams#manage-the-security-roles-of-a-team) to set this up properly. Global tables are associated to the root business unit. To locate the root business unit and default teams, follow the instructions below.

1. Log on to the Dataverse(CE/CDS/CRM) environment (e.g. ```https://???.dynamics.com```) using a web browser;
2. In the different tab, issue 
   ```https://???.dynamics.com/api/data/v9.0/businessunits?$select=name,businessunitid&$filter=_parentbusinessunitid_value%20eq%20null``` to get the result as below;

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
 3. Record the GUID value of ***businessunitid***;
 4. In another tab, issue ```https://???.dynamics.com/api/data/v9.0/teams?$select=name,teamid&$filter=_businessunitid_value%20eq%20[businessunitid]%20and%20isdefault%20eq%20true```, while replacing ***[businessunitid]*** with the value recorded at step 3, and observe the result;

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
The value of ***name*** property is the default team of the root business unit.


## What if you missed the security setup for the default owning team?

When dual-write is invoked to propagate data changes from Finance and Operations apps to Dataverse, it uses the specific team as the owner of the record 
to be dual-written in Dataverse. If the security role with read permissions is not assigned, then Dataverse table will throw an exception like below: 

```
Unable to write data to table
...
Principal team (Id=***, ..., is missing prvReadcol_*** privilege (Id=***) on OTC=***.
```

In such case, follow the steps to assign proper permission to the team to allow dual-write to work as expected.

1. Log on to the Dataverse environment (e.g. ttps://???.dynamics.com) using a web browser

2. In another tab, issue 

```
https://???.crm.dynamics.com/api/data/v9.0/teams?$select=name&$filter=teamid eq [ID]
```

The value of **[ID]** should be the same as the one shown in the error message

3. Record the **name** of the team

4. Log on to Power Platform Admin Center (https://admin.powerplatform.microsoft.com/environments)

![Principal Team Security Role1](media/PrincipalTeam-Security-Role-1.png)

5. Locate the click the power apps environment associated with the Dataverse environment

6. From **Access** tab, click **See all** under **Teams**

![Principal Team Security Role2](media/PrincipalTeam-Security-Role-2.png)

7. From the list, select the team with name that matches the one recorded at step 3.

8. From the command bar, select **Manage Security Roles**

![Principal Team Security Role3](media/PrincipalTeam-Security-Role-3.png)

9. From the list of the security roles, select one that has the read privilege to the Dataverse table. Alternatively you can create a custom security role 
with the read permissions to the Dataverse table and select it from the list of security roles.  

![Principal Team Security Role4](media/PrincipalTeam-Security-Role-4.png)

10. For more information on Dataverse security role and privilege, please refer to https://docs.microsoft.com/en-us/power-platform/admin/database-security.





