
# Worker

*This model accepts additional fields of type array.*

## Structure

`Worker`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Worker resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `activityName` | `?string` | Optional | The `friendly_name` of the Worker's current Activity. | getActivityName(): ?string | setActivityName(?string activityName): void |
| `activitySid` | `?string` | Optional | The SID of the Worker's current Activity.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` | getActivitySid(): ?string | setActivitySid(?string activitySid): void |
| `attributes` | `?string` | Optional | The JSON string that describes the Worker. For example: `{ "email": "Bob@example.com", "phone": "+5095551234" }`. **Note** If this property has been assigned a value, it will only be displayed in FETCH actions that return a single resource. Otherwise, this property will be null, even if it has a value. This data is passed to the `assignment_callback_url` when TaskRouter assigns a Task to the Worker. | getAttributes(): ?string | setAttributes(?string attributes): void |
| `available` | `?bool` | Optional | Whether the Worker is available to perform tasks. | getAvailable(): ?bool | setAvailable(?bool available): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateStatusChanged` | `?DateTime` | Optional | The date and time in GMT of the last change to the Worker's activity specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. Used to calculate Workflow statistics. | getDateStatusChanged(): ?\DateTime | setDateStatusChanged(?\DateTime dateStatusChanged): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `friendlyName` | `?string` | Optional | The string that you assigned to describe the resource. Friendly names are case insensitive, and unique within the TaskRouter Workspace. | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `sid` | `?string` | Optional | The unique string that we created to identify the Worker resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WK[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the Worker.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `url` | `?string` | Optional | The absolute URL of the Worker resource. | getUrl(): ?string | setUrl(?string url): void |
| `links` | `?array` | Optional | The URLs of related resources. | getLinks(): ?array | setLinks(?array links): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid4",
  "activity_name": "activity_name6",
  "activity_sid": "activity_sid6",
  "attributes": "attributes2",
  "available": false,
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

