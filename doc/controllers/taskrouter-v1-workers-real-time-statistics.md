# Taskrouter V1 Workers Real Time Statistics

```php
$taskrouterV1WorkersRealTimeStatisticsApi = $client->getTaskrouterV1WorkersRealTimeStatisticsApi();
```

## Class Name

`TaskrouterV1WorkersRealTimeStatisticsApi`


# Fetch Workers Real Time Statistics

```php
function fetchWorkersRealTimeStatistics(string $workspaceSid, ?string $taskChannel = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `taskChannel` | `?string` | Query, Optional | Only calculate real-time statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`WorkersRealTimeStatistics`](../../doc/models/workers-real-time-statistics.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$taskChannel = 'voice';

$taskrouterV1WorkersRealTimeStatisticsApi = $client->getTaskrouterV1WorkersRealTimeStatisticsApi();
$apiResponse = $taskrouterV1WorkersRealTimeStatisticsApi->fetchWorkersRealTimeStatistics(
    $workspaceSid,
    $taskChannel
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'WorkersRealTimeStatistics:';
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
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/RealTimeStatistics",
  "total_workers": 15,
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
```

