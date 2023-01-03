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

When dual-write is invoked to propagate data changes from Finance and Operations apps to Dataverse, it uses the specific team as the owner of the record 
to be dual-written in Dataverse. The team in question will require at least read privilege for the Dataverse entity, otherwise the following exceptions will be 
thrown from the Dataverse platform.

```
Unable to write data to entity
...
Principal team (Id=***, ..., is missing prvReadcol_*** privilege (Id=***) on OTC=***.
```

Follow the steps to assign proper permission privilege to the team to allow dual-write to work as expected.

1. Log on to the Dataverse environment (e.g. ttps://???.dynamics.com) using a web browser

2. In another tab, issue 

```
https://???.crm.dynamics.com/api/data/v9.0/teams?$select=name&$filter=teamid eq [ID]
```

The value of **[ID]** should be the same as the one shown in the error message

3. Record the **name** of the team

4. Log on to Power Platform Admin Center (https://admin.powerplatform.microsoft.com/environments)

![Principal Team Security Role1](/media/PrincipalTeam-Security-Role-1.png)

5. Locate the click the power apps environment associated with the Dataverse environment

6. From **Access** tab, click **See all** under **Teams**

![Principal Team Security Role2](/media/PrincipalTeam-Security-Role-2.pngg)

7. From the list, select the team with name that matches the one recorded at step 3.

8. From the command bar, select **Manage Security Roles**

![Principal Team Security Role3](/media/PrincipalTeam-Security-Role-3.png)

9. From the list of the security roles, select one that has the read privilege to the Dataverse entity. Alternatively you can create a custom security role 
with the read permissions to the Dataverse table and select it from the list of security roles.  

![Principal Team Security Role4](/media/PrincipalTeam-Security-Role-4.png)

10. For more information on Dataverse security role and privilege, please refer to https://docs.microsoft.com/en-us/power-platform/admin/database-security.





