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


# Make a field mandatory using workspace classes
There is support for inferring properties such as mandatory, field length, and type when using the mobile app designer to select fields for actions. The workspace classes can be used to update these properties. For example, you might want to specify that the **Name** field is mandatory when a customer record is created, as shown in the following images.

![Action showing fields](media/workspace-api/MarkFieldAsMandatoryDesigner.png)

![Action with mandatory field marked](media/workspace-api/MarkFieldAsMandatoryAction.png)

The workspace class can be used to make the **Delivery terms** field as mandatory using the following steps.

1. Get the control name using app designer. In this example, the control name is **DynamicDetail_DlvTerm**.
2. Add the following code to set the **Mandatory** property for the control. This code uses the reflection-based **setProperty** method to set **Mandatory** property.

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

The **Delivery terms** field is marked as **Mandatory**, as shown in the following image.

![Delivery terms field marked as mandatory](media/workspace-api/MarkFieldAsMandatoryFinal.png)

