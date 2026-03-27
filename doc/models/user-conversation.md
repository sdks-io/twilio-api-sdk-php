
# User Conversation

*This model accepts additional fields of type array.*

## Structure

`UserConversation`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `chatServiceSid` | `?string` | Optional | The unique ID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` | getChatServiceSid(): ?string | setChatServiceSid(?string chatServiceSid): void |
| `conversationSid` | `?string` | Optional | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this User Conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CH[0-9a-fA-F]{32}$` | getConversationSid(): ?string | setConversationSid(?string conversationSid): void |
| `unreadMessagesCount` | `?int` | Optional | The number of unread Messages in the Conversation for the Participant. | getUnreadMessagesCount(): ?int | setUnreadMessagesCount(?int unreadMessagesCount): void |
| `lastReadMessageIndex` | `?int` | Optional | The index of the last Message in the Conversation that the Participant has read. | getLastReadMessageIndex(): ?int | setLastReadMessageIndex(?int lastReadMessageIndex): void |
| `participantSid` | `?string` | Optional | The unique ID of the [participant](https://www.twilio.com/docs/conversations/api/conversation-participant-resource) the user conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MB[0-9a-fA-F]{32}$` | getParticipantSid(): ?string | setParticipantSid(?string participantSid): void |
| `userSid` | `?string` | Optional | The unique string that identifies the [User resource](https://www.twilio.com/docs/conversations/api/user-resource).<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^US[0-9a-fA-F]{32}$` | getUserSid(): ?string | setUserSid(?string userSid): void |
| `friendlyName` | `?string` | Optional | The human-readable name of this conversation, limited to 256 characters. Optional. | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `conversationState` | [`?string(UserConversationState)`](../../doc/models/user-conversation-state.md) | Optional | The current state of this User Conversation. One of `inactive`, `active` or `closed`. | getConversationState(): ?string | setConversationState(?string conversationState): void |
| `timers` | `?array` | Optional | Timer date values representing state update for this conversation. | getTimers(): ?array | setTimers(?array timers): void |
| `attributes` | `?string` | Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. | getAttributes(): ?string | setAttributes(?string attributes): void |
| `dateCreated` | `?DateTime` | Optional | The date that this conversation was created, given in ISO 8601 format. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date that this conversation was last updated, given in ISO 8601 format. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `createdBy` | `?string` | Optional | Identity of the creator of this Conversation. | getCreatedBy(): ?string | setCreatedBy(?string createdBy): void |
| `notificationLevel` | [`?string(UserConversationNotificationLevel)`](../../doc/models/user-conversation-notification-level.md) | Optional | The Notification Level of this User Conversation. One of `default` or `muted`. | getNotificationLevel(): ?string | setNotificationLevel(?string notificationLevel): void |
| `uniqueName` | `?string` | Optional | An application-defined string that uniquely identifies the Conversation resource. It can be used to address the resource in place of the resource's `conversation_sid` in the URL. | getUniqueName(): ?string | setUniqueName(?string uniqueName): void |
| `url` | `?string` | Optional | - | getUrl(): ?string | setUrl(?string url): void |
| `links` | `?array` | Optional | Contains absolute URLs to access the [participant](https://www.twilio.com/docs/conversations/api/conversation-participant-resource) and [conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) of this conversation. | getLinks(): ?array | setLinks(?array links): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid6",
  "chat_service_sid": "chat_service_sid0",
  "conversation_sid": "conversation_sid4",
  "unread_messages_count": 104,
  "last_read_message_index": 250,
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

