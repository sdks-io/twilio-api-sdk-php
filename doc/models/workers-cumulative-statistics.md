
# Workers Cumulative Statistics

*This model accepts additional fields of type array.*

## Structure

`WorkersCumulativeStatistics`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Worker resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `startTime` | `?DateTime` | Optional | The beginning of the interval during which these statistics were calculated, in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getStartTime(): ?\DateTime | setStartTime(?\DateTime startTime): void |
| `endTime` | `?DateTime` | Optional | The end of the interval during which these statistics were calculated, in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getEndTime(): ?\DateTime | setEndTime(?\DateTime endTime): void |
| `activityDurations` | `?(array[])` | Optional | The minimum, average, maximum, and total time (in seconds) that Workers spent in each Activity. | getActivityDurations(): ?array | setActivityDurations(?array activityDurations): void |
| `reservationsCreated` | `?int` | Optional | The total number of Reservations that were created.<br><br>**Default**: `0` | getReservationsCreated(): ?int | setReservationsCreated(?int reservationsCreated): void |
| `reservationsAccepted` | `?int` | Optional | The total number of Reservations that were accepted.<br><br>**Default**: `0` | getReservationsAccepted(): ?int | setReservationsAccepted(?int reservationsAccepted): void |
| `reservationsRejected` | `?int` | Optional | The total number of Reservations that were rejected.<br><br>**Default**: `0` | getReservationsRejected(): ?int | setReservationsRejected(?int reservationsRejected): void |
| `reservationsTimedOut` | `?int` | Optional | The total number of Reservations that were timed out.<br><br>**Default**: `0` | getReservationsTimedOut(): ?int | setReservationsTimedOut(?int reservationsTimedOut): void |
| `reservationsCanceled` | `?int` | Optional | The total number of Reservations that were canceled.<br><br>**Default**: `0` | getReservationsCanceled(): ?int | setReservationsCanceled(?int reservationsCanceled): void |
| `reservationsRescinded` | `?int` | Optional | The total number of Reservations that were rescinded.<br><br>**Default**: `0` | getReservationsRescinded(): ?int | setReservationsRescinded(?int reservationsRescinded): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the Workers.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `url` | `?string` | Optional | The absolute URL of the Workers statistics resource. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "reservations_created": 0,
  "reservations_accepted": 0,
  "reservations_rejected": 0,
  "reservations_timed_out": 0,
  "reservations_canceled": 0,
  "reservations_rescinded": 0,
  "account_sid": "account_sid2",
  "start_time": "2016-03-13T12:52:32.123Z",
  "end_time": "2016-03-13T12:52:32.123Z",
  "activity_durations": [
    {
      "key1": "val1",
      "key2": "val2"
    }
  ],
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

