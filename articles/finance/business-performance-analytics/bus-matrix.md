---

title: Business performance analytics bus matrix data model
description: This article provides information about the relationship between facts and dimensions as part of the Business performance analytics data model.
author: carylhenry
ms.author: carylhenry
ms.reviewer: twheeloc 
ms.date: 5/04/2024
ms.topic: article 

ms.custom:
ms.search.form: business-performance-analytics
audience: Application User
ms.application-unique-name: msdyn_BusinessPerformanceAnalytics
---

# Business performance analytics bus matrix data model

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for Business performance analytics, contact <bpaquestions@service.microsoft.com>.

## Definitions

A *bus matrix* shows the relationship between facts and dimensions. *Facts* represent business metrics of interest. In Business performance analytics, facts are record-type data, such as transactions, orders, and records. Each fact is associated with one or more *dimensions*. Dimensions represent descriptive data elements and provide more information about the facts that are associated with them.

### Bus matrix

The following business matrix table shows the relationship between facts and dimensions in the context of Business performance analytics. Rows represent dimensions, while columns represent facts.


| Dimensions  | Budget | Budget reservation | General ledger | Product receipt | Purchase invoice | Purchase invoice matching | Purchase order | Purchase payment | Purchase payment matching | Purchase requisition | Purchase sub-ledger | Sales invoice | Sales payment | Sales payment matching | Sales sub-ledger |
| ------- | ------ | --- | -- | ----- | ---------- | ----------- | -------------- | --------- | ------------- | --------- | ----- | ------------- | ------------- | ---------------------- | ---------------- |
| Asset    |        |      |        |          | X                |          |          |            |        |          |             |               |               |                        |                  |
| Bank account     |        |      |         |         |      |       |      |        |          |          |                     |               | X             |                        |                  |
| Budget reservation number   |        | X     |      |       |       |     |      |                  |     |     |                     |               |               |                        |                  |
| Buying party   |        |       |                |      |       |      |       |     |        |    |                     | X             | X             | X                      | X                |
| Currency       | X      |     | X              | X               | X                |    | X              | X                |      |        | X       |      | X             | X     | X                |
| Date (Accounting)   | X      | X     | X  | X    | X      | X    | X    | X    | X    | X    | X      | X             | X             | X                      | X                |
| Delivery method    |        |    |     |    |     |     | X     |         |     |                      |                     |               |               |                        |                  |
| Delivery postal address    |        |    |       | X     |       |   | X        |       |        |       |         |     |     |        |            |
| General ledger account   | X      | X   | X      |     |        |       |  |    |    |                      |                     |               |               |                        |                  |
| Ledger   |        | X        |        |      |       |  |   |         |     |                      |                     |               |               |                        |                  |
| Party        |        |     |   |       | X                | X   |      | X         | X      |         | X                   | X             |               | X                      | X                |
| Procurement category     |        | X    |     | X      | X     | X  | X     |     |       | X       |                     |               |               |                        |                  |
| Product   |        |     |     | X      | X     | X   | X    |        |        | X      |                     | X             |               |                        |                  |
| Product receipt number |        |    |    | X       |  | X    |    |    |     |     |                     |               |               |                        |                  |
| Project    |        | X    |      |    | X |       | X    |         |      | X                    |                     |               |               |                        |                  |
| Purchase invoice line number  |    |   |      |     | X   | X      |      |     |     |                      |                     |               |               |                        |                  |
| Purchase invoice number   |        |  |     |       | X    | X   |     |    |    |                      | X                   |               |               |                        |                  |
| Purchase matched document number |  |     |      |   | X     | X      |     | X    | X       |       |                     |               |               |                        |                  |
| Purchase order line number       |        |    |      | X     |     | X        | X       |     |    |      |                     |               |               |                        |                  |
| Purchase order number   |        |     |     | X    | X      | X        | X              |     |        |      |        |               |               |                        |                  |
| Purchase requisition number      |        |      |      |       |     |    | X    |     |      | X       |        |               |               |                        |                  |
| Reporting dimension | X      | X    | X     |   |   |     |      |      |     |                      |                     |               |               |                        |                  |
| Requesting party      |    |     |          |   |         |     | X    |     |    | X                    |                     |               |               |                        |                  |
| Sales category     |      |   |     |    |      |    |      |    |        |                      |                     | X             |               |                        |                  |
| Sales invoice line number     |   |      |      |        |   |      |   |     |            |           |                     | X             |               |                        |                  |
| Sales invoice number    |        |     |    |    |  |     |      |      |        |                      |                     | X             |               |                        | X                |
| Sales order number     |        |    |    |      |      |      |    |      |   |                      |                     | X             |               |                        |                  |
| Sales payment matched number   |  |    |      |    |      |     |      |  |        |             |                     |               |               | X                      | X                |
| Sales payment matching number    |   |    |         |  |    |    |   |      |     |  |                     |               |               | X                      | X                |
| Selling party           |     |   |    | X      | X    | X      | X     | X   | X    | X     | X                   |               |               |                        |                  |
| Selling party postal address     |     | |    | X   | X       |   | X    | X  |   | X     | X                   |               |               |                        |                  |
| Storage location      |     |   |      | X     | X  | X     | X    |     |     | X                    |                     | X             |               |                        |                  |
| Sub-ledger number     |        | X     |     |     | X      |     |      | X        | X        |     | X                   | X             | X             | X                      | X                |
