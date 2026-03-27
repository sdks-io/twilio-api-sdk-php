
# Task Queue

*This model accepts additional fields of type array.*

## Structure

`TaskQueue`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the TaskQueue resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `assignmentActivitySid` | `?string` | Optional | The SID of the Activity to assign Workers when a task is assigned for them.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` | getAssignmentActivitySid(): ?string | setAssignmentActivitySid(?string assignmentActivitySid): void |
| `assignmentActivityName` | `?string` | Optional | The name of the Activity to assign Workers when a task is assigned for them. | getAssignmentActivityName(): ?string | setAssignmentActivityName(?string assignmentActivityName): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [RFC 2822](https://www.ietf.org/rfc/rfc2822.txt) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `friendlyName` | `?string` | Optional | The string that you assigned to describe the resource. | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `maxReservedWorkers` | `?int` | Optional | The maximum number of Workers to reserve for the assignment of a task in the queue. Can be an integer between 1 and 50, inclusive and defaults to 1.<br><br>**Default**: `0` | getMaxReservedWorkers(): ?int | setMaxReservedWorkers(?int maxReservedWorkers): void |
| `reservationActivitySid` | `?string` | Optional | The SID of the Activity to assign Workers once a task is reserved for them.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` | getReservationActivitySid(): ?string | setReservationActivitySid(?string reservationActivitySid): void |
| `reservationActivityName` | `?string` | Optional | The name of the Activity to assign Workers once a task is reserved for them. | getReservationActivityName(): ?string | setReservationActivityName(?string reservationActivityName): void |
| `sid` | `?string` | Optional | The unique string that we created to identify the TaskQueue resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `targetWorkers` | `?string` | Optional | A string describing the Worker selection criteria for any Tasks that enter the TaskQueue. For example `'"language" == "spanish"'` If no TargetWorkers parameter is provided, Tasks will wait in the TaskQueue until they are either deleted or moved to another TaskQueue. Additional examples on how to describing Worker selection criteria below. Defaults to 1==1. | getTargetWorkers(): ?string | setTargetWorkers(?string targetWorkers): void |
| `taskOrder` | [`?string(TaskQueueTaskOrder)`](../../doc/models/task-queue-task-order.md) | Optional | How Tasks will be assigned to Workers. Set this parameter to `LIFO` to assign most recently created Task first or `FIFO` to assign the oldest Task. Default is FIFO. [Click here](https://www.twilio.com/docs/taskrouter/queue-ordering-last-first-out-lifo) to learn more. | getTaskOrder(): ?string | setTaskOrder(?string taskOrder): void |
| `url` | `?string` | Optional | The absolute URL of the TaskQueue resource. | getUrl(): ?string | setUrl(?string url): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the TaskQueue.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `links` | `?array` | Optional | The URLs of related resources. | getLinks(): ?array | setLinks(?array links): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "max_reserved_workers": 0,
  "account_sid": "account_sid0",
  "assignment_activity_sid": "assignment_activity_sid8",
  "assignment_activity_name": "assignment_activity_name2",
  "date_created": "2016-03-13T12:52:32.123Z",
  "date_updated": "2016-03-13T12:52:32.123Z",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

