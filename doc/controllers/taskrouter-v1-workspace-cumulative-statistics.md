# Taskrouter V1 Workspace Cumulative Statistics

```php
$taskrouterV1WorkspaceCumulativeStatisticsApi = $client->getTaskrouterV1WorkspaceCumulativeStatisticsApi();
```

## Class Name

`TaskrouterV1WorkspaceCumulativeStatisticsApi`


# Fetch Workspace Cumulative Statistics

```php
function fetchWorkspaceCumulativeStatistics(
    string $workspaceSid,
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
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `endDate` | `?DateTime` | Query, Optional | Only include usage that occurred on or before this date, specified in GMT as an [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date-time. |
| `minutes` | `?int` | Query, Optional | Only calculate statistics since this many minutes in the past. The default 15 minutes. This is helpful for displaying statistics for the last 15 minutes, 240 minutes (4 hours), and 480 minutes (8 hours) to see trends. |
| `startDate` | `?DateTime` | Query, Optional | Only calculate statistics from this date and time and later, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `taskChannel` | `?string` | Query, Optional | Only calculate cumulative statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |
| `splitByWaitTime` | `?string` | Query, Optional | A comma separated list of values that describes the thresholds, in seconds, to calculate statistics on. For each threshold specified, the number of Tasks canceled and reservations accepted above and below the specified thresholds in seconds are computed. For example, `5,30` would show splits of Tasks that were canceled or accepted before and after 5 seconds and before and after 30 seconds. This can be used to show short abandoned Tasks or Tasks that failed to meet an SLA. TaskRouter will calculate statistics on up to 10,000 Tasks for any given threshold. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`WorkspaceCumulativeStatistics`](../../doc/models/workspace-cumulative-statistics.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$endDate = DateTimeHelper::fromRfc3339DateTime('07/30/2015 20:00:00');

$startDate = DateTimeHelper::fromRfc3339DateTime('07/30/2015 20:00:00');

$taskrouterV1WorkspaceCumulativeStatisticsApi = $client->getTaskrouterV1WorkspaceCumulativeStatisticsApi();
$apiResponse = $taskrouterV1WorkspaceCumulativeStatisticsApi->fetchWorkspaceCumulativeStatistics(
    $workspaceSid,
    $endDate,
    null,
    $startDate
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'WorkspaceCumulativeStatistics:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

