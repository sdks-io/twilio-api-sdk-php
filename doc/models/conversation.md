
# Conversation

*This model accepts additional fields of type array.*

## Structure

`Conversation`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `chatServiceSid` | `?string` | Optional | The unique ID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` | getChatServiceSid(): ?string | setChatServiceSid(?string chatServiceSid): void |
| `messagingServiceSid` | `?string` | Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` | getMessagingServiceSid(): ?string | setMessagingServiceSid(?string messagingServiceSid): void |
| `sid` | `?string` | Optional | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CH[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `friendlyName` | `?string` | Optional | The human-readable name of this conversation, limited to 256 characters. Optional. | getFriendlyName(): ?string | setFriendlyName(?string friendlyName): void |
| `uniqueName` | `?string` | Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. | getUniqueName(): ?string | setUniqueName(?string uniqueName): void |
| `attributes` | `?string` | Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. | getAttributes(): ?string | setAttributes(?string attributes): void |
| `state` | [`?string(ConversationState)`](../../doc/models/conversation-state.md) | Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` | getState(): ?string | setState(?string state): void |
| `dateCreated` | `?DateTime` | Optional | The date that this resource was created. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date that this resource was last updated. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `timers` | `?array` | Optional | Timer date values representing state update for this conversation. | getTimers(): ?array | setTimers(?array timers): void |
| `url` | `?string` | Optional | An absolute API resource URL for this conversation. | getUrl(): ?string | setUrl(?string url): void |
| `links` | `?array` | Optional | Contains absolute URLs to access the [participants](https://www.twilio.com/docs/conversations/api/conversation-participant-resource), [messages](https://www.twilio.com/docs/conversations/api/conversation-message-resource) and [webhooks](https://www.twilio.com/docs/conversations/api/conversation-scoped-webhook-resource) of this conversation. | getLinks(): ?array | setLinks(?array links): void |
| `bindings` | `?array` | Optional | - | getBindings(): ?array | setBindings(?array bindings): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid2",
  "chat_service_sid": "chat_service_sid6",
  "messaging_service_sid": "messaging_service_sid6",
  "sid": "sid8",
  "friendly_name": "friendly_name2",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

