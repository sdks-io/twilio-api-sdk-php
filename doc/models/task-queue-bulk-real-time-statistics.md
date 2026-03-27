
# Task Queue Bulk Real Time Statistics

*This model accepts additional fields of type array.*

## Structure

`TaskQueueBulkRealTimeStatistics`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the TaskQueue resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the TaskQueue.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `taskQueueData` | `?(array[])` | Optional | The real-time statistics for each requested TaskQueue SID. `task_queue_data` returns the following attributes:<br><br>`task_queue_sid`: The SID of the TaskQueue from which these statistics were calculated.<br><br>`total_available_workers`: The total number of Workers available for Tasks in the TaskQueue.<br><br>`total_eligible_workers`: The total number of Workers eligible for Tasks in the TaskQueue, regardless of their Activity state.<br><br>`total_tasks`: The total number of Tasks.<br><br>`longest_task_waiting_age`: The age of the longest waiting Task.<br><br>`longest_task_waiting_sid`: The SID of the longest waiting Task.<br><br>`tasks_by_status`: The number of Tasks grouped by their current status.<br><br>`tasks_by_priority`: The number of Tasks grouped by priority.<br><br>`activity_statistics`: The number of current Workers grouped by Activity. | getTaskQueueData(): ?array | setTaskQueueData(?array taskQueueData): void |
| `taskQueueResponseCount` | `?int` | Optional | The number of TaskQueue statistics received in task_queue_data.<br><br>**Default**: `0` | getTaskQueueResponseCount(): ?int | setTaskQueueResponseCount(?int taskQueueResponseCount): void |
| `url` | `?string` | Optional | The absolute URL of the TaskQueue statistics resource. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "task_queue_response_count": 0,
  "account_sid": "account_sid0",
  "workspace_sid": "workspace_sid8",
  "task_queue_data": [
    {
      "key1": "val1",
      "key2": "val2"
    },
    {
      "key1": "val1",
      "key2": "val2"
    }
  ],
  "url": "url8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

