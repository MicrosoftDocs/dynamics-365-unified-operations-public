---
title: Display the company logo on the customer account statement
description: This article provides information about displaying the company logo on the customer account statement in Microsoft Dynamics 365 Finance.
author: JodiChristiansen
ms.author: jchrist
ms.reviewer: twheeloc 
ms.date: 04/24/2024
ms.custom:
ms.search.form: 
audience: Application User
ms.topic: how-to

---
# Display the company logo on the customer account statement

[!include [banner](../includes/banner.md)]

This article explains how to display the company logo on the customer account statement.

Prior to Dynamics 365 Finance version 10.0.40, company logo was previously added to a field in a temporary table used for the customer account statement report so it could easily be added to a report design. 
However, adding the image to the temporary table uses a lot of database space and causes serious database issues when running the report for a large number of customers.

## Add a logo
In Dynamics 365 Finance version 10.0.40 or later, the image for the company logo isn't added to the temporary table if the **Include company logo** option on the report dialog is unmarked. This ensures the 
database isn't negatively impacted.

The company logo isn't a part of the standard customer account statement report designs and no change is needed unless one or more of the report designs has been customized to add the company logo.

### Customized report
If the report is customized to add the company logo, an image can be added directly to the report layout and stored with the design. To add the company logo, follow these steps:
1. Go to the report and right-click the design and **Insert** > **Image**.
2. This approach displays the company logo even if the **Include company logo** option is unmarked. It uses the same company logo for all companies.
