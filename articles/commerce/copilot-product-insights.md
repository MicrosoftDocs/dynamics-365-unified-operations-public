# Product insights by Copilot (preview)
This article describes how store associates can use Microsoft Copilot generated product insights to quickly understand product information and deliver informed shopping assistance in the Microsoft Dynamics 365 Commerce Store Commerce app.

## Overview
Product insights by Copilot is a feature in the Dynamics 365 Commerce Store Commerce app that uses AI to generate natural language summaries of product information for store associates.

Store associates frequently interact with customers who want to understand:

- The benefits of a product
- Its availability
- Current offers or applicable discounts
- Recommended complementary items

However, modern retail environments often contain a large assortment of dynamically changing products. Learning and remembering detailed product specifications, pricing, and promotional information can be difficult—particularly for new associates.
Product insights by Copilot connects relevant product data from Dynamics 365 Commerce and presents it to store associates in an intuitive and actionable way directly within the point‑of‑sale (POS) experience.
By using Product insights by Copilot, store associates can:

- View summarized product highlights and benefits
- Understand inventory availability in real time
- Identify applicable discounts and promotions
- Discover complementary or related products

Store associates can use these insights during customer conversations to:

- Explain the value of a product
- Communicate fulfillment expectations accurately
- Offer eligible discounts
- Suggest additional products that enhance the purchase

## Enable Product insights by Copilot in the Store Commerce app

To enable Product insights by Copilot in the Store Commerce app, follow these steps:
- In Commerce headquarters, go to Feature management (Systems administration > Workspaces > Feature management), and enable the Enable Copilot in Store Commerce feature flag.
- Go to Commerce shared parameters (Retail and Commerce > Headquarters setup > Parameters > Commerce shared parameters), and enable the Enable Copilot in Store Commerce parameter.
- Go to your POS functionality profile (Retail and Commerce > Channel setup > POS setup > POS profiles > Functionality profiles).
- On the Copilot FastTab, enable Product insights.
- Run the 1070 (Channel configuration) job to sync the updated settings to the channel database.
