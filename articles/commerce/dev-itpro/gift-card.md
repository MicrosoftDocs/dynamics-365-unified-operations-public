---
# required metadata

title: Support for external gift cards
description: This topic provides information about the support for external gift cards that is now available in Microsoft Dynamics 365 Commerce.
author: sericks007
manager: AnnBe
ms.date: 02/21/2020
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

This topic explains how to set up external gift cards in Retail Modern POS, the call center, and the storefront.

> [!NOTE]
> Support for external gift cards in the call center is new in version 10.0.10. Support for external gift cards in the storefront will be added in a future version. 

Microsoft Dynamics 365 Commerce supports both *internal* and *external* gift cards. Internal gift cards are managed entirely in Dynamics 365 Commerce, whereas external gift cards are administered by a third party. If a retailer's operations are run entirely in Microsoft Dynamics, internal gift cards are sometimes the best solution. For complex enterprises that span multiple countries or regions, and multiple point of sale (POS) systems, it's often best to use a third party to manage gift card balances and enable gift cards to be used across those systems.

Like support for other card payment types, support for external gift cards must be built into the payment connector that is used. The out-of-box payment connector for Adyen supports external gift cards through SVS and Givex in POS, the call center, and the e-commerce storefront.

## External gift card setup

> [!NOTE]
> Some setup steps assume that demo data is used. The steps might vary, depending on the dataset that is used.

### Card types

1. Search for **Card Types**. 
2. Select **New**, add the following values, and then select **Save**.

    | Field name     | Value                  |
    |----------------|------------------------|
    | Card ID        | **EXTGC**              |
    | Card type name | **External Gift Card** |
    | Card types     | **Gift card**          |
    | Card issuer    | Enter any description. |

### Card numbers

1. On the **Card types** page, select the newly created gift card, and then select **Card numbers**.
2. Specify the range of card numbers that should be used for external gift cards, and then select **Save**.

In the following example, if the first four digits of a card number are **6036**, the card will be mapped to the gift card that you set up in the "Card types" section of this topic.

| Field name         | Value |
|--------------------|-------|
| Card number from   | 6000  |
| Card number to     | 6999  |
| Digits to identify | 4     |

### Payment methods

1. Search for **Payment methods** to open the **Payment methods** page.
2. Select **New**, and then follow these steps:

    1. In the **Payment method** field, enter **12**.
    2. In the **Payment method name** field, enter **External Gift Card**.
    3. In the **Default function** field, select **Card**.
    4. Select **Save**.

## Store setup

1. Search for **All stores** to open the **All stores** page.
2. Select the **San Francisco** store in the list.
3. On the Action Pane, on the **Set up** tab, in the **Set up** group, select **Payment methods**.
4. Select **New**.
5. In the **Payment method** field, enter **12**. The **Payment method name** and **Function** fields should then be set automatically.
6. On the **General** FastTab, set the following fields:

    - Set the **Operation name** field to **Pay gift card**.
    - Set the **Connector name** field to **TestConnector**.

9. On the **Posting** FastTab, set the **Gift card item number** field to **0010**.

    ![Setting the Gift card item number field](./media/05_02.png)

10. Select **Save**.
11. Select **Card setup**, and then select **New** to map the gift card payment method to the newly created external gift card payment method for the San Francisco store.

## POS setup

1. In Dynamics 365 Commerce Headquarters, search for **Hardware profiles** to open the **POS hardware profile** page.
2. In the left pane, select **Virtual**.
3. Select **Edit**.
4. On the **EFT service** FastTab, in the **Connectors** grid, select the first entry, **TestConnector**.
5. In the **Supported Tender Types** field, add **GiftCard**.

    ![Adding GiftCard to the list of supported tender types](./media/01.png)

6. Select **Save**.

    > [!NOTE]
    > You can also use the **New** button to create multiple payment connectors. In this way, you can take advantage of the support for multiple connectors that has been added to the solution. You can then have different payment connectors for different payment methods. For example, all credit cards can be processed through one connector, but gift cards can be processed through a different connector.

