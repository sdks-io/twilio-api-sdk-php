# Taskrouter V1 Task Queue Real Time Statistics

```php
$taskrouterV1TaskQueueRealTimeStatisticsApi = $client->getTaskrouterV1TaskQueueRealTimeStatisticsApi();
```

## Class Name

`TaskrouterV1TaskQueueRealTimeStatisticsApi`


# Fetch Task Queue Real Time Statistics

```php
function fetchTaskQueueRealTimeStatistics(
    string $workspaceSid,
    string $taskQueueSid,
    ?string $taskChannel = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the TaskQueue to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `taskQueueSid` | `string` | Template, Required | The SID of the TaskQueue for which to fetch statistics.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |
| `taskChannel` | `?string` | Query, Optional | The TaskChannel for which to fetch statistics. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`TaskQueueRealTimeStatistics`](../../doc/models/task-queue-real-time-statistics.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$taskQueueSid = 'TaskQueueSid8';

$taskChannel = 'voice';

$taskrouterV1TaskQueueRealTimeStatisticsApi = $client->getTaskrouterV1TaskQueueRealTimeStatisticsApi();
$apiResponse = $taskrouterV1TaskQueueRealTimeStatisticsApi->fetchTaskQueueRealTimeStatistics(
    $workspaceSid,
    $taskQueueSid,
    $taskChannel
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'TaskQueueRealTimeStatistics:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

