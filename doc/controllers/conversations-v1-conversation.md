# Conversations V1 Conversation

```php
$conversationsV1ConversationApi = $client->getConversationsV1ConversationApi();
```

## Class Name

`ConversationsV1ConversationApi`

## Methods

* [Create Conversation](../../doc/controllers/conversations-v1-conversation.md#create-conversation)
* [List Conversation](../../doc/controllers/conversations-v1-conversation.md#list-conversation)
* [Update Conversation](../../doc/controllers/conversations-v1-conversation.md#update-conversation)
* [Delete Conversation](../../doc/controllers/conversations-v1-conversation.md#delete-conversation)
* [Fetch Conversation](../../doc/controllers/conversations-v1-conversation.md#fetch-conversation)
* [Create Service Conversation](../../doc/controllers/conversations-v1-conversation.md#create-service-conversation)
* [List Service Conversation](../../doc/controllers/conversations-v1-conversation.md#list-service-conversation)
* [Update Service Conversation](../../doc/controllers/conversations-v1-conversation.md#update-service-conversation)
* [Delete Service Conversation](../../doc/controllers/conversations-v1-conversation.md#delete-service-conversation)
* [Fetch Service Conversation](../../doc/controllers/conversations-v1-conversation.md#fetch-service-conversation)


# Create Conversation

Create a new conversation in your account's default service

```php
function createConversation(
    ?string $xTwilioWebhookEnabled = null,
    ?string $friendlyName = null,
    ?string $uniqueName = null,
    ?\DateTime $dateCreated = null,
    ?\DateTime $dateUpdated = null,
    ?string $messagingServiceSid = null,
    ?string $attributes = null,
    ?string $state = null,
    ?string $timersInactive = null,
    ?string $timersClosed = null,
    ?string $bindingsEmailAddress = null,
    ?string $bindingsEmailName = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `?string` | Form, Optional | The human-readable name of this conversation, limited to 256 characters. Optional. |
| `uniqueName` | `?string` | Form, Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. |
| `dateCreated` | `?DateTime` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `?DateTime` | Form, Optional | The date that this resource was last updated. |
| `messagingServiceSid` | `?string` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `attributes` | `?string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `state` | [`?string(ConversationState)`](../../doc/models/conversation-state.md) | Form, Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` |
| `timersInactive` | `?string` | Form, Optional | ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `timersClosed` | `?string` | Form, Optional | ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |
| `bindingsEmailAddress` | `?string` | Form, Optional | The default email address that will be used when sending outbound emails in this conversation. |
| `bindingsEmailName` | `?string` | Form, Optional | The default name that will be used when sending outbound emails in this conversation. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Conversation`](../../doc/models/conversation.md).

## Example Usage

```php
$friendlyName = 'friendly_name';

$uniqueName = 'unique_name';

$dateCreated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:37');

$dateUpdated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:38');

$messagingServiceSid = 'MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$attributes = '{ "topic": "feedback" }';

$state = ConversationState::INACTIVE;

$timersInactive = 'PT1M';

$timersClosed = 'PT10M';

$conversationsV1ConversationApi = $client->getConversationsV1ConversationApi();
$apiResponse = $conversationsV1ConversationApi->createConversation(
    null,
    $friendlyName,
    $uniqueName,
    $dateCreated,
    $dateUpdated,
    $messagingServiceSid,
    $attributes,
    $state,
    $timersInactive,
    $timersClosed
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Conversation:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# List Conversation

Retrieve a list of conversations in your account's default service

```php
function listConversation(
    ?string $startDate = null,
    ?string $endDate = null,
    ?string $state = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `startDate` | `?string` | Query, Optional | Specifies the beginning of the date range for filtering Conversations based on their creation date. Conversations that were created on or after this date will be included in the results. The date must be in ISO8601 format, specifically starting at the beginning of the specified date (YYYY-MM-DDT00:00:00Z), for precise filtering. This parameter can be combined with other filters. If this filter is used, the returned list is sorted by latest conversation creation date in descending order. |
| `endDate` | `?string` | Query, Optional | Defines the end of the date range for filtering conversations by their creation date. Only conversations that were created on or before this date will appear in the results.  The date must be in ISO8601 format, specifically capturing up to the end of the specified date (YYYY-MM-DDT23:59:59Z), to ensure that conversations from the entire end day are included. This parameter can be combined with other filters. If this filter is used, the returned list is sorted by latest conversation creation date in descending order. |
| `state` | [`?string(ConversationState)`](../../doc/models/conversation-state.md) | Query, Optional | State for sorting and filtering list of Conversations. Can be `active`, `inactive` or `closed` |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListConversationResponse`](../../doc/models/list-conversation-response.md).

## Example Usage

```php
$conversationsV1ConversationApi = $client->getConversationsV1ConversationApi();
$apiResponse = $conversationsV1ConversationApi->listConversation();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListConversationResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Update Conversation

Update an existing conversation in your account's default service

```php
function updateConversation(
    string $sid,
    ?string $xTwilioWebhookEnabled = null,
    ?string $friendlyName = null,
    ?\DateTime $dateCreated = null,
    ?\DateTime $dateUpdated = null,
    ?string $attributes = null,
    ?string $messagingServiceSid = null,
    ?string $state = null,
    ?string $timersInactive = null,
    ?string $timersClosed = null,
    ?string $uniqueName = null,
    ?string $bindingsEmailAddress = null,
    ?string $bindingsEmailName = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `?string` | Form, Optional | The human-readable name of this conversation, limited to 256 characters. Optional. |
| `dateCreated` | `?DateTime` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `?DateTime` | Form, Optional | The date that this resource was last updated. |
| `attributes` | `?string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `messagingServiceSid` | `?string` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `state` | [`?string(ConversationState)`](../../doc/models/conversation-state.md) | Form, Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` |
| `timersInactive` | `?string` | Form, Optional | ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `timersClosed` | `?string` | Form, Optional | ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |
| `uniqueName` | `?string` | Form, Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. |
| `bindingsEmailAddress` | `?string` | Form, Optional | The default email address that will be used when sending outbound emails in this conversation. |
| `bindingsEmailName` | `?string` | Form, Optional | The default name that will be used when sending outbound emails in this conversation. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Conversation`](../../doc/models/conversation.md).

## Example Usage

```php
$sid = 'Sid8';

$friendlyName = 'friendly_name';

$dateCreated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:37');

$dateUpdated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:38');

$attributes = '{ "topic": "feedback" }';

$messagingServiceSid = 'MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaab';

$state = ConversationState::INACTIVE;

$timersInactive = 'PT1M';

$timersClosed = 'PT10M';

$uniqueName = 'unique_name';

$conversationsV1ConversationApi = $client->getConversationsV1ConversationApi();
$apiResponse = $conversationsV1ConversationApi->updateConversation(
    $sid,
    null,
    $friendlyName,
    $dateCreated,
    $dateUpdated,
    $attributes,
    $messagingServiceSid,
    $state,
    $timersInactive,
    $timersClosed,
    $uniqueName
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Conversation:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete Conversation

Remove a conversation from your account's default service

```php
function deleteConversation(string $sid, ?string $xTwilioWebhookEnabled = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$sid = 'Sid8';

$conversationsV1ConversationApi = $client->getConversationsV1ConversationApi();
$apiResponse = $conversationsV1ConversationApi->deleteConversation($sid);

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


# Fetch Conversation

Fetch a conversation from your account's default service

```php
function fetchConversation(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Conversation`](../../doc/models/conversation.md).

## Example Usage

```php
$sid = 'Sid8';

$conversationsV1ConversationApi = $client->getConversationsV1ConversationApi();
$apiResponse = $conversationsV1ConversationApi->fetchConversation($sid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Conversation:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Create Service Conversation

Create a new conversation in your service

```php
function createServiceConversation(
    string $chatServiceSid,
    ?string $xTwilioWebhookEnabled = null,
    ?string $friendlyName = null,
    ?string $uniqueName = null,
    ?string $attributes = null,
    ?string $messagingServiceSid = null,
    ?\DateTime $dateCreated = null,
    ?\DateTime $dateUpdated = null,
    ?string $state = null,
    ?string $timersInactive = null,
    ?string $timersClosed = null,
    ?string $bindingsEmailAddress = null,
    ?string $bindingsEmailName = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `?string` | Form, Optional | The human-readable name of this conversation, limited to 256 characters. Optional. |
| `uniqueName` | `?string` | Form, Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. |
| `attributes` | `?string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `messagingServiceSid` | `?string` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `dateCreated` | `?DateTime` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `?DateTime` | Form, Optional | The date that this resource was last updated. |
| `state` | [`?string(ServiceConversationState)`](../../doc/models/service-conversation-state.md) | Form, Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` |
| `timersInactive` | `?string` | Form, Optional | ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `timersClosed` | `?string` | Form, Optional | ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |
| `bindingsEmailAddress` | `?string` | Form, Optional | The default email address that will be used when sending outbound emails in this conversation. |
| `bindingsEmailName` | `?string` | Form, Optional | The default name that will be used when sending outbound emails in this conversation. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceConversation`](../../doc/models/service-conversation.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$friendlyName = 'friendly_name';

$uniqueName = 'unique_name';

$attributes = '{ "topic": "feedback" }';

$messagingServiceSid = 'MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$dateCreated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:37');

$dateUpdated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:38');

$state = ServiceConversationState::INACTIVE;

$timersInactive = 'PT1M';

$timersClosed = 'PT10M';

$conversationsV1ConversationApi = $client->getConversationsV1ConversationApi();
$apiResponse = $conversationsV1ConversationApi->createServiceConversation(
    $chatServiceSid,
    null,
    $friendlyName,
    $uniqueName,
    $attributes,
    $messagingServiceSid,
    $dateCreated,
    $dateUpdated,
    $state,
    $timersInactive,
    $timersClosed
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceConversation:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# List Service Conversation

Retrieve a list of conversations in your service

```php
function listServiceConversation(
    string $chatServiceSid,
    ?string $startDate = null,
    ?string $endDate = null,
    ?string $state = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `startDate` | `?string` | Query, Optional | Specifies the beginning of the date range for filtering Conversations based on their creation date. Conversations that were created on or after this date will be included in the results. The date must be in ISO8601 format, specifically starting at the beginning of the specified date (YYYY-MM-DDT00:00:00Z), for precise filtering. This parameter can be combined with other filters. If this filter is used, the returned list is sorted by latest conversation creation date in descending order. |
| `endDate` | `?string` | Query, Optional | Defines the end of the date range for filtering conversations by their creation date. Only conversations that were created on or before this date will appear in the results.  The date must be in ISO8601 format, specifically capturing up to the end of the specified date (YYYY-MM-DDT23:59:59Z), to ensure that conversations from the entire end day are included. This parameter can be combined with other filters. If this filter is used, the returned list is sorted by latest conversation creation date in descending order. |
| `state` | [`?string(ServiceConversationState)`](../../doc/models/service-conversation-state.md) | Query, Optional | State for sorting and filtering list of Conversations. Can be `active`, `inactive` or `closed` |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListServiceConversationResponse`](../../doc/models/list-service-conversation-response.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationsV1ConversationApi = $client->getConversationsV1ConversationApi();
$apiResponse = $conversationsV1ConversationApi->listServiceConversation($chatServiceSid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListServiceConversationResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Update Service Conversation

Update an existing conversation in your service

```php
function updateServiceConversation(
    string $chatServiceSid,
    string $sid,
    ?string $xTwilioWebhookEnabled = null,
    ?string $friendlyName = null,
    ?\DateTime $dateCreated = null,
    ?\DateTime $dateUpdated = null,
    ?string $attributes = null,
    ?string $messagingServiceSid = null,
    ?string $state = null,
    ?string $timersInactive = null,
    ?string $timersClosed = null,
    ?string $uniqueName = null,
    ?string $bindingsEmailAddress = null,
    ?string $bindingsEmailName = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `?string` | Form, Optional | The human-readable name of this conversation, limited to 256 characters. Optional. |
| `dateCreated` | `?DateTime` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `?DateTime` | Form, Optional | The date that this resource was last updated. |
| `attributes` | `?string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `messagingServiceSid` | `?string` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this conversation belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `state` | [`?string(ServiceConversationState)`](../../doc/models/service-conversation-state.md) | Form, Optional | Current state of this conversation. Can be either `initializing`, `active`, `inactive` or `closed` and defaults to `active` |
| `timersInactive` | `?string` | Form, Optional | ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `timersClosed` | `?string` | Form, Optional | ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |
| `uniqueName` | `?string` | Form, Optional | An application-defined string that uniquely identifies the resource. It can be used to address the resource in place of the resource's `sid` in the URL. |
| `bindingsEmailAddress` | `?string` | Form, Optional | The default email address that will be used when sending outbound emails in this conversation. |
| `bindingsEmailName` | `?string` | Form, Optional | The default name that will be used when sending outbound emails in this conversation. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceConversation`](../../doc/models/service-conversation.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$sid = 'Sid8';

$friendlyName = 'friendly_name';

$dateCreated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:37');

$dateUpdated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:38');

$attributes = '{ "topic": "feedback" }';

$messagingServiceSid = 'MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaab';

$state = ServiceConversationState::INACTIVE;

$timersInactive = 'PT1M';

$timersClosed = 'PT10M';

$uniqueName = 'unique_name';

$conversationsV1ConversationApi = $client->getConversationsV1ConversationApi();
$apiResponse = $conversationsV1ConversationApi->updateServiceConversation(
    $chatServiceSid,
    $sid,
    null,
    $friendlyName,
    $dateCreated,
    $dateUpdated,
    $attributes,
    $messagingServiceSid,
    $state,
    $timersInactive,
    $timersClosed,
    $uniqueName
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceConversation:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete Service Conversation

Remove a conversation from your service

```php
function deleteServiceConversation(
    string $chatServiceSid,
    string $sid,
    ?string $xTwilioWebhookEnabled = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$sid = 'Sid8';

$conversationsV1ConversationApi = $client->getConversationsV1ConversationApi();
$apiResponse = $conversationsV1ConversationApi->deleteServiceConversation(
    $chatServiceSid,
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


# Fetch Service Conversation

Fetch a conversation from your service

```php
function fetchServiceConversation(string $chatServiceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Can also be the `unique_name` of the Conversation. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceConversation`](../../doc/models/service-conversation.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$sid = 'Sid8';

$conversationsV1ConversationApi = $client->getConversationsV1ConversationApi();
$apiResponse = $conversationsV1ConversationApi->fetchServiceConversation(
    $chatServiceSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceConversation:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

