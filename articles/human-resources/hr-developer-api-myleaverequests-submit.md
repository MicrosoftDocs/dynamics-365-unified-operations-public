---
# required metadata

title: Submit a leave request to workflow
description: In Microsoft Dynamics 365 Human Resources, you can use the MyLeaveRequests submit() application programming interface (API) to submit a leave request to workflow.
author: twheeloc
ms.date: 07/09/2024
ms.topic: article
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ajitchandran
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Submit a leave request to workflow



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

In Microsoft Dynamics 365 Human Resources, you can use the MyLeaveRequests submit() application programming interface (API) to submit a leave request to workflow. This API is exposed as an action on the MyLeaveRequests OData entity.

## Prerequisites

The leave request must be saved in the database and must be retrievable through the MyLeaveRequests entity.

## Permissions

One of the following permissions is required to call this API. For more information about permissions and how to select them, see [Authentication](hr-developer-api-authentication.md).

| Permission type                    | Permissions (from least privileged to most privileged) |
|------------------------------------|--------------------------------------------------------|
| Delegated (work or school account) | user\_impersonation                                    |

## HTTPS request

<!-- { "blockType": "ignored" } -->
```HTTP
POST https://{cluster}.hr.talent.dynamics.com/namespaces/{namespace_guid}/data/MyLeaveRequests(RequestId='{requestId}', LeaveType='{leaveType}', LeaveDate={leaveDate}, dataAreaId={dataArea})/Microsoft.Dynamics.DataEntities.submit?cross-company=true
```

The request conforms to OData standards. The {requestId}, {leaveType}, {leaveDate}, and {dataArea} parameters refer to the fields that make up the composite natural key for the MyLeaveRequests entity.

> [!NOTE]
> While the fields for the MyLeaveRequests entity refer to an individual line in the leave request, calling the submit API will submit the entire leave request (all lines) to workflow.

### Request headers

| Header         | Value                     |
|----------------|---------------------------|
| Authorization  | Bearer {token} (required) |
| Content-Type   | application/json          |

### Request body

Don't supply a request body for this method.

### Response

A successful response is always a **204 No Content** response.

Unauthorized callers receive a **401 Unauthorized** or a **403 Forbidden** response.

If submission is unsuccessful (because of validation, for example), the response is a **500 Server Error**, and the response body will include a JSON object with further details.

## Example

```http
POST https://aos-rts-sf-550e5c091f6-prod-westus2.hr.talent.dynamics.com/namespaces/b2eb8003-334f-4a84-ab63-edbe23569090/data/MyLeaveRequests(RequestId='USMF-000065', LeaveType='Vacation', LeaveDate=2019-10-04T12:00:00Z, dataAreaId='USMF')/Microsoft.Dynamics.DataEntities.submit
```

```json
{
  "error": {
    "code": "",
    "message": "An error has occurred.",
    "innererror": {
      "message": "Exception occurred while executing action submit on Entity MyLeaveRequest: The request would put the 'Vacation' balance below the allowed minimum balance on 9/10/2019.",
      "type": "System.InvalidOperationException",
      "stacktrace": "   at Microsoft.Dynamics.Platform.Integration.Services.OData.Action.ActionInvokable.Invoke()   at Microsoft.Dynamics.Platform.Integration.Services.OData.Update.UpdateProcessor.ActionInvocation(ChangeOperationContext context, ActionInvokable action)   at Microsoft.Dynamics.Platform.Integration.Services.OData.Update.UpdateManager.<>c__DisplayClass13_0.<ScheduleInvokable>b__0(ChangeOperationContext context)   at Microsoft.Dynamics.Platform.Integration.Services.OData.Update.ChangeInfo.ExecuteActionsInCompanyContext(IEnumerable`1 actionList, ChangeOperationContext operationContext)\r\n   at Microsoft.Dynamics.Platform.Integration.Services.OData.Update.ChangeInfo.ExecuteActions(ChangeOperationContext context)   at Microsoft.Dynamics.Platform.Integration.Services.OData.Update.UpdateManager.SaveChanges()   at Microsoft.Dynamics.Platform.Integration.Services.OData.AxODataDelegatingHandler.<SaveChangesAsync>d__3.MoveNext()"
    }
  }
}
```

## Validation and error messages

As part of the call to the submit API, Human Resources performs business logic validation before submission, which ensures the leave request is in a valid state for submission. The possible error messages you may receive in the response if validations fail are:

 - The request would put the '{LeaveTypeId}' balance below the allowed minimum balance on {date}.
 - Time off request in **Completed** state can't be submitted.
 - Unable to submit or save request as no changes have been made. Add or update the amount or the leave type and try again.
 - The time off request entered contains one or more days with the same date and leave type as an existing pending request. Recall the existing request to make changes.
 - Reason code '{ReasonCodeId}' doesn't apply to any of the leave types in the request.
 - Leave type '{LeaveTypeId}' requires a reason code. Select the appropriate type and reason code.
 - The time off wasn't submitted successfully. The time off has been saved as a draft request.

## See also

- [MyLeaveRequests overview](hr-developer-api-myleaverequests-overview.md)
- [Authentication](hr-developer-api-authentication.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
