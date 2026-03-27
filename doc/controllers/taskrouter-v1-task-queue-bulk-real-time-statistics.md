# Taskrouter V1 Task Queue Bulk Real Time Statistics

```php
$taskrouterV1TaskQueueBulkRealTimeStatisticsApi = $client->getTaskrouterV1TaskQueueBulkRealTimeStatisticsApi();
```

## Class Name

`TaskrouterV1TaskQueueBulkRealTimeStatisticsApi`


# Create Task Queue Bulk Real Time Statistics

Fetch a Task Queue Real Time Statistics in bulk for the array of TaskQueue SIDs, support upto 50 in a request.

```php
function createTaskQueueBulkRealTimeStatistics(string $workspaceSid, ?array $body = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The unique SID identifier of the Workspace.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `body` | `?array` | Body, Optional | - |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`TaskQueueBulkRealTimeStatistics`](../../doc/models/task-queue-bulk-real-time-statistics.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$taskrouterV1TaskQueueBulkRealTimeStatisticsApi = $client->getTaskrouterV1TaskQueueBulkRealTimeStatisticsApi();
$apiResponse = $taskrouterV1TaskQueueBulkRealTimeStatisticsApi->createTaskQueueBulkRealTimeStatistics($workspaceSid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'TaskQueueBulkRealTimeStatistics:';
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
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/TaskQueues/RealTimeStatistics",
  "task_queue_data": [
    {
      "task_queue_sid": "WQaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "longest_task_waiting_age": 100,
      "longest_task_waiting_sid": "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "total_tasks": 100,
      "total_eligible_workers": 100,
      "total_available_workers": 100,
      "tasks_by_status": {
        "reserved": 0,
        "pending": 0,
        "assigned": 0,
        "wrapping": 0
      },
      "tasks_by_priority": {},
      "activity_statistics": [
        {
          "friendly_name": "Idle",
          "workers": 0,
          "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
        },
        {
          "friendly_name": "Busy",
          "workers": 9,
          "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
        },
        {
          "friendly_name": "Offline",
          "workers": 6,
          "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
        },
        {
          "friendly_name": "Reserved",
          "workers": 0,
          "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
        }
      ]
    }
  ],
  "task_queue_response_count": 100
}
```

