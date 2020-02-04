---
# required metadata

title: Support for external gift cards
description: This topic provides information about the support for external gift cards that is now available in Microsoft Dynamics 365 Commerce.
author: sericks007
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod:
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
 # ROBOTS: 
audience: Developer
ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: retail
ms.author: ivanv
ms.search.validFrom: 2017-10-02
ms.dyn365.ops.version: Application update 4
---

# Support for external gift cards

[!include [banner](../../includes/banner.md)]

To provide a seamless experience for their customers, retailers want to be able to accept a wide variety of payment methods. Gift cards are one of the most frequently used payment methods after cash and credit cards. An important requirement for many retailers is the ability to accept various types of gift cards, from various providers, at the point of sale (POS).

Microsoft Dynamics 365 Commerce now supports external gift cards. Therefore, retailers can accept third-party gift cards from gift card providers such GiveX by using the POS. To take advantage of this functionality, you must have an account with an external gift card service provider. This functionality differs from the out-of-box gift card support that the solution offered.

The out-of-box Verifone Payment connector has also been updated so that it supports the functionality for external gift cards. The initial update enables integration with GiveX.

The external gift card must be configured for both the Headquarters and the POS. Before the gift card can be configured, the retailer must have an account with an external gift card service provider.

## Headquarters configuration

1. In Dynamics 365 Commerce Headquarters, search for **Hardware profiles** to open the **POS hardware profile** page.
2. On the **POS hardware profile** page, follow these steps:

   1. On the navigation bar on the left side of the page, select **Virtual**.
   2. Select **Edit**.
   3. On the **ETF service** FastTab, in the **Connectors** grid, select the first entry, **TestConnector**.
   4. In the **Supported Tender Types** field, add **GiftCard**.

       ![Adding GiftCard to the list of supported tender types](./media/01.png)

   5. Select **Save**.

      > [!NOTE]
      > You can also use the **New** button to create multiple payment connectors. In this way, you can take advantage of the support for multiple connectors that has been added to the solution. You can then have different payment connectors for different payment methods. For example, all credit cards can be processed through one connector, but the gift card can be processed through a different connector.

### Card Types

1. Search for **Card Types** 
2. Click **New**, add the following values, and then click **Save**:

| Field Name     | Value              |
|----------------|--------------------|
| Card ID        | EXTGC              |
| Card type name | External Gift Card |
| Card types     | Gift card          |
| Card issuer    | *Any description*  |

### Payment Methods

1. Search for **Payment methods** to open the **Payment methods** page.
2. Click **New**, and then follow these steps:

    1. In the **Payment method** field, enter **12**.
    2. In the **Payment method name** field, enter **External Gift Card**.
    3. In the **Default function** field, select **Card**.
    4. Select **Save**.

3. Open the **All stores** page.
4. In the list, select the **Houston** store.
5. On the Action Pane, click **Set up** &gt; **Payment methods**.
6. Click **New**.
7. In the **Payment method** field, enter **12**. The **Payment method name** and **Function** fields should then be set automatically.
8. On the **General** FastTab, set the following fields:

    - Set the **Operation name** field to **Pay gift card**.
    - Set the **Connector name** field to **TestConnector**.

9. On the **Posting** FastTab, set the **Gift card item number** field to **0010**.

    ![Setting the Gift card item number field](./media/05_02.png)

10. Click **Save**.
11. Click **Card setup** and click **New** to map the gift card created in step 4 to the newly created external gift card payment method.

### Update button grid

1. Go to the **Button grid** page.
2. In the navigation bar on the left side of the page, search for **F2S1M**, and select the filtered option.
3. On the Action Pane, click **Designer** to download the button designer application.
4. When the grid designer appears, right-click on an empty (gray) area, and then click **New button**.

    ![New button](./media/07.png)

5. Right-click the new button, and then select **Button properties**.
6. Set the **Action**, **Payment type**, and **Text on button** properties according to the following matrix.

    | Action            | Payment type       | Text on button        |
    |-------------------|--------------------|-----------------------|
    | Issue gift card   | External Gift Card | Ext Issue gift card   |
    | Add to gift card  | External Gift Card | Ext Add to gift card  |
    | Gift card balance | External Gift Card | Ext Gift card balance |
    | Pay gift card     | External Gift Card | Ext Pay gift card     |

    When you've finished, your button layout should resemble the following illustration.

    ![Completed button layout](./media/10.png)

7. Close the designer.
8. Search for **Distribution Schedule**.
9. In the navigation bar on the left side of the page, search for **1090**, **1115**, and **1070**.
10. On the Action Pane, click **Run now**.
11. Check the status of the job by searching for **Download sessions**.
12. Wait until **Applied** appears next to all the jobs, and then close the browser.

    > [!NOTE]
    > If you are using Retail Commerce Scale Unit (RCSU) that is located in the store, you need to perform an IIS rest to clear the cache. You can either do this through the IIS application or open an admin Command Prompt window and enter `iisreset`. Otherwise, wait for the RCSU to be updated.

## Update merchant properties

1. In File Explorer, go to **C:\\Program Files (x86)\\Microsoft Dynamics 365\\70\\Retail Hardware Station\\ConfigurationUtility**.
2. Run the **HardwareStationConfigurationUtility** executable program.
3. Configure the utility by entering the correct Commerce Scale Unit URL, and then select **Install**.
4. To verify that the download was successful, go to **C:\\ProgramData\\Microsoft Dynamics AX\\Retail Hardware Station**, and look at the timestamp of the **MerchantInformation.xml** file. It should be very recent.

## Configure and test Modern POS

1. Start the Modern POS (MPOS) application.
2. Sign in by using the standard credentials.
3. When you're prompted, select **Perform a non-drawer operation**.
4. On the main screen, select **Select hardware station**.
5. On the bar on the right side of the page, select **Manage**.
6. Turn on **Virtual Peripherals**, and then select **OK**.
7. In the **Available paired stations** field, select **Virtual Peripherals**.
8. You're prompted to either open a new shift or perform non-drawer operations. You can now open a new shift.
9. On the main screen, select **Current transaction**.
10. Select **Gift cards**.
11. Select **Ext Issue gift card**.
12. Enter a number that starts with **9**, and then provide an amount.
13. After items are added to the cart, you can pay by using cash or a card.

## Troubleshooting 

### Issue: An error occurs when you start the HardwareStationConfigurationUtility program

1. From an elevated command prompt, open the **HardwareStationConfigurationUtility.exe.config** file in Notepad.
2. In the file, follow these steps:

    1. Replace the **DataServiceUrl** value with the correct Commerce Scale Unit URL.
    2. Verify that the **AADLogonUrl** value is correct.

3. Save and close the file.
4. Restart the utility.

### Issue: A token error occurs when you try to pair virtual peripherals

1. Exit MPOS.
2. Go to **C:\\Program Files (x86)\\Microsoft Dynamics 365\\70\\Retail Hardware Station\\Package**.
3. From an elevated command prompt, open the **Web.config** file in Notepad.
4. Replace the **RetailServer** value with the correct Commerce Scale Unit value.
5. Save and close the file.
6. Restart MPOS.
7. If the issue persists, exit MPOS, use Task Manager to end any instances of dllhost.exe that are running, and then do another reset of Internet Information Services (IIS).
