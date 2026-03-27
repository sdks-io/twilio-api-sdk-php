
# Task Queue Cumulative

*This model accepts additional fields of type array.*

## Structure

`TaskQueueCumulative`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the TaskQueue resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `avgTaskAcceptanceTime` | `?int` | Optional | The average time in seconds between Task creation and acceptance.<br><br>**Default**: `0` | getAvgTaskAcceptanceTime(): ?int | setAvgTaskAcceptanceTime(?int avgTaskAcceptanceTime): void |
| `startTime` | `?DateTime` | Optional | The beginning of the interval during which these statistics were calculated, in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getStartTime(): ?\DateTime | setStartTime(?\DateTime startTime): void |
| `endTime` | `?DateTime` | Optional | The end of the interval during which these statistics were calculated, in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getEndTime(): ?\DateTime | setEndTime(?\DateTime endTime): void |
| `reservationsCreated` | `?int` | Optional | The total number of Reservations created for Tasks in the TaskQueue.<br><br>**Default**: `0` | getReservationsCreated(): ?int | setReservationsCreated(?int reservationsCreated): void |
| `reservationsAccepted` | `?int` | Optional | The total number of Reservations accepted for Tasks in the TaskQueue.<br><br>**Default**: `0` | getReservationsAccepted(): ?int | setReservationsAccepted(?int reservationsAccepted): void |
| `reservationsRejected` | `?int` | Optional | The total number of Reservations rejected for Tasks in the TaskQueue.<br><br>**Default**: `0` | getReservationsRejected(): ?int | setReservationsRejected(?int reservationsRejected): void |
| `reservationsTimedOut` | `?int` | Optional | The total number of Reservations that timed out for Tasks in the TaskQueue.<br><br>**Default**: `0` | getReservationsTimedOut(): ?int | setReservationsTimedOut(?int reservationsTimedOut): void |
| `reservationsCanceled` | `?int` | Optional | The total number of Reservations canceled for Tasks in the TaskQueue.<br><br>**Default**: `0` | getReservationsCanceled(): ?int | setReservationsCanceled(?int reservationsCanceled): void |
| `reservationsRescinded` | `?int` | Optional | The total number of Reservations rescinded.<br><br>**Default**: `0` | getReservationsRescinded(): ?int | setReservationsRescinded(?int reservationsRescinded): void |
| `splitByWaitTime` | `?array` | Optional | A list of objects that describe the number of Tasks canceled and reservations accepted above and below the thresholds specified in seconds. | getSplitByWaitTime(): ?array | setSplitByWaitTime(?array splitByWaitTime): void |
| `taskQueueSid` | `?string` | Optional | The SID of the TaskQueue from which these statistics were calculated.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` | getTaskQueueSid(): ?string | setTaskQueueSid(?string taskQueueSid): void |
| `waitDurationUntilAccepted` | `?array` | Optional | The wait duration statistics (`avg`, `min`, `max`, `total`) for Tasks accepted while in the TaskQueue. Calculation is based on the time when the Tasks were created. For transfers, the wait duration is counted from the moment ***the Task was created***, and not from when the transfer was initiated. | getWaitDurationUntilAccepted(): ?array | setWaitDurationUntilAccepted(?array waitDurationUntilAccepted): void |
| `waitDurationUntilCanceled` | `?array` | Optional | The wait duration statistics (`avg`, `min`, `max`, `total`) for Tasks canceled while in the TaskQueue. | getWaitDurationUntilCanceled(): ?array | setWaitDurationUntilCanceled(?array waitDurationUntilCanceled): void |
| `waitDurationInQueueUntilAccepted` | `?array` | Optional | The relative wait duration statistics (`avg`, `min`, `max`, `total`) for Tasks accepted while in the TaskQueue. Calculation is based on the time when the Tasks entered the TaskQueue. | getWaitDurationInQueueUntilAccepted(): ?array | setWaitDurationInQueueUntilAccepted(?array waitDurationInQueueUntilAccepted): void |
| `tasksCanceled` | `?int` | Optional | The total number of Tasks canceled in the TaskQueue.<br><br>**Default**: `0` | getTasksCanceled(): ?int | setTasksCanceled(?int tasksCanceled): void |
| `tasksCompleted` | `?int` | Optional | The total number of Tasks completed in the TaskQueue.<br><br>**Default**: `0` | getTasksCompleted(): ?int | setTasksCompleted(?int tasksCompleted): void |
| `tasksDeleted` | `?int` | Optional | The total number of Tasks deleted in the TaskQueue.<br><br>**Default**: `0` | getTasksDeleted(): ?int | setTasksDeleted(?int tasksDeleted): void |
| `tasksEntered` | `?int` | Optional | The total number of Tasks entered into the TaskQueue.<br><br>**Default**: `0` | getTasksEntered(): ?int | setTasksEntered(?int tasksEntered): void |
| `tasksMoved` | `?int` | Optional | The total number of Tasks that were moved from one queue to another.<br><br>**Default**: `0` | getTasksMoved(): ?int | setTasksMoved(?int tasksMoved): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the TaskQueue.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `url` | `?string` | Optional | The absolute URL of the TaskQueue statistics resource. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "avg_task_acceptance_time": 0,
  "reservations_created": 0,
  "reservations_accepted": 0,
  "reservations_rejected": 0,
  "reservations_timed_out": 0,
  "reservations_canceled": 0,
  "reservations_rescinded": 0,
  "tasks_canceled": 0,
  "tasks_completed": 0,
  "tasks_deleted": 0,
  "tasks_entered": 0,
  "tasks_moved": 0,
  "account_sid": "account_sid2",
  "start_time": "2016-03-13T12:52:32.123Z",
  "end_time": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

