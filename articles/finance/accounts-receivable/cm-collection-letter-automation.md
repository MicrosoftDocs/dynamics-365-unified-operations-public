---
title: Collection letter automation overview for Dynamics 365 Finance
description: Learn how collection letter automation uses the oldest qualifying invoice to set collection stages and generate one communication per customer. 
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 07/20/2026
ms.topic: article
---

# Collection letter automation overview

[!INCLUDE [banner](../../includes/banner.md)]

Collection letter automation is a Dynamics 365 Finance feature that helps organizations streamline customer collections by automatically determining when to send collection communications and what collection stage to apply to a customer. The feature reduces manual review effort while helping collection activities run consistently based on configured aging and due date criteria.

Collection automation evaluates the customer account as a whole rather than assessing each invoice independently. The system reviews eligible customer transactions, determines the appropriate collection stage, and generates one communication for the customer during a processing run. It supports both pre-dunning communications, which are sent before invoices become due, and overdue collection communications, which are sent after invoices become overdue.

The automation process helps organizations reduce manual collection effort, standardize follow-up processes, send timely reminders, and progress customers through collection stages consistently.

> [!IMPORTANT]
> This article explains the concepts and expected behavior of collection letter automation. For configuration steps, see the related setup article, [Set up collection letter automation](coll-process-auto-faq.md#collections-process-automation-setup).

## How collection automation evaluates customers

Collection automation operates at the customer level, not at the invoice level. The system evaluates all eligible invoices for a customer and determines the appropriate collection action based on the customer's overall aging position.

Because the customer is a single collection entity:

* Select one collection stage per customer.
* Generate one collection communication during a processing run.
* Include multiple invoices in that communication if they meet the configured criteria.

In the following example, the system uses the oldest qualifying invoice to determine the collection stage. The customer receives one collection communication based on that stage.

| **Invoice** | **Status**      |
|-------------|-----------------|
| Invoice A   | 40 days overdue |
| Invoice B   | 10 days overdue |
| Invoice C   | Not yet due     |

## How collection stages are determined

The customer's oldest qualifying invoice determines the collection stage. The oldest invoice sets the severity or escalation level that you apply to the customer.

For example, if a customer has invoices that are overdue by different durations, the invoice with the greatest aging drives the collection stage selection. This design helps ensure that collection activities reflect the customer's highest collection priority instead of treating every invoice as a separate communication path.

## Which invoices appear in collection communications

Although the oldest qualifying invoice determines the collection stage, the communication itself can contain multiple invoices. You generate the communication for the customer and it can include all invoices that meet the configured eligibility criteria.

Eligibility depends on the automation configuration and may include factors such as whether the transaction remains open, whether the invoice is overdue, and whether the invoice satisfies the process filters.

In the following example, if you configure the automation process to include overdue invoices only, Invoice A and Invoice B appear in the communication. Invoice C is excluded because it's not yet due.

| **Invoice** | **Status**      | **Included when overdue-only?** |
|-------------|-----------------|---------------------------------|
| Invoice A   | 30 days overdue | Yes                             |
| Invoice B   | 5 days overdue  | Yes                             |
| Invoice C   | Not yet due     | No                              |

## Track step

Track step determines whether the system remembers previously executed collection activities for a customer.

When you enable **Track step**, the system maintains collection progression history and tracks which collection activities are already completed. This history helps customers progress through the collection process sequentially and helps avoid repeated communications for the same completed stage.

When you disable **Track step**, the system doesn't consider previous collection activity during subsequent automation runs. As a result, the system can generate the same collection communication again if the customer still qualifies for the same stage.

Use Track step when the collection process should behave like a controlled journey, where customers move forward through stages and completed stages aren't repeated unnecessarily.

| **Scenario** | **Track step enabled** | **Track step disabled** |
|---|---|---|
| First run: Customer qualifies for 30-day overdue stage | 30-day communication is generated | 30-day communication is generated |
| Next run: Customer still qualifies for 30-day overdue stage | Same communication isn't generated again | Same communication can be generated again |

## Pre-dunning communications

Pre-dunning allows organizations to remind customers about upcoming payment due dates before invoices become overdue.

Pre-dunning is only applicable when the customer's oldest qualifying invoice isn't yet overdue. If the customer already has an older overdue invoice, overdue processing takes precedence and pre-dunning activities are skipped. This behavior helps the collections process focus on existing delinquency before sending reminders for future due dates.

In the following example, although Invoice B qualifies for a pre-dunning reminder, no pre-dunning communication is generated because Invoice A is already overdue and represents the customer's highest collection priority.

| **Invoice** | **Status**     |
|-------------|----------------|
| Invoice A   | 5 days overdue |
| Invoice B   | Due in 10 days |

## Key considerations

* Collection automation evaluates customers rather than individual invoices.
* The oldest qualifying invoice determines the collection stage.
* Communications can include multiple eligible invoices.
* Track step controls progression tracking and repeat processing behavior.
* Pre-dunning communications are generated only when no older overdue invoices exist for the customer.

## Frequently asked questions

### Is collection automation processed per invoice?

No. Collection automation evaluates the customer account as a single collection entity and determines one collection outcome per customer during a processing run.

### Can multiple invoices appear in a collection communication?

Yes. The communication can contain multiple eligible invoices, even though a single invoice determines the collection stage.

### Which invoice determines the collection stage?

The oldest qualifying invoice determines the collection stage and escalation level applied to the customer.

### How many communications can a customer receive in one automation run?

Collection automation generates a single communication per customer during a processing run.

### What is the purpose of Track step?

Track step helps prevent duplicate collection activities and supports controlled progression through collection stages.

### Why was the same collection communication sent again?

This situation can occur when you disable the **Track step** because the system doesn't retain collection progression history between automation runs.

### Why wasn't a pre-dunning reminder generated?

The system skips pre-dunning reminders when the customer already has an older overdue invoice. Overdue processing takes precedence over future due date reminders.


