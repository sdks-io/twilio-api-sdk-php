
# Service Webhook Configuration

*This model accepts additional fields of type array.*

## Structure

`ServiceWebhookConfiguration`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this service.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `chatServiceSid` | `?string` | Optional | The unique ID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` | getChatServiceSid(): ?string | setChatServiceSid(?string chatServiceSid): void |
| `preWebhookUrl` | `?string` | Optional | The absolute url the pre-event webhook request should be sent to. | getPreWebhookUrl(): ?string | setPreWebhookUrl(?string preWebhookUrl): void |
| `postWebhookUrl` | `?string` | Optional | The absolute url the post-event webhook request should be sent to. | getPostWebhookUrl(): ?string | setPostWebhookUrl(?string postWebhookUrl): void |
| `filters` | `?(string[])` | Optional | The list of events that your configured webhook targets will receive. Events not configured here will not fire. Possible values are `onParticipantAdd`, `onParticipantAdded`, `onDeliveryUpdated`, `onConversationUpdated`, `onConversationRemove`, `onParticipantRemove`, `onConversationUpdate`, `onMessageAdd`, `onMessageRemoved`, `onParticipantUpdated`, `onConversationAdded`, `onMessageAdded`, `onConversationAdd`, `onConversationRemoved`, `onParticipantUpdate`, `onMessageRemove`, `onMessageUpdated`, `onParticipantRemoved`, `onMessageUpdate` or `onConversationStateUpdated`. | getFilters(): ?array | setFilters(?array filters): void |
| `method` | [`?string(ServiceWebhookConfigurationMethod)`](../../doc/models/service-webhook-configuration-method.md) | Optional | The HTTP method to be used when sending a webhook request. One of `GET` or `POST`. | getMethod(): ?string | setMethod(?string method): void |
| `url` | `?string` | Optional | An absolute API resource URL for this webhook. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid2",
  "chat_service_sid": "chat_service_sid6",
  "pre_webhook_url": "pre_webhook_url8",
  "post_webhook_url": "post_webhook_url2",
  "filters": [
    "filters6",
    "filters5"
  ],
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

