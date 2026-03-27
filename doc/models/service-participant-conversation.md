
# Service Participant Conversation

*This model accepts additional fields of type array.*

## Structure

`ServiceParticipantConversation`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `chatServiceSid` | `?string` | Optional | The unique ID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` | getChatServiceSid(): ?string | setChatServiceSid(?string chatServiceSid): void |
| `participantSid` | `?string` | Optional | The unique ID of the [Participant](https://www.twilio.com/docs/conversations/api/conversation-participant-resource).<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MB[0-9a-fA-F]{32}$` | getParticipantSid(): ?string | setParticipantSid(?string participantSid): void |
| `participantUserSid` | `?string` | Optional | The unique string that identifies the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource).<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^US[0-9a-fA-F]{32}$` | getParticipantUserSid(): ?string | setParticipantUserSid(?string participantUserSid): void |
| `participantIdentity` | `?string` | Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the Conversations SDK to communicate. Limited to 256 characters. | getParticipantIdentity(): ?string | setParticipantIdentity(?string participantIdentity): void |
| `participantMessagingBinding` | `?array` | Optional | Information about how this participant exchanges messages with the conversation. A JSON parameter consisting of type and address fields of the participant. | getParticipantMessagingBinding(): ?array | setParticipantMessagingBinding(?array participantMessagingBinding): void |
| `conversationSid` | `?string` | Optional | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) this Participant belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CH[0-9a-fA-F]{32}$` | getConversationSid(): ?string | setConversationSid(?string conversationSid): void |
| `conversationUniqueName` | `?string` | Optional | An application-defined string that uniquely identifies the Conversation resource. | getConversationUniqueName(): ?string | setConversationUniqueName(?string conversationUniqueName): void |
| `conversationFriendlyName` | `?string` | Optional | The human-readable name of this conversation, limited to 256 characters. Optional. | getConversationFriendlyName(): ?string | setConversationFriendlyName(?string conversationFriendlyName): void |
| `conversationAttributes` | `?string` | Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. | getConversationAttributes(): ?string | setConversationAttributes(?string conversationAttributes): void |
| `conversationDateCreated` | `?DateTime` | Optional | The date that this conversation was created, given in ISO 8601 format. | getConversationDateCreated(): ?\DateTime | setConversationDateCreated(?\DateTime conversationDateCreated): void |
| `conversationDateUpdated` | `?DateTime` | Optional | The date that this conversation was last updated, given in ISO 8601 format. | getConversationDateUpdated(): ?\DateTime | setConversationDateUpdated(?\DateTime conversationDateUpdated): void |
| `conversationCreatedBy` | `?string` | Optional | Identity of the creator of this Conversation. | getConversationCreatedBy(): ?string | setConversationCreatedBy(?string conversationCreatedBy): void |
| `conversationState` | [`?string(ServiceParticipantConversationState)`](../../doc/models/service-participant-conversation-state.md) | Optional | The current state of this User Conversation. One of `inactive`, `active` or `closed`. | getConversationState(): ?string | setConversationState(?string conversationState): void |
| `conversationTimers` | `?array` | Optional | Timer date values representing state update for this conversation. | getConversationTimers(): ?array | setConversationTimers(?array conversationTimers): void |
| `links` | `?array` | Optional | Contains absolute URLs to access the [participant](https://www.twilio.com/docs/conversations/api/conversation-participant-resource) and [conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) of this conversation. | getLinks(): ?array | setLinks(?array links): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid4",
  "chat_service_sid": "chat_service_sid8",
  "participant_sid": "participant_sid6",
  "participant_user_sid": "participant_user_sid4",
  "participant_identity": "participant_identity0",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

