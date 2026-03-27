# Taskrouter V1 Activity

```php
$taskrouterV1ActivityApi = $client->getTaskrouterV1ActivityApi();
```

## Class Name

`TaskrouterV1ActivityApi`

## Methods

* [Fetch Activity](../../doc/controllers/taskrouter-v1-activity.md#fetch-activity)
* [Update Activity](../../doc/controllers/taskrouter-v1-activity.md#update-activity)
* [Delete Activity](../../doc/controllers/taskrouter-v1-activity.md#delete-activity)
* [List Activity](../../doc/controllers/taskrouter-v1-activity.md#list-activity)
* [Create Activity](../../doc/controllers/taskrouter-v1-activity.md#create-activity)


# Fetch Activity

```php
function fetchActivity(string $workspaceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Activity resources to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Activity resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Activity`](../../doc/models/activity.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$sid = 'Sid8';

$taskrouterV1ActivityApi = $client->getTaskrouterV1ActivityApi();
$apiResponse = $taskrouterV1ActivityApi->fetchActivity(
    $workspaceSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Activity:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "available": true,
  "date_created": "2014-05-14T10:50:02Z",
  "date_updated": "2014-05-14T23:26:06Z",
  "friendly_name": "New Activity",
  "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
  }
}
```


# Update Activity

```php
function updateActivity(string $workspaceSid, string $sid, ?string $friendlyName = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Activity resources to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Activity resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |
| `friendlyName` | `?string` | Form, Optional | A descriptive string that you create to describe the Activity resource. It can be up to 64 characters long. These names are used to calculate and expose statistics about Workers, and provide visibility into the state of each Worker. Examples of friendly names include: `on-call`, `break`, and `email`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Activity`](../../doc/models/activity.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$sid = 'Sid8';

$friendlyName = 'friendly_name';

$taskrouterV1ActivityApi = $client->getTaskrouterV1ActivityApi();
$apiResponse = $taskrouterV1ActivityApi->updateActivity(
    $workspaceSid,
    $sid,
    $friendlyName
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Activity:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "available": true,
  "date_created": "2014-05-14T10:50:02Z",
  "date_updated": "2014-05-14T23:26:06Z",
  "friendly_name": "New Activity",
  "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
  }
}
```


# Delete Activity

```php
function deleteActivity(string $workspaceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Activity resources to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Activity resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$sid = 'Sid8';

$taskrouterV1ActivityApi = $client->getTaskrouterV1ActivityApi();
$apiResponse = $taskrouterV1ActivityApi->deleteActivity(
    $workspaceSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'void:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# List Activity

```php
function listActivity(
    string $workspaceSid,
    ?string $friendlyName = null,
    ?string $available = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Activity resources to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `friendlyName` | `?string` | Query, Optional | The `friendly_name` of the Activity resources to read. |
| `available` | `?string` | Query, Optional | Whether return only Activity resources that are available or unavailable. A value of `true` returns only available activities. Values of '1' or `yes` also indicate `true`. All other values represent `false` and return activities that are unavailable. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListActivityResponse`](../../doc/models/list-activity-response.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$friendlyName = 'friendly_name';

$available = 'true';

$taskrouterV1ActivityApi = $client->getTaskrouterV1ActivityApi();
$apiResponse = $taskrouterV1ActivityApi->listActivity(
    $workspaceSid,
    $friendlyName,
    $available
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListActivityResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "activities": [
    {
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "available": true,
      "date_created": "2014-05-14T10:50:02Z",
      "date_updated": "2014-05-14T23:26:06Z",
      "friendly_name": "New Activity",
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "links": {
        "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
      }
    }
  ],
  "meta": {
    "first_page_url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities?Available=true&FriendlyName=friendly_name&PageSize=50&Page=0",
    "key": "activities",
    "next_page_url": null,
    "page": 0,
    "page_size": 50,
    "previous_page_url": null,
    "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities?Available=true&FriendlyName=friendly_name&PageSize=50&Page=0"
  }
}
```


# Create Activity

```php
function createActivity(string $workspaceSid, string $friendlyName, ?bool $available = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace that the new Activity belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `friendlyName` | `string` | Form, Required | A descriptive string that you create to describe the Activity resource. It can be up to 64 characters long. These names are used to calculate and expose statistics about Workers, and provide visibility into the state of each Worker. Examples of friendly names include: `on-call`, `break`, and `email`. |
| `available` | `?bool` | Form, Optional | Whether the Worker should be eligible to receive a Task when it occupies the Activity. A value of `true`, `1`, or `yes` specifies the Activity is available. All other values specify that it is not. The value cannot be changed after the Activity is created. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Activity`](../../doc/models/activity.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$friendlyName = 'friendly_name';

$available = true;

$taskrouterV1ActivityApi = $client->getTaskrouterV1ActivityApi();
$apiResponse = $taskrouterV1ActivityApi->createActivity(
    $workspaceSid,
    $friendlyName,
    $available
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Activity:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "available": true,
  "date_created": "2014-05-14T10:50:02Z",
  "date_updated": "2014-05-14T23:26:06Z",
  "friendly_name": "New Activity",
  "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
  }
}
```

