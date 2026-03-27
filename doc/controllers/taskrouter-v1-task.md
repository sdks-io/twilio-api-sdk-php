# Taskrouter V1 Task

```php
$taskrouterV1TaskApi = $client->getTaskrouterV1TaskApi();
```

## Class Name

`TaskrouterV1TaskApi`

## Methods

* [Fetch Task](../../doc/controllers/taskrouter-v1-task.md#fetch-task)
* [Update Task](../../doc/controllers/taskrouter-v1-task.md#update-task)
* [Delete Task](../../doc/controllers/taskrouter-v1-task.md#delete-task)
* [List Task](../../doc/controllers/taskrouter-v1-task.md#list-task)
* [Create Task](../../doc/controllers/taskrouter-v1-task.md#create-task)


# Fetch Task

```php
function fetchTask(string $workspaceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Task to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Task resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`TaskRouterTask`](../../doc/models/task-router-task.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$sid = 'Sid8';

$taskrouterV1TaskApi = $client->getTaskrouterV1TaskApi();
$apiResponse = $taskrouterV1TaskApi->fetchTask(
    $workspaceSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'TaskRouterTask:';
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
  "age": 25200,
  "assignment_status": "pending",
  "attributes": "{\"body\": \"hello\"}",
  "date_created": "2014-05-14T18:50:02Z",
  "date_updated": "2014-05-15T07:26:06Z",
  "task_queue_entered_date": "2014-05-14T18:50:02Z",
  "virtual_start_time": "2014-05-14T18:50:02Z",
  "priority": 0,
  "reason": "Test Reason",
  "sid": "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_queue_sid": "WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_channel_sid": "TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_channel_unique_name": "task-channel",
  "timeout": 60,
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workflow_sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workflow_friendly_name": "Test Workflow",
  "task_queue_friendly_name": "Test Queue",
  "ignore_capacity": false,
  "routing_target": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "addons": "{}",
  "links": {
    "task_queue": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workflow": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "reservations": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations"
  }
}
```


# Update Task

```php
function updateTask(
    string $workspaceSid,
    string $sid,
    ?string $ifMatch = null,
    ?string $attributes = null,
    ?string $assignmentStatus = null,
    ?string $reason = null,
    ?int $priority = null,
    ?string $taskChannel = null,
    ?\DateTime $virtualStartTime = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Task to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Task resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |
| `ifMatch` | `?string` | Header, Optional | If provided, applies this mutation if (and only if) the [ETag](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag) header of the Task matches the provided value. This matches the semantics of (and is implemented with) the HTTP [If-Match header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/If-Match). |
| `attributes` | `?string` | Form, Optional | The JSON string that describes the custom attributes of the task. |
| `assignmentStatus` | [`?string(TaskStatus)`](../../doc/models/task-status.md) | Form, Optional | The current status of the Task's assignment. Can be: `pending`, `reserved`, `assigned`, `canceled`, `wrapping`, or `completed`. |
| `reason` | `?string` | Form, Optional | The reason that the Task was canceled or completed. This parameter is required only if the Task is canceled or completed. Setting this value queues the task for deletion and logs the reason. |
| `priority` | `?int` | Form, Optional | The Task's new priority value. When supplied, the Task takes on the specified priority unless it matches a Workflow Target with a Priority set. Value can be 0 to 2^31^ (2,147,483,647). |
| `taskChannel` | `?string` | Form, Optional | When MultiTasking is enabled, specify the TaskChannel with the task to update. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |
| `virtualStartTime` | `?DateTime` | Form, Optional | The task's new virtual start time value. When supplied, the Task takes on the specified virtual start time. Value can't be in the future or before the year of 1900. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`TaskRouterTask`](../../doc/models/task-router-task.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$sid = 'Sid8';

$attributes = 'attributes';

$assignmentStatus = TaskStatus::PENDING;

$reason = 'reason';

$priority = 1;

$virtualStartTime = DateTimeHelper::fromRfc3339DateTime('08/02/2023 12:34:56');

$taskrouterV1TaskApi = $client->getTaskrouterV1TaskApi();
$apiResponse = $taskrouterV1TaskApi->updateTask(
    $workspaceSid,
    $sid,
    null,
    $attributes,
    $assignmentStatus,
    $reason,
    $priority,
    null,
    $virtualStartTime
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'TaskRouterTask:';
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
  "age": 25200,
  "assignment_status": "pending",
  "attributes": "{\"body\": \"hello\"}",
  "date_created": "2014-05-14T18:50:02Z",
  "date_updated": "2014-05-15T07:26:06Z",
  "task_queue_entered_date": "2014-05-14T18:50:02Z",
  "virtual_start_time": "2023-08-02T12:34:56Z",
  "priority": 0,
  "reason": "Test Reason",
  "sid": "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_queue_sid": "WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_channel_sid": "TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_channel_unique_name": "task-channel",
  "timeout": 60,
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workflow_sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workflow_friendly_name": "Test Workflow",
  "task_queue_friendly_name": "Test Queue",
  "addons": "{}",
  "ignore_capacity": false,
  "routing_target": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "task_queue": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workflow": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "reservations": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations"
  }
}
```


# Delete Task

```php
function deleteTask(string $workspaceSid, string $sid, ?string $ifMatch = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Task to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Task resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |
| `ifMatch` | `?string` | Header, Optional | If provided, deletes this Task if (and only if) the [ETag](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag) header of the Task matches the provided value. This matches the semantics of (and is implemented with) the HTTP [If-Match header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/If-Match). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$sid = 'Sid8';

$taskrouterV1TaskApi = $client->getTaskrouterV1TaskApi();
$apiResponse = $taskrouterV1TaskApi->deleteTask(
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


# List Task

```php
function listTask(
    string $workspaceSid,
    ?int $priority = null,
    ?array $assignmentStatus = null,
    ?string $workflowSid = null,
    ?string $workflowName = null,
    ?string $taskQueueSid = null,
    ?string $taskQueueName = null,
    ?string $evaluateTaskAttributes = null,
    ?string $routingTarget = null,
    ?string $ordering = null,
    ?bool $hasAddons = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Tasks to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `priority` | `?int` | Query, Optional | The priority value of the Tasks to read. Returns the list of all Tasks in the Workspace with the specified priority. |
| `assignmentStatus` | `?(string[])` | Query, Optional | The `assignment_status` of the Tasks you want to read. Can be: `pending`, `reserved`, `assigned`, `canceled`, `wrapping`, or `completed`. Returns all Tasks in the Workspace with the specified `assignment_status`. |
| `workflowSid` | `?string` | Query, Optional | The SID of the Workflow with the Tasks to read. Returns the Tasks controlled by the Workflow identified by this SID.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |
| `workflowName` | `?string` | Query, Optional | The friendly name of the Workflow with the Tasks to read. Returns the Tasks controlled by the Workflow identified by this friendly name. |
| `taskQueueSid` | `?string` | Query, Optional | The SID of the TaskQueue with the Tasks to read. Returns the Tasks waiting in the TaskQueue identified by this SID.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |
| `taskQueueName` | `?string` | Query, Optional | The `friendly_name` of the TaskQueue with the Tasks to read. Returns the Tasks waiting in the TaskQueue identified by this friendly name. |
| `evaluateTaskAttributes` | `?string` | Query, Optional | The attributes of the Tasks to read. Returns the Tasks that match the attributes specified in this parameter. |
| `routingTarget` | `?string` | Query, Optional | A SID of a Worker, Queue, or Workflow to route a Task to |
| `ordering` | `?string` | Query, Optional | How to order the returned Task resources. By default, Tasks are sorted by ascending DateCreated. This value is specified as: `Attribute:Order`, where `Attribute` can be either `DateCreated`, `Priority`, or `VirtualStartTime` and `Order` can be either `asc` or `desc`. For example, `Priority:desc` returns Tasks ordered in descending order of their Priority. Pairings of sort orders can be specified in a comma-separated list such as `Priority:desc,DateCreated:asc`, which returns the Tasks in descending Priority order and ascending DateCreated Order. The only ordering pairing not allowed is DateCreated and VirtualStartTime. |
| `hasAddons` | `?bool` | Query, Optional | Whether to read Tasks with Add-ons. If `true`, returns only Tasks with Add-ons. If `false`, returns only Tasks without Add-ons. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListTaskResponse`](../../doc/models/list-task-response.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$priority = 1;

$assignmentStatus = [
    'pending',
    'reserved'
];

$workflowSid = 'WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$workflowName = 'workflow_name';

$taskQueueSid = 'WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$taskQueueName = 'task_queue_name';

$routingTarget = 'WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$taskrouterV1TaskApi = $client->getTaskrouterV1TaskApi();
$apiResponse = $taskrouterV1TaskApi->listTask(
    $workspaceSid,
    $priority,
    $assignmentStatus,
    $workflowSid,
    $workflowName,
    $taskQueueSid,
    $taskQueueName,
    null,
    $routingTarget
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListTaskResponse:';
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
    "first_page_url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks?TaskQueueSid=WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&RoutingTarget=WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&TaskQueueName=task_queue_name&WorkflowName=workflow_name&WorkflowSid=WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&AssignmentStatus=pending%2Creserved&Priority=1&PageSize=50&Page=0",
    "key": "tasks",
    "next_page_url": null,
    "page": 0,
    "page_size": 50,
    "previous_page_url": null,
    "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks?TaskQueueSid=WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&RoutingTarget=WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&TaskQueueName=task_queue_name&WorkflowName=workflow_name&WorkflowSid=WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa&AssignmentStatus=pending%2Creserved&Priority=1&PageSize=50&Page=0"
  },
  "tasks": [
    {
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "age": 25200,
      "assignment_status": "pending",
      "attributes": "{\"body\": \"hello\"}",
      "date_created": "2014-05-14T14:26:54Z",
      "date_updated": "2014-05-15T16:03:42Z",
      "task_queue_entered_date": "2014-05-14T14:26:54Z",
      "virtual_start_time": "2014-05-14T14:26:54Z",
      "priority": 0,
      "reason": "Test Reason",
      "sid": "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "task_queue_sid": "WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "task_channel_sid": "TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "task_channel_unique_name": "task-channel",
      "timeout": 60,
      "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "workflow_sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "workflow_friendly_name": "Test Workflow",
      "task_queue_friendly_name": "Test Queue",
      "ignore_capacity": false,
      "routing_target": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "addons": "{}",
      "links": {
        "task_queue": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "workflow": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "reservations": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations"
      }
    }
  ]
}
```


# Create Task

```php
function createTask(
    string $workspaceSid,
    ?int $timeout = null,
    ?int $priority = null,
    ?string $taskChannel = null,
    ?string $workflowSid = null,
    ?string $attributes = null,
    ?\DateTime $virtualStartTime = null,
    ?string $routingTarget = null,
    ?string $ignoreCapacity = null,
    ?string $taskQueueSid = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace that the new Task belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `timeout` | `?int` | Form, Optional | The amount of time in seconds the new task can live before being assigned. Can be up to a maximum of 2 weeks (1,209,600 seconds). The default value is 24 hours (86,400 seconds). On timeout, the `task.canceled` event will fire with description `Task TTL Exceeded`. |
| `priority` | `?int` | Form, Optional | The priority to assign the new task and override the default. When supplied, the new Task will have this priority unless it matches a Workflow Target with a Priority set. When not supplied, the new Task will have the priority of the matching Workflow Target. Value can be 0 to 2^31^ (2,147,483,647). |
| `taskChannel` | `?string` | Form, Optional | When MultiTasking is enabled, specify the TaskChannel by passing either its `unique_name` or `sid`. Default value is `default`. |
| `workflowSid` | `?string` | Form, Optional | The SID of the Workflow that you would like to handle routing for the new Task. If there is only one Workflow defined for the Workspace that you are posting the new task to, this parameter is optional.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |
| `attributes` | `?string` | Form, Optional | A JSON string with the attributes of the new task. This value is passed to the Workflow's `assignment_callback_url` when the Task is assigned to a Worker. For example: `{ "task_type": "call", "twilio_call_sid": "CAxxx", "customer_ticket_number": "12345" }`. |
| `virtualStartTime` | `?DateTime` | Form, Optional | The virtual start time to assign the new task and override the default. When supplied, the new task will have this virtual start time. When not supplied, the new task will have the virtual start time equal to `date_created`. Value can't be in the future or before the year of 1900. |
| `routingTarget` | `?string` | Form, Optional | A SID of a Worker, Queue, or Workflow to route a Task to |
| `ignoreCapacity` | `?string` | Form, Optional | A boolean that indicates if the Task should respect a Worker's capacity and availability during assignment. This field can only be used when the `RoutingTarget` field is set to a Worker SID. By setting `IgnoreCapacity` to a value of `true`, `1`, or `yes`, the Task will be routed to the Worker without respecting their capacity and availability. Any other value will enforce the Worker's capacity and availability. The default value of `IgnoreCapacity` is `true` when the `RoutingTarget` is set to a Worker SID. |
| `taskQueueSid` | `?string` | Form, Optional | The SID of the TaskQueue in which the Task belongs<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`TaskRouterTask`](../../doc/models/task-router-task.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$timeout = 1;

$priority = 1;

$taskChannel = 'channel';

$workflowSid = 'WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$attributes = '{"body": "attributes"}';

$virtualStartTime = DateTimeHelper::fromRfc3339DateTime('05/14/2014 18:50:02');

$routingTarget = 'WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$ignoreCapacity = 'false';

$taskQueueSid = 'WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$taskrouterV1TaskApi = $client->getTaskrouterV1TaskApi();
$apiResponse = $taskrouterV1TaskApi->createTask(
    $workspaceSid,
    $timeout,
    $priority,
    $taskChannel,
    $workflowSid,
    $attributes,
    $virtualStartTime,
    $routingTarget,
    $ignoreCapacity,
    $taskQueueSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'TaskRouterTask:';
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
  "age": 25200,
  "assignment_status": "pending",
  "attributes": "{\"body\": \"attributes\"}",
  "date_created": "2014-05-14T18:50:02Z",
  "date_updated": "2014-05-15T07:26:06Z",
  "task_queue_entered_date": null,
  "virtual_start_time": "2014-05-14T18:50:02Z",
  "priority": 1,
  "reason": "Test Reason",
  "sid": "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_queue_sid": "WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_channel_sid": "TCaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_channel_unique_name": "unique",
  "timeout": 60,
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workflow_sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workflow_friendly_name": "Example Workflow",
  "task_queue_friendly_name": "Example Task Queue",
  "ignore_capacity": false,
  "routing_target": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "addons": "{}",
  "links": {
    "task_queue": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workflow": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "reservations": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations"
  }
}
```

