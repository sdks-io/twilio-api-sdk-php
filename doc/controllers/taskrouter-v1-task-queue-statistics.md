# Taskrouter V1 Task Queue Statistics

```php
$taskrouterV1TaskQueueStatisticsApi = $client->getTaskrouterV1TaskQueueStatisticsApi();
```

## Class Name

`TaskrouterV1TaskQueueStatisticsApi`


# Fetch Task Queue Statistics

```php
function fetchTaskQueueStatistics(
    string $workspaceSid,
    string $taskQueueSid,
    ?\DateTime $endDate = null,
    ?int $minutes = null,
    ?\DateTime $startDate = null,
    ?string $taskChannel = null,
    ?string $splitByWaitTime = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the TaskQueue to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `taskQueueSid` | `string` | Template, Required | The SID of the TaskQueue for which to fetch statistics.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` |
| `endDate` | `?DateTime` | Query, Optional | Only calculate statistics from this date and time and earlier, specified in GMT as an [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date-time. |
| `minutes` | `?int` | Query, Optional | Only calculate statistics since this many minutes in the past. The default is 15 minutes. |
| `startDate` | `?DateTime` | Query, Optional | Only calculate statistics from this date and time and later, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `taskChannel` | `?string` | Query, Optional | Only calculate real-time and cumulative statistics for the specified TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |
| `splitByWaitTime` | `?string` | Query, Optional | A comma separated list of values that describes the thresholds, in seconds, to calculate statistics on. For each threshold specified, the number of Tasks canceled and reservations accepted above and below the specified thresholds in seconds are computed. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`TaskQueueStatistics`](../../doc/models/task-queue-statistics.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$taskQueueSid = 'TaskQueueSid8';

$endDate = DateTimeHelper::fromRfc3339DateTime('01/02/2008 00:00:00');

$minutes = 1;

$startDate = DateTimeHelper::fromRfc3339DateTime('01/02/2008 00:00:00');

$taskrouterV1TaskQueueStatisticsApi = $client->getTaskrouterV1TaskQueueStatisticsApi();
$apiResponse = $taskrouterV1TaskQueueStatisticsApi->fetchTaskQueueStatistics(
    $workspaceSid,
    $taskQueueSid,
    $endDate,
    $minutes,
    $startDate
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'TaskQueueStatistics:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

