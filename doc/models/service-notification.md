
# Service Notification

*This model accepts additional fields of type array.*

## Structure

`ServiceNotification`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this configuration.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `chatServiceSid` | `?string` | Optional | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Configuration applies to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` | getChatServiceSid(): ?string | setChatServiceSid(?string chatServiceSid): void |
| `newMessage` | `?array` | Optional | The Push Notification configuration for New Messages. | getNewMessage(): ?array | setNewMessage(?array newMessage): void |
| `addedToConversation` | `?array` | Optional | The Push Notification configuration for being added to a Conversation. | getAddedToConversation(): ?array | setAddedToConversation(?array addedToConversation): void |
| `removedFromConversation` | `?array` | Optional | The Push Notification configuration for being removed from a Conversation. | getRemovedFromConversation(): ?array | setRemovedFromConversation(?array removedFromConversation): void |
| `logEnabled` | `?bool` | Optional | Weather the notification logging is enabled. | getLogEnabled(): ?bool | setLogEnabled(?bool logEnabled): void |
| `url` | `?string` | Optional | An absolute API resource URL for this configuration. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid6",
  "chat_service_sid": "chat_service_sid0",
  "new_message": {
    "key1": "val1",
    "key2": "val2"
  },
  "added_to_conversation": {
    "key1": "val1",
    "key2": "val2"
  },
  "removed_from_conversation": {
    "key1": "val1",
    "key2": "val2"
  },
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

