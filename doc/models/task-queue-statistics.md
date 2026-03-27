
# Task Queue Statistics

*This model accepts additional fields of type array.*

## Structure

`TaskQueueStatistics`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the TaskQueue resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `cumulative` | `?array` | Optional | An object that contains the cumulative statistics for the TaskQueue. | getCumulative(): ?array | setCumulative(?array cumulative): void |
| `realtime` | `?array` | Optional | An object that contains the real-time statistics for the TaskQueue. | getRealtime(): ?array | setRealtime(?array realtime): void |
| `taskQueueSid` | `?string` | Optional | The SID of the TaskQueue from which these statistics were calculated.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` | getTaskQueueSid(): ?string | setTaskQueueSid(?string taskQueueSid): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the TaskQueue.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `url` | `?string` | Optional | The absolute URL of the TaskQueue statistics resource. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid4",
  "cumulative": {
    "key1": "val1",
    "key2": "val2"
  },
  "realtime": {
    "key1": "val1",
    "key2": "val2"
  },
  "task_queue_sid": "task_queue_sid2",
  "workspace_sid": "workspace_sid6",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

