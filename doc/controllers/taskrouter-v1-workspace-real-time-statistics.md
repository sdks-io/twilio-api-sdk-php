# Taskrouter V1 Workspace Real Time Statistics

```php
$taskrouterV1WorkspaceRealTimeStatisticsApi = $client->getTaskrouterV1WorkspaceRealTimeStatisticsApi();
```

## Class Name

`TaskrouterV1WorkspaceRealTimeStatisticsApi`


# Fetch Workspace Real Time Statistics

```php
function fetchWorkspaceRealTimeStatistics(string $workspaceSid, ?string $taskChannel = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `taskChannel` | `?string` | Query, Optional | Only calculate real-time statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`WorkspaceRealTimeStatistics`](../../doc/models/workspace-real-time-statistics.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$taskChannel = 'voice';

$taskrouterV1WorkspaceRealTimeStatisticsApi = $client->getTaskrouterV1WorkspaceRealTimeStatisticsApi();
$apiResponse = $taskrouterV1WorkspaceRealTimeStatisticsApi->fetchWorkspaceRealTimeStatistics(
    $workspaceSid,
    $taskChannel
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'WorkspaceRealTimeStatistics:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

