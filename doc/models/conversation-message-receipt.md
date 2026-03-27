
# Conversation Message Receipt

*This model accepts additional fields of type array.*

## Structure

`ConversationMessageReceipt`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `conversationSid` | `?string` | Optional | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CH[0-9a-fA-F]{32}$` | getConversationSid(): ?string | setConversationSid(?string conversationSid): void |
| `sid` | `?string` | Optional | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^DY[0-9a-fA-F]{32}$` | getSid(): ?string | setSid(?string sid): void |
| `messageSid` | `?string` | Optional | The SID of the message within a [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) the delivery receipt belongs to<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` | getMessageSid(): ?string | setMessageSid(?string messageSid): void |
| `channelMessageSid` | `?string` | Optional | A messaging channel-specific identifier for the message delivered to participant e.g. `SMxx` for SMS, `WAxx` for Whatsapp etc.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^[a-zA-Z]{2}[0-9a-fA-F]{32}$` | getChannelMessageSid(): ?string | setChannelMessageSid(?string channelMessageSid): void |
| `participantSid` | `?string` | Optional | The unique ID of the participant the delivery receipt belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MB[0-9a-fA-F]{32}$` | getParticipantSid(): ?string | setParticipantSid(?string participantSid): void |
| `status` | [`?string(ConversationMessageReceiptDeliveryStatus)`](../../doc/models/conversation-message-receipt-delivery-status.md) | Optional | The message delivery status, can be `read`, `failed`, `delivered`, `undelivered`, `sent` or null. | getStatus(): ?string | setStatus(?string status): void |
| `errorCode` | `?int` | Optional | The message [delivery error code](https://www.twilio.com/docs/sms/api/message-resource#delivery-related-errors) for a `failed` status,<br><br>**Default**: `0` | getErrorCode(): ?int | setErrorCode(?int errorCode): void |
| `dateCreated` | `?DateTime` | Optional | The date that this resource was created. | getDateCreated(): ?\DateTime | setDateCreated(?\DateTime dateCreated): void |
| `dateUpdated` | `?DateTime` | Optional | The date that this resource was last updated. `null` if the delivery receipt has not been updated. | getDateUpdated(): ?\DateTime | setDateUpdated(?\DateTime dateUpdated): void |
| `url` | `?string` | Optional | An absolute API resource URL for this delivery receipt. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "error_code": 0,
  "account_sid": "account_sid0",
  "conversation_sid": "conversation_sid0",
  "sid": "sid4",
  "message_sid": "message_sid2",
  "channel_message_sid": "channel_message_sid0",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

