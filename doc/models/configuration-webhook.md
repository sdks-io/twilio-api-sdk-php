
# Configuration Webhook

*This model accepts additional fields of type array.*

## Structure

`ConfigurationWebhook`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accountSid` | `?string` | Optional | The unique ID of the [Account](https://www.twilio.com/docs/iam/api/account) responsible for this conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` | getAccountSid(): ?string | setAccountSid(?string accountSid): void |
| `method` | [`?string(ConfigurationWebhookMethod)`](../../doc/models/configuration-webhook-method.md) | Optional | The HTTP method to be used when sending a webhook request. | getMethod(): ?string | setMethod(?string method): void |
| `filters` | `?(string[])` | Optional | The list of webhook event triggers that are enabled for this Service: `onMessageAdded`, `onMessageUpdated`, `onMessageRemoved`, `onMessageAdd`, `onMessageUpdate`, `onMessageRemove`, `onConversationUpdated`, `onConversationRemoved`, `onConversationAdd`, `onConversationAdded`, `onConversationRemove`, `onConversationUpdate`, `onConversationStateUpdated`, `onParticipantAdded`, `onParticipantUpdated`, `onParticipantRemoved`, `onParticipantAdd`, `onParticipantRemove`, `onParticipantUpdate`, `onDeliveryUpdated`, `onUserAdded`, `onUserUpdate`, `onUserUpdated` | getFilters(): ?array | setFilters(?array filters): void |
| `preWebhookUrl` | `?string` | Optional | The absolute url the pre-event webhook request should be sent to. | getPreWebhookUrl(): ?string | setPreWebhookUrl(?string preWebhookUrl): void |
| `postWebhookUrl` | `?string` | Optional | The absolute url the post-event webhook request should be sent to. | getPostWebhookUrl(): ?string | setPostWebhookUrl(?string postWebhookUrl): void |
| `target` | [`?string(ConfigurationWebhookTarget)`](../../doc/models/configuration-webhook-target.md) | Optional | The routing target of the webhook. Can be ordinary or route internally to Flex | getTarget(): ?string | setTarget(?string target): void |
| `url` | `?string` | Optional | An absolute API resource API resource URL for this webhook. | getUrl(): ?string | setUrl(?string url): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example (as JSON)

```json
{
  "account_sid": "account_sid4",
  "method": "GET",
  "filters": [
    "filters8",
    "filters7"
  ],
  "pre_webhook_url": "pre_webhook_url0",
  "post_webhook_url": "post_webhook_url4",
  "exampleAdditionalProperty": {
    "key1": "val1",
    "key2": "val2"
  }
}
```

