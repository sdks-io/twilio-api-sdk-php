# Taskrouter V1 Workspace

```php
$taskrouterV1WorkspaceApi = $client->getTaskrouterV1WorkspaceApi();
```

## Class Name

`TaskrouterV1WorkspaceApi`

## Methods

* [Fetch Workspace](../../doc/controllers/taskrouter-v1-workspace.md#fetch-workspace)
* [Update Workspace](../../doc/controllers/taskrouter-v1-workspace.md#update-workspace)
* [Delete Workspace](../../doc/controllers/taskrouter-v1-workspace.md#delete-workspace)
* [List Workspace](../../doc/controllers/taskrouter-v1-workspace.md#list-workspace)
* [Create Workspace](../../doc/controllers/taskrouter-v1-workspace.md#create-workspace)


# Fetch Workspace

```php
function fetchWorkspace(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the Workspace resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Workspace`](../../doc/models/workspace.md).

## Example Usage

```php
$sid = 'Sid8';

$taskrouterV1WorkspaceApi = $client->getTaskrouterV1WorkspaceApi();
$apiResponse = $taskrouterV1WorkspaceApi->fetchWorkspace($sid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Workspace:';
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
  "date_created": "2016-08-01T22:10:40Z",
  "date_updated": "2016-08-01T22:10:40Z",
  "default_activity_name": "Offline",
  "default_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "event_callback_url": "",
  "events_filter": null,
  "friendly_name": "new",
  "links": {
    "activities": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities",
    "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
    "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
    "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics",
    "task_queues": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues",
    "tasks": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks",
    "workers": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers",
    "workflows": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows",
    "task_channels": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskChannels",
    "events": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Events"
  },
  "multi_task_enabled": false,
  "prioritize_queue_order": "FIFO",
  "sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "timeout_activity_name": "Offline",
  "timeout_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Update Workspace

```php
function updateWorkspace(
    string $sid,
    ?string $defaultActivitySid = null,
    ?string $eventCallbackUrl = null,
    ?string $eventsFilter = null,
    ?string $friendlyName = null,
    ?bool $multiTaskEnabled = null,
    ?string $timeoutActivitySid = null,
    ?string $prioritizeQueueOrder = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the Workspace resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `defaultActivitySid` | `?string` | Form, Optional | The SID of the Activity that will be used when new Workers are created in the Workspace.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |
| `eventCallbackUrl` | `?string` | Form, Optional | The URL we should call when an event occurs. See [Workspace Events](https://www.twilio.com/docs/taskrouter/api/event) for more information. This parameter supports Twilio's [Webhooks (HTTP callbacks) Connection Overrides](https://www.twilio.com/docs/usage/webhooks/webhooks-connection-overrides). |
| `eventsFilter` | `?string` | Form, Optional | The list of Workspace events for which to call event_callback_url. For example if `EventsFilter=task.created,task.canceled,worker.activity.update`, then TaskRouter will call event_callback_url only when a task is created, canceled, or a Worker activity is updated. |
| `friendlyName` | `?string` | Form, Optional | A descriptive string that you create to describe the Workspace resource. For example: `Sales Call Center` or `Customer Support Team`. |
| `multiTaskEnabled` | `?bool` | Form, Optional | Whether to enable multi-tasking. Can be: `true` to enable multi-tasking, or `false` to disable it. However, all workspaces should be maintained as multi-tasking. There is no default when omitting this parameter. A multi-tasking Workspace can't be updated to single-tasking unless it is not a Flex Project and another (legacy) single-tasking Workspace exists. Multi-tasking allows Workers to handle multiple Tasks simultaneously. In multi-tasking mode, each Worker can receive parallel reservations up to the per-channel maximums defined in the Workers section. In single-tasking mode (legacy mode), each Worker will only receive a new reservation when the previous task is completed. Learn more at [Multitasking](https://www.twilio.com/docs/taskrouter/multitasking). |
| `timeoutActivitySid` | `?string` | Form, Optional | The SID of the Activity that will be assigned to a Worker when a Task reservation times out without a response.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |
| `prioritizeQueueOrder` | [`?string(WorkspaceQueueOrder)`](../../doc/models/workspace-queue-order.md) | Form, Optional | The type of TaskQueue to prioritize when Workers are receiving Tasks from both types of TaskQueues. Can be: `LIFO` or `FIFO` and the default is `FIFO`. For more information, see [Queue Ordering](https://www.twilio.com/docs/taskrouter/queue-ordering-last-first-out-lifo). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Workspace`](../../doc/models/workspace.md).

## Example Usage

```php
$sid = 'Sid8';

$defaultActivitySid = 'WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$eventCallbackUrl = '/example';

$friendlyName = 'friendly_name';

$timeoutActivitySid = 'WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$taskrouterV1WorkspaceApi = $client->getTaskrouterV1WorkspaceApi();
$apiResponse = $taskrouterV1WorkspaceApi->updateWorkspace(
    $sid,
    $defaultActivitySid,
    $eventCallbackUrl,
    null,
    $friendlyName,
    null,
    $timeoutActivitySid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Workspace:';
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
  "date_created": "2016-08-01T22:10:40Z",
  "date_updated": "2016-08-01T22:10:40Z",
  "default_activity_name": "Offline",
  "default_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "event_callback_url": "",
  "events_filter": null,
  "friendly_name": "new",
  "links": {
    "activities": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities",
    "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
    "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
    "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics",
    "task_queues": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues",
    "tasks": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks",
    "workers": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers",
    "workflows": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows",
    "task_channels": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskChannels",
    "events": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Events"
  },
  "multi_task_enabled": false,
  "prioritize_queue_order": "FIFO",
  "sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "timeout_activity_name": "Offline",
  "timeout_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Workspace

```php
function deleteWorkspace(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the Workspace resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$sid = 'Sid8';

$taskrouterV1WorkspaceApi = $client->getTaskrouterV1WorkspaceApi();
$apiResponse = $taskrouterV1WorkspaceApi->deleteWorkspace($sid);

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


# List Workspace

```php
function listWorkspace(
    ?string $friendlyName = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `friendlyName` | `?string` | Query, Optional | The `friendly_name` of the Workspace resources to read. For example `Customer Support` or `2014 Election Campaign`. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListWorkspaceResponse`](../../doc/models/list-workspace-response.md).

## Example Usage

```php
$friendlyName = 'friendly_name';

$taskrouterV1WorkspaceApi = $client->getTaskrouterV1WorkspaceApi();
$apiResponse = $taskrouterV1WorkspaceApi->listWorkspace($friendlyName);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListWorkspaceResponse:';
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
    "first_page_url": "https://taskrouter.twilio.com/v1/Workspaces?FriendlyName=friendly_name&PageSize=50&Page=0",
    "key": "workspaces",
    "next_page_url": null,
    "page": 0,
    "page_size": 50,
    "previous_page_url": null,
    "url": "https://taskrouter.twilio.com/v1/Workspaces?FriendlyName=friendly_name&PageSize=50&Page=0"
  },
  "workspaces": [
    {
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "date_created": "2016-08-01T22:10:40Z",
      "date_updated": "2016-08-01T22:10:40Z",
      "default_activity_name": "Offline",
      "default_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "event_callback_url": "",
      "events_filter": null,
      "friendly_name": "new",
      "links": {
        "activities": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities",
        "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
        "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
        "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics",
        "task_queues": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues",
        "tasks": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks",
        "workers": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers",
        "workflows": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows",
        "task_channels": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskChannels",
        "events": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Events"
      },
      "multi_task_enabled": false,
      "prioritize_queue_order": "FIFO",
      "sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "timeout_activity_name": "Offline",
      "timeout_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```


# Create Workspace

```php
function createWorkspace(
    string $friendlyName,
    ?string $eventCallbackUrl = null,
    ?string $eventsFilter = null,
    ?bool $multiTaskEnabled = null,
    ?string $template = null,
    ?string $prioritizeQueueOrder = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `friendlyName` | `string` | Form, Required | A descriptive string that you create to describe the Workspace resource. It can be up to 64 characters long. For example: `Customer Support` or `2014 Election Campaign`. |
| `eventCallbackUrl` | `?string` | Form, Optional | The URL we should call when an event occurs. If provided, the Workspace will publish events to this URL, for example, to collect data for reporting. See [Workspace Events](https://www.twilio.com/docs/taskrouter/api/event) for more information. This parameter supports Twilio's [Webhooks (HTTP callbacks) Connection Overrides](https://www.twilio.com/docs/usage/webhooks/webhooks-connection-overrides). |
| `eventsFilter` | `?string` | Form, Optional | The list of Workspace events for which to call event_callback_url. For example, if `EventsFilter=task.created, task.canceled, worker.activity.update`, then TaskRouter will call event_callback_url only when a task is created, canceled, or a Worker activity is updated. |
| `multiTaskEnabled` | `?bool` | Form, Optional | Whether to enable multi-tasking. Can be: `true` to enable multi-tasking, or `false` to disable it. However, all workspaces should be created as multi-tasking. The default is `true`. Multi-tasking allows Workers to handle multiple Tasks simultaneously. When enabled (`true`), each Worker can receive parallel reservations up to the per-channel maximums defined in the Workers section. In single-tasking mode (legacy mode), each Worker will only receive a new reservation when the previous task is completed. Learn more at [Multitasking](https://www.twilio.com/docs/taskrouter/multitasking). |
| `template` | `?string` | Form, Optional | An available template name. Can be: `NONE` or `FIFO` and the default is `NONE`. Pre-configures the Workspace with the Workflow and Activities specified in the template. `NONE` will create a Workspace with only a set of default activities. `FIFO` will configure TaskRouter with a set of default activities and a single TaskQueue for first-in, first-out distribution, which can be useful when you are getting started with TaskRouter. |
| `prioritizeQueueOrder` | [`?string(WorkspaceQueueOrder)`](../../doc/models/workspace-queue-order.md) | Form, Optional | The type of TaskQueue to prioritize when Workers are receiving Tasks from both types of TaskQueues. Can be: `LIFO` or `FIFO` and the default is `FIFO`. For more information, see [Queue Ordering](https://www.twilio.com/docs/taskrouter/queue-ordering-last-first-out-lifo). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Workspace`](../../doc/models/workspace.md).

## Example Usage

```php
$friendlyName = 'friendly_name';

$eventCallbackUrl = '/example';

$template = 'template';

$taskrouterV1WorkspaceApi = $client->getTaskrouterV1WorkspaceApi();
$apiResponse = $taskrouterV1WorkspaceApi->createWorkspace(
    $friendlyName,
    $eventCallbackUrl,
    null,
    null,
    $template
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Workspace:';
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
  "date_created": "2016-08-01T22:10:40Z",
  "date_updated": "2016-08-01T22:10:40Z",
  "default_activity_name": "Offline",
  "default_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "event_callback_url": "",
  "events_filter": null,
  "friendly_name": "new",
  "links": {
    "activities": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Activities",
    "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
    "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
    "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics",
    "task_queues": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues",
    "tasks": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks",
    "workers": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers",
    "workflows": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows",
    "task_channels": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskChannels",
    "events": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Events"
  },
  "multi_task_enabled": false,
  "prioritize_queue_order": "FIFO",
  "sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "timeout_activity_name": "Offline",
  "timeout_activity_sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```

