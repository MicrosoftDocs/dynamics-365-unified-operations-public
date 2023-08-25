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

Dynamics 365 Commerce headquarters includes a collection of workspaces to help users through pages that include common tasks, links, and tiles. These workspaces provide aggregated views that help users perform their jobs more efficiently. 

In Commerce version 10.0.37, a **Payment** workspace has been added to Commerce headquarters. This workspace provides combined views of common payment connector and payment method processing configurations in one place. The **Payment** workspace helps users diagnose configuration issues and includes links so that users can easily go to headquarters payment configuration pages. 

## The Payment workspace view

You can open the **Payment** workspace by selecting it under **Workspaces** on the headquarters menu. Alternative, select **Retail and Commerce \> Channels \> Payment workspace** under **Modules**. 

### Payment configurations

In the **Payment** workspace, the main section for **Payment configurations** includes the following tabs on the left navigation pane. These tabs fill in the grid view with relevant data when they're selected.

- **All call centers** – This view shows all payment service payment connector configurations that are set up at **Accounts receivable \> Payments setup \> Payment services** and that apply to all call center channels in the environment that's associated with the legal entity. 
- **Online stores** – This view shows all online channel payment connector configurations that are set up in payment accounts at **Retail and Commerce \> Channels \> Online stores**. All configured online channel payment connector details are listed in this view.
- **All stores** – This view shows all retail store payment connector configurations in the electronic funds transfer (EFT) service payment connector settings at **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Hardware profile**. This view breaks each configuration setting down to the IP address of the personal identification number (PIN) pad. 
- **Card types** – This view shows all card type items that are configured for the legal entity, and any Bank Identification Number (BIN) range variations that are set per card type.
- **Available connectors** – This view shows a simple list of all payment connectors that are configured in the environment and that can be used for [processor payment method mapping](../wallets.md#processor-payment-method-mapping).

The details that are shown are relevant to the configurations of the organizational legal entity that's selected in the dropdown list in the upper right in headquarters. No sensitive data (such as merchant security keys) is included in the column options. 

### Workspace grid views

The workspace grid views have common workspace view capabilities. For example, they allow for grid column adjustments and saved view arrangements. Data in the views can be exported, and columns can be inserted, frozen, or hidden. By organizing views, users can quickly access common configuration details that are relevant to their assigned coverage. This capability helps users perform tasks such as coordinating with IT administrators for support cases.

Values that are listed in the view grid aren't directly editable from the grid. You must set or edit values from the appropriate area configuration pages. 

Some column values include quick links to the contextually relevant configuration pages in headquarters. Where available, when you hover over a value in the workspace grid view, one or more underlined links are shown with a **Click to follow the link** tooltip. Here are some examples:

- **All call centers** – The tooltip includes a link to **Payment service**. 
- **Online stores** – The tooltip includes links to **Name** and **Payment method link**.
- **All stores** – The tooltip includes links to **Store number**, **Register number**, and **Hardware profile**.
- **Card types** – The tooltip includes a link to **Card ID**. 

### Links

The **Links** section includes common channel and channel setup links to the most common payment-relevant configuration pages. Here are some examples:

- **All call centers**
- **All stores**
- **Online stores**
- **Registers**
- **Card numbers**
- **Card types**
- **Hardware profiles**
- **Payment methods**
- **Payments services**
