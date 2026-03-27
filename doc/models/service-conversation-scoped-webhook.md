
# Service Conversation Scoped Webhook

*This model accepts additional fields of type array.*

## Structure

`ServiceConversationScopedWebhook`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `sid` | `?string` | Optional | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `accountSid` | `?string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `chatServiceSid` | `?string` | Optional | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` | getChatServiceSid(): ?string | setChatServiceSid(?string chatServiceSid): void |
| `conversationSid` | `?string` | Optional | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CH[0-9a-fA-F]{32}$` | getConversationSid(): ?string | setConversationSid(?string conversationSid): void |
| `target` | `?string` | Optional | The target of this webhook: `webhook`, `studio`, `trigger` | getTarget(): ?string | setTarget(?string target): void |
| `url` | `?string` | Optional | An absolute API resource URL for this webhook. | getUrl(): ?string | setUrl(?string url): void |
| `configuration` | `?array` | Optional | The configuration of this webhook. Is defined based on target. | getConfiguration(): ?array | setConfiguration(?array configuration): void |
| `dateCreated` | `?DateTime` | Optional | The date that this resource was created. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date that this resource was last updated. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "sid": "sid6",
  "account_sid": "account_sid8",
  "chat_service_sid": "chat_service_sid2",
  "conversation_sid": "conversation_sid2",
  "target": "target0",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

