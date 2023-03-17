---
title: Document class sales point for Latin America
description: This topic provides information about the sales point additional settings configuration for Latin America. 
author: Fhernandez0088
ms.date: 03/17/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe 
ms.custom: bap-template
---
# Document class sales point for Latin America
You can add a configuration with sales point, account type and sequence number to any document class in this form.
## Prerequisites
The following prerequisites must be met before you can set up additional settings for sales points in Latin America organizations:
- **Sales point prefixes** must be created previously.
- **Document classes** must be configured.
- **Number sequences** must be created.
## Set up sales point additional settings for Latin America
1. Go to **Organization administration > Setup > LATAM > Document class sales point**.
2. Select **New** to create a record.
3. In the **General** section complete the following fields:

| Field                | Description                  |
|----------------------|------------------------------|
| Document class Id.   | Select a document class.     |
| Account type         | Select an account type.      |
| Sales point prefix   | Select a sales point prefix. |
| Number sequence code | Select a number sequence.    |

4. The **Printing** section is optional, it is used as additional information to be printed in the fiscal document.
## Setup a sales authorization code:
You can use the **Sales CA** button from the action pane to access the sales authorization code configuration for the sales point.
## Prerequisites:
The sales point assigned to the **Document class sales point** configuration must have the option **Validate AC** option enabled.
The document class assigned to the **Document class sales point** must have the **Require CA number** option enabled.
The document mask configuration for the document class selected must be automatic.
Steps:
1. Select the button **Sales CA** from the action pane.
2. Select **New**.
3. Complete the following fields:

| Field                   | Description                                                                   |
|-------------------------|-------------------------------------------------------------------------------|
| Authorization code (CA) | Enter the authorization code provided usually by the fiscal authority.        |
| Date from               | Select a date from when the authorization code is valid.                      |
| Date to                 | Select the date until when the authorization code is valid.                   |
| From voucher number     | Enter the minimum document number that will use the sales authorization code. |
| To voucher number       | Enter the maximum document number that will use the sales authorization code. |
4. Select **Save** and return to the **Document class sales point** form.
