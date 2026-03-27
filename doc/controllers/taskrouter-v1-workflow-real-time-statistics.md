# Taskrouter V1 Workflow Real Time Statistics

```php
$taskrouterV1WorkflowRealTimeStatisticsApi = $client->getTaskrouterV1WorkflowRealTimeStatisticsApi();
```

## Class Name

`TaskrouterV1WorkflowRealTimeStatisticsApi`


# Fetch Workflow Real Time Statistics

```php
function fetchWorkflowRealTimeStatistics(
    string $workspaceSid,
    string $workflowSid,
    ?string $taskChannel = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the Workflow to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `workflowSid` | `string` | Template, Required | Returns the list of Tasks that are being controlled by the Workflow with the specified SID value.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` |
| `taskChannel` | `?string` | Query, Optional | Only calculate real-time statistics on this TaskChannel. Can be the TaskChannel's SID or its `unique_name`, such as `voice`, `sms`, or `default`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`WorkflowRealTimeStatistics`](../../doc/models/workflow-real-time-statistics.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$workflowSid = 'WorkflowSid4';

$taskChannel = 'voice';

$taskrouterV1WorkflowRealTimeStatisticsApi = $client->getTaskrouterV1WorkflowRealTimeStatisticsApi();
$apiResponse = $taskrouterV1WorkflowRealTimeStatisticsApi->fetchWorkflowRealTimeStatistics(
    $workspaceSid,
    $workflowSid,
    $taskChannel
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'WorkflowRealTimeStatistics:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

