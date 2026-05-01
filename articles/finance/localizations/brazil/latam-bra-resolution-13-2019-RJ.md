---
title: SPED fiscal resolution 13/2019 RJ
description: Learn about resolution 13/2019, and how a Nota fiscal eletrônica (NF-e) should be issued and recorded, including an overview on SPED fiscal records.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/04/2026
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2017-12-31
---

# SPED fiscal resolution 13/2019 RJ

[!include [banner](../../includes/banner.md)]

The state of Rio de Janeiro (RJ) published Resolution 13/2019. This resolution defines how to issue a Nota fiscal eletrônica (NF-e) and how to record the information in the EFD-ICMS/IPI when you run the following operations (Decree No. 27.815/01):

- Exemption
- Reduction of the basis of calculation or reduction of rate
- Presumed credit
- Taxation on billing, taxation on receipt, or taxation on output
- Deferral
- Ineligibility for credit reversal
- Fiscal credit repair or accumulated credit balance transfer

According to the resolution, you register exonerations as adjustments on fiscal documents and in fiscal books. You should report them in Sistema Público de Escrituração Digital (SPED) files.

The resolution requirements affect the output of lines E111, E115, C195, C197, and 0460 in SPED Fiscal.

## SPED Fiscal records by operation

### Exemption and credit reversal

During the synchronization process, the system creates two types of adjustment transactions in the Imposto Sobre Operações Relativas à Circulação de Mercadorias e Serviços (ICMS) tax assessment when the following conditions are met:

- An outgoing fiscal document that is issued from RJ state has a taxation code of **30** or **40**.
- The benefit codes from table 5.2 and table 5.3, and also observation codes, are assigned to the related item and state of the fiscal document. For example, the code from table 5.2 is **RJ801137**, and the code from table 5.3 is **RJ90980000**.

Here are some examples of adjustment transactions that the system automatically creates in SPED Fiscal:

- The adjustment code from table 5.2 generates an E115 record:

    \|E115\|RJ801137\|0\|\|

- The adjustment code from table 5.3 generates a C197 record:

    \|C197\|RJ90980000\|RJ801137\|ItemId\|0.00\|0.00\|0.00\|0.88\|

    > [!NOTE]
    > In this example, the base amount is 3.5, the ICMS percentage is 18, and the Fundo de Combate e Erradicação à Pobreza (FCP) rate is 0.02. Therefore, the amount 0.88 is calculated in the following way:
    >
    > 3.5 ÷ (1 – \[0.18 + 0.02\]) × (0.18 + 0.02)

- The observation code that is assigned to the related item and state of the fiscal document generates C195 and 0460 records:

    \|C195\|\<Observation code\>\|\<Observation code description\>\|

    \|0460\|\<Observation code\>\|\<Observation code description\>\|

To register the credit reversal, create a manual adjustment in the General tax adjustment/benefit/incentive journal, and add the code from table 5.2 to the **Description** field.

Here's an example of an adjustment transaction that the system automatically creates in SPED Fiscal:

\|E111\|RJ18003\|RJ801137\|\<Adjustment amount\>\|

### Reduction of tax base or percentage

During the synchronization process, the system creates two types of adjustment transactions in the ICMS tax assessment when the following conditions are met:

- An outgoing fiscal document that is issued from RJ state has a taxation code of **20** or **70**.
- The benefit codes from table 5.2 and table 5.3 are assigned to the related item and state of the fiscal document. For example, the code from table 5.2 is **RJ802164**, and the code from table 5.3 is **RJ90980000**.

Here are some examples of adjustment transactions that the system automatically creates in SPED Fiscal:

- The adjustment code from table 5.2 generates an E115 record:

    \|E115\|RJ802164\|0\|\|

- The adjustment code from table 5.3 generates a C197 record:

    \|C197\|RJ90980000\|RJ802164\|ItemId\|0.00\|0.00\|0.00\|0,20\|

    > [!NOTE]
    > In this example, the base amount is 3.5, the ICMS percentage is 12, and the percentage reduction is 41.67. Therefore, the amount 0.20 is calculated in the following way:
    >
    > 3.5 × (1 – \[0.12 × (1 – 0.4167)\]) ÷ (1 – 0.12) – 3.5

