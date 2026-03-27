
# Task Queue Real Time Statistics

*This model accepts additional fields of type array.*

## Structure

`TaskQueueRealTimeStatistics`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the TaskQueue resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `activityStatistics` | `?(array[])` | Optional | The number of current Workers by Activity. | getActivityStatistics(): ?array | setActivityStatistics(?array activityStatistics): void |
| `longestTaskWaitingAge` | `?int` | Optional | The age of the longest waiting Task.<br><br>**Default**: `0` | getLongestTaskWaitingAge(): ?int | setLongestTaskWaitingAge(?int longestTaskWaitingAge): void |
| `longestTaskWaitingSid` | `?string` | Optional | The SID of the longest waiting Task.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` | getLongestTaskWaitingSid(): ?string | setLongestTaskWaitingSid(?string longestTaskWaitingSid): void |
| `longestRelativeTaskAgeInQueue` | `?int` | Optional | The relative age in the TaskQueue for the longest waiting Task. Calculation is based on the time when the Task entered the TaskQueue.<br><br>**Default**: `0` | getLongestRelativeTaskAgeInQueue(): ?int | setLongestRelativeTaskAgeInQueue(?int longestRelativeTaskAgeInQueue): void |
| `longestRelativeTaskSidInQueue` | `?string` | Optional | The Task SID of the Task waiting in the TaskQueue the longest. Calculation is based on the time when the Task entered the TaskQueue.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` | getLongestRelativeTaskSidInQueue(): ?string | setLongestRelativeTaskSidInQueue(?string longestRelativeTaskSidInQueue): void |
| `taskQueueSid` | `?string` | Optional | The SID of the TaskQueue from which these statistics were calculated.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` | getTaskQueueSid(): ?string | setTaskQueueSid(?string taskQueueSid): void |
| `tasksByPriority` | `?array` | Optional | The number of Tasks by priority. For example: `{"0": "10", "99": "5"}` shows 10 Tasks at priority 0 and 5 at priority 99. | getTasksByPriority(): ?array | setTasksByPriority(?array tasksByPriority): void |
| `tasksByStatus` | `?array` | Optional | The number of Tasks by their current status. For example: `{"pending": "1", "reserved": "3", "assigned": "2", "completed": "5"}`. | getTasksByStatus(): ?array | setTasksByStatus(?array tasksByStatus): void |
| `totalAvailableWorkers` | `?int` | Optional | The total number of Workers in the TaskQueue with an `available` status. Workers with an `available` status may already have active interactions or may have none.<br><br>**Default**: `0` | getTotalAvailableWorkers(): ?int | setTotalAvailableWorkers(?int totalAvailableWorkers): void |
| `totalEligibleWorkers` | `?int` | Optional | The total number of Workers eligible for Tasks in the TaskQueue, independent of their Activity state.<br><br>**Default**: `0` | getTotalEligibleWorkers(): ?int | setTotalEligibleWorkers(?int totalEligibleWorkers): void |
| `totalTasks` | `?int` | Optional | The total number of Tasks.<br><br>**Default**: `0` | getTotalTasks(): ?int | setTotalTasks(?int totalTasks): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the TaskQueue.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `url` | `?string` | Optional | The absolute URL of the TaskQueue statistics resource. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "longest_task_waiting_age": 0,
  "longest_relative_task_age_in_queue": 0,
  "total_available_workers": 0,
  "total_eligible_workers": 0,
  "total_tasks": 0,
  "account_sid": "account_sid8",
  "activity_statistics": [
    {
      "key1": "val1",
      "key2": "val2"
    },
    {
      "key1": "val1",
      "key2": "val2"
    },
    {
      "key1": "val1",
      "key2": "val2"
    }
  ],
  "longest_task_waiting_sid": "longest_task_waiting_sid6",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

