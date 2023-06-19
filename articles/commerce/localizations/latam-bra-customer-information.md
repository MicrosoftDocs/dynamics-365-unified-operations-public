---
title: Manage customer information in POS for Brazil
description: This article describes how to manage customer information in Commerce point of sale (POS) for Brazil.
author: EvgenyPopovMBS
ms.date: 12/01/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Brazil
ms.author: josaw
ms.search.validFrom: 2021-01-01
ms.dyn365.ops.version: 10.0.18
ms.search.industry: Retail
ms.search.form: 
---
# Manage customer information in POS for Brazil

[!include [banner](../includes/banner.md)]

This article describes how to manage customer information in Commerce point of sale (POS) for Brazil. This information includes CNPJ (Cadastro Nacional da Pessoa Jurídica)/CPF (Cadastro de Pessoas Físicas), CCM (Cadastro de Contribuinte Mobiliário), and IE (Inscrição Estadual) numbers. 

You can specify customer tax registration number, name, and address information when you create or edit a named customer master record and a customer address record in POS. You can also manually enter the minimum required information (including the CNPJ number) for a sales transaction. Customer tax registration numbers can then be used for customer searches in POS, added to the cart, printed on DANFE (Documento Auxiliar de Nota Fiscal Eletrônica) fiscal receipts, and used for invoicing purposes.

> [!NOTE]
> You can't specify registration numbers for named customers in POS if **Create customer in async mode** is enabled in the POS functionality profile. Support for the async customer creation mode might be added in future updates.

For more information about how to set up this functionality, see [Customer information management](latam-bra-deployment.md#customer-information-management) and [Enable customer searches based on tax registration numbers in POS](latam-bra-deployment.md#enable-customer-searches-based-on-tax-registration-numbers-in-pos).

## Example scenarios

The following example scenarios show how to manage customer information in Commerce POS for Brazil.

### Scenario 1: Make a sale to an anonymous customer

To make a sale to an anonymous customer, follow these steps.

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer information**, and then select **Enter manually**.
1. Enter the customer's CNPJ/CPF number or foreigner ID, name, and address, and then select **OK**.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's CNPJ/CPF number or foreigner ID, name, and address.

### Scenario 2: Make a sale to an existing named customer

To make a sale to a named customer, follow these steps.

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then find and select the desired customer (for example, by searching for tax registration numbers).
1. Add the customer to the transaction.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's tax registration numbers or foreigner ID, name, and address.

### Scenario 3: Make a sale to a new named customer

To make a sale to a new named customer, follow these steps.

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then select **Create customer**.
1. Specify the new customer's attributes.
1. In the **CNPJ/CPF** field, enter the customer's CNPJ/CPF number if the customer isn't a foreigner.
1. In the **IE** field, enter the customer's IE number if it's required.
1. In the **CCM** field, enter the customer's CCM number if it's required.
1. In the **Foreigner ID** field, enter the customer's foreigner ID, if it's required.
1. Select **Add address**, and then enter the new customer's contact information and address.
1. Save the customer record and the customer address record, and then add the customer to the transaction.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's tax registration numbers or foreigner ID, name, and address.

> [!NOTE]
> If you have to specify a different customer for the transaction, you must first clear the customer information. Then select another customer.

### Scenario 4: Change the customer information for a sale to a named customer

To change the customer information for a sale to a named customer, follow these steps.

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then select a customer account to add to the transaction.
1. Select **Add customer information**, and then select **Clear** to clear the customer information from the transaction.
1. Select **Enter manually**.
1. Enter the customer's CNPJ/CPF number or foreigner ID, name, and address, and then select **OK**.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's CNPJ/CPF number or foreigner ID, name, and address.

## Additional resources

[Set up and deploy Commerce localization for Brazil](latam-bra-deployment.md)

[Commerce localization for Brazil](latam-bra-commerce-localization.md)

[NFC-e fiscal document functionality in Commerce POS for Brazil](latam-bra-nfce.md)

[Cancellation and return of NFC-e documents in Commerce POS for Brazil](latam-bra-nfce-cancel-return.md)

[Postponed registration of NFC-e documents issued in offline contingency mode](latam-bra-nfce-contingency-mode.md)

[Post Brazilian fiscal documents via retail statements in Commerce headquarters](latam-bra-retail-statements.md)
