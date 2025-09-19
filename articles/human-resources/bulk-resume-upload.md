---
# required metadata

title: Set up the Bulk resume upload AI feature in Dynamics 365 Human Resources Recruiting add-on (preview)
description: Learn about the Bulk resume upload AI feature in Microsoft Dynamics 365 Human Resources Recruiting add-on.
author: twheeloc
ms.date: 04/14/2025
ms.topic: how-to
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2020-12-03
ms.dyn365.ops.version: Human Resources

---

# Set up the Bulk resume upload AI feature in Dynamics 365 Human Resources Recruiting add-on (preview)

[This article is prerelease documentation and is subject to change.]

This article describes the Bulk resume upload AI feature in Microsoft Dynamics 365 Human Resources Recruiting add-on.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

The Bulk resume upload AI feature in Dynamics 365 Human Resources Recruiting add-on is an AI-powered tool that is designed to optimize and automate the process of uploading, organizing, and analyzing large numbers of resumes simultaneously. Because this feature facilitates more efficient management and processing, it's beneficial to companies and recruiters that receive many applications for open positions.

Recruiters can use the feature to upload multiple resumes simultaneously in various file formats (PDF, JPG, PNG, or JPEG). Because resumes don't have to be manually uploaded one at a time, the feature saves significant time.

The action of uploading a resume creates a batch that generates candidate profiles from resumes. AI parses the uploaded resumes and extracts all relevant information to generate the candidate profiles. A progress bar shows the progress of profile creation.

For each candidate profile, a candidate profile ID is generated. Recruiters can select the ID to open the detailed profile that AI extracted. They can then review and edit the profiles as required.

## Activate Bulk resume upload

> [!NOTE]
> An administrator must complete this procedure.

To activate the **Bulk resume upload** AI feature, follow these steps.

1. From the left pane, go to **Environment variables**.
1. Search for and select **msdyn_hcm_ResumeParser**.
1. Set the default value to **Yes**. Alternatively, create a new environment variable, and set the **Value** field to **Yes**.
1. Save your changes.

## Upload resumes in bulk

To upload resumes in bulk, follow these steps.
1. In the left pane, select **Bulk resume upload**.
2. Select **Upload resume**.
3. Browse to the location, and select the resumes to upload.

    The selected resumes are processed. A progress bar shows the number of resumes that have been parsed.

For each parsed resume, AI generates a candidate profile. Each candidate profile has a **Candidate ID** value. Select the candidate ID to view the details that AI extracted.

## Edit the candidate profile that Bulk resume upload generates

To edit the candidate profile that the **Bulk resume upload** AI feature generated, follow these steps.

1. After a candidate profile is generated, a **Candidate ID** value is generated inside a batch. Select the candidate ID to open the candidate profile and view the details that AI extracted. 
1. Review the candidate profile that AI generated, and edit the information as required.

### Activate resume upload in careers 
To enable resume parsing functionality, follow these steps:
Set up the Bulk resume upload AI feature in Dynamics 365 Human Resources Recruiting add-on (preview) - Human Resources | Dynamics 365 | Microsoft Learn 
1. Go to Power Page.
2. In the left-hand navigation panel, select **Setup**.
3. Under **Integrations**, select **Cloud Flows**.
4. Click **Add existing flows**.
5. From the list, select **Retrieve feature control** setting.
6. Assign the **Authenticated users** roles.
7. Click **Add**.
8. The flow appears in the list of added flows.
9. Repeat the same for **Resume parse** flow.
10. After adding the flows, click **Sync**.
11. After completed, the **Upload resume** button appears on the **Create profile** page. 


 
