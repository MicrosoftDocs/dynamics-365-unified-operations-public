---
title: Integration for LinkedIn overview
description: The Integration for LinkedIn lets you post jobs from Dynamics 365 Human Resources directly to LinkedIn. Learn how to set up and manage the integration.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 07/30/2026
ms.topic: article
---

# Integration for LinkedIn overview

Integration for LinkedIn in the Recruiting add-on that organizations use to post jobs to LinkedIn for both recruiters and candidates. If your organization already has a valid LinkedIn Recruiter or LinkedIn job posting license, you can activate the integration directly in the Recruiting add-on settings. An administrator authenticates the LinkedIn account, maps the required permissions, and enables job distribution.

The LinkedIn job posting integration enables recruiters to publish job advertisements from Dynamics 365 Human Resources directly to LinkedIn. It uses secure authentication and controlled API-based communication between LinkedIn and the Recruiting add-on.

## Prerequisites

- A valid LinkedIn Recruiter or LinkedIn job posting license.
- A recruiting administrator role in the Recruiting add-on to enable the LinkedIn integration.
- The required permissions on the customer's LinkedIn company page and LinkedIn credentials to enable premium jobs.

## Integration benefits

The Integration for LinkedIn provides:

- Quick and easy setup
- One-click job posting
- Broader candidate reach
- Seamless navigation from LinkedIn to Careers
- A secure, enterprise-grade recruiting experience

### Setup

Only a recruiting administrator in the Recruiting add-on can enable the Integration for LinkedIn. To enable premium jobs, that same user also needs the required permissions on the customer's LinkedIn company page and must sign in to the LinkedIn widget with LinkedIn credentials.

To set up the Integration for LinkedIn, follow these steps:

1. Go to **Set up > LinkedIn** and turn on the **Enable LinkedIn integration** toggle.
1. Accept the LinkedIn terms and conditions presented.
1. Wait for the customer child app provisioning to complete in the background. You're notified after it completes and asked to complete the rest of the setup.
1. Search for the LinkedIn company by using the dropdown and select the company that belongs to your organization.
   > [!NOTE]
   >Choosing the wrong company can cause the job posting to fail, create incorrect job-company associations, and lead to compliance issues.
1. Enter the Careers site URL.
1. Click **Next** to complete premium job setup.
1. In the LinkedIn premium job widget, sign in using the LinkedIn company page administrator.
1. Select the appropriate LinkedIn contract, choose a default **Job poster**.
1. After you select the job poster, select **Submit** to complete the setup.

After the setup is complete, the organization can post jobs created in the Recruiting add-on to LinkedIn.

### Job posting

After you publish a job, post it to LinkedIn.

To post a job to LinkedIn, follow these steps:

1. Go to the **External job boards**.
1. Select **+New**, and select the LinkedIn-related option.
1. Select a contract if more than one contract is enabled for your integration.
1. Update poster information as needed and select **Share**.
1. Wait for the job to be posted on LinkedIn.
1. Select **Refresh** to see the updated status of the job and the LinkedIn posting URL.

### Candidate experience

After reviewing the job description, candidates can select **Apply** on LinkedIn and are redirected to the organization's Careers portal to complete the application. Candidate data is transferred securely, access is permission-based, and the organization retains full control of recruitment data within its Careers environment.

### Contracts

A LinkedIn posting contract represents your organization's commercial agreement with LinkedIn. It contains the job slots or inventory that your company can use to publish job advertisements on LinkedIn.

When posting premium jobs, selecting a Contract ID is mandatory. The Contract ID is a unique numeric identifier that allows LinkedIn to validate the posting and associate it with the correct corporate account.

If you're unsure which contract to use for a specific job, contact your recruiting administrator or your organization's LinkedIn page administrator for guidance.

### Frequently asked questions

- I posted a job, but it still shows as **Processing**. Do I need to do anything?
No action is usually required. The LinkedIn Job Posting API typically takes one to two minutes to process and publish a job. If your job still shows a status of **Processing**, wait a few moments and then select the **Refresh** icon.

- I closed a job and now want to reopen it. How can I do that?
You can reactivate a previously closed job by going to the **External job boards** section and selecting **Reactivate job**.
When you reactivate a job, LinkedIn doesn't reopen the original posting. Instead, the original job remains closed, and a new LinkedIn job posting is created with a new job link.

- My job posting failed. How can I find the reason?

If a job posting fails, LinkedIn returns an error message that explains the reason for the failure.
To view the details, follow these steps:

1. Select **More details** associated with the failed posting.
1. Review the error message and resolve the issue.
1. Select **Try posting again** to resubmit the job to LinkedIn.
Common causes include missing required information, invalid contract selection, or configuration issues with the Integration for LinkedIn.
