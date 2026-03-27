# Taskrouter V1 Workflow

```php
$taskrouterV1WorkflowApi = $client->getTaskrouterV1WorkflowApi();
```

## Class Name

`TaskrouterV1WorkflowApi`

## Methods

* [Fetch Workflow](../../doc/controllers/taskrouter-v1-workflow.md#fetch-workflow)
* [Update Workflow](../../doc/controllers/taskrouter-v1-workflow.md#update-workflow)
* [Delete Workflow](../../doc/controllers/taskrouter-v1-workflow.md#delete-workflow)
* [List Workflow](../../doc/controllers/taskrouter-v1-workflow.md#list-workflow)
* [Create Workflow](../../doc/controllers/taskrouter-v1-workflow.md#create-workflow)


# Fetch Workflow

```php
function fetchWorkflow(string $workspaceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Workflow to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Workflow resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Workflow`](../../doc/models/workflow.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$sid = 'Sid8';

$taskrouterV1WorkflowApi = $client->getTaskrouterV1WorkflowApi();
$apiResponse = $taskrouterV1WorkflowApi->fetchWorkflow(
    $workspaceSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Workflow:';
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
  "assignment_callback_url": "http://example.com",
  "configuration": "task-routing:\\n  - filter: \\n      - 1 == 1\\n    target:\\n      - queue: WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa\\n        set-priority: 0\\n",
  "date_created": "2014-05-14T10:50:02Z",
  "date_updated": "2014-05-14T23:26:06Z",
  "document_content_type": "application/json",
  "fallback_assignment_callback_url": null,
  "friendly_name": "Default Fifo Workflow",
  "sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_reservation_timeout": 120,
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
    "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
    "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics"
  }
}
```


# Update Workflow

```php
function updateWorkflow(
    string $workspaceSid,
    string $sid,
    ?string $friendlyName = null,
    ?string $assignmentCallbackUrl = null,
    ?string $fallbackAssignmentCallbackUrl = null,
    ?string $configuration = null,
    ?int $taskReservationTimeout = null,
    ?string $reEvaluateTasks = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Workflow to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Workflow resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |
| `friendlyName` | `?string` | Form, Optional | A descriptive string that you create to describe the Workflow resource. For example, `Inbound Call Workflow` or `2014 Outbound Campaign`. |
| `assignmentCallbackUrl` | `?string` | Form, Optional | The URL from your application that will process task assignment events. See [Handling Task Assignment Callback](https://www.twilio.com/docs/taskrouter/handle-assignment-callbacks) for more details. |
| `fallbackAssignmentCallbackUrl` | `?string` | Form, Optional | The URL that we should call when a call to the `assignment_callback_url` fails. |
| `configuration` | `?string` | Form, Optional | A JSON string that contains the rules to apply to the Workflow. See [Configuring Workflows](https://www.twilio.com/docs/taskrouter/workflow-configuration) for more information. |
| `taskReservationTimeout` | `?int` | Form, Optional | How long TaskRouter will wait for a confirmation response from your application after it assigns a Task to a Worker. Can be up to `86,400` (24 hours) and the default is `120`. |
| `reEvaluateTasks` | `?string` | Form, Optional | Whether or not to re-evaluate Tasks. The default is `false`, which means Tasks in the Workflow will not be processed through the assignment loop again. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Workflow`](../../doc/models/workflow.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$sid = 'Sid8';

$friendlyName = 'friendly_name';

$assignmentCallbackUrl = 'http://example.com';

$fallbackAssignmentCallbackUrl = 'http://example.com';

$configuration = 'configuration';

$taskReservationTimeout = 1;

$reEvaluateTasks = 'false';

$taskrouterV1WorkflowApi = $client->getTaskrouterV1WorkflowApi();
$apiResponse = $taskrouterV1WorkflowApi->updateWorkflow(
    $workspaceSid,
    $sid,
    $friendlyName,
    $assignmentCallbackUrl,
    $fallbackAssignmentCallbackUrl,
    $configuration,
    $taskReservationTimeout,
    $reEvaluateTasks
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Workflow:';
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
  "assignment_callback_url": "http://example.com",
  "configuration": "task-routing:\\n  - filter: \\n      - 1 == 1\\n    target:\\n      - queue: WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa\\n        set-priority: 0\\n",
  "date_created": "2014-05-14T10:50:02Z",
  "date_updated": "2014-05-14T23:26:06Z",
  "document_content_type": "application/json",
  "fallback_assignment_callback_url": null,
  "friendly_name": "Default Fifo Workflow",
  "sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_reservation_timeout": 120,
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
    "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
    "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics"
  },
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Workflow

```php
function deleteWorkflow(string $workspaceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Workflow to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Workflow resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$sid = 'Sid8';

$taskrouterV1WorkflowApi = $client->getTaskrouterV1WorkflowApi();
$apiResponse = $taskrouterV1WorkflowApi->deleteWorkflow(
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


# List Workflow

```php
function listWorkflow(
    string $workspaceSid,
    ?string $friendlyName = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Workflow to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `friendlyName` | `?string` | Query, Optional | The `friendly_name` of the Workflow resources to read. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListWorkflowResponse`](../../doc/models/list-workflow-response.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$friendlyName = 'friendly_name';

$taskrouterV1WorkflowApi = $client->getTaskrouterV1WorkflowApi();
$apiResponse = $taskrouterV1WorkflowApi->listWorkflow(
    $workspaceSid,
    $friendlyName
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListWorkflowResponse:';
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
    "first_page_url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows?FriendlyName=friendly_name&PageSize=50&Page=0",
    "key": "workflows",
    "next_page_url": null,
    "page": 0,
    "page_size": 50,
    "previous_page_url": null,
    "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows?FriendlyName=friendly_name&PageSize=50&Page=0"
  },
  "workflows": [
    {
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "assignment_callback_url": "http://example.com",
      "configuration": "task-routing:\\n  - filter: \\n      - 1 == 1\\n    target:\\n      - queue: WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa\\n        set-priority: 0\\n",
      "date_created": "2014-05-14T10:50:02Z",
      "date_updated": "2014-05-15T16:47:51Z",
      "document_content_type": "application/json",
      "fallback_assignment_callback_url": null,
      "friendly_name": "Default Fifo Workflow",
      "sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "task_reservation_timeout": 120,
      "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "links": {
        "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
        "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
        "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics"
      },
      "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```


# Create Workflow

```php
function createWorkflow(
    string $workspaceSid,
    string $friendlyName,
    string $configuration,
    ?string $assignmentCallbackUrl = null,
    ?string $fallbackAssignmentCallbackUrl = null,
    ?int $taskReservationTimeout = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace that the new Workflow to create belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `friendlyName` | `string` | Form, Required | A descriptive string that you create to describe the Workflow resource. For example, `Inbound Call Workflow` or `2014 Outbound Campaign`. |
| `configuration` | `string` | Form, Required | A JSON string that contains the rules to apply to the Workflow. See [Configuring Workflows](https://www.twilio.com/docs/taskrouter/workflow-configuration) for more information. |
| `assignmentCallbackUrl` | `?string` | Form, Optional | The URL from your application that will process task assignment events. See [Handling Task Assignment Callback](https://www.twilio.com/docs/taskrouter/handle-assignment-callbacks) for more details. |
| `fallbackAssignmentCallbackUrl` | `?string` | Form, Optional | The URL that we should call when a call to the `assignment_callback_url` fails. |
| `taskReservationTimeout` | `?int` | Form, Optional | How long TaskRouter will wait for a confirmation response from your application after it assigns a Task to a Worker. Can be up to `86,400` (24 hours) and the default is `120`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Workflow`](../../doc/models/workflow.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$friendlyName = 'friendly_name';

$configuration = 'configuration';

$assignmentCallbackUrl = 'http://example.com';

$fallbackAssignmentCallbackUrl = 'http://example.com';

$taskReservationTimeout = 1;

$taskrouterV1WorkflowApi = $client->getTaskrouterV1WorkflowApi();
$apiResponse = $taskrouterV1WorkflowApi->createWorkflow(
    $workspaceSid,
    $friendlyName,
    $configuration,
    $assignmentCallbackUrl,
    $fallbackAssignmentCallbackUrl,
    $taskReservationTimeout
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Workflow:';
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
  "assignment_callback_url": "http://example.com",
  "configuration": "task-routing:\\n  - filter: \\n      - 1 == 1\\n    target:\\n      - queue: WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa\\n        set-priority: 0\\n",
  "date_created": "2014-05-14T10:50:02Z",
  "date_updated": "2014-05-14T23:26:06Z",
  "document_content_type": "application/json",
  "fallback_assignment_callback_url": null,
  "friendly_name": "Default Fifo Workflow",
  "sid": "WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_reservation_timeout": 120,
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Statistics",
    "real_time_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/RealTimeStatistics",
    "cumulative_statistics": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workflows/WWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/CumulativeStatistics"
  }
}
```

