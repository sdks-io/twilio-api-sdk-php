# Conversations V1 User

```php
$conversationsV1UserApi = $client->getConversationsV1UserApi();
```

## Class Name

`ConversationsV1UserApi`

## Methods

* [Create Service User](../../doc/controllers/conversations-v1-user.md#create-service-user)
* [List Service User](../../doc/controllers/conversations-v1-user.md#list-service-user)
* [Update Service User](../../doc/controllers/conversations-v1-user.md#update-service-user)
* [Delete Service User](../../doc/controllers/conversations-v1-user.md#delete-service-user)
* [Fetch Service User](../../doc/controllers/conversations-v1-user.md#fetch-service-user)
* [Create User](../../doc/controllers/conversations-v1-user.md#create-user)
* [List User](../../doc/controllers/conversations-v1-user.md#list-user)
* [Update User](../../doc/controllers/conversations-v1-user.md#update-user)
* [Delete User](../../doc/controllers/conversations-v1-user.md#delete-user)
* [Fetch User](../../doc/controllers/conversations-v1-user.md#fetch-user)


# Create Service User

Add a new conversation user to your service

```php
function createServiceUser(
    string $chatServiceSid,
    string $identity,
    ?string $xTwilioWebhookEnabled = null,
    ?string $friendlyName = null,
    ?string $attributes = null,
    ?string $roleSid = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the User resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `identity` | `string` | Form, Required | The application-defined string that uniquely identifies the resource's User within the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource). This value is often a username or an email address, and is case-sensitive. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `?string` | Form, Optional | The string that you assigned to describe the resource. |
| `attributes` | `?string` | Form, Optional | The JSON Object string that stores application-specific data. If attributes have not been set, `{}` is returned. |
| `roleSid` | `?string` | Form, Optional | The SID of a service-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the user.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceUser`](../../doc/models/service-user.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$identity = 'admin';

$friendlyName = 'name';

$attributes = '{ "duty": "tech" }';

$roleSid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$conversationsV1UserApi = $client->getConversationsV1UserApi();
$apiResponse = $conversationsV1UserApi->createServiceUser(
    $chatServiceSid,
    $identity,
    null,
    $friendlyName,
    $attributes,
    $roleSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceUser:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "identity": "admin",
  "friendly_name": "name",
  "attributes": "{ \"duty\": \"tech\" }",
  "is_online": true,
  "is_notifiable": null,
  "date_created": "2019-12-16T22:18:37Z",
  "date_updated": "2019-12-16T22:18:38Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "user_conversations": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
  }
}
```


# List Service User

Retrieve a list of all conversation users in your service

```php
function listServiceUser(
    string $chatServiceSid,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to read the User resources from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListServiceUserResponse`](../../doc/models/list-service-user-response.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationsV1UserApi = $client->getConversationsV1UserApi();
$apiResponse = $conversationsV1UserApi->listServiceUser($chatServiceSid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListServiceUserResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "users"
  },
  "users": [
    {
      "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "identity": "admin",
      "friendly_name": "name",
      "attributes": "{ \"duty\": \"tech\" }",
      "is_online": true,
      "is_notifiable": null,
      "date_created": "2019-12-16T22:18:37Z",
      "date_updated": "2019-12-16T22:18:38Z",
      "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "links": {
        "user_conversations": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
      }
    },
    {
      "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "identity": "agent0034",
      "friendly_name": "John from customs",
      "attributes": "{ \"duty\": \"agent\" }",
      "is_online": false,
      "is_notifiable": null,
      "date_created": "2020-03-24T20:38:21Z",
      "date_updated": "2020-03-24T20:38:21Z",
      "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "links": {
        "user_conversations": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
      }
    }
  ]
}
```


# Update Service User

Update an existing conversation user in your service

```php
function updateServiceUser(
    string $chatServiceSid,
    string $sid,
    ?string $xTwilioWebhookEnabled = null,
    ?string $friendlyName = null,
    ?string $attributes = null,
    ?string $roleSid = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the User resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the User resource to update. This value can be either the `sid` or the `identity` of the User resource to update. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `?string` | Form, Optional | The string that you assigned to describe the resource. |
| `attributes` | `?string` | Form, Optional | The JSON Object string that stores application-specific data. If attributes have not been set, `{}` is returned. |
| `roleSid` | `?string` | Form, Optional | The SID of a service-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the user.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceUser`](../../doc/models/service-user.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$sid = 'Sid8';

$friendlyName = 'new name';

$attributes = '{ "duty": "tech", "team": "internals" }';

$roleSid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$conversationsV1UserApi = $client->getConversationsV1UserApi();
$apiResponse = $conversationsV1UserApi->updateServiceUser(
    $chatServiceSid,
    $sid,
    null,
    $friendlyName,
    $attributes,
    $roleSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceUser:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "identity": "admin",
  "friendly_name": "new name",
  "attributes": "{ \"duty\": \"tech\", \"team\": \"internals\" }",
  "is_online": true,
  "is_notifiable": null,
  "date_created": "2019-12-16T22:18:37Z",
  "date_updated": "2019-12-16T22:18:38Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "user_conversations": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
  }
}
```


# Delete Service User

Remove a conversation user from your service

```php
function deleteServiceUser(
    string $chatServiceSid,
    string $sid,
    ?string $xTwilioWebhookEnabled = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to delete the User resource from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the User resource to delete. This value can be either the `sid` or the `identity` of the User resource to delete. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$sid = 'Sid8';

$conversationsV1UserApi = $client->getConversationsV1UserApi();
$apiResponse = $conversationsV1UserApi->deleteServiceUser(
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


# Fetch Service User

Fetch a conversation user from your service

```php
function fetchServiceUser(string $chatServiceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to fetch the User resource from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the User resource to fetch. This value can be either the `sid` or the `identity` of the User resource to fetch. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceUser`](../../doc/models/service-user.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$sid = 'Sid8';

$conversationsV1UserApi = $client->getConversationsV1UserApi();
$apiResponse = $conversationsV1UserApi->fetchServiceUser(
    $chatServiceSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceUser:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "identity": "admin",
  "friendly_name": "name",
  "attributes": "{ \"duty\": \"tech\" }",
  "is_online": true,
  "is_notifiable": null,
  "date_created": "2019-12-16T22:18:37Z",
  "date_updated": "2019-12-16T22:18:38Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "user_conversations": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
  }
}
```


# Create User

Add a new conversation user to your account's default service

```php
function createUser(
    string $identity,
    ?string $xTwilioWebhookEnabled = null,
    ?string $friendlyName = null,
    ?string $attributes = null,
    ?string $roleSid = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `identity` | `string` | Form, Required | The application-defined string that uniquely identifies the resource's User within the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource). This value is often a username or an email address, and is case-sensitive. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `?string` | Form, Optional | The string that you assigned to describe the resource. |
| `attributes` | `?string` | Form, Optional | The JSON Object string that stores application-specific data. If attributes have not been set, `{}` is returned. |
| `roleSid` | `?string` | Form, Optional | The SID of a service-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the user.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`User`](../../doc/models/user.md).

## Example Usage

```php
$identity = 'admin';

$friendlyName = 'name';

$attributes = '{ "duty": "tech" }';

$roleSid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$conversationsV1UserApi = $client->getConversationsV1UserApi();
$apiResponse = $conversationsV1UserApi->createUser(
    $identity,
    null,
    $friendlyName,
    $attributes,
    $roleSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'User:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "identity": "admin",
  "friendly_name": "name",
  "attributes": "{ \"duty\": \"tech\" }",
  "is_online": true,
  "is_notifiable": null,
  "date_created": "2019-12-16T22:18:37Z",
  "date_updated": "2019-12-16T22:18:38Z",
  "url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "user_conversations": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
  }
}
```


# List User

Retrieve a list of all conversation users in your account's default service

```php
function listUser(?int $pageSize = null, ?int $page = null, ?string $pageToken = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListUserResponse`](../../doc/models/list-user-response.md).

## Example Usage

```php
$conversationsV1UserApi = $client->getConversationsV1UserApi();
$apiResponse = $conversationsV1UserApi->listUser();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListUserResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://conversations.twilio.com/v1/Users?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Users?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "users"
  },
  "users": [
    {
      "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "identity": "admin",
      "friendly_name": "name",
      "attributes": "{ \"duty\": \"tech\" }",
      "is_online": true,
      "is_notifiable": null,
      "date_created": "2019-12-16T22:18:37Z",
      "date_updated": "2019-12-16T22:18:38Z",
      "url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "links": {
        "user_conversations": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
      }
    },
    {
      "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "identity": "agent0034",
      "friendly_name": "John from customs",
      "attributes": "{ \"duty\": \"agent\" }",
      "is_online": false,
      "is_notifiable": null,
      "date_created": "2020-03-24T20:38:21Z",
      "date_updated": "2020-03-24T20:38:21Z",
      "url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "links": {
        "user_conversations": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
      }
    }
  ]
}
```


# Update User

Update an existing conversation user in your account's default service

```php
function updateUser(
    string $sid,
    ?string $xTwilioWebhookEnabled = null,
    ?string $friendlyName = null,
    ?string $attributes = null,
    ?string $roleSid = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the User resource to update. This value can be either the `sid` or the `identity` of the User resource to update. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `friendlyName` | `?string` | Form, Optional | The string that you assigned to describe the resource. |
| `attributes` | `?string` | Form, Optional | The JSON Object string that stores application-specific data. If attributes have not been set, `{}` is returned. |
| `roleSid` | `?string` | Form, Optional | The SID of a service-level [Role](https://www.twilio.com/docs/conversations/api/role-resource) to assign to the user.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`User`](../../doc/models/user.md).

## Example Usage

```php
$sid = 'Sid8';

$friendlyName = 'new name';

$attributes = '{ "duty": "tech", "team": "internals" }';

$roleSid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$conversationsV1UserApi = $client->getConversationsV1UserApi();
$apiResponse = $conversationsV1UserApi->updateUser(
    $sid,
    null,
    $friendlyName,
    $attributes,
    $roleSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'User:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "identity": "admin",
  "friendly_name": "new name",
  "attributes": "{ \"duty\": \"tech\", \"team\": \"internals\" }",
  "is_online": true,
  "is_notifiable": null,
  "date_created": "2019-12-16T22:18:37Z",
  "date_updated": "2019-12-16T22:18:38Z",
  "url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "user_conversations": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
  }
}
```


# Delete User

Remove a conversation user from your account's default service

```php
function deleteUser(string $sid, ?string $xTwilioWebhookEnabled = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the User resource to delete. This value can be either the `sid` or the `identity` of the User resource to delete. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$sid = 'Sid8';

$conversationsV1UserApi = $client->getConversationsV1UserApi();
$apiResponse = $conversationsV1UserApi->deleteUser($sid);

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


# Fetch User

Fetch a conversation user from your account's default service

```php
function fetchUser(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the User resource to fetch. This value can be either the `sid` or the `identity` of the User resource to fetch. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`User`](../../doc/models/user.md).

## Example Usage

```php
$sid = 'Sid8';

$conversationsV1UserApi = $client->getConversationsV1UserApi();
$apiResponse = $conversationsV1UserApi->fetchUser($sid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'User:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "identity": "admin",
  "friendly_name": "name",
  "attributes": "{ \"duty\": \"tech\" }",
  "is_online": true,
  "is_notifiable": null,
  "date_created": "2019-12-16T22:18:37Z",
  "date_updated": "2019-12-16T22:18:38Z",
  "url": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "user_conversations": "https://conversations.twilio.com/v1/Users/USaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations"
  }
}
```

