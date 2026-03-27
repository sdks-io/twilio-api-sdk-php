# Taskrouter V1 Task Queues Statistics

```php
$taskrouterV1TaskQueuesStatisticsApi = $client->getTaskrouterV1TaskQueuesStatisticsApi();
```

## Class Name

`TaskrouterV1TaskQueuesStatisticsApi`


# List Task Queues Statistics

```php
function listTaskQueuesStatistics(
    string $workspaceSid,
    ?\DateTime $endDate = null,
    ?string $friendlyName = null,
    ?int $minutes = null,
    ?\DateTime $startDate = null,
    ?string $taskChannel = null,
    ?string $splitByWaitTime = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the TaskQueues to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `endDate` | `?DateTime` | Query, Optional | Only calculate statistics from this date and time and earlier, specified in GMT as an [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) date-time. |
| `friendlyName` | `?string` | Query, Optional | The `friendly_name` of the TaskQueue statistics to read. |
| `minutes` | `?int` | Query, Optional | Only calculate statistics since this many minutes in the past. The default is 15 minutes. |
| `startDate` | `?DateTime` | Query, Optional | Only calculate statistics from this date and time and later, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. |
| `taskChannel` | `?string` | Query, Optional | Only calculate statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |
| `splitByWaitTime` | `?string` | Query, Optional | A comma separated list of values that describes the thresholds, in seconds, to calculate statistics on. For each threshold specified, the number of Tasks canceled and reservations accepted above and below the specified thresholds in seconds are computed. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListTaskQueuesStatisticsResponse`](../../doc/models/list-task-queues-statistics-response.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$endDate = DateTimeHelper::fromRfc3339DateTime('01/02/2008 00:00:00');

$friendlyName = 'friendly_name';

$minutes = 1;

$startDate = DateTimeHelper::fromRfc3339DateTime('01/02/2008 00:00:00');

$taskrouterV1TaskQueuesStatisticsApi = $client->getTaskrouterV1TaskQueuesStatisticsApi();
$apiResponse = $taskrouterV1TaskQueuesStatisticsApi->listTaskQueuesStatistics(
    $workspaceSid,
    $endDate,
    $friendlyName,
    $minutes,
    $startDate
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListTaskQueuesStatisticsResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

