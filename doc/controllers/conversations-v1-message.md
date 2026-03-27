# Conversations V1 Message

```php
$conversationsV1MessageApi = $client->getConversationsV1MessageApi();
```

## Class Name

`ConversationsV1MessageApi`

## Methods

* [Create Conversation Message](../../doc/controllers/conversations-v1-message.md#create-conversation-message)
* [List Conversation Message](../../doc/controllers/conversations-v1-message.md#list-conversation-message)
* [Update Conversation Message](../../doc/controllers/conversations-v1-message.md#update-conversation-message)
* [Delete Conversation Message](../../doc/controllers/conversations-v1-message.md#delete-conversation-message)
* [Fetch Conversation Message](../../doc/controllers/conversations-v1-message.md#fetch-conversation-message)
* [Create Service Conversation Message](../../doc/controllers/conversations-v1-message.md#create-service-conversation-message)
* [List Service Conversation Message](../../doc/controllers/conversations-v1-message.md#list-service-conversation-message)
* [Update Service Conversation Message](../../doc/controllers/conversations-v1-message.md#update-service-conversation-message)
* [Delete Service Conversation Message](../../doc/controllers/conversations-v1-message.md#delete-service-conversation-message)
* [Fetch Service Conversation Message](../../doc/controllers/conversations-v1-message.md#fetch-service-conversation-message)


# Create Conversation Message

Add a new message to the conversation

```php
function createConversationMessage(
    string $conversationSid,
    ?string $xTwilioWebhookEnabled = null,
    ?string $author = null,
    ?string $body = null,
    ?\DateTime $dateCreated = null,
    ?\DateTime $dateUpdated = null,
    ?string $attributes = null,
    ?string $mediaSid = null,
    ?string $contentSid = null,
    ?string $contentVariables = null,
    ?string $subject = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `author` | `?string` | Form, Optional | The channel specific identifier of the message's author. Defaults to `system`. |
| `body` | `?string` | Form, Optional | The content of the message, can be up to 1,600 characters long. |
| `dateCreated` | `?DateTime` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `?DateTime` | Form, Optional | The date that this resource was last updated. `null` if the message has not been edited. |
| `attributes` | `?string` | Form, Optional | A string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `mediaSid` | `?string` | Form, Optional | The Media SID to be attached to the new Message.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^ME[0-9a-fA-F]{32}$` |
| `contentSid` | `?string` | Form, Optional | The unique ID of the multi-channel [Rich Content](https://www.twilio.com/docs/content) template, required for template-generated messages.  **Note** that if this field is set, `Body` and `MediaSid` parameters are ignored.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^HX[0-9a-fA-F]{32}$` |
| `contentVariables` | `?string` | Form, Optional | A structurally valid JSON string that contains values to resolve Rich Content template variables. |
| `subject` | `?string` | Form, Optional | The subject of the message, can be up to 256 characters long. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ConversationMessage`](../../doc/models/conversation-message.md).

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$author = 'message author';

$body = 'Hello';

$dateCreated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:37');

$dateUpdated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:38');

$attributes = '{ "importance": "high" }';

$mediaSid = 'MEaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$contentSid = 'HXaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$contentVariables = '{"name": "John"}';

$subject = 'message subject';

$conversationsV1MessageApi = $client->getConversationsV1MessageApi();
$apiResponse = $conversationsV1MessageApi->createConversationMessage(
    $conversationSid,
    null,
    $author,
    $body,
    $dateCreated,
    $dateUpdated,
    $attributes,
    $mediaSid,
    $contentSid,
    $contentVariables,
    $subject
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ConversationMessage:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# List Conversation Message

Retrieve a list of all messages in the conversation

```php
function listConversationMessage(
    string $conversationSid,
    ?string $order = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for messages. |
| `order` | [`?string(ConversationMessageOrderType)`](../../doc/models/conversation-message-order-type.md) | Query, Optional | The sort order of the returned messages. Can be: `asc` (ascending) or `desc` (descending), with `asc` as the default. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListConversationMessageResponse`](../../doc/models/list-conversation-message-response.md).

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$order = ConversationMessageOrderType::DESC;

$conversationsV1MessageApi = $client->getConversationsV1MessageApi();
$apiResponse = $conversationsV1MessageApi->listConversationMessage(
    $conversationSid,
    $order
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListConversationMessageResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Update Conversation Message

Update an existing message in the conversation

```php
function updateConversationMessage(
    string $conversationSid,
    string $sid,
    ?string $xTwilioWebhookEnabled = null,
    ?string $author = null,
    ?string $body = null,
    ?\DateTime $dateCreated = null,
    ?\DateTime $dateUpdated = null,
    ?string $attributes = null,
    ?string $subject = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `author` | `?string` | Form, Optional | The channel specific identifier of the message's author. Defaults to `system`. |
| `body` | `?string` | Form, Optional | The content of the message, can be up to 1,600 characters long. |
| `dateCreated` | `?DateTime` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `?DateTime` | Form, Optional | The date that this resource was last updated. `null` if the message has not been edited. |
| `attributes` | `?string` | Form, Optional | A string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `subject` | `?string` | Form, Optional | The subject of the message, can be up to 256 characters long. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ConversationMessage`](../../doc/models/conversation-message.md).

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$author = 'message author';

$body = 'Hello';

$dateCreated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:37');

$dateUpdated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:38');

$attributes = '{ "importance": "high" }';

$conversationsV1MessageApi = $client->getConversationsV1MessageApi();
$apiResponse = $conversationsV1MessageApi->updateConversationMessage(
    $conversationSid,
    $sid,
    null,
    $author,
    $body,
    $dateCreated,
    $dateUpdated,
    $attributes
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ConversationMessage:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete Conversation Message

Remove a message from the conversation

```php
function deleteConversationMessage(
    string $conversationSid,
    string $sid,
    ?string $xTwilioWebhookEnabled = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$conversationsV1MessageApi = $client->getConversationsV1MessageApi();
$apiResponse = $conversationsV1MessageApi->deleteConversationMessage(
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


# Fetch Conversation Message

Fetch a message from the conversation

```php
function fetchConversationMessage(string $conversationSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ConversationMessage`](../../doc/models/conversation-message.md).

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$conversationsV1MessageApi = $client->getConversationsV1MessageApi();
$apiResponse = $conversationsV1MessageApi->fetchConversationMessage(
    $conversationSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ConversationMessage:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Create Service Conversation Message

Add a new message to the conversation in a specific service

```php
function createServiceConversationMessage(
    string $chatServiceSid,
    string $conversationSid,
    ?string $xTwilioWebhookEnabled = null,
    ?string $author = null,
    ?string $body = null,
    ?\DateTime $dateCreated = null,
    ?\DateTime $dateUpdated = null,
    ?string $attributes = null,
    ?string $mediaSid = null,
    ?string $contentSid = null,
    ?string $contentVariables = null,
    ?string $subject = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `author` | `?string` | Form, Optional | The channel specific identifier of the message's author. Defaults to `system`. |
| `body` | `?string` | Form, Optional | The content of the message, can be up to 1,600 characters long. |
| `dateCreated` | `?DateTime` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `?DateTime` | Form, Optional | The date that this resource was last updated. `null` if the message has not been edited. |
| `attributes` | `?string` | Form, Optional | A string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `mediaSid` | `?string` | Form, Optional | The Media SID to be attached to the new Message.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^ME[0-9a-fA-F]{32}$` |
| `contentSid` | `?string` | Form, Optional | The unique ID of the multi-channel [Rich Content](https://www.twilio.com/docs/content) template, required for template-generated messages.  **Note** that if this field is set, `Body` and `MediaSid` parameters are ignored.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^HX[0-9a-fA-F]{32}$` |
| `contentVariables` | `?string` | Form, Optional | A structurally valid JSON string that contains values to resolve Rich Content template variables. |
| `subject` | `?string` | Form, Optional | The subject of the message, can be up to 256 characters long. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceConversationMessage`](../../doc/models/service-conversation-message.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$author = 'message author';

$body = 'Hello';

$dateCreated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:37');

$dateUpdated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:38');

$attributes = '{ "importance": "high" }';

$mediaSid = 'MEaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$contentSid = 'HXaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$contentVariables = '{"name": "John"}';

$subject = 'message subject';

$conversationsV1MessageApi = $client->getConversationsV1MessageApi();
$apiResponse = $conversationsV1MessageApi->createServiceConversationMessage(
    $chatServiceSid,
    $conversationSid,
    null,
    $author,
    $body,
    $dateCreated,
    $dateUpdated,
    $attributes,
    $mediaSid,
    $contentSid,
    $contentVariables,
    $subject
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceConversationMessage:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# List Service Conversation Message

Retrieve a list of all messages in the conversation

```php
function listServiceConversationMessage(
    string $chatServiceSid,
    string $conversationSid,
    ?string $order = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for messages. |
| `order` | [`?string(ServiceConversationMessageOrderType)`](../../doc/models/service-conversation-message-order-type.md) | Query, Optional | The sort order of the returned messages. Can be: `asc` (ascending) or `desc` (descending), with `asc` as the default. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListServiceConversationMessageResponse`](../../doc/models/list-service-conversation-message-response.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$order = ServiceConversationMessageOrderType::DESC;

$conversationsV1MessageApi = $client->getConversationsV1MessageApi();
$apiResponse = $conversationsV1MessageApi->listServiceConversationMessage(
    $chatServiceSid,
    $conversationSid,
    $order
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListServiceConversationMessageResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Update Service Conversation Message

Update an existing message in the conversation

```php
function updateServiceConversationMessage(
    string $chatServiceSid,
    string $conversationSid,
    string $sid,
    ?string $xTwilioWebhookEnabled = null,
    ?string $author = null,
    ?string $body = null,
    ?\DateTime $dateCreated = null,
    ?\DateTime $dateUpdated = null,
    ?string $attributes = null,
    ?string $subject = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `author` | `?string` | Form, Optional | The channel specific identifier of the message's author. Defaults to `system`. |
| `body` | `?string` | Form, Optional | The content of the message, can be up to 1,600 characters long. |
| `dateCreated` | `?DateTime` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `?DateTime` | Form, Optional | The date that this resource was last updated. `null` if the message has not been edited. |
| `attributes` | `?string` | Form, Optional | A string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `subject` | `?string` | Form, Optional | The subject of the message, can be up to 256 characters long. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceConversationMessage`](../../doc/models/service-conversation-message.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$author = 'message author';

$body = 'Hello';

$dateCreated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:37');

$dateUpdated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:38');

$attributes = '{ "importance": "high" }';

$conversationsV1MessageApi = $client->getConversationsV1MessageApi();
$apiResponse = $conversationsV1MessageApi->updateServiceConversationMessage(
    $chatServiceSid,
    $conversationSid,
    $sid,
    null,
    $author,
    $body,
    $dateCreated,
    $dateUpdated,
    $attributes
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceConversationMessage:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete Service Conversation Message

Remove a message from the conversation

```php
function deleteServiceConversationMessage(
    string $chatServiceSid,
    string $conversationSid,
    string $sid,
    ?string $xTwilioWebhookEnabled = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$conversationsV1MessageApi = $client->getConversationsV1MessageApi();
$apiResponse = $conversationsV1MessageApi->deleteServiceConversationMessage(
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


# Fetch Service Conversation Message

Fetch a message from the conversation

```php
function fetchServiceConversationMessage(
    string $chatServiceSid,
    string $conversationSid,
    string $sid
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceConversationMessage`](../../doc/models/service-conversation-message.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$conversationsV1MessageApi = $client->getConversationsV1MessageApi();
$apiResponse = $conversationsV1MessageApi->fetchServiceConversationMessage(
    $chatServiceSid,
    $conversationSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceConversationMessage:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

