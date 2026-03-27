
# Workflow Cumulative Statistics

*This model accepts additional fields of type array.*

## Structure

`WorkflowCumulativeStatistics`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Workflow resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `avgTaskAcceptanceTime` | `?int` | Optional | The average time in seconds between Task creation and acceptance.<br><br>**Default**: `0` | getAvgTaskAcceptanceTime(): ?int | setAvgTaskAcceptanceTime(?int avgTaskAcceptanceTime): void |
| `startTime` | `?DateTime` | Optional | The beginning of the interval during which these statistics were calculated, in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getStartTime(): ?\DateTime | setStartTime(?\DateTime startTime): void |
| `endTime` | `?DateTime` | Optional | The end of the interval during which these statistics were calculated, in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getEndTime(): ?\DateTime | setEndTime(?\DateTime endTime): void |
| `reservationsCreated` | `?int` | Optional | The total number of Reservations that were created for Workers.<br><br>**Default**: `0` | getReservationsCreated(): ?int | setReservationsCreated(?int reservationsCreated): void |
| `reservationsAccepted` | `?int` | Optional | The total number of Reservations accepted by Workers.<br><br>**Default**: `0` | getReservationsAccepted(): ?int | setReservationsAccepted(?int reservationsAccepted): void |
| `reservationsRejected` | `?int` | Optional | The total number of Reservations that were rejected.<br><br>**Default**: `0` | getReservationsRejected(): ?int | setReservationsRejected(?int reservationsRejected): void |
| `reservationsTimedOut` | `?int` | Optional | The total number of Reservations that were timed out.<br><br>**Default**: `0` | getReservationsTimedOut(): ?int | setReservationsTimedOut(?int reservationsTimedOut): void |
| `reservationsCanceled` | `?int` | Optional | The total number of Reservations that were canceled.<br><br>**Default**: `0` | getReservationsCanceled(): ?int | setReservationsCanceled(?int reservationsCanceled): void |
| `reservationsRescinded` | `?int` | Optional | The total number of Reservations that were rescinded.<br><br>**Default**: `0` | getReservationsRescinded(): ?int | setReservationsRescinded(?int reservationsRescinded): void |
| `splitByWaitTime` | `?array` | Optional | A list of objects that describe the number of Tasks canceled and reservations accepted above and below the thresholds specified in seconds. | getSplitByWaitTime(): ?array | setSplitByWaitTime(?array splitByWaitTime): void |
| `waitDurationUntilAccepted` | `?array` | Optional | The wait duration statistics (`avg`, `min`, `max`, `total`) for Tasks that were accepted. | getWaitDurationUntilAccepted(): ?array | setWaitDurationUntilAccepted(?array waitDurationUntilAccepted): void |
| `waitDurationUntilCanceled` | `?array` | Optional | The wait duration statistics (`avg`, `min`, `max`, `total`) for Tasks that were canceled. | getWaitDurationUntilCanceled(): ?array | setWaitDurationUntilCanceled(?array waitDurationUntilCanceled): void |
| `tasksCanceled` | `?int` | Optional | The total number of Tasks that were canceled.<br><br>**Default**: `0` | getTasksCanceled(): ?int | setTasksCanceled(?int tasksCanceled): void |
| `tasksCompleted` | `?int` | Optional | The total number of Tasks that were completed.<br><br>**Default**: `0` | getTasksCompleted(): ?int | setTasksCompleted(?int tasksCompleted): void |
| `tasksEntered` | `?int` | Optional | The total number of Tasks that entered the Workflow.<br><br>**Default**: `0` | getTasksEntered(): ?int | setTasksEntered(?int tasksEntered): void |
| `tasksDeleted` | `?int` | Optional | The total number of Tasks that were deleted.<br><br>**Default**: `0` | getTasksDeleted(): ?int | setTasksDeleted(?int tasksDeleted): void |
| `tasksMoved` | `?int` | Optional | The total number of Tasks that were moved from one queue to another.<br><br>**Default**: `0` | getTasksMoved(): ?int | setTasksMoved(?int tasksMoved): void |
| `tasksTimedOutInWorkflow` | `?int` | Optional | The total number of Tasks that were timed out of their Workflows (and deleted).<br><br>**Default**: `0` | getTasksTimedOutInWorkflow(): ?int | setTasksTimedOutInWorkflow(?int tasksTimedOutInWorkflow): void |
| `workflowSid` | `?string` | Optional | Returns the list of Tasks that are being controlled by the Workflow with the specified Sid value.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` | getWorkflowSid(): ?string | setWorkflowSid(?string workflowSid): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the Workflow.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `url` | `?string` | Optional | The absolute URL of the Workflow statistics resource. | getUrl(): ?string | setUrl(?string url): void |
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
  "tasks_entered": 0,
  "tasks_deleted": 0,
  "tasks_moved": 0,
  "tasks_timed_out_in_workflow": 0,
  "account_sid": "account_sid0",
  "start_time": "2016-03-13T12:52:32.123Z",
  "end_time": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

