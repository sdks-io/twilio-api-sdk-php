
# Workflow Statistics

*This model accepts additional fields of type array.*

## Structure

`WorkflowStatistics`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Workflow resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `cumulative` | `?array` | Optional | An object that contains the cumulative statistics for the Workflow. | getCumulative(): ?array | setCumulative(?array cumulative): void |
| `realtime` | `?array` | Optional | An object that contains the real-time statistics for the Workflow. | getRealtime(): ?array | setRealtime(?array realtime): void |
| `workflowSid` | `?string` | Optional | Returns the list of Tasks that are being controlled by the Workflow with the specified SID value.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` | getWorkflowSid(): ?string | setWorkflowSid(?string workflowSid): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the Workflow.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `url` | `?string` | Optional | The absolute URL of the Workflow statistics resource. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid2",
  "cumulative": {
    "key1": "val1",
    "key2": "val2"
  },
  "realtime": {
    "key1": "val1",
    "key2": "val2"
  },
  "workflow_sid": "workflow_sid6",
  "workspace_sid": "workspace_sid4",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

