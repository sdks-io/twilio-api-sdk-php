# Conversations V1 Participant Conversation

```php
$conversationsV1ParticipantConversationApi = $client->getConversationsV1ParticipantConversationApi();
```

## Class Name

`ConversationsV1ParticipantConversationApi`

## Methods

* [List Participant Conversation](../../doc/controllers/conversations-v1-participant-conversation.md#list-participant-conversation)
* [List Service Participant Conversation](../../doc/controllers/conversations-v1-participant-conversation.md#list-service-participant-conversation)


# List Participant Conversation

Retrieve a list of all Conversations that this Participant belongs to by identity or by address. Only one parameter should be specified.

```php
function listParticipantConversation(
    ?string $identity = null,
    ?string $address = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `identity` | `?string` | Query, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the Conversations SDK to communicate. Limited to 256 characters. |
| `address` | `?string` | Query, Optional | A unique string identifier for the conversation participant who's not a Conversation User. This parameter could be found in messaging_binding.address field of Participant resource. It should be url-encoded. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListParticipantConversationResponse`](../../doc/models/list-participant-conversation-response.md).

## Example Usage

```php
$identity = 'identity';

$address = '+375255555555';

$conversationsV1ParticipantConversationApi = $client->getConversationsV1ParticipantConversationApi();
$apiResponse = $conversationsV1ParticipantConversationApi->listParticipantConversation(
    $identity,
    $address
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListParticipantConversationResponse:';
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
    "first_page_url": "https://conversations.twilio.com/v1/ParticipantConversations?Identity=identity&PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/ParticipantConversations?Identity=identity&PageSize=50&Page=0",
    "next_page_url": null,
    "key": "conversations"
  }
}
```


# List Service Participant Conversation

Retrieve a list of all Conversations that this Participant belongs to by identity or by address. Only one parameter should be specified.

```php
function listServiceParticipantConversation(
    string $chatServiceSid,
    ?string $identity = null,
    ?string $address = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Participant Conversations resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `identity` | `?string` | Query, Optional | A unique string identifier for the conversation participant as [Conversation User](https://www.twilio.com/docs/conversations/api/user-resource). This parameter is non-null if (and only if) the participant is using the Conversations SDK to communicate. Limited to 256 characters. |
| `address` | `?string` | Query, Optional | A unique string identifier for the conversation participant who's not a Conversation User. This parameter could be found in messaging_binding.address field of Participant resource. It should be url-encoded. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListServiceParticipantConversationResponse`](../../doc/models/list-service-participant-conversation-response.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$identity = 'identity';

$address = '+375255555555';

$conversationsV1ParticipantConversationApi = $client->getConversationsV1ParticipantConversationApi();
$apiResponse = $conversationsV1ParticipantConversationApi->listServiceParticipantConversation(
    $chatServiceSid,
    $identity,
    $address
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListServiceParticipantConversationResponse:';
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
    "first_page_url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/ParticipantConversations?Identity=identity&PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/ParticipantConversations?Identity=identity&PageSize=50&Page=0",
    "next_page_url": null,
    "key": "conversations"
  }
}
```

