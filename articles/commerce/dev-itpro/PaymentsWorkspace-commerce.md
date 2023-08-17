---
title: Payments Workspace in Headquarters
description: This article provides an overview of the new Payments Workspace in Headquarters for Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 08/15/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2023-08-15
ms.dyn365.ops.version: 10.0.37
ms.search.industry: Retail
---
# Payment workspace in Headquarters

[!include[banner](../includes/banner.md)]

This article provides an overview of the new Payment workspace in Headquarters for Microsoft Dynamics 365 Commerce.

Dynamics 365 Finance and Operations includes a collection of workspaces to assist users with pages containing common tasks, links, tiles, and more. These workspaces provide easier or aggregated views to perform their jobs more efficiently. In 10.0.37, Commerce has now added a **Payment workspace** to assist in payment connector and payment method configuration views for a one-stop view of common configurations for payment processing. The **Payment workspace** includes common channel and environment payment configuration views as well as common links to easily navigate to Headquarter payment configuration pages. This workspace assists in configuring, diagnosing configuration issues, and navigating through to the multiple pages within Headquarters in which common payment configurations occur.

## The Payment Workspace View

The **Payment workspace** can be found in the Headquarters' menu under the **Workspaces** section. It can also be navigated to using the **Retail and Commerce > Channels > Payment workspace** path in Headquarters **Modules** menu section. 

### Payment configurations

In the **Payment workspace**, the main section for **Payment configurations** includes numerous view tabs which populate the grid view with relevant data. These views are:

- **All call centers** - Displays all the Payment Service payment connectors configurations in **Accounts receivable > Payments setup > Payment services**. The payment configurations in Payment services apply to all the Call Center channels in the environment set up for the Legal Entity. 
- **Online stores** - Displays all Online channel payment connector configurations as configured in the **Retail and Commerce > Channels > Online stores** payment accounts. All configured online channel payment connector details are displayed in this view.
- **All stores** - Displays all Retail store payment connector configurations in the **Retail and Commerce > Channel setup > POS setup > POS profiles > Hardware profile** EFT service payment connector settings. This view breaks out each configuration setting down to the PIN pad IP. 
- **Card types** - This view shows all card type items configured for the entity, as well as any bin-range variations set per card type.
- **Available connectors** - This view is a simple list of all payment connectors set in the environment which can used for **Processor payment mapping methods**.  

Details displayed are relevant to the configurations set per the Organizational Legal Entity set in the top-right context of Headquarters (or 'cmp' parameter in the Headquarters URL set in the browser navigational toolbar). No sensitive data, such as merchant security keys, are included in the column options. 

#### About the Grid View

The workspace grid views follow common workspace view capabilities. Views allow for grid column adjustments and saved view arrangements. Data in the views can be exported, columns can be inserted, frozen, or hidden. Organizing views allow workers to quickly assess common configuration details relevant to their assigned coverage or for coordinating with IT Admins for support cases.

Values within the view grid are not editable in the grid directly. Values must continue to be set or edited in the specific pages the configurations are instructed to be set. Some column values include quick-links to their contextually relevant configuration pages within Headquarters. Where available, hovering over the value in the grid view will then show the link underlined with a tooltip to "Click to follow the link". Examples include:

- All call centers > **Payment service** 
- Online stores > **Name** and **Payment method link**
- All stores > **Store number**, **Register number**, **Hardware profile**
- Card types > **Card ID**

### Links

The **Links** section includes common **Channel** and **Channel Setup** links to the most common payment relevant configuration pages. These options include:

- All call centers
- All stores
- Online stores
- Registers
- Card numbers
- Card types
- Hardware profiles
- Payment methods
- Payments services