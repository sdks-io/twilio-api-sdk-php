# Taskrouter V1 Worker

```php
$taskrouterV1WorkerApi = $client->getTaskrouterV1WorkerApi();
```

## Class Name

`TaskrouterV1WorkerApi`

## Methods

* [List Worker](../../doc/controllers/taskrouter-v1-worker.md#list-worker)
* [Create Worker](../../doc/controllers/taskrouter-v1-worker.md#create-worker)
* [Fetch Worker](../../doc/controllers/taskrouter-v1-worker.md#fetch-worker)
* [Update Worker](../../doc/controllers/taskrouter-v1-worker.md#update-worker)
* [Delete Worker](../../doc/controllers/taskrouter-v1-worker.md#delete-worker)


# List Worker

```php
function listWorker(
    string $workspaceSid,
    ?string $activityName = null,
    ?string $activitySid = null,
    ?string $available = null,
    ?string $friendlyName = null,
    ?string $targetWorkersExpression = null,
    ?string $taskQueueName = null,
    ?string $taskQueueSid = null,
    ?string $ordering = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Workers to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `activityName` | `?string` | Query, Optional | The `activity_name` of the Worker resources to read. |
| `activitySid` | `?string` | Query, Optional | The `activity_sid` of the Worker resources to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |
| `available` | `?string` | Query, Optional | Whether to return only Worker resources that are available or unavailable. Can be `true`, `1`, or `yes` to return Worker resources that are available, and `false`, or any value returns the Worker resources that are not available. |
| `friendlyName` | `?string` | Query, Optional | The `friendly_name` of the Worker resources to read. |
| `targetWorkersExpression` | `?string` | Query, Optional | Filter by Workers that would match an expression. In addition to fields in the workers' attributes, the expression can include the following worker fields: `sid`, `friendly_name`, `activity_sid`, or `activity_name` |
| `taskQueueName` | `?string` | Query, Optional | The `friendly_name` of the TaskQueue that the Workers to read are eligible for. |
| `taskQueueSid` | `?string` | Query, Optional | The SID of the TaskQueue that the Workers to read are eligible for.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |
| `ordering` | `?string` | Query, Optional | Sorting parameter for Workers |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListWorkerResponse`](../../doc/models/list-worker-response.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$activityName = 'activity_name';

$activitySid = 'WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$available = 'available';

$friendlyName = 'friendly_name';

$targetWorkersExpression = 'target_workers_expression';

$taskQueueName = 'task_queue_name';

$taskQueueSid = 'WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$taskrouterV1WorkerApi = $client->getTaskrouterV1WorkerApi();
$apiResponse = $taskrouterV1WorkerApi->listWorker(
    $workspaceSid,
    $activityName,
    $activitySid,
    $available,
    $friendlyName,
    $targetWorkersExpression,
    $taskQueueName,
    $taskQueueSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListWorkerResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers?Available=available&TargetWorkersExpression=target_workers_expression&TaskQueueName=task_queue_name&ActivityName=activity_name&ActivitySid=WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&TaskQueueSid=WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&FriendlyName=friendly_name&PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers?Available=available&TargetWorkersExpression=target_workers_expression&TaskQueueName=task_queue_name&ActivityName=activity_name&ActivitySid=WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&TaskQueueSid=WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&FriendlyName=friendly_name&PageSize=50&Page=0",
    "next_page_url": null,
    "key": "workers"
  },
  "workers": [
    {
      "sid": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "testWorker",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "activity_name": "Offline",
      "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "attributes": "{}",
      "available": false,
      "date_created": "2017-05-30T23:05:29Z",
      "date_updated": "2017-05-30T23:05:29Z",
      "date_status_changed": "2017-05-30T23:05:29Z",
      "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "links": {
        "channels": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Channels",
        "activity": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/Statistics",
        "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/RealTimeStatistics",
        "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/CumulativeStatistics",
        "worker_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
        "worker_channels": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Channels",
        "reservations": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations"
      }
    }
  ]
}
```


# Create Worker

```php
function createWorker(
    string $workspaceSid,
    string $friendlyName,
    ?string $activitySid = null,
    ?string $attributes = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace that the new Worker belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `friendlyName` | `string` | Form, Required | A descriptive string that you create to describe the new Worker. It can be up to 64 characters long. |
| `activitySid` | `?string` | Form, Optional | The SID of a valid Activity that will describe the new Worker's initial state. See [Activities](https://www.twilio.com/docs/taskrouter/api/activity) for more information. If not provided, the new Worker's initial state is the `default_activity_sid` configured on the Workspace.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |
| `attributes` | `?string` | Form, Optional | A valid JSON string that describes the new Worker. For example: `{ "email": "Bob@example.com", "phone": "+5095551234" }`. This data is passed to the `assignment_callback_url` when TaskRouter assigns a Task to the Worker. Defaults to {}. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Worker`](../../doc/models/worker.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$friendlyName = 'friendly_name';

$activitySid = 'WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$attributes = 'attributes';

$taskrouterV1WorkerApi = $client->getTaskrouterV1WorkerApi();
$apiResponse = $taskrouterV1WorkerApi->createWorker(
    $workspaceSid,
    $friendlyName,
    $activitySid,
    $attributes
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Worker:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "NewWorker",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "activity_name": "Offline",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "attributes": "{}",
  "available": false,
  "date_created": "2017-05-30T23:19:38Z",
  "date_updated": "2017-05-30T23:19:38Z",
  "date_status_changed": "2017-05-30T23:19:38Z",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "channels": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Channels",
    "activity": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/Statistics",
    "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/RealTimeStatistics",
    "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/CumulativeStatistics",
    "worker_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
    "worker_channels": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Channels",
    "reservations": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations"
  }
}
```


# Fetch Worker

```php
function fetchWorker(string $workspaceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Worker to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Worker resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WK[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Worker`](../../doc/models/worker.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$sid = 'Sid8';

$taskrouterV1WorkerApi = $client->getTaskrouterV1WorkerApi();
$apiResponse = $taskrouterV1WorkerApi->fetchWorker(
    $workspaceSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Worker:';
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
  "activity_name": "available",
  "activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "attributes": "{}",
  "available": false,
  "date_created": "2017-05-30T23:32:39Z",
  "date_status_changed": "2017-05-30T23:32:39Z",
  "date_updated": "2017-05-30T23:32:39Z",
  "friendly_name": "NewWorker3",
  "sid": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "channels": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Channels",
    "activity": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/Statistics",
    "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/RealTimeStatistics",
    "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/CumulativeStatistics",
    "worker_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
    "worker_channels": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Channels",
    "reservations": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations"
  }
}
```


# Update Worker

```php
function updateWorker(
    string $workspaceSid,
    string $sid,
    ?string $ifMatch = null,
    ?string $activitySid = null,
    ?string $attributes = null,
    ?string $friendlyName = null,
    ?bool $rejectPendingReservations = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Worker to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Worker resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WK[0-9a-fA-F]{32}$` |
| `ifMatch` | `?string` | Header, Optional | The If-Match HTTP request header |
| `activitySid` | `?string` | Form, Optional | The SID of a valid Activity that will describe the Worker's initial state. See [Activities](https://www.twilio.com/docs/taskrouter/api/activity) for more information.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |
| `attributes` | `?string` | Form, Optional | The JSON string that describes the Worker. For example: `{ "email": "Bob@example.com", "phone": "+5095551234" }`. This data is passed to the `assignment_callback_url` when TaskRouter assigns a Task to the Worker. Defaults to {}. |
| `friendlyName` | `?string` | Form, Optional | A descriptive string that you create to describe the Worker. It can be up to 64 characters long. |
| `rejectPendingReservations` | `?bool` | Form, Optional | Whether to reject the Worker's pending reservations. This option is only valid if the Worker's new [Activity](https://www.twilio.com/docs/taskrouter/api/activity) resource has its `availability` property set to `False`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Worker`](../../doc/models/worker.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$sid = 'Sid8';

$activitySid = 'WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$attributes = 'attributes';

$friendlyName = 'friendly_name';

$taskrouterV1WorkerApi = $client->getTaskrouterV1WorkerApi();
$apiResponse = $taskrouterV1WorkerApi->updateWorker(
    $workspaceSid,
    $sid,
    null,
    $activitySid,
    $attributes,
    $friendlyName
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Worker:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "blah",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "activity_name": "Offline",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "attributes": "{}",
  "available": false,
  "date_created": "2017-05-30T23:32:22Z",
  "date_updated": "2017-05-31T00:05:57Z",
  "date_status_changed": "2017-05-30T23:32:22Z",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "channels": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Channels",
    "activity": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/Statistics",
    "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/RealTimeStatistics",
    "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/CumulativeStatistics",
    "worker_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
    "worker_channels": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Channels",
    "reservations": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations"
  }
}
```


# Delete Worker

```php
function deleteWorker(string $workspaceSid, string $sid, ?string $ifMatch = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Worker to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Worker resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WK[0-9a-fA-F]{32}$` |
| `ifMatch` | `?string` | Header, Optional | The If-Match HTTP request header |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$sid = 'Sid8';

$taskrouterV1WorkerApi = $client->getTaskrouterV1WorkerApi();
$apiResponse = $taskrouterV1WorkerApi->deleteWorker(
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

