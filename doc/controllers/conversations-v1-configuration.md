# Conversations V1 Configuration

```php
$conversationsV1ConfigurationApi = $client->getConversationsV1ConfigurationApi();
```

## Class Name

`ConversationsV1ConfigurationApi`

## Methods

* [Fetch Configuration](../../doc/controllers/conversations-v1-configuration.md#fetch-configuration)
* [Update Configuration](../../doc/controllers/conversations-v1-configuration.md#update-configuration)
* [Fetch Service Configuration](../../doc/controllers/conversations-v1-configuration.md#fetch-service-configuration)
* [Update Service Configuration](../../doc/controllers/conversations-v1-configuration.md#update-service-configuration)


# Fetch Configuration

Fetch the global configuration of conversations on your account

```php
function fetchConfiguration(): ApiResponse
```

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Configuration`](../../doc/models/configuration.md).

## Example Usage

```php
$conversationsV1ConfigurationApi = $client->getConversationsV1ConfigurationApi();
$apiResponse = $conversationsV1ConfigurationApi->fetchConfiguration();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Configuration:';
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
  "default_chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_inactive_timer": "PT1M",
  "default_closed_timer": "PT10M",
  "url": "https://conversations.twilio.com/v1/Configuration",
  "links": {
    "service": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration",
    "webhooks": "https://conversations.twilio.com/v1/Configuration/Webhooks"
  }
}
```


# Update Configuration

Update the global configuration of conversations on your account

```php
function updateConfiguration(
    ?string $defaultChatServiceSid = null,
    ?string $defaultMessagingServiceSid = null,
    ?string $defaultInactiveTimer = null,
    ?string $defaultClosedTimer = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `defaultChatServiceSid` | `?string` | Form, Optional | The SID of the default [Conversation Service](https://www.twilio.com/docs/conversations/api/service-resource) to use when creating a conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `defaultMessagingServiceSid` | `?string` | Form, Optional | The SID of the default [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) to use when creating a conversation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `defaultInactiveTimer` | `?string` | Form, Optional | Default ISO8601 duration when conversation will be switched to `inactive` state. Minimum value for this timer is 1 minute. |
| `defaultClosedTimer` | `?string` | Form, Optional | Default ISO8601 duration when conversation will be switched to `closed` state. Minimum value for this timer is 10 minutes. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Configuration`](../../doc/models/configuration.md).

## Example Usage

```php
$defaultChatServiceSid = 'ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$defaultMessagingServiceSid = 'MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$defaultInactiveTimer = 'PT1M';

$defaultClosedTimer = 'PT10M';

$conversationsV1ConfigurationApi = $client->getConversationsV1ConfigurationApi();
$apiResponse = $conversationsV1ConfigurationApi->updateConfiguration(
    $defaultChatServiceSid,
    $defaultMessagingServiceSid,
    $defaultInactiveTimer,
    $defaultClosedTimer
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Configuration:';
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
  "default_chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_inactive_timer": "PT1M",
  "default_closed_timer": "PT10M",
  "url": "https://conversations.twilio.com/v1/Configuration",
  "links": {
    "service": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration",
    "webhooks": "https://conversations.twilio.com/v1/Configuration/Webhooks"
  }
}
```


# Fetch Service Configuration

Fetch the configuration of a conversation service

```php
function fetchServiceConfiguration(string $chatServiceSid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the Service configuration resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceConfiguration`](../../doc/models/service-configuration.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$conversationsV1ConfigurationApi = $client->getConversationsV1ConfigurationApi();
$apiResponse = $conversationsV1ConfigurationApi->fetchServiceConfiguration($chatServiceSid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceConfiguration:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_conversation_creator_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_conversation_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_chat_service_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "reachability_enabled": false,
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration",
  "links": {
    "notifications": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Notifications",
    "webhooks": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Webhooks"
  }
}
```


# Update Service Configuration

Update configuration settings of a conversation service

```php
function updateServiceConfiguration(
    string $chatServiceSid,
    ?string $defaultConversationCreatorRoleSid = null,
    ?string $defaultConversationRoleSid = null,
    ?string $defaultChatServiceRoleSid = null,
    ?bool $reachabilityEnabled = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `chatServiceSid` | `string` | Template, Required | The SID of the Service configuration resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `defaultConversationCreatorRoleSid` | `?string` | Form, Optional | The conversation-level role assigned to a conversation creator when they join a new conversation. See [Conversation Role](https://www.twilio.com/docs/conversations/api/role-resource) for more info about roles.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `defaultConversationRoleSid` | `?string` | Form, Optional | The conversation-level role assigned to users when they are added to a conversation. See [Conversation Role](https://www.twilio.com/docs/conversations/api/role-resource) for more info about roles.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `defaultChatServiceRoleSid` | `?string` | Form, Optional | The service-level role assigned to users when they are added to the service. See [Conversation Role](https://www.twilio.com/docs/conversations/api/role-resource) for more info about roles.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^RL[0-9a-fA-F]{32}$` |
| `reachabilityEnabled` | `?bool` | Form, Optional | Whether the [Reachability Indicator](https://www.twilio.com/docs/conversations/reachability) is enabled for this Conversations Service. The default is `false`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ServiceConfiguration`](../../doc/models/service-configuration.md).

## Example Usage

```php
$chatServiceSid = 'ChatServiceSid4';

$defaultConversationCreatorRoleSid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$defaultConversationRoleSid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$defaultChatServiceRoleSid = 'RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$reachabilityEnabled = false;

$conversationsV1ConfigurationApi = $client->getConversationsV1ConfigurationApi();
$apiResponse = $conversationsV1ConfigurationApi->updateServiceConfiguration(
    $chatServiceSid,
    $defaultConversationCreatorRoleSid,
    $defaultConversationRoleSid,
    $defaultChatServiceRoleSid,
    $reachabilityEnabled
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ServiceConfiguration:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "chat_service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_conversation_creator_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_conversation_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "default_chat_service_role_sid": "RLaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "reachability_enabled": false,
  "url": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration",
  "links": {
    "notifications": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Notifications",
    "webhooks": "https://conversations.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Configuration/Webhooks"
  }
}
```

