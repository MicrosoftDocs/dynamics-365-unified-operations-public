---
# required metadata

title: Customer information management for Brazil
description: This topic describes how to handle customer information in Commerce point of sale (POS) for Brazil.
author: v-ankvik
manager: annbe
ms.date: 06/07/2021
ms.topic: article
ms.prod:
ms.service: dynamics-365-retail
ms.technology:

# optional metadata

ms.search.form:
audience: Application User
# ms.devlang:
ms.reviewer: v-chgri
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Brazil
ms.search.industry: Retail
ms.author: sepism
ms.search.validFrom: 2021-01-01
ms.dyn365.ops.version: 10.0.18

---
# Customer information management for Brazil

[!include [banner](../includes/banner.md)]

This topic describes how you can handle Brazil-specific fiscal data of customers, such as the customer's CNPJ/CPF number, in Commerce point of sale (POS). You can specify the customer's tax registration numbers, name and address when you add a named customer to a cart in POS. You can also specify this data for a sales transaction manually. The customer information can then be printed on DANFE fiscal receipts, and it can be used for invoicing purposes.

For more information how to set up this functionality, see [Customer information management](latam-bra-deployment.md#customer-information-management).

## Example scenarios

The following example scenarios show how to work with customer information in POS for Brazil.

### Scenario 1: Make a sale to an anonymous customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer information**, and then select **Enter manually**.
1. Enter the customer's **CNPJ/CPF number or Foreigner ID, name, and address** and then select **OK**.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed DANFE receipt contains the customer's CNPJ/CPF number, or foreigner ID, name, and address.

### Scenario 2: Make a sale to a named customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then find and select the desired customer.
1. **Add the customer to the transaction**.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's CNPJ/CPF number, or foreigner ID, name, and address.

### Scenario 3: Make a sale to a new named customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then select **Create customer**.
1. Specify the new customer's attributes.
1. In the **CNPJ/CPF** field, enter the customer's CNPJ/CPF number.
1. In the **Foreigner ID** field, enter the customer's foreigner ID, if needed.
1. Click **Add address**. Then specify the new customer's contact information and an address.
1. Save the customer record and the customer address record, and add the customer to the transaction.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's CNPJ/CPF number, or foreigner ID, name, and address.

> [!NOTE]
> If you must specify a different customer for the transaction, you must clear the customer information and then choose another customer.

### Scenario 4: Change the customer information for a sale to a named customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then select a customer account to add it to the transaction.
1. Select **Add customer information**, and then select **Clear** to clear the customer information from the transaction.
1. Click on the **Enter manually** button.
1. Specify the customer's **CNPJ/CPF number or Foreigner ID, name, and address**, and then select **OK**.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's CNPJ/CPF number, or foreigner ID, name, and address.
