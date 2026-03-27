
# Worker Statistics

*This model accepts additional fields of type array.*

## Structure

`WorkerStatistics`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `realtime` | `?array` | Optional | An object that contains the real-time statistics for the Worker. | getRealtime(): ?array | setRealtime(?array realtime): void |
| `cumulative` | `?array` | Optional | An object that contains the cumulative statistics for the Worker. | getCumulative(): ?array | setCumulative(?array cumulative): void |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Worker resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the Worker.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `url` | `?string` | Optional | The absolute URL of the Worker statistics resource. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "realtime": {
    "key1": "val1",
    "key2": "val2"
  },
  "cumulative": {
    "key1": "val1",
    "key2": "val2"
  },
  "account_sid": "account_sid2",
  "workspace_sid": "workspace_sid6",
  "url": "url0",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

