
# Task Channel

*This model accepts additional fields of type array.*

## Structure

`TaskChannel`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) that created the Task Channel resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `dateCreated` | `?DateTime` | Optional | The date and time in GMT when the resource was created specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date and time in GMT when the resource was last updated specified in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `friendlyName` | `?string` | Optional | The string that you assigned to describe the resource. | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `sid` | `?string` | Optional | The unique string that we created to identify the Task Channel resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^TC[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `uniqueName` | `?string` | Optional | An application-defined string that uniquely identifies the Task Channel, such as `voice` or `sms`. | getUniqueName(): ?string | setUniqueName(?string uniqueName): void |
| `workspaceSid` | `?string` | Optional | The SID of the Workspace that contains the Task Channel.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` | getWorkspaceSid(): ?string | setWorkspaceSid(?string workspaceSid): void |
| `channelOptimizedRouting` | `?bool` | Optional | Whether the Task Channel will prioritize Workers that have been idle. When `true`, Workers that have been idle the longest are prioritized. | getChannelOptimizedRouting(): ?bool | setChannelOptimizedRouting(?bool channelOptimizedRouting): void |
| `url` | `?string` | Optional | The absolute URL of the Task Channel resource. | getUrl(): ?string | setUrl(?string url): void |
| `links` | `?array` | Optional | The URLs of related resources. | getLinks(): ?array | setLinks(?array links): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid4",
  "date_created": "2016-03-13T12:52:32.123Z",
  "date_updated": "2016-03-13T12:52:32.123Z",
  "friendly_name": "friendly_name4",
  "sid": "sid0",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

