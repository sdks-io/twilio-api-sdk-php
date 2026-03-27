# Conversations V1 Role

```php
$conversationsV1RoleApi = $client->getConversationsV1RoleApi();
```

## Class Name

`ConversationsV1RoleApi`

## Methods

* [Create Role](../../doc/controllers/conversations-v1-role.md#create-role)
* [List Role](../../doc/controllers/conversations-v1-role.md#list-role)
* [Update Role](../../doc/controllers/conversations-v1-role.md#update-role)
* [Delete Role](../../doc/controllers/conversations-v1-role.md#delete-role)
* [Fetch Role](../../doc/controllers/conversations-v1-role.md#fetch-role)
* [Create Service Role](../../doc/controllers/conversations-v1-role.md#create-service-role)
* [List Service Role](../../doc/controllers/conversations-v1-role.md#list-service-role)
* [Update Service Role](../../doc/controllers/conversations-v1-role.md#update-service-role)
* [Delete Service Role](../../doc/controllers/conversations-v1-role.md#delete-service-role)
* [Fetch Service Role](../../doc/controllers/conversations-v1-role.md#fetch-service-role)


# Create Role

Create a new user role in your account's default service

```php
function createRole(string $friendlyName, string $type, array $permission): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `friendlyName` | `string` | Form, Required | A descriptive string that you create to describe the new resource. It can be up to 64 characters long. |
| `type` | [`string(RoleRoleType)`](../../doc/models/role-role-type.md) | Form, Required | The type of role. Can be: `conversation` for [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) roles or `service` for [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) roles. |
| `permission` | `string[]` | Form, Required | A permission that you grant to the new role. Only one permission can be granted per parameter. To assign more than one permission, repeat this parameter for each permission value. The values for this parameter depend on the role's `type`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Role`](../../doc/models/role.md).

## Example Usage

```php
$friendlyName = 'Conversation Role';

$type = RoleRoleType::CONVERSATION;

$permission = [
    'Permission5'
];

$conversationsV1RoleApi = $client->getConversationsV1RoleApi();
$apiResponse = $conversationsV1RoleApi->createRole(
    $friendlyName,
    $type,
    $permission
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Role:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# List Role

Retrieve a list of all user roles in your account's default service

```php
function listRole(?int $pageSize = null, ?int $page = null, ?string $pageToken = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListRoleResponse`](../../doc/models/list-role-response.md).

## Example Usage

```php
$conversationsV1RoleApi = $client->getConversationsV1RoleApi();
$apiResponse = $conversationsV1RoleApi->listRole();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListRoleResponse:';
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
    "first_page_url": "https://conversations.twilio.com/v1/Roles?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Roles?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "roles"
  },
  "roles": [
    {
      "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Conversation Role",
      "type": "conversation",
      "permissions": [
        "sendMessage",
        "leaveConversation",
        "editOwnMessage",
        "deleteOwnMessage"
      ],
      "date_created": "2016-03-03T19:47:15Z",
      "date_updated": "2016-03-03T19:47:15Z",
      "url": "https://conversations.twilio.com/v1/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```


# Update Role

Update an existing user role in your account's default service

```php
function updateRole(string $sid, array $permission): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the Role resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `permission` | `string[]` | Form, Required | A permission that you grant to the role. Only one permission can be granted per parameter. To assign more than one permission, repeat this parameter for each permission value. Note that the update action replaces all previously assigned permissions with those defined in the update action. To remove a permission, do not include it in the subsequent update action. The values for this parameter depend on the role's `type`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Role`](../../doc/models/role.md).

## Example Usage

```php
$sid = 'Sid8';

$permission = [
    'Permission5'
];

$conversationsV1RoleApi = $client->getConversationsV1RoleApi();
$apiResponse = $conversationsV1RoleApi->updateRole(
    $sid,
    $permission
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Role:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Role

Remove a user role from your account's default service

```php
function deleteRole(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the Role resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$sid = 'Sid8';

$conversationsV1RoleApi = $client->getConversationsV1RoleApi();
$apiResponse = $conversationsV1RoleApi->deleteRole($sid);

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


# Fetch Role

Fetch a user role from your account's default service

```php
function fetchRole(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the Role resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Role`](../../doc/models/role.md).

## Example Usage

```php
$sid = 'Sid8';

$conversationsV1RoleApi = $client->getConversationsV1RoleApi();
$apiResponse = $conversationsV1RoleApi->fetchRole($sid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Role:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Create Service Role

Create a new user role in your service

```php
function createServiceRole(
    string $chatServiceSid,
    string $friendlyName,
    string $type,
    array $permission
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to create the Role resource under.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `friendlyName` | `string` | Form, Required | A descriptive string that you create to describe the new resource. It can be up to 64 characters long. |
| `type` | [`string(ServiceRoleRoleType)`](../../doc/models/service-role-role-type.md) | Form, Required | The type of role. Can be: `conversation` for [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) roles or `service` for [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) roles. |
| `permission` | `string[]` | Form, Required | A permission that you grant to the new role. Only one permission can be granted per parameter. To assign more than one permission, repeat this parameter for each permission value. The values for this parameter depend on the role's `type`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceRole`](../../doc/models/service-role.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$friendlyName = 'Conversation Role';

$type = ServiceRoleRoleType::CONVERSATION;

$permission = [
    'Permission5'
];

$conversationsV1RoleApi = $client->getConversationsV1RoleApi();
$apiResponse = $conversationsV1RoleApi->createServiceRole(
    $chatServiceSid,
    $friendlyName,
    $type,
    $permission
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceRole:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# List Service Role

Retrieve a list of all user roles in your service

```php
function listServiceRole(
    string $chatServiceSid,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to read the Role resources from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListServiceRoleResponse`](../../doc/models/list-service-role-response.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationsV1RoleApi = $client->getConversationsV1RoleApi();
$apiResponse = $conversationsV1RoleApi->listServiceRole($chatServiceSid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListServiceRoleResponse:';
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
    "first_page_url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "roles"
  },
  "roles": [
    {
      "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Conversation Role",
      "type": "conversation",
      "permissions": [
        "sendMessage",
        "leaveConversation",
        "editOwnMessage",
        "deleteOwnMessage"
      ],
      "date_created": "2016-03-03T19:47:15Z",
      "date_updated": "2016-03-03T19:47:15Z",
      "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```


# Update Service Role

Update an existing user role in your service

```php
function updateServiceRole(string $chatServiceSid, string $sid, array $permission): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to update the Role resource in.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Role resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `permission` | `string[]` | Form, Required | A permission that you grant to the role. Only one permission can be granted per parameter. To assign more than one permission, repeat this parameter for each permission value. Note that the update action replaces all previously assigned permissions with those defined in the update action. To remove a permission, do not include it in the subsequent update action. The values for this parameter depend on the role's `type`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceRole`](../../doc/models/service-role.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$sid = 'Sid8';

$permission = [
    'Permission5'
];

$conversationsV1RoleApi = $client->getConversationsV1RoleApi();
$apiResponse = $conversationsV1RoleApi->updateServiceRole(
    $chatServiceSid,
    $sid,
    $permission
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceRole:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Service Role

Remove a user role from your service

```php
function deleteServiceRole(string $chatServiceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to delete the Role resource from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Role resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$sid = 'Sid8';

$conversationsV1RoleApi = $client->getConversationsV1RoleApi();
$apiResponse = $conversationsV1RoleApi->deleteServiceRole(
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


# Fetch Service Role

Fetch a user role from your service

```php
function fetchServiceRole(string $chatServiceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to fetch the Role resource from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Role resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceRole`](../../doc/models/service-role.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$sid = 'Sid8';

$conversationsV1RoleApi = $client->getConversationsV1RoleApi();
$apiResponse = $conversationsV1RoleApi->fetchServiceRole(
    $chatServiceSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceRole:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Conversation Role",
  "type": "conversation",
  "permissions": [
    "sendMessage",
    "leaveConversation",
    "editOwnMessage",
    "deleteOwnMessage"
  ],
  "date_created": "2016-03-03T19:47:15Z",
  "date_updated": "2016-03-03T19:47:15Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Roles/RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```

