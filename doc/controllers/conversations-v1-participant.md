# Conversations V1 Participant

```php
$conversationsV1ParticipantApi = $client->getConversationsV1ParticipantApi();
```

## Class Name

`ConversationsV1ParticipantApi`

## Methods

* [Create Conversation Participant](../../doc/controllers/conversations-v1-participant.md#create-conversation-participant)
* [List Conversation Participant](../../doc/controllers/conversations-v1-participant.md#list-conversation-participant)
* [Update Conversation Participant](../../doc/controllers/conversations-v1-participant.md#update-conversation-participant)
* [Delete Conversation Participant](../../doc/controllers/conversations-v1-participant.md#delete-conversation-participant)
* [Fetch Conversation Participant](../../doc/controllers/conversations-v1-participant.md#fetch-conversation-participant)
* [Create Service Conversation Participant](../../doc/controllers/conversations-v1-participant.md#create-service-conversation-participant)
* [List Service Conversation Participant](../../doc/controllers/conversations-v1-participant.md#list-service-conversation-participant)
* [Update Service Conversation Participant](../../doc/controllers/conversations-v1-participant.md#update-service-conversation-participant)
* [Delete Service Conversation Participant](../../doc/controllers/conversations-v1-participant.md#delete-service-conversation-participant)
* [Fetch Service Conversation Participant](../../doc/controllers/conversations-v1-participant.md#fetch-service-conversation-participant)


# Create Conversation Participant

Add a new participant to the conversation

```php
function createConversationParticipant(
    string $conversationSid,
    ?string $xTwilioWebhookEnabled = null,
    ?string $identity = null,
    ?string $messagingBindingAddress = null,
    ?string $messagingBindingProxyAddress = null,
    ?\DateTime $dateCreated = null,
    ?\DateTime $dateUpdated = null,
    ?string $attributes = null,
    ?string $messagingBindingProjectedAddress = null,
    ?string $roleSid = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `identity` | `?string` | Form, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the Conversations SDK to communicate. Limited to 256 characters. |
| `messagingBindingAddress` | `?string` | Form, Optional | The address of the participant's device, e.g. a phone or WhatsApp number. Together with the Proxy address, this determines a participant uniquely. This field (with proxy_address) is only null when the participant is interacting from an SDK endpoint (see the 'identity' field). |
| `messagingBindingProxyAddress` | `?string` | Form, Optional | The address of the Twilio phone number (or WhatsApp number) that the participant is in contact with. This field, together with participant address, is only null when the participant is interacting from an SDK endpoint (see the 'identity' field). |
| `dateCreated` | `?DateTime` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `?DateTime` | Form, Optional | The date that this resource was last updated. |
| `attributes` | `?string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `messagingBindingProjectedAddress` | `?string` | Form, Optional | The address of the Twilio phone number that is used in Group MMS. Communication mask for the Conversation participant with Identity. |
| `roleSid` | `?string` | Form, Optional | The SID of a conversation-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ConversationParticipant`](../../doc/models/conversation-participant.md).

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$identity = 'IDENTITY';

$messagingBindingAddress = '+15558675310';

$messagingBindingProxyAddress = '+15017122661';

$dateCreated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:37');

$dateUpdated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:38');

$attributes = '{ "role": "driver" }';

$messagingBindingProjectedAddress = '+15017122661';

$roleSid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$conversationsV1ParticipantApi = $client->getConversationsV1ParticipantApi();
$apiResponse = $conversationsV1ParticipantApi->createConversationParticipant(
    $conversationSid,
    null,
    $identity,
    $messagingBindingAddress,
    $messagingBindingProxyAddress,
    $dateCreated,
    $dateUpdated,
    $attributes,
    $messagingBindingProjectedAddress,
    $roleSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ConversationParticipant:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# List Conversation Participant

Retrieve a list of all participants of the conversation

```php
function listConversationParticipant(
    string $conversationSid,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for participants. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListConversationParticipantResponse`](../../doc/models/list-conversation-participant-response.md).

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$conversationsV1ParticipantApi = $client->getConversationsV1ParticipantApi();
$apiResponse = $conversationsV1ParticipantApi->listConversationParticipant($conversationSid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListConversationParticipantResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Update Conversation Participant

Update an existing participant in the conversation

```php
function updateConversationParticipant(
    string $conversationSid,
    string $sid,
    ?string $xTwilioWebhookEnabled = null,
    ?\DateTime $dateCreated = null,
    ?\DateTime $dateUpdated = null,
    ?string $attributes = null,
    ?string $roleSid = null,
    ?string $messagingBindingProxyAddress = null,
    ?string $messagingBindingProjectedAddress = null,
    ?string $identity = null,
    ?int $lastReadMessageIndex = null,
    ?string $lastReadTimestamp = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `dateCreated` | `?DateTime` | Form, Optional | The date that this resource was created. |
| `dateUpdated` | `?DateTime` | Form, Optional | The date that this resource was last updated. |
| `attributes` | `?string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set "{}" will be returned. |
| `roleSid` | `?string` | Form, Optional | The SID of a conversation-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `messagingBindingProxyAddress` | `?string` | Form, Optional | The address of the Twilio phone number that the participant is in contact with. 'null' value will remove it. |
| `messagingBindingProjectedAddress` | `?string` | Form, Optional | The address of the Twilio phone number that is used in Group MMS. 'null' value will remove it. |
| `identity` | `?string` | Form, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the Conversations SDK to communicate. Limited to 256 characters. |
| `lastReadMessageIndex` | `?int` | Form, Optional | Index of last “read” message in the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for the Participant. |
| `lastReadTimestamp` | `?string` | Form, Optional | Timestamp of last “read” message in the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for the Participant. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ConversationParticipant`](../../doc/models/conversation-participant.md).

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$dateCreated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:37');

$dateUpdated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:38');

$attributes = '{ "role": "driver" }';

$roleSid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$messagingBindingProjectedAddress = '+15017122661';

$conversationsV1ParticipantApi = $client->getConversationsV1ParticipantApi();
$apiResponse = $conversationsV1ParticipantApi->updateConversationParticipant(
    $conversationSid,
    $sid,
    null,
    $dateCreated,
    $dateUpdated,
    $attributes,
    $roleSid,
    null,
    $messagingBindingProjectedAddress
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ConversationParticipant:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete Conversation Participant

Remove a participant from the conversation

```php
function deleteConversationParticipant(
    string $conversationSid,
    string $sid,
    ?string $xTwilioWebhookEnabled = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$conversationsV1ParticipantApi = $client->getConversationsV1ParticipantApi();
$apiResponse = $conversationsV1ParticipantApi->deleteConversationParticipant(
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


# Fetch Conversation Participant

Fetch a participant of the conversation

```php
function fetchConversationParticipant(string $conversationSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Alternatively, you can pass a Participant's `identity` rather than the SID. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ConversationParticipant`](../../doc/models/conversation-participant.md).

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$conversationsV1ParticipantApi = $client->getConversationsV1ParticipantApi();
$apiResponse = $conversationsV1ParticipantApi->fetchConversationParticipant(
    $conversationSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ConversationParticipant:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Create Service Conversation Participant

Add a new participant to the conversation in a specific service

```php
function createServiceConversationParticipant(
    string $chatServiceSid,
    string $conversationSid,
    ?string $xTwilioWebhookEnabled = null,
    ?string $identity = null,
    ?string $messagingBindingAddress = null,
    ?string $messagingBindingProxyAddress = null,
    ?\DateTime $dateCreated = null,
    ?\DateTime $dateUpdated = null,
    ?string $attributes = null,
    ?string $messagingBindingProjectedAddress = null,
    ?string $roleSid = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `identity` | `?string` | Form, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the [Conversation SDK](https://www.twilio.com/docs/conversations/sdk-overview) to communicate. Limited to 256 characters. |
| `messagingBindingAddress` | `?string` | Form, Optional | The address of the participant's device, e.g. a phone or WhatsApp number. Together with the Proxy address, this determines a participant uniquely. This field (with `proxy_address`) is only null when the participant is interacting from an SDK endpoint (see the `identity` field). |
| `messagingBindingProxyAddress` | `?string` | Form, Optional | The address of the Twilio phone number (or WhatsApp number) that the participant is in contact with. This field, together with participant address, is only null when the participant is interacting from an SDK endpoint (see the `identity` field). |
| `dateCreated` | `?DateTime` | Form, Optional | The date on which this resource was created. |
| `dateUpdated` | `?DateTime` | Form, Optional | The date on which this resource was last updated. |
| `attributes` | `?string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set `{}` will be returned. |
| `messagingBindingProjectedAddress` | `?string` | Form, Optional | The address of the Twilio phone number that is used in Group MMS. |
| `roleSid` | `?string` | Form, Optional | The SID of a conversation-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceConversationParticipant`](../../doc/models/service-conversation-participant.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$identity = 'IDENTITY';

$messagingBindingAddress = '+15558675310';

$messagingBindingProxyAddress = '+15017122661';

$dateCreated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:37');

$dateUpdated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:38');

$attributes = '{ "role": "driver" }';

$messagingBindingProjectedAddress = '+15017122661';

$roleSid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$conversationsV1ParticipantApi = $client->getConversationsV1ParticipantApi();
$apiResponse = $conversationsV1ParticipantApi->createServiceConversationParticipant(
    $chatServiceSid,
    $conversationSid,
    null,
    $identity,
    $messagingBindingAddress,
    $messagingBindingProxyAddress,
    $dateCreated,
    $dateUpdated,
    $attributes,
    $messagingBindingProjectedAddress,
    $roleSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceConversationParticipant:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# List Service Conversation Participant

Retrieve a list of all participants of the conversation

```php
function listServiceConversationParticipant(
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
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for participants. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListServiceConversationParticipantResponse`](../../doc/models/list-service-conversation-participant-response.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$conversationsV1ParticipantApi = $client->getConversationsV1ParticipantApi();
$apiResponse = $conversationsV1ParticipantApi->listServiceConversationParticipant(
    $chatServiceSid,
    $conversationSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListServiceConversationParticipantResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Update Service Conversation Participant

Update an existing participant in the conversation

```php
function updateServiceConversationParticipant(
    string $chatServiceSid,
    string $conversationSid,
    string $sid,
    ?string $xTwilioWebhookEnabled = null,
    ?\DateTime $dateCreated = null,
    ?\DateTime $dateUpdated = null,
    ?string $identity = null,
    ?string $attributes = null,
    ?string $roleSid = null,
    ?string $messagingBindingProxyAddress = null,
    ?string $messagingBindingProjectedAddress = null,
    ?int $lastReadMessageIndex = null,
    ?string $lastReadTimestamp = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `dateCreated` | `?DateTime` | Form, Optional | The date on which this resource was created. |
| `dateUpdated` | `?DateTime` | Form, Optional | The date on which this resource was last updated. |
| `identity` | `?string` | Form, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the [Conversation SDK](https://www.twilio.com/docs/conversations/sdk-overview) to communicate. Limited to 256 characters. |
| `attributes` | `?string` | Form, Optional | An optional string metadata field you can use to store any data you wish. The string value must contain structurally valid JSON if specified.  **Note** that if the attributes are not set `{}` will be returned. |
| `roleSid` | `?string` | Form, Optional | The SID of a conversation-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the participant.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `messagingBindingProxyAddress` | `?string` | Form, Optional | The address of the Twilio phone number that the participant is in contact with. 'null' value will remove it. |
| `messagingBindingProjectedAddress` | `?string` | Form, Optional | The address of the Twilio phone number that is used in Group MMS. 'null' value will remove it. |
| `lastReadMessageIndex` | `?int` | Form, Optional | Index of last “read” message in the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for the Participant. |
| `lastReadTimestamp` | `?string` | Form, Optional | Timestamp of last “read” message in the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for the Participant. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceConversationParticipant`](../../doc/models/service-conversation-participant.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$dateCreated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:37');

$dateUpdated = DateTimeHelper::fromRfc3339DateTime('12/16/2015 22:18:38');

$attributes = '{ "role": "driver" }';

$roleSid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$messagingBindingProjectedAddress = '+15017122661';

$conversationsV1ParticipantApi = $client->getConversationsV1ParticipantApi();
$apiResponse = $conversationsV1ParticipantApi->updateServiceConversationParticipant(
    $chatServiceSid,
    $conversationSid,
    $sid,
    null,
    $dateCreated,
    $dateUpdated,
    null,
    $attributes,
    $roleSid,
    null,
    $messagingBindingProjectedAddress
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceConversationParticipant:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete Service Conversation Participant

Remove a participant from the conversation

```php
function deleteServiceConversationParticipant(
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
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$conversationsV1ParticipantApi = $client->getConversationsV1ParticipantApi();
$apiResponse = $conversationsV1ParticipantApi->deleteServiceConversationParticipant(
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


# Fetch Service Conversation Participant

Fetch a participant of the conversation

```php
function fetchServiceConversationParticipant(
    string $chatServiceSid,
    string $conversationSid,
    string $sid
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this participant. |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource. Alternatively, you can pass a Participant's `identity` rather than the SID. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceConversationParticipant`](../../doc/models/service-conversation-participant.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$sid = 'Sid8';

$conversationsV1ParticipantApi = $client->getConversationsV1ParticipantApi();
$apiResponse = $conversationsV1ParticipantApi->fetchServiceConversationParticipant(
    $chatServiceSid,
    $conversationSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceConversationParticipant:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