### Update the button grid

1. Go to the **Button grid** page.
2. In the navigation bar on the left side of the page, search for **F2S1M**, and select the filtered option.
3. On the Action Pane, select **Designer** to download the button designer application.
4. When the grid designer appears, right-click on an empty (gray) area, and then select **New button**.

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
10. On the Action Pane, select **Run now**.
11. Check the status of the job by searching for **Download sessions**.
12. Wait until **Applied** appears next to all the jobs, and then close the browser.

    > [!NOTE]
    > If you are using Retail Commerce Scale Unit (RCSU) that is located in the store, you need to perform an IIS rest to clear the cache. You can either do this through the IIS application or open an admin Command Prompt window and enter `iisreset`. Otherwise, wait for the RCSU to be updated.

## Update merchant properties

> [!NOTE]
> As of version 10.0.6, this step is no longer required.

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

When you use the test connector to demonstrate support for external gift cards, you should use card number **61234** to make payments. You won't be prompted for a personal identification number (PIN). The test connector should **never** be used in production.

## External gift cards for the call center and storefront

> [!NOTE]
> This feature is new in version 10.0.9. To use it, you must set the **Enable advanced external gift card** option to **Yes** on the **Omni-channel payments** tab of the **Commerce shared parameters** page. Support for gift cards in the out-of-box storefront will be added in a future release. You should also set the **Use omni-channel payments** option to **Yes**.

![Enable advanced external gift card option](media/Configure-external-gift.png)

### Tokenization

The out-of-box implementation and Payments software development kit (SDK) support for external gift cards in the call center and storefront requires tokenization. External gift cards that are issued and managed through the back office don't include the full gift card number in the user interface (UI), and the full gift card number isn't written to the database.

External gift card numbers are always masked wherever they are saved for later reference (for example, on an order line). When external gift cards are processed, tokens are used to refer to the actual gift card number.

### Purchases and refunds

When an external gift card is used for a purchase, the tender line for the gift card is saved as a prepayment. Therefore, the funds for the purchase are captured when the order is created.

External gift cards aren't eligible for refunds. In part, this limitation is in place to prevent a refund from being given for a gift card that the user has discarded. If an unprocessed order includes an external gift card as payment, and the customer wants to cancel the order, a new gift card or some other form of credit must be issued to the customer.

Gift cards lines that are issued as part of an order can be canceled before fulfillment.

### Issuing gift cards through fulfillment

Physical gift cards and virtual gift cards have distinct fulfillment methods.

Physical gift cards are gift cards that are mapped to a mode of delivery of the **Shipping** type. They must be issued directly through the gift card provider as part of order processing. The gift card number must then be mapped to the order line as part of the pick list registration process. Next, the masked gift card number is saved back to the order line. The gift card that is issued is then activated as part of order invoicing.

Virtual gift cards are issued as part of order invoicing. When a gift card line is marked as **Packed**, it becomes eligible to be issued. Virtual gift cards are issued as part of invoicing. When invoicing occurs, the gift card number is obtained from the provider through the payment connector. The number for the activated gift card is then sent to the gift card recipient via email. When invoicing occurs, the masked gift card number is then saved back to the order line.

### Using modes of delivery for gift card products in the call center and e-commerce

In the call center and storefront channels, unlike in POS, a dedication operation isn't used to issue gift cards. Instead, gift cards are issued by adding a line item to a transaction. Specifically, gift card products for e-commerce and the call center can be either mapped to product variants or modeled as standard products.

If product variants are used, the person who creates the gift card order is prompted to select the variant. The relevant mode of delivery will then be available for that product variant.

Modes of delivery must support the type of gift card. For example, a gift card product variant of the **Physical** style must be mapped to a mode of delivery that is related to shipping. A gift card product variant of the **Email** style must be mapped to an electronic mode of delivery. The electronic mode of delivery is defined on the **Customer orders** tab of the **Commerce parameters** page.

