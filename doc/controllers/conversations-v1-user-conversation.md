# Conversations V1 User Conversation

```php
$conversationsV1UserConversationApi = $client->getConversationsV1UserConversationApi();
```

## Class Name

`ConversationsV1UserConversationApi`

## Methods

* [Update Service User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#update-service-user-conversation)
* [Delete Service User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#delete-service-user-conversation)
* [Fetch Service User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#fetch-service-user-conversation)
* [List Service User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#list-service-user-conversation)
* [Update User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#update-user-conversation)
* [Delete User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#delete-user-conversation)
* [Fetch User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#fetch-user-conversation)
* [List User Conversation](../../doc/controllers/conversations-v1-user-conversation.md#list-user-conversation)


# Update Service User Conversation

Update a specific User Conversation.

```php
function updateServiceUserConversation(
    string $chatServiceSid,
    string $userSid,
    string $conversationSid,
    ?string $notificationLevel = null,
    ?\DateTime $lastReadTimestamp = null,
    ?int $lastReadMessageIndex = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversationSid` | `string` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |
| `notificationLevel` | [`?string(ServiceUserConversationNotificationLevel)`](../../doc/models/service-user-conversation-notification-level.md) | Form, Optional | The Notification Level of this User Conversation. One of `default` or `muted`. |
| `lastReadTimestamp` | `?DateTime` | Form, Optional | The date of the last message read in conversation by the user, given in ISO 8601 format. |
| `lastReadMessageIndex` | `?int` | Form, Optional | The index of the last Message in the Conversation that the Participant has read. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceUserConversation`](../../doc/models/service-user-conversation.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$userSid = 'UserSid6';

$conversationSid = 'ConversationSid0';

$notificationLevel = ServiceUserConversationNotificationLevel::DEFAULT_;

$lastReadTimestamp = DateTimeHelper::fromRfc3339DateTime('07/30/2015 20:00:00');

$lastReadMessageIndex = 100;

$conversationsV1UserConversationApi = $client->getConversationsV1UserConversationApi();
$apiResponse = $conversationsV1UserConversationApi->updateServiceUserConversation(
    $chatServiceSid,
    $userSid,
    $conversationSid,
    $notificationLevel,
    $lastReadTimestamp,
    $lastReadMessageIndex
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceUserConversation:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete Service User Conversation

Delete a specific User Conversation.

```php
function deleteServiceUserConversation(
    string $chatServiceSid,
    string $userSid,
    string $conversationSid
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversationSid` | `string` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$userSid = 'UserSid6';

$conversationSid = 'ConversationSid0';

$conversationsV1UserConversationApi = $client->getConversationsV1UserConversationApi();
$apiResponse = $conversationsV1UserConversationApi->deleteServiceUserConversation(
    $chatServiceSid,
    $userSid,
    $conversationSid
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


# Fetch Service User Conversation

Fetch a specific User Conversation.

```php
function fetchServiceUserConversation(
    string $chatServiceSid,
    string $userSid,
    string $conversationSid
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversationSid` | `string` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceUserConversation`](../../doc/models/service-user-conversation.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$userSid = 'UserSid6';

$conversationSid = 'ConversationSid0';

$conversationsV1UserConversationApi = $client->getConversationsV1UserConversationApi();
$apiResponse = $conversationsV1UserConversationApi->fetchServiceUserConversation(
    $chatServiceSid,
    $userSid,
    $conversationSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceUserConversation:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# List Service User Conversation

Retrieve a list of all User Conversations for the User.

```php
function listServiceUserConversation(
    string $chatServiceSid,
    string $userSid,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Conversation resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListServiceUserConversationResponse`](../../doc/models/list-service-user-conversation-response.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$userSid = 'UserSid6';

$conversationsV1UserConversationApi = $client->getConversationsV1UserConversationApi();
$apiResponse = $conversationsV1UserConversationApi->listServiceUserConversation(
    $chatServiceSid,
    $userSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListServiceUserConversationResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "conversations": [],
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "conversations"
  }
}
```


# Update User Conversation

Update a specific User Conversation.

```php
function updateUserConversation(
    string $userSid,
    string $conversationSid,
    ?string $notificationLevel = null,
    ?\DateTime $lastReadTimestamp = null,
    ?int $lastReadMessageIndex = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversationSid` | `string` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |
| `notificationLevel` | [`?string(UserConversationNotificationLevel)`](../../doc/models/user-conversation-notification-level.md) | Form, Optional | The Notification Level of this User Conversation. One of `default` or `muted`. |
| `lastReadTimestamp` | `?DateTime` | Form, Optional | The date of the last message read in conversation by the user, given in ISO 8601 format. |
| `lastReadMessageIndex` | `?int` | Form, Optional | The index of the last Message in the Conversation that the Participant has read. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`UserConversation`](../../doc/models/user-conversation.md).

## Example Usage

```php
$userSid = 'UserSid6';

$conversationSid = 'ConversationSid0';

$notificationLevel = UserConversationNotificationLevel::DEFAULT_;

$lastReadTimestamp = DateTimeHelper::fromRfc3339DateTime('07/30/2015 20:00:00');

$lastReadMessageIndex = 100;

$conversationsV1UserConversationApi = $client->getConversationsV1UserConversationApi();
$apiResponse = $conversationsV1UserConversationApi->updateUserConversation(
    $userSid,
    $conversationSid,
    $notificationLevel,
    $lastReadTimestamp,
    $lastReadMessageIndex
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'UserConversation:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete User Conversation

Delete a specific User Conversation.

```php
function deleteUserConversation(string $userSid, string $conversationSid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversationSid` | `string` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$userSid = 'UserSid6';

$conversationSid = 'ConversationSid0';

$conversationsV1UserConversationApi = $client->getConversationsV1UserConversationApi();
$apiResponse = $conversationsV1UserConversationApi->deleteUserConversation(
    $userSid,
    $conversationSid
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


# Fetch User Conversation

Fetch a specific User Conversation.

```php
function fetchUserConversation(string $userSid, string $conversationSid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `conversationSid` | `string` | Template, Required | The unique SID identifier of the Conversation. This value can be either the `sid` or the `unique_name` of the [Conversation resource](https://www.twilio.com/docs/conversations/api/conversation-resource). |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`UserConversation`](../../doc/models/user-conversation.md).

## Example Usage

```php
$userSid = 'UserSid6';

$conversationSid = 'ConversationSid0';

$conversationsV1UserConversationApi = $client->getConversationsV1UserConversationApi();
$apiResponse = $conversationsV1UserConversationApi->fetchUserConversation(
    $userSid,
    $conversationSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'UserConversation:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# List User Conversation

Retrieve a list of all User Conversations for the User.

```php
function listUserConversation(
    string $userSid,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `userSid` | `string` | Template, Required | The unique SID identifier of the [User resource](https://www.twilio.com/docs/conversations/api/user-resource). This value can be either the `sid` or the `identity` of the User resource. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListUserConversationResponse`](../../doc/models/list-user-conversation-response.md).

## Example Usage

```php
$userSid = 'UserSid6';

$conversationsV1UserConversationApi = $client->getConversationsV1UserConversationApi();
$apiResponse = $conversationsV1UserConversationApi->listUserConversation($userSid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListUserConversationResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "conversations": [],
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "conversations"
  }
}
```

