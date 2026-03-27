# Conversations V1 Delivery Receipt

```php
$conversationsV1DeliveryReceiptApi = $client->getConversationsV1DeliveryReceiptApi();
```

## Class Name

`ConversationsV1DeliveryReceiptApi`

## Methods

* [Fetch Conversation Message Receipt](../../doc/controllers/conversations-v1-delivery-receipt.md#fetch-conversation-message-receipt)
* [List Conversation Message Receipt](../../doc/controllers/conversations-v1-delivery-receipt.md#list-conversation-message-receipt)
* [Fetch Service Conversation Message Receipt](../../doc/controllers/conversations-v1-delivery-receipt.md#fetch-service-conversation-message-receipt)
* [List Service Conversation Message Receipt](../../doc/controllers/conversations-v1-delivery-receipt.md#list-service-conversation-message-receipt)


# Fetch Conversation Message Receipt

Fetch the delivery and read receipts of the conversation message

```php
function fetchConversationMessageReceipt(string $conversationSid, string $messageSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `messageSid` | `string` | Template, Required | The SID of the message within a [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) the delivery receipt belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^DY[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ConversationMessageReceipt`](../../doc/models/conversation-message-receipt.md).

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$messageSid = 'MessageSid4';

$sid = 'Sid8';

$conversationsV1DeliveryReceiptApi = $client->getConversationsV1DeliveryReceiptApi();
$apiResponse = $conversationsV1DeliveryReceiptApi->fetchConversationMessageReceipt(
    $conversationSid,
    $messageSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ConversationMessageReceipt:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "conversation_sid": "CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "message_sid": "IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "channel_message_sid": "SMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "status": "failed",
  "error_code": 3000,
  "participant_sid": "MBaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "date_created": "2016-03-24T20:37:57Z",
  "date_updated": "2016-03-24T20:37:57Z",
  "url": "https://conversations.twilio.com/v1/Conversations/CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Messages/IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Receipts/DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# List Conversation Message Receipt

Retrieve a list of all delivery and read receipts of the conversation message

```php
function listConversationMessageReceipt(
    string $conversationSid,
    string $messageSid,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `messageSid` | `string` | Template, Required | The SID of the message within a [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) the delivery receipt belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListConversationMessageReceiptResponse`](../../doc/models/list-conversation-message-receipt-response.md).

## Example Usage

```php
$conversationSid = 'ConversationSid0';

$messageSid = 'MessageSid4';

$conversationsV1DeliveryReceiptApi = $client->getConversationsV1DeliveryReceiptApi();
$apiResponse = $conversationsV1DeliveryReceiptApi->listConversationMessageReceipt(
    $conversationSid,
    $messageSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListConversationMessageReceiptResponse:';
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
    "first_page_url": "https://conversations.twilio.com/v1/Conversations/CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Messages/IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Receipts?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Conversations/CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Messages/IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Receipts?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "delivery_receipts"
  },
  "delivery_receipts": [
    {
      "sid": "DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "conversation_sid": "CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "message_sid": "IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "channel_message_sid": "SMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "status": "failed",
      "error_code": 3000,
      "participant_sid": "MBaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "date_created": "2016-03-24T20:37:57Z",
      "date_updated": "2016-03-24T20:37:57Z",
      "url": "https://conversations.twilio.com/v1/Conversations/CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Messages/IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Receipts/DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    },
    {
      "sid": "DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "conversation_sid": "CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "message_sid": "IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "channel_message_sid": "SMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "status": "failed",
      "error_code": 3000,
      "participant_sid": "MBaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "date_created": "2016-03-24T20:37:57Z",
      "date_updated": "2016-03-24T20:37:57Z",
      "url": "https://conversations.twilio.com/v1/Conversations/CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Messages/IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Receipts/DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    },
    {
      "sid": "DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "conversation_sid": "CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "message_sid": "IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "channel_message_sid": "SMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "status": "failed",
      "error_code": 3000,
      "participant_sid": "MBaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "date_created": "2016-03-24T20:37:57Z",
      "date_updated": "2016-03-24T20:37:57Z",
      "url": "https://conversations.twilio.com/v1/Conversations/CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Messages/IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Receipts/DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```


# Fetch Service Conversation Message Receipt

Fetch the delivery and read receipts of the conversation message

```php
function fetchServiceConversationMessageReceipt(
    string $chatServiceSid,
    string $conversationSid,
    string $messageSid,
    string $sid
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Message resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `messageSid` | `string` | Template, Required | The SID of the message within a [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) the delivery receipt belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^DY[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceConversationMessageReceipt`](../../doc/models/service-conversation-message-receipt.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$messageSid = 'MessageSid4';

$sid = 'Sid8';

$conversationsV1DeliveryReceiptApi = $client->getConversationsV1DeliveryReceiptApi();
$apiResponse = $conversationsV1DeliveryReceiptApi->fetchServiceConversationMessageReceipt(
    $chatServiceSid,
    $conversationSid,
    $messageSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceConversationMessageReceipt:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "conversation_sid": "CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "message_sid": "IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "channel_message_sid": "SMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "status": "failed",
  "error_code": 3000,
  "participant_sid": "MBaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "date_created": "2016-03-24T20:37:57Z",
  "date_updated": "2016-03-24T20:37:57Z",
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations/CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Messages/IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Receipts/DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# List Service Conversation Message Receipt

Retrieve a list of all delivery and read receipts of the conversation message

```php
function listServiceConversationMessageReceipt(
    string $chatServiceSid,
    string $conversationSid,
    string $messageSid,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) the Message resource is associated with.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `conversationSid` | `string` | Template, Required | The unique ID of the [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) for this message. |
| `messageSid` | `string` | Template, Required | The SID of the message within a [Conversation](https://www.twilio.com/docs/conversations/api/conversation-resource) the delivery receipt belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IM[0-9a-fA-F]{32}$` |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListServiceConversationMessageReceiptResponse`](../../doc/models/list-service-conversation-message-receipt-response.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationSid = 'ConversationSid0';

$messageSid = 'MessageSid4';

$conversationsV1DeliveryReceiptApi = $client->getConversationsV1DeliveryReceiptApi();
$apiResponse = $conversationsV1DeliveryReceiptApi->listServiceConversationMessageReceipt(
    $chatServiceSid,
    $conversationSid,
    $messageSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListServiceConversationMessageReceiptResponse:';
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
    "first_page_url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations/CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Messages/IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Receipts?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations/CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Messages/IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Receipts?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "delivery_receipts"
  },
  "delivery_receipts": [
    {
      "sid": "DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "conversation_sid": "CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "message_sid": "IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "channel_message_sid": "SMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "status": "failed",
      "error_code": 3000,
      "participant_sid": "MBaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "date_created": "2016-03-24T20:37:57Z",
      "date_updated": "2016-03-24T20:37:57Z",
      "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations/CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Messages/IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Receipts/DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    },
    {
      "sid": "DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "conversation_sid": "CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "message_sid": "IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "channel_message_sid": "SMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "status": "failed",
      "error_code": 3000,
      "participant_sid": "MBaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "date_created": "2016-03-24T20:37:57Z",
      "date_updated": "2016-03-24T20:37:57Z",
      "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations/CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Messages/IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Receipts/DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    },
    {
      "sid": "DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "conversation_sid": "CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "message_sid": "IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "channel_message_sid": "SMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "status": "failed",
      "error_code": 3000,
      "participant_sid": "MBaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "date_created": "2016-03-24T20:37:57Z",
      "date_updated": "2016-03-24T20:37:57Z",
      "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Conversations/CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Messages/IMaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Receipts/DYaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```

