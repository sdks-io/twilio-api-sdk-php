# Conversations V1 Binding

```php
$conversationsV1BindingApi = $client->getConversationsV1BindingApi();
```

## Class Name

`ConversationsV1BindingApi`

## Methods

* [Delete Service Binding](../../doc/controllers/conversations-v1-binding.md#delete-service-binding)
* [Fetch Service Binding](../../doc/controllers/conversations-v1-binding.md#fetch-service-binding)
* [List Service Binding](../../doc/controllers/conversations-v1-binding.md#list-service-binding)


# Delete Service Binding

Remove a push notification binding from the conversation service

```php
function deleteServiceBinding(string $chatServiceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to delete the Binding resource from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the Binding resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^BS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$sid = 'Sid8';

$conversationsV1BindingApi = $client->getConversationsV1BindingApi();
$apiResponse = $conversationsV1BindingApi->deleteServiceBinding(
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


# Fetch Service Binding

Fetch a push notification binding from the conversation service

```php
function fetchServiceBinding(string $chatServiceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Binding resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^BS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceBinding`](../../doc/models/service-binding.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$sid = 'Sid8';

$conversationsV1BindingApi = $client->getConversationsV1BindingApi();
$apiResponse = $conversationsV1BindingApi->fetchServiceBinding(
    $chatServiceSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceBinding:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "BSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "date_created": "2016-10-21T11:37:03Z",
  "date_updated": "2016-10-21T11:37:03Z",
  "endpoint": "TestUser-endpoint",
  "identity": "TestUser",
  "binding_type": "gcm",
  "credential_sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "message_types": [
    "removed_from_conversation",
    "new_message",
    "added_to_conversation"
  ],
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings/BSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# List Service Binding

Retrieve a list of all push notification bindings in the conversation service

```php
function listServiceBinding(
    string $chatServiceSid,
    ?array $bindingType = null,
    ?array $identity = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Binding resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `bindingType` | [`?(string(ServiceBindingBindingType)[])`](../../doc/models/service-binding-binding-type.md) | Query, Optional | The push technology used by the Binding resources to read.  Can be: `apn`, `gcm`, `fcm`, or `twilsock`.  See [push notification configuration](https://www.twilio.com/docs/chat/push-notification-configuration) for more info. |
| `identity` | `?(string[])` | Query, Optional | The identity of a [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource) this binding belongs to. See [access tokens](https://www.twilio.com/docs/conversations/create-tokens) for more details. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListServiceBindingResponse`](../../doc/models/list-service-binding-response.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationsV1BindingApi = $client->getConversationsV1BindingApi();
$apiResponse = $conversationsV1BindingApi->listServiceBinding($chatServiceSid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListServiceBindingResponse:';
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
    "first_page_url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "bindings"
  },
  "bindings": [
    {
      "sid": "BSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "date_created": "2016-10-21T11:37:03Z",
      "date_updated": "2016-10-21T11:37:03Z",
      "endpoint": "TestUser-endpoint",
      "identity": "TestUser",
      "binding_type": "gcm",
      "credential_sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "message_types": [
        "removed_from_conversation",
        "new_message",
        "added_to_conversation"
      ],
      "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings/BSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```

