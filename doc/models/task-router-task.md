
# Task Router Task

*This model accepts additional fields of type array.*

## Structure

`TaskRouterTask`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Task resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `age` | `?int` | Optional | The number of seconds since the Task was created.<br><br>**Default**: `0` | getAge(): ?int | setAge(?int age): void |
| `assignmentStatus` | [`?string(TaskStatus)`](../../doc/models/task-status.md) | Optional | The current status of the Task's assignment. Can be: `pending`, `reserved`, `assigned`, `canceled`, `wrapping`, or `completed`. | getAssignmentStatus(): ?string | setAssignmentStatus(?string assignmentStatus): void |
| `attributes` | `?string` | Optional | The JSON string with custom attributes of the work. **Note** If this property has been assigned a value, it will only be displayed in FETCH action that returns a single resource. Otherwise, it will be null. | getAttributes(): ?string | setAttributes(?string attributes): void |
| `addons` | `?string` | Optional | An object that contains the [Add-on](https://www.twilio.com/docs/add-ons) data for all installed Add-ons. | getAddons(): ?string | setAddons(?string addons): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `taskQueueEnteredDate` | `?DateTime` | Optional | The date and time in GMT when the Task entered the TaskQueue, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getTaskQueueEnteredDate(): ?\DateTime | setTaskQueueEnteredDate(?\DateTime taskQueueEnteredDate): void |
| `priority` | `?int` | Optional | The current priority score of the Task as assigned to a Worker by the workflow. Tasks with higher priority values will be assigned before Tasks with lower values.<br><br>**Default**: `0` | getPriority(): ?int | setPriority(?int priority): void |
| `reason` | `?string` | Optional | The reason the Task was canceled or completed, if applicable. | getReason(): ?string | setReason(?string reason): void |
| `sid` | `?string` | Optional | The unique string that we created to identify the Task resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `taskQueueSid` | `?string` | Optional | The SID of the TaskQueue.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WQ[0-9a-fA-F]{32}$` | getTaskQueueSid(): ?string | setTaskQueueSid(?string taskQueueSid): void |
| `taskQueueFriendlyName` | `?string` | Optional | The friendly name of the TaskQueue. | getTaskQueueFriendlyName(): ?string | setTaskQueueFriendlyName(?string taskQueueFriendlyName): void |
| `taskChannelSid` | `?string` | Optional | The SID of the TaskChannel.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^TC[0-9a-fA-F]{32}$` | getTaskChannelSid(): ?string | setTaskChannelSid(?string taskChannelSid): void |
| `taskChannelUniqueName` | `?string` | Optional | The unique name of the TaskChannel. | getTaskChannelUniqueName(): ?string | setTaskChannelUniqueName(?string taskChannelUniqueName): void |
| `timeout` | `?int` | Optional | The amount of time in seconds that the Task can live before being assigned.<br><br>**Default**: `0` | getTimeout(): ?int | setTimeout(?int timeout): void |
| `workflowSid` | `?string` | Optional | The SID of the Workflow that is controlling the Task.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WW[0-9a-fA-F]{32}$` | getWorkflowSid(): ?string | setWorkflowSid(?string workflowSid): void |
| `workflowFriendlyName` | `?string` | Optional | The friendly name of the Workflow that is controlling the Task. | getWorkflowFriendlyName(): ?string | setWorkflowFriendlyName(?string workflowFriendlyName): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the Task.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `url` | `?string` | Optional | The absolute URL of the Task resource. | getUrl(): ?string | setUrl(?string url): void |
| `links` | `?array` | Optional | The URLs of related resources. | getLinks(): ?array | setLinks(?array links): void |
| `virtualStartTime` | `?DateTime` | Optional | The date and time in GMT indicating the ordering for routing of the Task specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getVirtualStartTime(): ?\DateTime | setVirtualStartTime(?\DateTime virtualStartTime): void |
| `ignoreCapacity` | `?bool` | Optional | A boolean that indicates if the Task should respect a Worker's capacity and availability during assignment. This field can only be used when the `RoutingTarget` field is set to a Worker SID. By setting `IgnoreCapacity` to a value of `true`, `1`, or `yes`, the Task will be routed to the Worker without respecting their capacity and availability. Any other value will enforce the Worker's capacity and availability. The default value of `IgnoreCapacity` is `true` when the `RoutingTarget` is set to a Worker SID. | getIgnoreCapacity(): ?bool | setIgnoreCapacity(?bool ignoreCapacity): void |
| `routingTarget` | `?string` | Optional | A SID of a Worker, Queue, or Workflow to route a Task to | getRoutingTarget(): ?string | setRoutingTarget(?string routingTarget): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "age": 0,
  "priority": 0,
  "timeout": 0,
  "account_sid": "account_sid6",
  "assignment_status": "assigned",
  "attributes": "attributes4",
  "addons": "addons8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

