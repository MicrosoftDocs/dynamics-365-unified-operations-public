---
# required metadata

title: Mapping Sales Order Status Setup
description: 
author:  robinarh
manager: AnnBe
ms.date: 06/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: 
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-06-25
---

# Mapping Sales Order Status Setup

[!include [banner](../../includes/banner.md)]

The sales order status fields work differently have different Enum values in Dynamics 365 Supply Chain Management and in Dynamics 365 Sales. To effectively map these fields additional setup is required.

## Status fields in Dynamics 365 Supply Chain Management vs Dynamics 365 Sales

This section describes the different status fields and the Enum values they can have as well as how they are mapped.

### Dynamics 365 Supply Chain Management

In Dynamics 365 Supply Chain Management we have two status related fields that are relevant here.

  - Status – Specifies the overall status of the order

| **Status Value (Enum)** |
| ----------------------- |
| Open Order              |
| Delivered               |
| Invoiced                |
| Cancelled               |

  - Document Status - specifies what the latest document generated for
    the order is. This field can have the following values:

| **Document Status Value (Enum)** |
| -------------------------------- |
| Confirmation                     |
| Picking List                     |
| Packing Slip                     |
| Invoice                          |

### Dynamics 365 Sales

In Dynamics 365 Sales we have the following status related fields:

  - Status – the overall status of the order

| **Status Value (Enum)** |
| ----------------------- |
| Active                  |
| Submitted               |
| Fulfilled               |
| Invoiced                |
| Cancelled               |

  - Processing Status – a status field that was introduced to map the
    status with D365 SCM

| **Processing Status Value** | **SCM Status** | **SCM Document Status** |
| --------------------------- | -------------- | ----------------------- |
| Active                      | Open Order     | None                    |
| Confirmed                   | Open Order     | Confirmation            |
| Picked                      | Open Order     | Picking List            |
| Partially Delivered         | Open Order     | Packing Slip            |
| Delivered                   | Delivered      | Packing Slip            |
| Partially Invoiced          | Delivered      | Invoice                 |
| Invoiced                    | Invoiced       | Invoiced                |
| Cancelled                   | Cancelled      | n/a                     |

### Mapping

| **Processing Status** | **CE Status** | **F\&O Status** |
| --------------------- | ------------- | --------------- |
| Active                | Active        | Open Order      |
| Confirmed             | Submitted     | Open Order      |
| Picked                | Submitted     | Open Order      |
| Partially Delivered   | Active        | Open Order      |
| Partially Invoiced    | Active        | Open Order      |
| Partially Invoiced    | Fulfilled     | Delivered       |
| Invoiced              | Invoiced      | Invoiced        |
| Cancelled             | Cancelled     | Cancelled       |

# Setup Steps

For the prerequisite, we need to enable IsSOPIntegrationEnabled” and
“isIntegrationUser" two attributes.

For the IsSOPIntegrationEnabled:

1.  Go to (replace \<test-name\> with the companies crm link)

2.  Find the organizationid in the page. Get the value of
    organizationid.

![](media/image1.jpeg)

3.  Open browser’s console in CRM page. Run following script, replace
    the organizationid with the value we got from last step.

Xrm.WebApi.updateRecord("organization",
"d9a7c5f7-acbf-4aa9-86e8-a891c43f748c", {"issopintegrationenabled" :
true}).then(

    function success(result) {

        console.log("Account updated");

        // perform operations on record update

    },

    function (error) {

        console.log(error.message);

        // handle error conditions

    }

);

![](media/image2.jpeg)

4.  Then we can validate if we enable “IsSOPIntegrationEnabled"
    Successfully. Use step 1’s link to check its value.

![](media/image3.jpeg)

For the “isIntegrationUser":

1.  In CRM, navigate to Setting -\> Customization -\> Customize the
    System, choose User entity, open Form -\> User

![](media/image4.jpeg)

2.  Find “Integartion user node” on right Field Explorer, double click
    it to add it on the form. Then save it.

![](media/image5.jpeg)

3.  In CRM, go to Setting -\> Security -\> Users, change Enabled Users
    to Application Users.

![](media/image6.jpeg)

4.  Click two DualWrite IntegrationUser, change integration user mode to
    Yes.

![](media/image7.jpeg)

![](media/image8.jpeg)

Once you’ve completed this setup your sales orders will be mapped
correctly.
