# Taskrouter V1 Task Queue

```php
$taskrouterV1TaskQueueApi = $client->getTaskrouterV1TaskQueueApi();
```

## Class Name

`TaskrouterV1TaskQueueApi`

## Methods

* [Fetch Task Queue](../../doc/controllers/taskrouter-v1-task-queue.md#fetch-task-queue)
* [Update Task Queue](../../doc/controllers/taskrouter-v1-task-queue.md#update-task-queue)
* [Delete Task Queue](../../doc/controllers/taskrouter-v1-task-queue.md#delete-task-queue)
* [List Task Queue](../../doc/controllers/taskrouter-v1-task-queue.md#list-task-queue)
* [Create Task Queue](../../doc/controllers/taskrouter-v1-task-queue.md#create-task-queue)


# Fetch Task Queue

```php
function fetchTaskQueue(string $workspaceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the TaskQueue to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the TaskQueue resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`TaskQueue`](../../doc/models/task-queue.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$sid = 'Sid8';

$taskrouterV1TaskQueueApi = $client->getTaskrouterV1TaskQueueApi();
$apiResponse = $taskrouterV1TaskQueueApi->fetchTaskQueue(
    $workspaceSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'TaskQueue:';
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
  "assignment_activity_name": "817ca1c5-3a05-11e5-9292-98e0d9a1eb73",
  "assignment_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "date_created": "2015-08-04T01:31:41Z",
  "date_updated": "2015-08-04T01:31:41Z",
  "friendly_name": "81f96435-3a05-11e5-9f81-98e0d9a1eb73",
  "max_reserved_workers": 1,
  "links": {
    "assignment_activity": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "reservation_activity": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
    "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
    "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics",
    "list_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/Statistics",
    "bulk_real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/RealTimeStatistics"
  },
  "reservation_activity_name": "80fa2beb-3a05-11e5-8fc8-98e0d9a1eb73",
  "reservation_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "sid": "WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "target_workers": null,
  "task_order": "FIFO",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Update Task Queue

```php
function updateTaskQueue(
    string $workspaceSid,
    string $sid,
    ?string $friendlyName = null,
    ?string $targetWorkers = null,
    ?string $reservationActivitySid = null,
    ?string $assignmentActivitySid = null,
    ?int $maxReservedWorkers = null,
    ?string $taskOrder = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the TaskQueue to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the TaskQueue resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |
| `friendlyName` | `?string` | Form, Optional | A descriptive string that you create to describe the TaskQueue. For example `Support-Tier 1`, `Sales`, or `Escalation`. |
| `targetWorkers` | `?string` | Form, Optional | A string describing the Worker selection criteria for any Tasks that enter the TaskQueue. For example '"language" == "spanish"' If no TargetWorkers parameter is provided, Tasks will wait in the queue until they are either deleted or moved to another queue. Additional examples on how to describing Worker selection criteria below. |
| `reservationActivitySid` | `?string` | Form, Optional | The SID of the Activity to assign Workers when a task is reserved for them.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |
| `assignmentActivitySid` | `?string` | Form, Optional | The SID of the Activity to assign Workers when a task is assigned for them.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |
| `maxReservedWorkers` | `?int` | Form, Optional | The maximum number of Workers to create reservations for the assignment of a task while in the queue. Maximum of 50. |
| `taskOrder` | [`?string(TaskQueueTaskOrder)`](../../doc/models/task-queue-task-order.md) | Form, Optional | How Tasks will be assigned to Workers. Set this parameter to `LIFO` to assign most recently created Task first or `FIFO` to assign the oldest Task. Default is FIFO. [Click here](https://www.twilio.com/docs/taskrouter/queue-ordering-last-first-out-lifo) to learn more. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`TaskQueue`](../../doc/models/task-queue.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$sid = 'Sid8';

$friendlyName = 'friendly_name';

$targetWorkers = 'target_workers';

$reservationActivitySid = 'WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$assignmentActivitySid = 'WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$maxReservedWorkers = 1;

$taskrouterV1TaskQueueApi = $client->getTaskrouterV1TaskQueueApi();
$apiResponse = $taskrouterV1TaskQueueApi->updateTaskQueue(
    $workspaceSid,
    $sid,
    $friendlyName,
    $targetWorkers,
    $reservationActivitySid,
    $assignmentActivitySid,
    $maxReservedWorkers
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'TaskQueue:';
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
  "assignment_activity_name": "817ca1c5-3a05-11e5-9292-98e0d9a1eb73",
  "assignment_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "date_created": "2015-08-04T01:31:41Z",
  "date_updated": "2015-08-04T01:31:41Z",
  "friendly_name": "81f96435-3a05-11e5-9f81-98e0d9a1eb73",
  "max_reserved_workers": 1,
  "links": {
    "assignment_activity": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "reservation_activity": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
    "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
    "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics",
    "list_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/Statistics",
    "bulk_real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/RealTimeStatistics"
  },
  "reservation_activity_name": "80fa2beb-3a05-11e5-8fc8-98e0d9a1eb73",
  "reservation_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "sid": "WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "target_workers": null,
  "task_order": "FIFO",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Task Queue

```php
function deleteTaskQueue(string $workspaceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the TaskQueue to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the TaskQueue resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$sid = 'Sid8';

$taskrouterV1TaskQueueApi = $client->getTaskrouterV1TaskQueueApi();
$apiResponse = $taskrouterV1TaskQueueApi->deleteTaskQueue(
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


# List Task Queue

```php
function listTaskQueue(
    string $workspaceSid,
    ?string $friendlyName = null,
    ?string $evaluateWorkerAttributes = null,
    ?string $workerSid = null,
    ?string $ordering = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the TaskQueue to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `friendlyName` | `?string` | Query, Optional | The `friendly_name` of the TaskQueue resources to read. |
| `evaluateWorkerAttributes` | `?string` | Query, Optional | The attributes of the Workers to read. Returns the TaskQueues with Workers that match the attributes specified in this parameter. |
| `workerSid` | `?string` | Query, Optional | The SID of the Worker with the TaskQueue resources to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WK[0-9a-fA-F]{32}$` |
| `ordering` | `?string` | Query, Optional | Sorting parameter for TaskQueues |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListTaskQueueResponse`](../../doc/models/list-task-queue-response.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$friendlyName = 'friendly_name';

$evaluateWorkerAttributes = 'evaluate_worker_attributes';

$taskrouterV1TaskQueueApi = $client->getTaskrouterV1TaskQueueApi();
$apiResponse = $taskrouterV1TaskQueueApi->listTaskQueue(
    $workspaceSid,
    $friendlyName,
    $evaluateWorkerAttributes
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListTaskQueueResponse:';
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
    "first_page_url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues?EvaluateWorkerAttributes=evaluate_worker_attributes&FriendlyName=friendly_name&PageSize=50&Page=0",
    "key": "task_queues",
    "next_page_url": null,
    "page": 0,
    "page_size": 50,
    "previous_page_url": null,
    "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues?EvaluateWorkerAttributes=evaluate_worker_attributes&FriendlyName=friendly_name&PageSize=50&Page=0"
  },
  "task_queues": [
    {
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "assignment_activity_name": "817ca1c5-3a05-11e5-9292-98e0d9a1eb73",
      "assignment_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "date_created": "2015-08-04T01:31:41Z",
      "date_updated": "2015-08-04T01:31:41Z",
      "friendly_name": "81f96435-3a05-11e5-9f81-98e0d9a1eb73",
      "max_reserved_workers": 1,
      "links": {
        "assignment_activity": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "reservation_activity": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
        "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
        "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics",
        "list_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/Statistics",
        "bulk_real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/RealTimeStatistics"
      },
      "reservation_activity_name": "80fa2beb-3a05-11e5-8fc8-98e0d9a1eb73",
      "reservation_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "sid": "WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "target_workers": null,
      "task_order": "FIFO",
      "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```


# Create Task Queue

```php
function createTaskQueue(
    string $workspaceSid,
    string $friendlyName,
    ?string $targetWorkers = null,
    ?int $maxReservedWorkers = null,
    ?string $taskOrder = null,
    ?string $reservationActivitySid = null,
    ?string $assignmentActivitySid = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace that the new TaskQueue belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `friendlyName` | `string` | Form, Required | A descriptive string that you create to describe the TaskQueue. For example `Support-Tier 1`, `Sales`, or `Escalation`. |
| `targetWorkers` | `?string` | Form, Optional | A string that describes the Worker selection criteria for any Tasks that enter the TaskQueue. For example, `'"language" == "spanish"'`. The default value is `1==1`. If this value is empty, Tasks will wait in the TaskQueue until they are deleted or moved to another TaskQueue. For more information about Worker selection, see [Describing Worker selection criteria](https://www.twilio.com/docs/taskrouter/api/taskqueues#target-workers). |
| `maxReservedWorkers` | `?int` | Form, Optional | The maximum number of Workers to reserve for the assignment of a Task in the queue. Can be an integer between 1 and 50, inclusive and defaults to 1. |
| `taskOrder` | [`?string(TaskQueueTaskOrder)`](../../doc/models/task-queue-task-order.md) | Form, Optional | How Tasks will be assigned to Workers. Set this parameter to `LIFO` to assign most recently created Task first or `FIFO` to assign the oldest Task. Default is FIFO. [Click here](https://www.twilio.com/docs/taskrouter/queue-ordering-last-first-out-lifo) to learn more. |
| `reservationActivitySid` | `?string` | Form, Optional | The SID of the Activity to assign Workers when a task is reserved for them.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |
| `assignmentActivitySid` | `?string` | Form, Optional | The SID of the Activity to assign Workers when a task is assigned to them.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`TaskQueue`](../../doc/models/task-queue.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$friendlyName = 'friendly_name';

$targetWorkers = 'target_workers';

$maxReservedWorkers = 1;

$reservationActivitySid = 'WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$assignmentActivitySid = 'WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$taskrouterV1TaskQueueApi = $client->getTaskrouterV1TaskQueueApi();
$apiResponse = $taskrouterV1TaskQueueApi->createTaskQueue(
    $workspaceSid,
    $friendlyName,
    $targetWorkers,
    $maxReservedWorkers,
    null,
    $reservationActivitySid,
    $assignmentActivitySid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'TaskQueue:';
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
  "assignment_activity_name": "817ca1c5-3a05-11e5-9292-98e0d9a1eb73",
  "assignment_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "date_created": "2015-08-04T01:31:41Z",
  "date_updated": "2015-08-04T01:31:41Z",
  "friendly_name": "81f96435-3a05-11e5-9f81-98e0d9a1eb73",
  "max_reserved_workers": 1,
  "links": {
    "assignment_activity": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "reservation_activity": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities/WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
    "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
    "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics",
    "list_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/Statistics",
    "bulk_real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/RealTimeStatistics"
  },
  "reservation_activity_name": "80fa2beb-3a05-11e5-8fc8-98e0d9a1eb73",
  "reservation_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "sid": "WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "target_workers": null,
  "task_order": "FIFO",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```