## Setup for the call center and storefront

### Payment services setup

In the back office, on the **Payment services** page, configure the payment services account for the call center. Each payment connector requires different setup steps. The payment service that the call center uses is marked as **Default**.

#### Adyen external gift card setup

For an example that shows how to set up payment services, see the [documentation for the Adyen payment connector](https://docs.microsoft.com/dynamics365/retail/dev-itpro/adyen-connector?tabs=8-1-3).

For the call center and storefront, the Adyen connector supports the following gift cards.

| Brand   | Gift card type   | Supported | Activation       |
|---------|------------------|-----------|------------------|
| SVS     | Physical         | Yes       | Manually         |
| SVS     | Email            | Yes       | Programmatically |
| Givex   | Physical         | Yes       | Manually         |

> [!NOTE]
> In the out-of-box Adyen connector, gift cards are configured by default. To specify the gift card provider in the merchant properties of the payment connector, follow the instructions in the previously mentioned documentation.

#### Test connector external gift card setup

To set up external gift cards for the test connector, on the **Payment services** page, select **Dyn Online**, and then, in the **Supported Tender Types** field, add **;GiftCard** after **Debit**. Then select **Credit card types**, and assign a payment journal to the gift card payment method.

### Gift card product setup

The following procedure shows how to set up an external gift card by using product masters. Product masters aren't required for external gift cards. However, they can be helpful when both physical and virtual gift cards are used.

1. Search for **Style groups** to open the **Style groups** page.
2. Select **New**.
3. Enter a name (for example, **Gift**) and a description (for example, **Gift card style group**).
4. Add styles to suit the types of gift cards that are available. For example, add **Physical** and **Email** styles.
5. Save your changes.
6. Search for **Product masters** to open the **Product masters** page.
7. Select **New**.
8. Enter a product number (for example, **Gift**), and assign a retail category.
9. In the **Product dimension group** field, select **Style**.
10. Select **OK**.
11. In the product master, select the style group that you created earlier (**Gift**).
12. On the Action Pane, on the **Product** tab, in the **Set up** group, select **Dimension groups**, and then assign a storage dimension group and a tracking dimension group.
13. Select **Save**.
14. Select **Product variants**, select **Variant suggestions**, and edit the gift card variant numbers as you require.
15. Select **Create**.

    ![External gift card product variants](media/VariantSuggestions.png)

16. Select **Release products**, select **Next** two times, select a company (for example, **USRT**), and then select **Next**. Finally select **Next** to release the product master.
17. Search for **Modes of delivery** to open the **Modes of delivery** page.
18. Select the **Electronic** mode of delivery, and add the **Email** gift card variant. Make sure that applicable call centers and online channels are included.

    ![Electronic mode of delivery](media/EmailMoD.png)

19. Select a shipping mode of delivery, and add the **Physical** gift card variant.
20. Select **Save**.
21. Search for **Process delivery modes** to open the **Process delivery modes** dialog box.
22. Select **OK**.

    > [!NOTE]
    > Gift cards aren't currently supported for MPOS customer order creation or for in-store pickup.

23. Search for **Released products by category** to open the **Released product details** page.
24. Select the external gift card item.
25. Set the following values.

    | FastTab           | Field               | Value                 |
    |-------------------|-------------------- |-----------------------|
    | General           | Item model group    | MA\_Retail            |
    | Purchase          | Purchase order unit | ea                    |
    | Sell              | Sales order unit    | ea                    |
    | Sell              | Allow price adjust  | Yes                   |
    | Manage inventory  | Inventory unit      | ea                    |
    | Manage costs      | Posting item group  | Any                   |

26. Select **Save**.

For the storefront, the gift card must also be included in the storefront's assortment. For more information, see [Assortment management](https://docs.microsoft.com/dynamics365/commerce/assortments).

> [!NOTE]
> The gift card product used for external gift card setup in the point of sale should not use product masters with item variants. Gift cards based on item variants may still be used for payments, balance inquiries and cash out in the point of sale, but gift card products associated with the point of sale for issuance must be standard products. 


### Set up notification emails for virtual gift cards

For information about email setup, see [Configure email functionality](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/configure-email-functionality-in-microsoft-dynamics-ax).

For information about how to set up email notifications for Commerce, see [Set up an email notification profile](https://docs.microsoft.com/dynamics365/commerce/email-notification-profiles).

For gift cards that are issued via email, the value of the **Retail email notification type** field is **Issue gift card**.

### Call center setup

1. Search for **All call centers** to open the **Call center** page.
2. In the list, select a call center.
3. On the Action Pane, on the **Channel** tab, in the **Users** group, select **Channel users**.
4. Add a user, select **Save**, and then close the **Channel users** page.

    > [!IMPORTANT]
    > Users must be call center users when they access the **Customer service** page and create orders. Otherwise, call center capabilities won't be available.

5. Back on the **Call center** page, on the Action Pane, on the **Set up** tab, in the **Set up** group, select **Payment methods**.
6. Select **New**.
7. In the **Payment method** field, enter **12**. The **Payment method name** and **Function** fields should then be set automatically.
8. On the **General** FastTab, select the connector that should be used for the external gift card.
9. Select **Card setup**, and then select **New** to map the gift card payment method to the external gift card payment method.
10. On the **Posting** FastTab, specify general ledger accounts for the external gift cards. In demo data, **112140** can be used as the general ledger account number.
11. Select **Save**.
12. Select **Card setup**.
13. Select **New**, select the external gift card that you created earlier, and then select **Save**.
14. Close the **Card setup** page, and refresh the **Payment methods** page.
15. Select the external gift card payment method, and then, on the **General** FastTab, in the **Gift card account** section, in the **Connector name** field, assign the **TestConnector** connector.
16. On the **Posting** FastTab, assign the gift card item number.
17. Select **Save**.
18. Select **Card setup**.
19. The **Card setup** page for the internal gift card now includes two additional configuration fields: **Check expiration date** and **PIN required**. Set these fields as required by the external gift card provider.

### Issue external gift cards in the call center

1. As a call center user, search for **Customer service** to open the **Customer service** page.
2. Add a customer by using the **Search** function.
3. Select **New sales order**.
4. Select **Header**, and add a valid mode of delivery.
5. Select **Lines**.
6. In the **Item number** field, specify the gift card item number.
7. In the **Variant number** field, specify the variant number if you're using a product master.
8. In the **Unit price** field, specify the unit price for the gift card.

    > [!NOTE]
    > If modes of delivery are mapped to variants, and if **Electronic** modes of delivery are specified for any gift cards, the gift card type should automatically be set to **Email** on the **Packing** tab.

9. On the **Line details** FastTab, on the **Packing** tab, follow one of these steps:

    - For virtual gift cards, set the **Buyer name**, **Buyer email**, **Recipient name**, **Recipient email**, and **Gift message** fields.
    - For physical gift cards, set the **Buyer name**, **Recipient name**, and **Gift message** fields.

10. On the **Price and discount** tab, in the **Reason code** field, specify the reason for the price override.
11. Select **Complete**, add a payment, and submit the order.

### Pay by using external gift cards in the call center

1. As a call center user, create an order, and select **Complete**.
2. On the **Payments** FastTab, select **Add**.
3. Select the external gift card payment method, and enter the number and PIN, if applicable. For the test connector, **61234** can be used as the number, and the PIN isn't validated.
4. Use a percentage amount or a payment amount to define the payment amount.

    ![External gift card payment in the call center](media/PayinCallCenter.png)

5. Select **OK**.
6. Select **Submit** to complete the order.

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
