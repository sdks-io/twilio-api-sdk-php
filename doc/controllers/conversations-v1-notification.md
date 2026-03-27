# Conversations V1 Notification

```php
$conversationsV1NotificationApi = $client->getConversationsV1NotificationApi();
```

## Class Name

`ConversationsV1NotificationApi`

## Methods

* [Update Service Notification](../../doc/controllers/conversations-v1-notification.md#update-service-notification)
* [Fetch Service Notification](../../doc/controllers/conversations-v1-notification.md#fetch-service-notification)


# Update Service Notification

Update push notification service settings

```php
function updateServiceNotification(
    string $chatServiceSid,
    ?bool $logEnabled = null,
    ?bool $newMessageEnabled = null,
    ?string $newMessageTemplate = null,
    ?string $newMessageSound = null,
    ?bool $newMessageBadgeCountEnabled = null,
    ?bool $addedToConversationEnabled = null,
    ?string $addedToConversationTemplate = null,
    ?string $addedToConversationSound = null,
    ?bool $removedFromConversationEnabled = null,
    ?string $removedFromConversationTemplate = null,
    ?string $removedFromConversationSound = null,
    ?bool $newMessageWithMediaEnabled = null,
    ?string $newMessageWithMediaTemplate = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Configuration applies to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `logEnabled` | `?bool` | Form, Optional | Weather the notification logging is enabled. |
| `newMessageEnabled` | `?bool` | Form, Optional | Whether to send a notification when a new message is added to a conversation. The default is `false`. |
| `newMessageTemplate` | `?string` | Form, Optional | The template to use to create the notification text displayed when a new message is added to a conversation and `new_message.enabled` is `true`. |
| `newMessageSound` | `?string` | Form, Optional | The name of the sound to play when a new message is added to a conversation and `new_message.enabled` is `true`. |
| `newMessageBadgeCountEnabled` | `?bool` | Form, Optional | Whether the new message badge is enabled. The default is `false`. |
| `addedToConversationEnabled` | `?bool` | Form, Optional | Whether to send a notification when a participant is added to a conversation. The default is `false`. |
| `addedToConversationTemplate` | `?string` | Form, Optional | The template to use to create the notification text displayed when a participant is added to a conversation and `added_to_conversation.enabled` is `true`. |
| `addedToConversationSound` | `?string` | Form, Optional | The name of the sound to play when a participant is added to a conversation and `added_to_conversation.enabled` is `true`. |
| `removedFromConversationEnabled` | `?bool` | Form, Optional | Whether to send a notification to a user when they are removed from a conversation. The default is `false`. |
| `removedFromConversationTemplate` | `?string` | Form, Optional | The template to use to create the notification text displayed to a user when they are removed from a conversation and `removed_from_conversation.enabled` is `true`. |
| `removedFromConversationSound` | `?string` | Form, Optional | The name of the sound to play to a user when they are removed from a conversation and `removed_from_conversation.enabled` is `true`. |
| `newMessageWithMediaEnabled` | `?bool` | Form, Optional | Whether to send a notification when a new message with media/file attachments is added to a conversation. The default is `false`. |
| `newMessageWithMediaTemplate` | `?string` | Form, Optional | The template to use to create the notification text displayed when a new message with media/file attachments is added to a conversation and `new_message.attachments.enabled` is `true`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceNotification`](../../doc/models/service-notification.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$logEnabled = true;

$newMessageEnabled = false;

$newMessageTemplate = 'You have a new message in ${CONVERSATION} from ${PARTICIPANT}: ${MESSAGE}';

$newMessageSound = 'ring';

$newMessageBadgeCountEnabled = true;

$addedToConversationEnabled = false;

$addedToConversationTemplate = 'You have been added to a Conversation: ${CONVERSATION}';

$addedToConversationSound = 'ring';

$removedFromConversationEnabled = false;

$removedFromConversationTemplate = 'You have been removed from a Conversation: ${CONVERSATION}';

$removedFromConversationSound = 'ring';

$newMessageWithMediaEnabled = false;

$newMessageWithMediaTemplate = 'You have a new message in ${CONVERSATION} with ${MEDIA_COUNT} media files: ${MEDIA}';

$conversationsV1NotificationApi = $client->getConversationsV1NotificationApi();
$apiResponse = $conversationsV1NotificationApi->updateServiceNotification(
    $chatServiceSid,
    $logEnabled,
    $newMessageEnabled,
    $newMessageTemplate,
    $newMessageSound,
    $newMessageBadgeCountEnabled,
    $addedToConversationEnabled,
    $addedToConversationTemplate,
    $addedToConversationSound,
    $removedFromConversationEnabled,
    $removedFromConversationTemplate,
    $removedFromConversationSound,
    $newMessageWithMediaEnabled,
    $newMessageWithMediaTemplate
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceNotification:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Fetch Service Notification

Fetch push notification service settings

```php
function fetchServiceNotification(string $chatServiceSid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Configuration applies to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceNotification`](../../doc/models/service-notification.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationsV1NotificationApi = $client->getConversationsV1NotificationApi();
$apiResponse = $conversationsV1NotificationApi->fetchServiceNotification($chatServiceSid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceNotification:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

