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

In Commerce version 10.0.37, a **Payment** workspace has been added to Commerce headquarters that provides combined views of common payment connector and payment method processing configurations in one place. The **Payment** workspace helps users diagnose configuration issues, and includes links for users to easily navigate to headquarters payment configuration pages. 

## The Payment workspace view

You can navigate to the **Payment** workspace via the headquarters menu under **Workspaces**, or by selecting **Retail and Commerce \> Channels \> Payment workspace** under **Modules**. 

### Payment configurations

In the **Payment** workspace, the main section for **Payment configurations** includes the following tabs in the left navigation pane that populate the grid view with relevant data when selected.

- **All call centers** - Displays all the payment service payment connector configurations set up in **Accounts receivable \> Payments setup \> Payment services** that apply to all call center channels in the environment associated with the legal entity. 
- **Online stores** - Displays all online channel payment connector configurations set up in **Retail and Commerce \> Channels \> Online stores** payment accounts. All configured online channel payment connector details are listed in this view.
- **All stores** - Displays all retail store payment connector configurations in the **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profile** EFT service payment connector settings. This view breaks out each configuration setting down to the PIN pad IP address. 
- **Card types** - Displays all card type items configured for the legal entity, and any Bank Identification Number (BIN) range variations that are set per card type.
- **Available connectors** - Displays a simple list of all payment connectors configured in the environment that can be used for [Processor payment method mapping](../wallets.md#processor-payment-method-mapping).  

The details displayed are relevant to the configurations of the organizational legal entity selected in the drop-down list at the top right in headquarters. No sensitive data (such as merchant security keys) is included in the column options. 

### Workspace grid views

The workspace grid views have common workspace view capabilities, such as allowing for grid column adjustments and saved view arrangements. Data in the views can be exported, and columns can be inserted, frozen, or hidden. Organizing views allows users to quickly access common configuration details relevant to their assigned coverage to help them perform tasks such as coordinating with IT administrators for support cases.

Values listed within the view grid aren't directly editable from the grid. You must set or edit values from the respective area configuration pages. 

Some column values include quick links to their contextually relevant configuration pages within headquarters. Where available, hovering over a value in the workspace grid view displays an underlined link (or links) with a **Click to follow the link** tooltip. Examples include:

- **All call centers** - Tooltip includes a link to **Payment service**. 
- **Online stores** - Tooltip includes links to **Name**, **Payment method link**.
- **All stores** - Tooltip includes links to **Store number**, **Register number**, **Hardware profile**.
- **Card types** - Tooltip includes a link to **Card ID**. 

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
