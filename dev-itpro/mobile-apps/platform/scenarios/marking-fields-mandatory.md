---
# required metadata

title: Make a field mandatory using workspace classes
description: 
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


# Marking a field as mandatory using workspace classes
Support has been added for inferring properties such as mandatory, field length, and type when using Operations mobile app designer to select fields for actions.

The workspace classes can be used to update these properties and, for example, mark/un-mark a field as mandatory.

Consider an action for creating customer. The designer has automatically inferred that "Name" is a mandatory field.

| ![alt text](media/workspace-api/MarkFieldAsMandatoryDesigner.png "Action showing fields")  | ![alt text](media/workspace-api/MarkFieldAsMandatoryAction.png "Action with mandatory field marked")|
|--|--|

The workspace class can be used to mark "Delivery terms" field as mandatory using the following steps.

1. Get the control name using app designer. For this demo the control name is "DynamicDetail_DlvTerm"
2. Add the following code to set the mandatory property for the control. Note that we are using the reflection based setProperty method to set mandatory property.

```javascript
public SysAppWorkspaceMetadata getWorkspaceMetadata()
{
    SysAppWorkspaceMetadata appMetadata;

    appMetadata = super();

    var createCustAction = appMetadata.getAction("createCust");
    this.setCustAccountMandatory(createCustAction);

    return appMetadata;
}

private void setCustAccountMandatory(SysAPpActionMetadata _createCustAction)
{
    var custAccount = +createCustAction.getControl("DynamicDetail_DlvTerm");
    custAccount.setProperty("Mandatory", true);
}
```

3. Build the solution and then refresh app metadata on the mobile app.

As shown below, the Delivery terms field is now marked as Mandatory.

![alt text](media/workspace-api/MarkFieldAsMandatoryFinal.png "Delivery terms field marked as mandatory")
