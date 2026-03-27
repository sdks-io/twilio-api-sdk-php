
# Workers Real Time Statistics

*This model accepts additional fields of type array.*

## Structure

`WorkersRealTimeStatistics`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Worker resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `activityStatistics` | `?(array[])` | Optional | The number of current Workers by Activity. | getActivityStatistics(): ?array | setActivityStatistics(?array activityStatistics): void |
| `totalWorkers` | `?int` | Optional | The total number of Workers.<br><br>**Default**: `0` | getTotalWorkers(): ?int | setTotalWorkers(?int totalWorkers): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the Workers.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `url` | `?string` | Optional | The absolute URL of the Workers statistics resource. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "total_workers": 0,
  "account_sid": "account_sid8",
  "activity_statistics": [
    {
      "key1": "val1",
      "key2": "val2"
    }
  ],
  "workspace_sid": "workspace_sid0",
  "url": "url6",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

