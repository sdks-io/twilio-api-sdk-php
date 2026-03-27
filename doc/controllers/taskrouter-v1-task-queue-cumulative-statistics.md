# Taskrouter V1 Task Queue Cumulative Statistics

```php
$taskrouterV1TaskQueueCumulativeStatisticsApi = $client->getTaskrouterV1TaskQueueCumulativeStatisticsApi();
```

## Class Name

`TaskrouterV1TaskQueueCumulativeStatisticsApi`


# Fetch Task Queue Cumulative Statistics

```php
function fetchTaskQueueCumulativeStatistics(
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
| `taskChannel` | `?string` | Query, Optional | Only calculate cumulative statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |
| `splitByWaitTime` | `?string` | Query, Optional | A comma separated list of values that describes the thresholds, in seconds, to calculate statistics on. For each threshold specified, the number of Tasks canceled and reservations accepted above and below the specified thresholds in seconds are computed. TaskRouter will calculate statistics on up to 10,000 Tasks/Reservations for any given threshold. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`TaskQueueCumulative`](../../doc/models/task-queue-cumulative.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$taskQueueSid = 'TaskQueueSid8';

$endDate = DateTimeHelper::fromRfc3339DateTime('07/30/2015 20:00:00');

$startDate = DateTimeHelper::fromRfc3339DateTime('07/30/2015 20:00:00');

$taskrouterV1TaskQueueCumulativeStatisticsApi = $client->getTaskrouterV1TaskQueueCumulativeStatisticsApi();
$apiResponse = $taskrouterV1TaskQueueCumulativeStatisticsApi->fetchTaskQueueCumulativeStatistics(
    $workspaceSid,
    $taskQueueSid,
    $endDate,
    null,
    $startDate
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'TaskQueueCumulative:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

