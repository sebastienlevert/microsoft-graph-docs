---
title: "Get accessReview"
description: "In the Azure AD access reviews feature, retrieve an accessReview object."
localization_priority: Normal
author: "markwahl-msft"
ms.prod: "microsoft-identity-platform"
doc_type: apiPageType
---

# Get accessReview

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

In the Azure AD [access reviews](../resources/accessreviews-root.md) feature, retrieve an [accessReviewScheduleDefinition](../resources/accessreview.md) object.  

To retrieve the reviewers of the access review, use the [list accessReview reviewers](accessreview-listreviewers.md) API. To retrieve the decisions of the access review, use the [list accessReview decisions](accessreview-listdecisions.md) API, or the [list my accessReview decisions](accessreview-listmydecisions.md) API.

If this is a recurring access review, no decisions will be associated with the recurring access review series. Instead, use the `instances` relationship of that series to retrieve an [accessReview](../resources/accessreview.md) collection of the past, current, and future instances of the access review. Each past and current instance will have decisions.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type                        | Permissions (from least to most privileged)              |
|:--------------------------------------|:---------------------------------------------------------|
|Delegated (work or school account)     | AccessReview.Read.All, AccessReview.ReadWrite.Membership, AccessReview.ReadWrite.All  |
|Delegated (personal Microsoft account) | Not supported. |
|Application                            | AccessReview.Read.All, AccessReview.ReadWrite.Membership  |

In order to call this API, the signed in user must also be in a directory role that permits them to read an access review, or the user can be assigned as a reviewer on the access review.  For more details, see the role and permission requirements for [access reviews](../resources/accessreviews-root.md).

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
GET /identityGovernance/accessReviews/definitions/{reviewId}
```
## Request headers
| Name         | Type        | Description |
|:-------------|:------------|:------------|
| Authorization | string | Bearer \{token\}. Required. |

## Request body
Do not supply a request body for this method.

## Response
If successful, this method returns a `200 OK` response code and an [accessReview](../resources/accessreview.md) object in the response body.

## Example
##### Request


# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "get_accessReview"
}-->
```msgraph-interactive
GET https://graph.microsoft.com/beta/identityGovernance/accessReviews/definitions/2b83cc42-09db-46f6-8c6e-16fec466a82d
```
# [C#](#tab/csharp)
[!INCLUDE [sample-code](../includes/snippets/csharp/get-accessreview-csharp-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [JavaScript](#tab/javascript)
[!INCLUDE [sample-code](../includes/snippets/javascript/get-accessreview-javascript-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

# [Objective-C](#tab/objc)
[!INCLUDE [sample-code](../includes/snippets/objc/get-accessreview-objc-snippets.md)]
[!INCLUDE [sdk-documentation](../includes/snippets/snippets-sdk-documentation-link.md)]

---


##### Response
>**Note:** The response object shown here might be shortened for readability. All the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.accessReview",
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "2b83cc42-09db-46f6-8c6e-16fec466a82d",
    "displayName": "15987",
    "descriptionForReviewers": "asdfasdf",
    "descriptionForAdmins": "asdfasdf",
    "scope": {
        "query": "/groups/8b55b80f-ccd2-415e-ab69-7f0b966869d4/members?$filter=microsoft.graph.user/userType eq ‘Guest’",
        "type": "MicrosoftGraph”
    },
    "reviewers": [
        {
            "query": "/groups/46d30af1-e626-4928-83f5-e9bfa400289e/owners?$filter=microsoft.graph.user/userType eq ‘Member’ and microsoft.graph.user/country eq 
            'USA’",
            "type": "MicrosoftGraph”
        }
    ],
    "settings": {
        "mailNotificationsEnabled": true,
        "reminderNotificationsEnabled": true,
        "justificationRequiredOnApproval": true,
        "recommendationsEnabled": true,
        "instanceDurationInDays": 3,
        "recurrence": {
            "pattern": {
                "type": "weekly",
                "interval": 1
            },
            "range": {
                "type": "noEnd",
                "startDate": "2018-08-03T21:02:30.667Z",
                "count": 0,
            }
         },
        "defaultDecisionEnabled": true,
        "defaultDecision":"Approve",
        "autoApplyDecisionsEnabled": true,

    }
}
```

## See also

- [Create accessReview](accessreview-create.md)
- [List accessReviews](accessreview-list.md)
- [List programControls](programcontrol-list.md)
- [List accessReview reviewers](accessreview-listreviewers.md)
- [List accessReview decisions](accessreview-listdecisions.md)
- [List my accessReview decisions](accessreview-listmydecisions.md)


<!--
{
  "type": "#page.annotation",
  "description": "Get accessReview",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
  ]
}
-->