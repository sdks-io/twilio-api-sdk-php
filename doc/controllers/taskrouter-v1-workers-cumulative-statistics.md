# Taskrouter V1 Workers Cumulative Statistics

```php
$taskrouterV1WorkersCumulativeStatisticsApi = $client->getTaskrouterV1WorkersCumulativeStatisticsApi();
```

## Class Name

`TaskrouterV1WorkersCumulativeStatisticsApi`


# Fetch Workers Cumulative Statistics

```php
function fetchWorkersCumulativeStatistics(
    string $workspaceSid,
    ?\DateTime $endDate = null,
    ?int $minutes = null,
    ?\DateTime $startDate = null,
    ?string $taskChannel = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `endDate` | `?DateTime` | Query, Optional | Only calculate statistics from this date and time and earlier, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `minutes` | `?int` | Query, Optional | Only calculate statistics since this many minutes in the past. The default 15 minutes. This is helpful for displaying statistics for the last 15 minutes, 240 minutes (4 hours), and 480 minutes (8 hours) to see trends. |
| `startDate` | `?DateTime` | Query, Optional | Only calculate statistics from this date and time and later, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `taskChannel` | `?string` | Query, Optional | Only calculate cumulative statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`WorkersCumulativeStatistics`](../../doc/models/workers-cumulative-statistics.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$endDate = DateTimeHelper::fromRfc3339DateTime('07/30/2015 20:00:00');

$startDate = DateTimeHelper::fromRfc3339DateTime('07/30/2015 20:00:00');

$taskrouterV1WorkersCumulativeStatisticsApi = $client->getTaskrouterV1WorkersCumulativeStatisticsApi();
$apiResponse = $taskrouterV1WorkersCumulativeStatisticsApi->fetchWorkersCumulativeStatistics(
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
    echo 'WorkersCumulativeStatistics:';
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
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/CumulativeStatistics",
  "reservations_created": 100,
  "reservations_accepted": 100,
  "reservations_rejected": 100,
  "reservations_timed_out": 100,
  "reservations_canceled": 100,
  "reservations_rescinded": 100,
  "activity_durations": [
    {
      "max": 0,
      "min": 900,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Offline",
      "avg": 1080,
      "total": 5400
    },
    {
      "max": 0,
      "min": 900,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Busy",
      "avg": 1012,
      "total": 8100
    },
    {
      "max": 0,
      "min": 0,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Idle",
      "avg": 0,
      "total": 0
    },
    {
      "max": 0,
      "min": 0,
      "sid": "WAaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Reserved",
      "avg": 0,
      "total": 0
    }
  ],
  "start_time": "2015-07-30T20:00:00Z",
  "end_time": "2015-07-30T20:00:00Z"
}
```

