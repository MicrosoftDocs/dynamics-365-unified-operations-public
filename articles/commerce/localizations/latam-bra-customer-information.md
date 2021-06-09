---
# required metadata

title: Manage customer information in POS for Brazil
description: This topic describes how to manage customer information in Commerce point of sale (POS) for Brazil.
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
# Manage customer information in POS for Brazil

[!include [banner](../includes/banner.md)]

This topic describes how to manage customer information, such as CNPJ (Cadastro Nacional da Pessoa Jurídica)/CPF (Cadastro de Pessoas Físicas) numbers, in Commerce point of sale (POS) for Brazil. You can specify customer tax registration number, name, and address information when you add a named customer to the cart in POS. You can also specify information for a sales transaction manually. Customer information can then be printed on DANFE (Documento Auxiliar de Nota Fiscal Eletrônica) fiscal receipts, and can be used for invoicing purposes.

For more information how to set up this functionality, see [Customer information management](latam-bra-deployment.md#customer-information-management).

## Example scenarios

The following example scenarios show how to work with customer information in Commerce POS for Brazil.

### Scenario 1: Make a sale to an anonymous customer

To make a sale to an anonymous customer, follow these steps.

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer information**, and then select **Enter manually**.
1. Enter the customer's CNPJ/CPF number or foreigner ID, name, and address, and then select **OK**.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed DANFE receipt contains the customer's CNPJ/CPF number, or the customer's foreigner ID, name, and address.

### Scenario 2: Make a sale to a named customer

To make a sale to a named customer, follow these steps.

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then find and select the desired customer.
1. Add the customer to the transaction.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's CNPJ/CPF number, or the customer's foreigner ID, name, and address.

### Scenario 3: Make a sale to a new named customer

To make a sale to a new named customer, follow these steps.

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then select **Create customer**.
1. Specify the new customer's attributes.
1. In the **CNPJ/CPF** field, enter the customer's CNPJ/CPF number.
1. In the **Foreigner ID** field, enter the customer's foreigner ID, if needed.
1. Select **Add address**, and then enter the new customer's contact information and address.
1. Save the customer record and the customer address record, and then add the customer to the transaction.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's CNPJ/CPF number, or the customer's foreigner ID, name, and address.

> [!NOTE]
> If you need to specify a different customer for the transaction, you must first clear the customer information and then choose another customer.

### Scenario 4: Change the customer information for a sale to a named customer

To change the customer information for a sale to a named customer, follow these steps.

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then select a customer account to add to the transaction.
1. Select **Add customer information**, and then select **Clear** to clear the customer information from the transaction.
1. Select **Enter manually**.
1. Enter the customer's CNPJ/CPF number or foreigner ID, name, and address, and then select **OK**.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's CNPJ/CPF number, or the customer's foreigner ID, name, and address.

## Additional resources


