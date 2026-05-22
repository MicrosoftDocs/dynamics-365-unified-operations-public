---
title: Cash out gift card balance for a retail customer
description: Learn about the cash out gift card feature of the Microsoft Dynamics 365 Commerce Store Commerce app.
author: josaw1
ms.date: 02/17/2026
ms.topic: how-to
ms.author: josaw
ms.reviewer: v-griffinc
ms.search.region: Global
ms.search.validFrom: 2019-10-02
ms.custom: 
  - bap-template
---

# Cash out gift card balance for a retail customer

[!include [banner](../../includes/banner.md)]

This article explains the cash out gift card feature of the Microsoft Dynamics 365 Commerce Store Commerce app.

The cash out feature enables cashiers to cash out the remaining amount on a gift card. Retailers often need to exchange a low balance gift card for cash at the customer's request.

## Prerequisites

- The payment connector and corresponding payment gateway or processor must support the feature. The *payment connector* is an extension that facilitates communication between Dynamics 365 Commerce (and associated components) and a payment service. The connector described in this article uses the standard payments SDK.
- If the gift cards are external gift cards, you must configure the external gift card for both Commerce headquarters and the POS. Before you can configure the gift card, you must have an account with an external gift card service provider.

## Scenarios

The cash out gift card feature applies to a scenario where, for example, in Washington state, the cash out threshold is $5. Retailers in this case set up an operation to cash out a gift card and set the gift card balance limits under which the cash out operation can be enabled.

## Configure headquarters

To configure headquarters, follow these steps:

1. In Commerce headquarters, go to the **All stores** page.
1. In the list, select the **Houston** store.
1. On the **Action Pane**, select **Set up > Payment methods**.
1. Search for **payment methods** to open the **Payment methods** page.
1. Select the **Gift Card** payment method, and then follow these steps:

    1. In the **Amount** FastTab section, select the **Cash Out Gift Card** field.
    1. In the **Cash Out Gift Card** field, enter the **Gift card Cash out threshold** amount.
    1. Select **Save**.

    :::image type="content" source="./media/GiftCardCashout01.png" alt-text="Screenshot of setting the gift card threshold.":::

1. Open the **Button grid** page.
1. In the navigation bar on the left side of the page, search for **F2S1M**, and select the filtered option.
1. On the **Action Pane**, select **Designer** to download the button designer application.
1. When the grid designer appears, right-click on an empty (gray) area, and then select **New button**.

    :::image type="content" source="./media/07.png" alt-text="Screenshot of creating a new button.":::

1. Right-click the new button, and then select **Button properties**.
1. Set the **Action**, **Cash out gift card**, and **Text on button** properties according to the following matrix.

    | Action            | Payment type       | Text on button        |
    |-------------------|--------------------|-----------------------|
    |Cash out gift card |     Gift Card      | Cash out gift card    |

    When you finish, your button layout should resemble the following illustration.

    :::image type="content" source="./media/GiftCardCashout02.png" alt-text="Screenshot of the completed button layout with the Configure button section highlighted.":::

1. Select **OK** and close the designer.
1. Search for **Distribution Schedule**.
1. In the navigation bar on the left side of the page, search for **1090**, **1115**, and **1070**.
1. On the **Action Pane**, select **Run now**.
1. Check the status of the job by searching for **Download sessions**.
1. Wait until **Applied** appears next to all the jobs, and then close the browser.

## Configure and test the Store Commerce app

To configure and test the Store Commerce app, follow these steps:

1. Start the Store Commerce application.
1. Sign in by using the standard credentials.
1. When prompted, select **Perform a non-drawer operation**.
1. On the main screen, select **Select hardware station**.
1. On the bar on the right side of the page, select **Manage**.
1. Turn on **Virtual Peripherals**, and then select **OK**.
1. In the **Available paired stations** field, select **Virtual Peripherals**.
1. You're prompted to either open a new shift or perform nondrawer operations. You can now open a new shift.
1. On the main screen, select **Current transaction**.
1. Select **Gift cards**.
1. Select **Cash out gift card**.
1. Enter or scan the gift number.
1. The line for **gift card cash out** is added to the **Current transaction** for cash out.
1. Select the **Cash** payment method and the drawer opens when the transaction is completed.

    :::image type="content" source="./media/GiftCardCashout03.png" alt-text="Screenshot of the POS screen with Cash out gift card highlighted.":::

## Troubleshooting

For all general problems, always consult the Store Commerce app or Internet Information Services (IIS) Hardware Station event logs. You can find the logs under these nodes in the Windows event log:
  - **Application and Services Logs > Microsoft > Dynamics > Commerce-ModernPOS**
  - **Application and Services Logs > Microsoft > Dynamics > Commerce-Hardware Station**

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
