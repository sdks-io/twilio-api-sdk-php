
# Task Reservation

*This model accepts additional fields of type array.*

## Structure

`TaskReservation`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the TaskReservation resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `reservationStatus` | [`?string(TaskReservationStatus)`](../../doc/models/task-reservation-status.md) | Optional | The current status of the reservation. Can be: `pending`, `accepted`, `rejected`, or `timeout`. | getReservationStatus(): ?string | setReservationStatus(?string reservationStatus): void |
| `sid` | `?string` | Optional | The unique string that we created to identify the TaskReservation resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WR[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `taskSid` | `?string` | Optional | The SID of the reserved Task resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` | getTaskSid(): ?string | setTaskSid(?string taskSid): void |
| `workerName` | `?string` | Optional | The `friendly_name` of the Worker that is reserved. | getWorkerName(): ?string | setWorkerName(?string workerName): void |
| `workerSid` | `?string` | Optional | The SID of the reserved Worker resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WK[0-9a-fA-F]{32}$` | getWorkerSid(): ?string | setWorkerSid(?string workerSid): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that this task is contained within.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `url` | `?string` | Optional | The absolute URL of the TaskReservation reservation. | getUrl(): ?string | setUrl(?string url): void |
| `links` | `?array` | Optional | The URLs of related resources. | getLinks(): ?array | setLinks(?array links): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid8",
  "date_created": "2016-03-13T12:52:32.123Z",
  "date_updated": "2016-03-13T12:52:32.123Z",
  "reservation_status": "rejected",
  "sid": "sid4",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

