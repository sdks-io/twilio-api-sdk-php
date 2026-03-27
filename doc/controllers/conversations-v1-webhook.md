# Conversations V1 Webhook

```php
$conversationsV1WebhookApi = $client->getConversationsV1WebhookApi();
```

## Class Name

`ConversationsV1WebhookApi`

## Methods

* [Fetch Configuration Webhook](../../doc/controllers/conversations-v1-webhook.md#fetch-configuration-webhook)
* [Update Configuration Webhook](../../doc/controllers/conversations-v1-webhook.md#update-configuration-webhook)
* [List Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#list-conversation-scoped-webhook)
* [Create Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#create-conversation-scoped-webhook)
* [Fetch Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#fetch-conversation-scoped-webhook)
* [Update Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#update-conversation-scoped-webhook)
* [Delete Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#delete-conversation-scoped-webhook)
* [Create Service Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#create-service-conversation-scoped-webhook)
* [List Service Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#list-service-conversation-scoped-webhook)
* [Update Service Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#update-service-conversation-scoped-webhook)
* [Delete Service Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#delete-service-conversation-scoped-webhook)
* [Fetch Service Conversation Scoped Webhook](../../doc/controllers/conversations-v1-webhook.md#fetch-service-conversation-scoped-webhook)
* [Update Service Webhook Configuration](../../doc/controllers/conversations-v1-webhook.md#update-service-webhook-configuration)
* [Fetch Service Webhook Configuration](../../doc/controllers/conversations-v1-webhook.md#fetch-service-webhook-configuration)


# Fetch Configuration Webhook

A Webhook resource manages a service-level set of callback URLs and their configuration for receiving all conversation events.

```php
function fetchConfigurationWebhook(): ApiResponse
```

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ConfigurationWebhook`](../../doc/models/configuration-webhook.md).

## Example Usage

```php
$conversationsV1WebhookApi = $client->getConversationsV1WebhookApi();
$apiResponse = $conversationsV1WebhookApi->fetchConfigurationWebhook();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ConfigurationWebhook:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "pre_webhook_url": "https://example.com/pre",
  "post_webhook_url": "https://example.com/post",
  "method": "GET",
  "filters": [
    "onMessageSend",
    "onConversationUpdated"
  ],
  "target": "webhook",
  "url": "https://conversations.twilio.com/v1/Configuration/Webhooks"
}
```


# Update Configuration Webhook

A Webhook resource manages a service-level set of callback URLs and their configuration for receiving all conversation events.

```php
function updateConfigurationWebhook(
    ?string $method = null,
    ?array $filters = null,
    ?string $preWebhookUrl = null,
    ?string $postWebhookUrl = null,
    ?string $target = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `method` | `?string` | Form, Optional | The HTTP method to be used when sending a webhook request. |
| `filters` | `?(string[])` | Form, Optional | The list of webhook event triggers that are enabled for this Service: `onMessageAdded`, `onMessageUpdated`, `onMessageRemoved`, `onMessageAdd`, `onMessageUpdate`, `onMessageRemove`, `onConversationUpdated`, `onConversationRemoved`, `onConversationAdd`, `onConversationAdded`, `onConversationRemove`, `onConversationUpdate`, `onConversationStateUpdated`, `onParticipantAdded`, `onParticipantUpdated`, `onParticipantRemoved`, `onParticipantAdd`, `onParticipantRemove`, `onParticipantUpdate`, `onDeliveryUpdated`, `onUserAdded`, `onUserUpdate`, `onUserUpdated` |
| `preWebhookUrl` | `?string` | Form, Optional | The absolute url the pre-event webhook request should be sent to. |
| `postWebhookUrl` | `?string` | Form, Optional | The absolute url the post-event webhook request should be sent to. |
| `target` | [`?string(ConfigurationWebhookTarget)`](../../doc/models/configuration-webhook-target.md) | Form, Optional | The routing target of the webhook. Can be ordinary or route internally to Flex |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ConfigurationWebhook`](../../doc/models/configuration-webhook.md).

## Example Usage

```php
$method = 'GET';

$filters = [
    'onConversationUpdated'
];

$preWebhookUrl = 'https://example.com/pre';

$postWebhookUrl = 'https://example.com/post';

$target = ConfigurationWebhookTarget::WEBHOOK;

$conversationsV1WebhookApi = $client->getConversationsV1WebhookApi();
$apiResponse = $conversationsV1WebhookApi->updateConfigurationWebhook(
    $method,
    $filters,
    $preWebhookUrl,
    $postWebhookUrl,
    $target
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ConfigurationWebhook:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "pre_webhook_url": "https://example.com/pre",
  "post_webhook_url": "http://example.com/post",
  "method": "GET",
  "filters": [
    "onConversationUpdated"
  ],
  "target": "webhook",
  "url": "https://conversations.twilio.com/v1/Configuration/Webhooks"
}
```


# List Conversation Scoped Webhook

Retrieve a list of all webhooks scoped to the conversation

```php
function listConversationScopedWebhook(
    string $conversationSid,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 5, and the maximum is 5.<br><br>**Constraints**: `>= 1`, `<= 5` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListConversationScopedWebhookResponse`](../../doc/models/list-conversation-scoped-webhook-response.md).

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$conversationsV1WebhookApi = $client->getConversationsV1WebhookApi();
$apiResponse = $conversationsV1WebhookApi->listConversationScopedWebhook($conversationSid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListConversationScopedWebhookResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Create Conversation Scoped Webhook

Create a new webhook scoped to the conversation

```php
function createConversationScopedWebhook(
    string $conversationSid,
    string $target,
    ?string $configurationUrl = null,
    ?string $configurationMethod = null,
    ?array $configurationFilters = null,
    ?array $configurationTriggers = null,
    ?string $configurationFlowSid = null,
    ?int $configurationReplayAfter = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `target` | [`string(ConversationScopedWebhookTarget)`](../../doc/models/conversation-scoped-webhook-target.md) | Form, Required | The target of this webhook: `webhook`, `studio`, `trigger` |
| `configurationUrl` | `?string` | Form, Optional | The absolute url the webhook request should be sent to. |
| `configurationMethod` | [`?string(ConversationScopedWebhookMethod)`](../../doc/models/conversation-scoped-webhook-method.md) | Form, Optional | - |
| `configurationFilters` | `?(string[])` | Form, Optional | The list of events, firing webhook event for this Conversation. |
| `configurationTriggers` | `?(string[])` | Form, Optional | The list of keywords, firing webhook event for this Conversation. |
| `configurationFlowSid` | `?string` | Form, Optional | The studio flow SID, where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |
| `configurationReplayAfter` | `?int` | Form, Optional | The message index for which and it's successors the webhook will be replayed. Not set by default |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ConversationScopedWebhook`](../../doc/models/conversation-scoped-webhook.md).

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$target = ConversationScopedWebhookTarget::WEBHOOK;

$configurationUrl = 'https://example.com';

$configurationMethod = ConversationScopedWebhookMethod::GET;

$configurationFilters = [
    'onMessageSent',
    'onConversationDestroyed'
];

$configurationReplayAfter = 7;

$conversationsV1WebhookApi = $client->getConversationsV1WebhookApi();
$apiResponse = $conversationsV1WebhookApi->createConversationScopedWebhook(
    $conversationSid,
    $target,
    $configurationUrl,
    $configurationMethod,
    $configurationFilters,
    null,
    null,
    $configurationReplayAfter
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ConversationScopedWebhook:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Fetch Conversation Scoped Webhook

Fetch the configuration of a conversation-scoped webhook

```php
function fetchConversationScopedWebhook(string $conversationSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ConversationScopedWebhook`](../../doc/models/conversation-scoped-webhook.md).

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$conversationsV1WebhookApi = $client->getConversationsV1WebhookApi();
$apiResponse = $conversationsV1WebhookApi->fetchConversationScopedWebhook(
    $conversationSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ConversationScopedWebhook:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Update Conversation Scoped Webhook

Update an existing conversation-scoped webhook

```php
function updateConversationScopedWebhook(
    string $conversationSid,
    string $sid,
    ?string $configurationUrl = null,
    ?string $configurationMethod = null,
    ?array $configurationFilters = null,
    ?array $configurationTriggers = null,
    ?string $configurationFlowSid = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |
| `configurationUrl` | `?string` | Form, Optional | The absolute url the webhook request should be sent to. |
| `configurationMethod` | [`?string(ConversationScopedWebhookMethod)`](../../doc/models/conversation-scoped-webhook-method.md) | Form, Optional | - |
| `configurationFilters` | `?(string[])` | Form, Optional | The list of events, firing webhook event for this Conversation. |
| `configurationTriggers` | `?(string[])` | Form, Optional | The list of keywords, firing webhook event for this Conversation. |
| `configurationFlowSid` | `?string` | Form, Optional | The studio flow SID, where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ConversationScopedWebhook`](../../doc/models/conversation-scoped-webhook.md).

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$configurationUrl = 'https://example.com';

$configurationMethod = ConversationScopedWebhookMethod::POST;

$configurationTriggers = [
    'keyword1',
    'keyword2'
];

$conversationsV1WebhookApi = $client->getConversationsV1WebhookApi();
$apiResponse = $conversationsV1WebhookApi->updateConversationScopedWebhook(
    $conversationSid,
    $sid,
    $configurationUrl,
    $configurationMethod,
    null,
    $configurationTriggers
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ConversationScopedWebhook:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete Conversation Scoped Webhook

Remove an existing webhook scoped to the conversation

```php
function deleteConversationScopedWebhook(string $conversationSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$conversationsV1WebhookApi = $client->getConversationsV1WebhookApi();
$apiResponse = $conversationsV1WebhookApi->deleteConversationScopedWebhook(
    $conversationSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'void:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Create Service Conversation Scoped Webhook

Create a new webhook scoped to the conversation in a specific service

```php
function createServiceConversationScopedWebhook(
    string $chatServiceSid,
    string $conversationSid,
    string $target,
    ?string $configurationUrl = null,
    ?string $configurationMethod = null,
    ?array $configurationFilters = null,
    ?array $configurationTriggers = null,
    ?string $configurationFlowSid = null,
    ?int $configurationReplayAfter = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `target` | [`string(ServiceConversationScopedWebhookTarget)`](../../doc/models/service-conversation-scoped-webhook-target.md) | Form, Required | The target of this webhook: `webhook`, `studio`, `trigger` |
| `configurationUrl` | `?string` | Form, Optional | The absolute url the webhook request should be sent to. |
| `configurationMethod` | [`?string(ServiceConversationScopedWebhookMethod)`](../../doc/models/service-conversation-scoped-webhook-method.md) | Form, Optional | - |
| `configurationFilters` | `?(string[])` | Form, Optional | The list of events, firing webhook event for this Conversation. |
| `configurationTriggers` | `?(string[])` | Form, Optional | The list of keywords, firing webhook event for this Conversation. |
| `configurationFlowSid` | `?string` | Form, Optional | The studio flow SID, where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |
| `configurationReplayAfter` | `?int` | Form, Optional | The message index for which and it's successors the webhook will be replayed. Not set by default |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceConversationScopedWebhook`](../../doc/models/service-conversation-scoped-webhook.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$target = ServiceConversationScopedWebhookTarget::WEBHOOK;

$configurationUrl = 'https://example.com';

$configurationMethod = ServiceConversationScopedWebhookMethod::GET;

$configurationFilters = [
    'onMessageSent',
    'onConversationDestroyed'
];

$configurationReplayAfter = 7;

$conversationsV1WebhookApi = $client->getConversationsV1WebhookApi();
$apiResponse = $conversationsV1WebhookApi->createServiceConversationScopedWebhook(
    $chatServiceSid,
    $conversationSid,
    $target,
    $configurationUrl,
    $configurationMethod,
    $configurationFilters,
    null,
    null,
    $configurationReplayAfter
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceConversationScopedWebhook:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# List Service Conversation Scoped Webhook

Retrieve a list of all webhooks scoped to the conversation

```php
function listServiceConversationScopedWebhook(
    string $chatServiceSid,
    string $conversationSid,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 5, and the maximum is 5.<br><br>**Constraints**: `>= 1`, `<= 5` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListServiceConversationScopedWebhookResponse`](../../doc/models/list-service-conversation-scoped-webhook-response.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$conversationsV1WebhookApi = $client->getConversationsV1WebhookApi();
$apiResponse = $conversationsV1WebhookApi->listServiceConversationScopedWebhook(
    $chatServiceSid,
    $conversationSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListServiceConversationScopedWebhookResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Update Service Conversation Scoped Webhook

Update an existing conversation-scoped webhook

```php
function updateServiceConversationScopedWebhook(
    string $chatServiceSid,
    string $conversationSid,
    string $sid,
    ?string $configurationUrl = null,
    ?string $configurationMethod = null,
    ?array $configurationFilters = null,
    ?array $configurationTriggers = null,
    ?string $configurationFlowSid = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |
| `configurationUrl` | `?string` | Form, Optional | The absolute url the webhook request should be sent to. |
| `configurationMethod` | [`?string(ServiceConversationScopedWebhookMethod)`](../../doc/models/service-conversation-scoped-webhook-method.md) | Form, Optional | - |
| `configurationFilters` | `?(string[])` | Form, Optional | The list of events, firing webhook event for this Conversation. |
| `configurationTriggers` | `?(string[])` | Form, Optional | The list of keywords, firing webhook event for this Conversation. |
| `configurationFlowSid` | `?string` | Form, Optional | The studio flow SID, where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceConversationScopedWebhook`](../../doc/models/service-conversation-scoped-webhook.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$configurationUrl = 'https://example.com';

$configurationMethod = ServiceConversationScopedWebhookMethod::POST;

$configurationTriggers = [
    'keyword1',
    'keyword2'
];

$conversationsV1WebhookApi = $client->getConversationsV1WebhookApi();
$apiResponse = $conversationsV1WebhookApi->updateServiceConversationScopedWebhook(
    $chatServiceSid,
    $conversationSid,
    $sid,
    $configurationUrl,
    $configurationMethod,
    null,
    $configurationTriggers
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceConversationScopedWebhook:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete Service Conversation Scoped Webhook

Remove an existing webhook scoped to the conversation

```php
function deleteServiceConversationScopedWebhook(
    string $chatServiceSid,
    string $conversationSid,
    string $sid
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$conversationsV1WebhookApi = $client->getConversationsV1WebhookApi();
$apiResponse = $conversationsV1WebhookApi->deleteServiceConversationScopedWebhook(
    $chatServiceSid,
    $conversationSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'void:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Fetch Service Conversation Scoped Webhook

Fetch the configuration of a conversation-scoped webhook

```php
function fetchServiceConversationScopedWebhook(
    string $chatServiceSid,
    string $conversationSid,
    string $sid
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this webhook. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WH[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceConversationScopedWebhook`](../../doc/models/service-conversation-scoped-webhook.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$conversationsV1WebhookApi = $client->getConversationsV1WebhookApi();
$apiResponse = $conversationsV1WebhookApi->fetchServiceConversationScopedWebhook(
    $chatServiceSid,
    $conversationSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceConversationScopedWebhook:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Update Service Webhook Configuration

Update a specific Webhook.

```php
function updateServiceWebhookConfiguration(
    string $chatServiceSid,
    ?string $preWebhookUrl = null,
    ?string $postWebhookUrl = null,
    ?array $filters = null,
    ?string $method = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The unique ID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `preWebhookUrl` | `?string` | Form, Optional | The absolute url the pre-event webhook request should be sent to. |
| `postWebhookUrl` | `?string` | Form, Optional | The absolute url the post-event webhook request should be sent to. |
| `filters` | `?(string[])` | Form, Optional | The list of events that your configured webhook targets will receive. Events not configured here will not fire. Possible values are `onParticipantAdd`, `onParticipantAdded`, `onDeliveryUpdated`, `onConversationUpdated`, `onConversationRemove`, `onParticipantRemove`, `onConversationUpdate`, `onMessageAdd`, `onMessageRemoved`, `onParticipantUpdated`, `onConversationAdded`, `onMessageAdded`, `onConversationAdd`, `onConversationRemoved`, `onParticipantUpdate`, `onMessageRemove`, `onMessageUpdated`, `onParticipantRemoved`, `onMessageUpdate` or `onConversationStateUpdated`. |
| `method` | `?string` | Form, Optional | The HTTP method to be used when sending a webhook request. One of `GET` or `POST`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceWebhookConfiguration`](../../doc/models/service-webhook-configuration.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$preWebhookUrl = 'https://www.example.com/pre';

$postWebhookUrl = 'https://www.example.com/post';

$filters = [
    'onMessageRemoved',
    'onParticipantAdded'
];

$method = 'GET';

$conversationsV1WebhookApi = $client->getConversationsV1WebhookApi();
$apiResponse = $conversationsV1WebhookApi->updateServiceWebhookConfiguration(
    $chatServiceSid,
    $preWebhookUrl,
    $postWebhookUrl,
    $filters,
    $method
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceWebhookConfiguration:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "pre_webhook_url": "https://www.example.com/pre",
  "post_webhook_url": "https://www.example.com/post",
  "filters": [
    "onMessageRemoved",
    "onParticipantAdded"
  ],
  "method": "GET",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Webhooks"
}
```


# Fetch Service Webhook Configuration

Fetch a specific service webhook configuration.

```php
function fetchServiceWebhookConfiguration(string $chatServiceSid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The unique ID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceWebhookConfiguration`](../../doc/models/service-webhook-configuration.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationsV1WebhookApi = $client->getConversationsV1WebhookApi();
$apiResponse = $conversationsV1WebhookApi->fetchServiceWebhookConfiguration($chatServiceSid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceWebhookConfiguration:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "pre_webhook_url": "https://www.example.com/pre",
  "post_webhook_url": "https://www.example.com/post",
  "filters": [
    "onMessageRemove",
    "onParticipantAdd"
  ],
  "method": "POST",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Webhooks"
}
```

