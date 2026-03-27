
# Activity

*This model accepts additional fields of type array.*

## Structure

`Activity`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Activity resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `available` | `?bool` | Optional | Whether the Worker is eligible to receive a Task when it occupies the Activity. A value of `true`, `1`, or `yes` indicates the Activity is available. All other values indicate that it is not. The value cannot be changed after the Activity is created. | getAvailable(): ?bool | setAvailable(?bool available): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `friendlyName` | `?string` | Optional | The string that you assigned to describe the Activity resource. | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `sid` | `?string` | Optional | The unique string that we created to identify the Activity resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the Activity.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `url` | `?string` | Optional | The absolute URL of the Activity resource. | getUrl(): ?string | setUrl(?string url): void |
| `links` | `?array` | Optional | - | getLinks(): ?array | setLinks(?array links): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid2",
  "available": false,
  "date_created": "2016-03-13T12:52:32.123Z",
  "date_updated": "2016-03-13T12:52:32.123Z",
  "friendly_name": "friendly_name8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

