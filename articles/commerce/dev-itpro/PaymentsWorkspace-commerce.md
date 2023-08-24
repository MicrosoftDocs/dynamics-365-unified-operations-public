---
title: Payment workspace
description: This article describes the Payment workspace in Microsoft Dynamics 365 Commerce headquarters.
author: BrianShook
ms.date: 09/01/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: brshoo
ms.search.validFrom: 2023-08-15

---

# Payment workspace

[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]

This article describes the **Payment** workspace in Microsoft Dynamics 365 Commerce headquarters.

Dynamics 365 Commerce headquarters includes a collection of workspaces to assist users with pages that include common tasks, links, and tiles. These workspaces provide aggregated views that help users perform their jobs more efficiently. 

Starting in Commerce version 10.0.37, a **Payment** workspace has been added to Commerce headquarters to provide combined views of common payment connector and payment method processing configurations in one place. In addition to common channel and environment payment configuration views, the **Payment** workspace includes links for users to easily navigate to headquarters payment configuration pages. 

<!--This workspace assists in configuring, diagnosing configuration issues, and navigating through to the multiple pages within headquarters in which common payment configurations occur.-->

## The Payment workspace view

You can access the **Payment** workspace via the headquarters menu under the **Workspaces** section. It can also be navigated to using the **Retail and Commerce \> Channels \> Payment workspace** path in headquarters **Modules** menu section. 

### Payment configurations

In the **Payment** workspace, the main section for **Payment configurations** includes numerous view tabs which populate the grid view with relevant data. These views are:

- **All call centers** - Displays all the payment service payment connectors configurations as set up in **Accounts receivable \> Payments setup \> Payment services**, which apply to all the call center channels in the environment associated with the legal entity. 
- **Online stores** - Displays all online channel payment connector configurations as set up in the **Retail and Commerce \> Channels \> Online stores** payment accounts. All configured online channel payment connector details are listed in this view.
- **All stores** - Displays all retail store payment connector configurations in the **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profile** EFT service payment connector settings. This view breaks out each configuration setting down to the PIN pad IP address. 
- **Card types** - Displays all card type items configured for the legal entity, as well as any bin-range variations that are set per card type.
- **Available connectors** - Displays a simple list of all payment connectors configured in the environment that can be used for **Processor payment mapping methods**.  

The details displayed are relevant to the configurations of the organizational legal entity selected in the drop-down list on the top-right in headquarters. No sensitive data (such as merchant security keys) is included in the column options. 

### Workspace grid view

The workspace grid views have common workspace view capabilities, such as allowing for grid column adjustments and saved view arrangements. Data in the views can be exported, and columns can be inserted, frozen, or hidden. Organizing views allows users to quickly assess common configuration details relevant to their assigned coverage, and coordinate with IT administrators for support cases as needed.

Values listed within the view grid are not directly editable from the grid. Users must still set or edit values from the respective area configuration pages. Some column values include quick links to their contextually relevant configuration pages within headquarters. Where available, hovering over a value in the grid view displays an underlined link (or links) with a **Click to follow the link** tooltip. 

Examples include:

- **All call centers** - Links to **Payment service**. 
- **Online stores** - Links to **Name**, **Payment method link**.
- **All stores** - Links to **Store number**, **Register number**, **Hardware profile**.
- **Card types** - Links to **Card ID**.

### Links

The **Links** section includes common channel and channel setup links to the most common payment relevant configuration pages, including the following:

- **All call centers**
- **All stores**
- **Online stores**
- **Registers**
- **Card numbers**
- **Card types**
- **Hardware profiles**
- **Payment methods**
- **Payments services**