- The observation code that is assigned to the related item and state of the fiscal document generates C195 and 0460 records:

    \|C195\|\<Observation code\>\|\<Observation code description\>\|

    \|0460\|\<Observation code\>\|\<Observation code description\>\|

### Presumed credit

**Out of scope:** The system can't calculate the extra percentage needed for C197 records.

To register the reversal of credits, create a manual adjustment in the General tax adjustment, benefit, or incentive journal, and add the code from table 5.2 to the **Description** field.

Here's an example of an adjustment transaction that the system automatically creates in SPED Fiscal:

\|E111\|RJ018003\|RJ805289\|\<Adjustment amount\>\|

### Tax on total sales, output, and billing

During the synchronization process, the system creates one type of adjustment transaction in the ICMS tax assessment when the following conditions are met:

- Outgoing fiscal documents that are issued from RJ state have a taxation code of **00**.
- The benefit code from table 5.2 is assigned to the related item and state of a fiscal document. The code from the table 5.3 isn't assigned. For example, the code from table 5.2 is **RJ822371**.

Here's an example of an adjustment transaction that the system automatically creates in SPED Fiscal:

- The adjustment code from table 5.2 generates an E115 record:

    \|E115\|RJ822371\|0\|\|

    > [!NOTE]
    > Because there's no code from table 5.3, the system doesn't create records C195, C197, and 0460.

To register the reversal of credits and debits, create manual adjustments in the General tax adjustment/benefit/incentive journal, and add the code from table 5.2 to the **Description** field.

Here are some examples of adjustment transactions that the system automatically creates in SPED Fiscal:

\|E111\|RJ18003\|RJ822371\|\<Adjustment amount\>\|

\|E111\|RJ38003\|RJ822371\|\<Adjustment amount\>\|

\|E111\|RJ08006\|RJ822371\|\<Adjustment amount\>\|

### Deferral

During the synchronization process, the system creates two types of adjustment transactions in the ICMS tax assessment when the following conditions are met:

- Outgoing fiscal documents are issued from RJ state and have a taxation code of **51**.
- The system assigns the benefit codes from table 5.2 and table 5.3 to the related item and state of a fiscal document. For example, the code from table 5.2 is **RJ818317**, and the code from table 5.3 is **RJ90980001**.

Here are some examples of adjustment transactions that the system automatically creates in SPED Fiscal:

- The adjustment code from table 5.2 generates an E115 record:

    \|E115\|RJ818317\|0\|\|

- The adjustment code from table 5.3 generates a C197 record:

    \|C197\|RJ90980001\|RJ818317\|ItemId\|0.00\|0.00\|0.00\|6585.36\|

    > [!NOTE]
    > In this example, the base amount is 30000.00. Therefore, the amount 6585.36 is calculated in the following way:
    >
    > 30000.00 ÷ (1 – 0.18) × 0.18

- The observation code that is assigned to the related item and state of the fiscal document generates C195 and 0460 records:

    \|C195\|\<Observation code\>\|\<Observation code description\>\|

    \|0460\|\<Observation code\>\|\<Observation code description\>\|

### Enforceability of credit reversal

During the synchronization process, the system creates two types of adjustment transactions in ICMS tax assessment when the following conditions are met:

- An outgoing fiscal document is issued from RJ state and has a taxation code of **40**.
- The benefit codes from table 5.2 and table 5.3 are assigned to the related item and state of the fiscal document. For example, the code from table 5.2 is **RJ801163**, and the code from table 5.3 is **RJ90980000**.

Here are some examples of adjustment transactions that the system automatically creates in SPED Fiscal:

- The adjustment code from table 5.2 generates an E115 record:

    \|E115\|RJ801163\|0\|\|

- The adjustment code from table 5.3 generates a C197 record:

    \|C197\|RJ90980000\|RJ801137\|ItemId\|0.00\|0.00\|0.00\|20\|

    > [!NOTE]
    > In this example, the base amount is 200, the ICMS percentage is 18, and the FCP rate is 0.02. Therefore, the amount 20 is calculated in the following way:
    >
    > 200 ÷ (1 – \[0.18 + 0.02\]) × (0.18 + 0.02)

