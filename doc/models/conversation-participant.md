
# Conversation Participant

*This model accepts additional fields of type array.*

## Structure

`ConversationParticipant`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `conversationSid` | `?string` | Optional | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CH[0-9a-fA-F]{32}$` | getConversationSid(): ?string | setConversationSid(?string conversationSid): void |
| `sid` | `?string` | Optional | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MB[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `identity` | `?string` | Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the Conversations SDK to communicate. Limited to 256 characters. | getIdentity(): ?string | setIdentity(?string identity): void |
| `attributes` | `?string` | Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. | getAttributes(): ?string | setAttributes(?string attributes): void |
| `messagingBinding` | `?array` | Optional | Information about how this participant exchanges messages with the conversation. A JSON parameter consisting of type and address fields of the participant. | getMessagingBinding(): ?array | setMessagingBinding(?array messagingBinding): void |
| `roleSid` | `?string` | Optional | The SID of a conversation-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` | getRoleSid(): ?string | setRoleSid(?string roleSid): void |
| `dateCreated` | `?DateTime` | Optional | The date that this resource was created. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date that this resource was last updated. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `url` | `?string` | Optional | An absolute API resource URL for this participant. | getUrl(): ?string | setUrl(?string url): void |
| `lastReadMessageIndex` | `?int` | Optional | Index of last “read” message in the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for the Participant. | getLastReadMessageIndex(): ?int | setLastReadMessageIndex(?int lastReadMessageIndex): void |
| `lastReadTimestamp` | `?string` | Optional | Timestamp of last “read” message in the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for the Participant. | getLastReadTimestamp(): ?string | setLastReadTimestamp(?string lastReadTimestamp): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid0",
  "conversation_sid": "conversation_sid0",
  "sid": "sid6",
  "identity": "identity8",
  "attributes": "attributes8",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

