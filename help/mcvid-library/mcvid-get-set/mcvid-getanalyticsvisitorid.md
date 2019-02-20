---
description: Returns the legacy Analytics ID (if any) that was stored in the s_vi cookie before the Experience Cloud ID service was implemented. It returns an empty string if a visitor was never assigned an Analytics ID.
keywords: ID Service
seo-description: Returns the legacy Analytics ID (if any) that was stored in the s_vi cookie before the Experience Cloud ID service was implemented. It returns an empty string if a visitor was never assigned an Analytics ID.
seo-title: getAnalyticsVisitorID
solution: Marketing Cloud
title: getAnalyticsVisitorID
uuid: 6bb8ddfc-9fc1-4105-b377-d9b4d247a0f8
index: y
internal: n
snippet: y
---

# getAnalyticsVisitorID{#getanalyticsvisitorid}

Returns the legacy Analytics ID (if any) that was stored in the s_vi cookie before the Experience Cloud ID service was implemented. It returns an empty string if a visitor was never assigned an Analytics ID.

 **Syntax** `var analyticsID = visitor.getAnalyticsVisitorID()`

Typically, this function is used with custom solutions that require reading the visitor ID. It is not used by a standard implementation. `getAnalyticsVisitorID` also works with callback functions to read [!DNL Analytics] IDs and bring them in to your system or application.

**Sample Code**

```js
//callback function 
var useAnalyticsVisitorID = function(id){ 
     //whatever your function does with the Experience Cloud ID 
}; 
 
//get Analytics ID and pass it to the function 
var analyticsID = visitor.getAnalyticsVisitorID(useAnalyticsVisitorID)
```

>[!TIP]
>
>If you're an [!DNL Analytics] customer, also check for and send the [!DNL Analytics] ID to your function. For example, you would want both identifiers when passing the visitor ID in a hidden form element to a server-side application that uses the data insertion API. In this case, you should collect and return the [!DNL Experience Cloud] and [!DNL Analytics] visitor IDs. See [getMarketingCloudVisitorID](../../mcvid-library/mcvid-get-set/mcvid-getmcvid.md#reference-7bcc9b5fe8e1430988d30657c60dba45).

**The "aid" Parameter is a Legacy Value**

The `aid` parameter appears in a query string under 2 different sets of conditions.

**Case 1**

You will see the `aid` parameter in a query string when:

* The [!DNL Experience Cloud] ID service is deployed correctly. 
* The user visiting a site has a pre-existing [!DNL Analytics] ID stored in their [s_vi cookie](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html).

**Case 2**

You will see the `aid` parameter in a query string when your organization is using a [grace period](../../mcvid-reference/mcvid-analytics-reference/mcvid-grace-period.md#concept-e4c0d796412b4985badae11e5aecb2fd) before fully implementing the ID service. If the user visiting your site is new, and you're not using a grace period, the visitor will get the `mid` ( [!DNL Experience Cloud] ID) parameter. 

>[!MORE_LIKE_THIS]
>
>* [Analytics Cookies](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/cookies_analytics.html)