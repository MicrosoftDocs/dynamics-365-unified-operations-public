---
title: Manage certificates (preview)
description: Manage global vendor certificates so you can track validity, upload evidence, review status, and sync records to local vendors.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Manage certificates (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Global vendor certificate management provides a single place to track supplier certifications across industries and legal entities. Managing certificates at the global vendor level helps you avoid maintaining the same record separately for each local vendor and makes compliance reviews easier. Certificate data synchronizes to related local vendor records in Supply Chain Management.

## Create a certificate record

Use this procedure to create a certificate for a global vendor. Create the record first, and then upload the supporting file or add a document URL if the evidence is stored externally.

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record) and go to the **General** tab.
1. In the **Certificates** section, select **New global vendor certificate**.
1. Enter the certificate details in the fields provided. Use the tooltips to understand the purpose of each field.
1. Select **Save**.

## <a name="open-certificate"></a>View and edit a certificate record

To view or edit a certificate record, follow these steps.

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record) and go to the **General** tab.
1. In the **Certificates** section, find the certificate record that you want to add a file to. Scroll to the right and select the **Go to record** button for your selected row.
1. The app displays certificate details, including review details and links to uploaded and external files. Edit the fields as needed and select **Save** to update the record.

## Upload a certificate file

After you create a certificate record, you can attach the supporting evidence directly to that record. Each certificate can have one uploaded file, or you can store a document URL that points to an external source instead.

1. [Open the certificate record](#open-certificate).
1. Do one of the following steps:
    - If the document is stored locally, select **Upload file**, go to the **Certificate file** section, and select **Choose file**. Then select the file to upload. If a file is already uploaded, you must first delete it by selecting **Delete**.
    - If the document is stored externally, go to the **Certificate file** section and enter the URL in the **Document URL**.

1. Select **Save**.

> [!NOTE]
> You can attach only one file to each certificate record.

## Track expired certificates

Each certificate includes an **Expiration date** field so you can monitor validity over time. A Power Automate flow checks whether the expiration date is the current date and then updates the certificate status to **Expired**.

Organizations can surface expiring or expired certificates through dashboards, views, or other reporting mechanisms so that reviewers can act before compliance issues affect supplier readiness.

## Synchronize certificates with Supply Chain Management

When you release a global vendor to a legal entity, the system synchronizes its certificate records to the related local vendor and marks them as global vendor certificates. For qualified vendors that already have related local vendors, newly created certificates synchronize automatically to all connected local vendor records.

This behavior helps teams maintain certificates once at the shared supplier level while still making the data available where operational users need it.

## Mark a certificate as reviewed

Use this procedure when an internal reviewer validates the certificate content and wants to capture the review result on the record.

1. [Open the certificate record](#open-certificate) that you want to review.
1. On the command bar, select **Mark as reviewed**.
1. Select **OK**.
1. Enter review comments.
1. Select **OK**.

After the action is completed, the system updates the following fields on the certificate:

- **Reviewed?** – Set to **Yes**
- **Reviewer** – Set to the current user
- **Review comment** – Populated with the entered review comments

## Related information

- [Global vendor management overview](supplier-engagement-global-vendors-overview.md)
- [Manage global vendor information](supplier-engagement-global-vendor-info.md)
- [Manage global vendor capabilities](supplier-engagement-global-vendor-capabilities.md)
- [Synchronize data between Supplier Engagement and Supply Chain Management](supplier-engagement-data-sync.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
