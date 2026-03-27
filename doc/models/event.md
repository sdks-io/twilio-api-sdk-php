
# Event

*This model accepts additional fields of type array.*

## Structure

`Event`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Event resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `actorSid` | `?string` | Optional | The SID of the resource that triggered the event.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^[a-zA-Z]{2}[0-9a-fA-F]{32}$` | getActorSid(): ?string | setActorSid(?string actorSid): void |
| `actorType` | `?string` | Optional | The type of resource that triggered the event. | getActorType(): ?string | setActorType(?string actorType): void |
| `actorUrl` | `?string` | Optional | The absolute URL of the resource that triggered the event. | getActorUrl(): ?string | setActorUrl(?string actorUrl): void |
| `description` | `?string` | Optional | A description of the event. | getDescription(): ?string | setDescription(?string description): void |
| `eventData` | `?array` | Optional | Data about the event. For more information, see [Event types](https://www.twilio.com/docs/taskrouter/api/event#event-types). | getEventData(): ?array | setEventData(?array eventData): void |
| `eventDate` | `?DateTime` | Optional | The time the event was sent, specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getEventDate(): ?\DateTime | setEventDate(?\DateTime eventDate): void |
| `eventDateMs` | `?int` | Optional | The time the event was sent in milliseconds. | getEventDateMs(): ?int | setEventDateMs(?int eventDateMs): void |
| `eventType` | `?string` | Optional | The identifier for the event. | getEventType(): ?string | setEventType(?string eventType): void |
| `resourceSid` | `?string` | Optional | The SID of the object the event is most relevant to, such as a TaskSid, ReservationSid, or a  WorkerSid.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^[a-zA-Z]{2}[0-9a-fA-F]{32}$` | getResourceSid(): ?string | setResourceSid(?string resourceSid): void |
| `resourceType` | `?string` | Optional | The type of object the event is most relevant to, such as a Task, Reservation, or a Worker). | getResourceType(): ?string | setResourceType(?string resourceType): void |
| `resourceUrl` | `?string` | Optional | The URL of the resource the event is most relevant to. | getResourceUrl(): ?string | setResourceUrl(?string resourceUrl): void |
| `sid` | `?string` | Optional | The unique string that we created to identify the Event resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^EV[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `source` | `?string` | Optional | Where the Event originated. | getSource(): ?string | setSource(?string source): void |
| `sourceIpAddress` | `?string` | Optional | The IP from which the Event originated. | getSourceIpAddress(): ?string | setSourceIpAddress(?string sourceIpAddress): void |
| `url` | `?string` | Optional | The absolute URL of the Event resource. | getUrl(): ?string | setUrl(?string url): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the Event.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid8",
  "actor_sid": "actor_sid4",
  "actor_type": "actor_type8",
  "actor_url": "actor_url6",
  "description": "description8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

