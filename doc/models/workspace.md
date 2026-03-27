
# Workspace

*This model accepts additional fields of type array.*

## Structure

`Workspace`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Workspace resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `defaultActivityName` | `?string` | Optional | The name of the default activity. | getDefaultActivityName(): ?string | setDefaultActivityName(?string defaultActivityName): void |
| `defaultActivitySid` | `?string` | Optional | The SID of the Activity that will be used when new Workers are created in the Workspace.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` | getDefaultActivitySid(): ?string | setDefaultActivitySid(?string defaultActivitySid): void |
| `eventCallbackUrl` | `?string` | Optional | The URL we call when an event occurs. If provided, the Workspace will publish events to this URL, for example, to collect data for reporting. See [Workspace Events](https://www.twilio.com/docs/taskrouter/api/event) for more information. This parameter supports Twilio's [Webhooks (HTTP callbacks) Connection Overrides](https://www.twilio.com/docs/usage/webhooks/webhooks-connection-overrides). | getEventCallbackUrl(): ?string | setEventCallbackUrl(?string eventCallbackUrl): void |
| `eventsFilter` | `?string` | Optional | The list of Workspace events for which to call `event_callback_url`. For example, if `EventsFilter=task.created, task.canceled, worker.activity.update`, then TaskRouter will call event_callback_url only when a task is created, canceled, or a Worker activity is updated. | getEventsFilter(): ?string | setEventsFilter(?string eventsFilter): void |
| `friendlyName` | `?string` | Optional | The string that you assigned to describe the Workspace resource. For example `Customer Support` or `2014 Election Campaign`. | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `multiTaskEnabled` | `?bool` | Optional | Whether multi-tasking is enabled. The default is `true`, which enables multi-tasking. Multi-tasking allows Workers to handle multiple Tasks simultaneously. When enabled (`true`), each Worker can receive parallel reservations up to the per-channel maximums defined in the Workers section. In single-tasking each Worker would only receive a new reservation when the previous task is completed. Learn more at [Multitasking](https://www.twilio.com/docs/taskrouter/multitasking). | getMultiTaskEnabled(): ?bool | setMultiTaskEnabled(?bool multiTaskEnabled): void |
| `sid` | `?string` | Optional | The unique string that we created to identify the Workspace resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `timeoutActivityName` | `?string` | Optional | The name of the timeout activity. | getTimeoutActivityName(): ?string | setTimeoutActivityName(?string timeoutActivityName): void |
| `timeoutActivitySid` | `?string` | Optional | The SID of the Activity that will be assigned to a Worker when a Task reservation times out without a response.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` | getTimeoutActivitySid(): ?string | setTimeoutActivitySid(?string timeoutActivitySid): void |
| `prioritizeQueueOrder` | [`?string(WorkspaceQueueOrder)`](../../doc/models/workspace-queue-order.md) | Optional | The type of TaskQueue to prioritize when Workers are receiving Tasks from both types of TaskQueues. Can be: `LIFO` or `FIFO` and the default is `FIFO`. For more information, see [Queue Ordering](https://www.twilio.com/docs/taskrouter/queue-ordering-last-first-out-lifo). | getPrioritizeQueueOrder(): ?string | setPrioritizeQueueOrder(?string prioritizeQueueOrder): void |
| `url` | `?string` | Optional | The absolute URL of the Workspace resource. | getUrl(): ?string | setUrl(?string url): void |
| `links` | `?array` | Optional | The URLs of related resources. | getLinks(): ?array | setLinks(?array links): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid8",
  "date_created": "2016-03-13T12:52:32.123Z",
  "date_updated": "2016-03-13T12:52:32.123Z",
  "default_activity_name": "default_activity_name4",
  "default_activity_sid": "default_activity_sid4",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

