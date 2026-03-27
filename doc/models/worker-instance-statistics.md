
# Worker Instance Statistics

*This model accepts additional fields of type array.*

## Structure

`WorkerInstanceStatistics`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Worker resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `cumulative` | `?array` | Optional | An object that contains the cumulative statistics for the Worker. | getCumulative(): ?array | setCumulative(?array cumulative): void |
| `workerSid` | `?string` | Optional | The SID of the Worker that contains the WorkerChannel.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WK[0-9a-fA-F]{32}$` | getWorkerSid(): ?string | setWorkerSid(?string workerSid): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the WorkerChannel.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `url` | `?string` | Optional | The absolute URL of the WorkerChannel statistics resource. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid8",
  "cumulative": {
    "key1": "val1",
    "key2": "val2"
  },
  "worker_sid": "worker_sid0",
  "workspace_sid": "workspace_sid0",
  "url": "url6",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