- The observation code that is assigned to the related item and state of the fiscal document generates C195 and 0460 records:

    \|C195\|\<Observation code\>\|\<Observation code description\>\|

    \|0460\|\<Observation code\>\|\<Observation code description\>\|

To register the reversal of credits, create manual adjustments in the General tax adjustment/benefit/incentive journal, and add the code from table 5.2 to the **Description** field.

Here's an example of an adjustment transaction that the system automatically creates in SPED Fiscal:

\|E111\|RJ18003\|RJ801163\|\<Adjustment amount\>\|

### Pass on or transfer a tax credit

During the synchronization process, the system creates two types of adjustment transactions in the ICMS tax assessment when the following conditions are met:

- An outgoing tax fiscal document that is issued from RJ state has a taxation code of **90**.
- The benefit codes from table 5.2 and table 5.3 are assigned to the related item/Código Fiscal de Operações e de Prestações (CFOP) and state of the fiscal document. For example, the code from table 5.2 is **RJ801163**, and the code from table 5.3 is **RJ90980000**.

To register the reversal of credits, the system automatically creates adjustments in the General tax adjustment, benefit, or incentive journal and relates the journal line to the tax fiscal document.

Here are some examples of adjustment transactions that the system automatically creates in SPED Fiscal for a sender:

\|E115\|RJ821231\|0\|\|

\|C197\|RJ40080001\|RJ821231\|codigoitem\|0.00\|0.00\|\<Tax amount\>\|0.00\|

Here are some examples of adjustment transactions that the system automatically creates in SPED Fiscal for a recipient:

\|E115\|RJ821231\|0\|\|

\|C197\|RJ10080002\|RJ821231\|codigoitem\|0.00\|0.00\|\<Tax amount\>\|0.00\|

## Setup

### Fiscal books parameters per state

Follow these steps to set up fiscal books parameters for each state.

1. Go to **Fiscal books** > **Setup** > **Fiscal books parameters per state**.
1. On the **SPED Fiscal** FastTab, in the **Resolution 13/2019** section, set the **Document adjustment** option to **Yes**. The system now processes document adjustments according to Resolution 13/2019. If you don't set this option to **Yes**, the resolution requirements aren't applied.
1. In the **Name** field, enter the name of the general tax adjustment, benefit, or incentive journal. The system uses this journal name when a user needs to do an ICMS transfer operation to another fiscal establishment.

## Benefit code per item or state

1. Go to **Tax** > **Setup** > **Sales tax** > **Benefit code per Item/State**.
1. Set up **Adjustment code 5.2**, **Adjustment code 5.3**, and **Observation code** as required.

These settings help guarantee that you get a correct SPED Fiscal according to the resolution.

Use these settings to automatically generate ICMS adjustment records for a fiscal document line during posting and during the Sync operation.

## Tax fiscal document

If the **Document adjustment** option is set to **Yes** on the **Fiscal books parameters per state** page, users can select only a sales tax code that has a fiscal value of 3  on the tax fiscal document line. The taxation code, as it's related to the sales tax code, has a fiscal value of 3, without credit/debit. 

> [!NOTE]
> For correct posting, the tax fiscal document and the selected sales tax code should have the following calculation settings:
>
> - **Origin:** Percentage of net amount
> - **Marginal base:** Net amount per line
> - **Calculation method:** Whole amount

When you post a tax fiscal document where a sales tax code is attached to the line, the system doesn't create a voucher transaction. When you run the Sync operation, the system creates and posts a General tax, adjustment, benefit, or incentive journal that relates to the posted tax fiscal document for ICMS transfer to another fiscal establishment. (To run the Sync operation, go to **Fiscal books** > **Common** > **Booking period**, and then select **Sync**.)

The system fills in data on the journal lines from the posting profile of adjustment code 5.3. It fills in the amount from the tax fiscal document.

> [!NOTE]
> Before you use this functionality, set up the benefit code per item/state for ICMS transfer by going to **Tax** \> **Setup** \> **Sales tax** \> **Benefit code per Item/ state**. According to the resolution, the following adjustment codes should be set up for ICMS transfer:
>
> - **For the sender:** Adjustment code from table 5.2 = RJ821231, and adjustment code from table 5.3 = RJ10080002
> - **For the recipient:** Adjustment code from table 5.2 = RJ821231, and adjustment code from table 5.3 = RJ10080002

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
