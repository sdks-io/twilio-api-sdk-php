
# Worker Channel

*This model accepts additional fields of type array.*

## Structure

`WorkerChannel`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Worker resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `assignedTasks` | `?int` | Optional | The total number of Tasks assigned to Worker for the TaskChannel type.<br><br>**Default**: `0` | getAssignedTasks(): ?int | setAssignedTasks(?int assignedTasks): void |
| `available` | `?bool` | Optional | Whether the Worker should receive Tasks of the TaskChannel type. | getAvailable(): ?bool | setAvailable(?bool available): void |
| `availableCapacityPercentage` | `?int` | Optional | The current percentage of capacity the TaskChannel has available. Can be a number between `0` and `100`. A value of `0` indicates that TaskChannel has no capacity available and a value of `100` means the  Worker is available to receive any Tasks of this TaskChannel type.<br><br>**Default**: `0` | getAvailableCapacityPercentage(): ?int | setAvailableCapacityPercentage(?int availableCapacityPercentage): void |
| `configuredCapacity` | `?int` | Optional | The current configured capacity for the WorkerChannel. TaskRouter will not create any reservations after the assigned Tasks for the Worker reaches the value.<br><br>**Default**: `0` | getConfiguredCapacity(): ?int | setConfiguredCapacity(?int configuredCapacity): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `sid` | `?string` | Optional | The unique string that we created to identify the WorkerChannel resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WC[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `taskChannelSid` | `?string` | Optional | The SID of the TaskChannel.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^TC[0-9a-fA-F]{32}$` | getTaskChannelSid(): ?string | setTaskChannelSid(?string taskChannelSid): void |
| `taskChannelUniqueName` | `?string` | Optional | The unique name of the TaskChannel, such as `voice` or `sms`. | getTaskChannelUniqueName(): ?string | setTaskChannelUniqueName(?string taskChannelUniqueName): void |
| `workerSid` | `?string` | Optional | The SID of the Worker that contains the WorkerChannel.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WK[0-9a-fA-F]{32}$` | getWorkerSid(): ?string | setWorkerSid(?string workerSid): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the WorkerChannel.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `url` | `?string` | Optional | The absolute URL of the WorkerChannel resource. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "assigned_tasks": 0,
  "available_capacity_percentage": 0,
  "configured_capacity": 0,
  "account_sid": "account_sid6",
  "available": false,
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

