
# Configuration

*This model accepts additional fields of type array.*

## Structure

`Configuration`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The SID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this configuration.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `defaultChatServiceSid` | `?string` | Optional | The SID of the default [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) used when creating a conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` | getDefaultChatServiceSid(): ?string | setDefaultChatServiceSid(?string defaultChatServiceSid): void |
| `defaultMessagingServiceSid` | `?string` | Optional | The SID of the default [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) used when creating a conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` | getDefaultMessagingServiceSid(): ?string | setDefaultMessagingServiceSid(?string defaultMessagingServiceSid): void |
| `defaultInactiveTimer` | `?string` | Optional | Default ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. | getDefaultInactiveTimer(): ?string | setDefaultInactiveTimer(?string defaultInactiveTimer): void |
| `defaultClosedTimer` | `?string` | Optional | Default ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. | getDefaultClosedTimer(): ?string | setDefaultClosedTimer(?string defaultClosedTimer): void |
| `url` | `?string` | Optional | An absolute API resource URL for this global configuration. | getUrl(): ?string | setUrl(?string url): void |
| `links` | `?array` | Optional | Contains absolute API resource URLs to access the webhook and default service configurations. | getLinks(): ?array | setLinks(?array links): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid8",
  "default_chat_service_sid": "default_chat_service_sid2",
  "default_messaging_service_sid": "default_messaging_service_sid6",
  "default_inactive_timer": "default_inactive_timer2",
  "default_closed_timer": "default_closed_timer2",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

