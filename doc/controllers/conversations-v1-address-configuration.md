# Conversations V1 Address Configuration

```php
$conversationsV1AddressConfigurationApi = $client->getConversationsV1AddressConfigurationApi();
```

## Class Name

`ConversationsV1AddressConfigurationApi`

## Methods

* [List Configuration Address](../../doc/controllers/conversations-v1-address-configuration.md#list-configuration-address)
* [Create Configuration Address](../../doc/controllers/conversations-v1-address-configuration.md#create-configuration-address)
* [Fetch Configuration Address](../../doc/controllers/conversations-v1-address-configuration.md#fetch-configuration-address)
* [Update Configuration Address](../../doc/controllers/conversations-v1-address-configuration.md#update-configuration-address)
* [Delete Configuration Address](../../doc/controllers/conversations-v1-address-configuration.md#delete-configuration-address)


# List Configuration Address

Retrieve a list of address configurations for an account

```php
function listConfigurationAddress(
    ?string $type = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `type` | `?string` | Query, Optional | Filter the address configurations by its type. This value can be one of: `whatsapp`, `sms`. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 50.<br><br>**Constraints**: `>= 1`, `<= 50` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListConfigurationAddressResponse`](../../doc/models/list-configuration-address-response.md).

## Example Usage

```php
$type = 'sms';

$conversationsV1AddressConfigurationApi = $client->getConversationsV1AddressConfigurationApi();
$apiResponse = $conversationsV1AddressConfigurationApi->listConfigurationAddress($type);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListConfigurationAddressResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Create Configuration Address

Create a new address configuration

```php
function createConfigurationAddress(
    string $type,
    string $address,
    ?string $friendlyName = null,
    ?bool $autoCreationEnabled = null,
    ?string $autoCreationType = null,
    ?string $autoCreationConversationServiceSid = null,
    ?string $autoCreationWebhookUrl = null,
    ?string $autoCreationWebhookMethod = null,
    ?array $autoCreationWebhookFilters = null,
    ?string $autoCreationStudioFlowSid = null,
    ?int $autoCreationStudioRetryCount = null,
    ?string $addressCountry = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `type` | [`string(ConfigurationAddressType)`](../../doc/models/configuration-address-type.md) | Form, Required | Type of Address, value can be `whatsapp` or `sms`. |
| `address` | `string` | Form, Required | The unique address to be configured. The address can be a whatsapp address or phone number |
| `friendlyName` | `?string` | Form, Optional | The human-readable name of this configuration, limited to 256 characters. Optional. |
| `autoCreationEnabled` | `?bool` | Form, Optional | Enable/Disable auto-creating conversations for messages to this address |
| `autoCreationType` | [`?string(ConfigurationAddressAutoCreationType)`](../../doc/models/configuration-address-auto-creation-type.md) | Form, Optional | - |
| `autoCreationConversationServiceSid` | `?string` | Form, Optional | Conversation Service for the auto-created conversation. If not set, the conversation is created in the default service.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `autoCreationWebhookUrl` | `?string` | Form, Optional | For type `webhook`, the url for the webhook request. |
| `autoCreationWebhookMethod` | [`?string(ConfigurationAddressMethod)`](../../doc/models/configuration-address-method.md) | Form, Optional | - |
| `autoCreationWebhookFilters` | `?(string[])` | Form, Optional | The list of events, firing webhook event for this Conversation. Values can be any of the following: `onMessageAdded`, `onMessageUpdated`, `onMessageRemoved`, `onConversationUpdated`, `onConversationStateUpdated`, `onConversationRemoved`, `onParticipantAdded`, `onParticipantUpdated`, `onParticipantRemoved`, `onDeliveryUpdated` |
| `autoCreationStudioFlowSid` | `?string` | Form, Optional | For type `studio`, the studio flow SID where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |
| `autoCreationStudioRetryCount` | `?int` | Form, Optional | For type `studio`, number of times to retry the webhook request |
| `addressCountry` | `?string` | Form, Optional | An ISO 3166-1 alpha-2n country code which the address belongs to. This is currently only applicable to short code addresses. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ConfigurationAddress`](../../doc/models/configuration-address.md).

## Example Usage

```php
$type = ConfigurationAddressType::SMS;

$address = '+37256123457';

$friendlyName = 'My Test Configuration';

$autoCreationEnabled = true;

$autoCreationType = ConfigurationAddressAutoCreationType::WEBHOOK;

$autoCreationConversationServiceSid = 'ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$autoCreationWebhookUrl = 'https://example.com';

$autoCreationWebhookMethod = ConfigurationAddressMethod::POST;

$autoCreationWebhookFilters = [
    'onParticipantAdded',
    'onMessageAdded'
];

$addressCountry = 'CA';

$conversationsV1AddressConfigurationApi = $client->getConversationsV1AddressConfigurationApi();
$apiResponse = $conversationsV1AddressConfigurationApi->createConfigurationAddress(
    $type,
    $address,
    $friendlyName,
    $autoCreationEnabled,
    $autoCreationType,
    $autoCreationConversationServiceSid,
    $autoCreationWebhookUrl,
    $autoCreationWebhookMethod,
    $autoCreationWebhookFilters,
    null,
    null,
    $addressCountry
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ConfigurationAddress:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Fetch Configuration Address

Fetch an address configuration

```php
function fetchConfigurationAddress(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the Address Configuration resource. This value can be either the `sid` or the `address` of the configuration |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ConfigurationAddress`](../../doc/models/configuration-address.md).

## Example Usage

```php
$sid = 'Sid8';

$conversationsV1AddressConfigurationApi = $client->getConversationsV1AddressConfigurationApi();
$apiResponse = $conversationsV1AddressConfigurationApi->fetchConfigurationAddress($sid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ConfigurationAddress:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Update Configuration Address

Update an existing address configuration

```php
function updateConfigurationAddress(
    string $sid,
    ?string $friendlyName = null,
    ?bool $autoCreationEnabled = null,
    ?string $autoCreationType = null,
    ?string $autoCreationConversationServiceSid = null,
    ?string $autoCreationWebhookUrl = null,
    ?string $autoCreationWebhookMethod = null,
    ?array $autoCreationWebhookFilters = null,
    ?string $autoCreationStudioFlowSid = null,
    ?int $autoCreationStudioRetryCount = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the Address Configuration resource. This value can be either the `sid` or the `address` of the configuration |
| `friendlyName` | `?string` | Form, Optional | The human-readable name of this configuration, limited to 256 characters. Optional. |
| `autoCreationEnabled` | `?bool` | Form, Optional | Enable/Disable auto-creating conversations for messages to this address |
| `autoCreationType` | [`?string(ConfigurationAddressAutoCreationType)`](../../doc/models/configuration-address-auto-creation-type.md) | Form, Optional | - |
| `autoCreationConversationServiceSid` | `?string` | Form, Optional | Conversation Service for the auto-created conversation. If not set, the conversation is created in the default service.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `autoCreationWebhookUrl` | `?string` | Form, Optional | For type `webhook`, the url for the webhook request. |
| `autoCreationWebhookMethod` | [`?string(ConfigurationAddressMethod)`](../../doc/models/configuration-address-method.md) | Form, Optional | - |
| `autoCreationWebhookFilters` | `?(string[])` | Form, Optional | The list of events, firing webhook event for this Conversation. Values can be any of the following: `onMessageAdded`, `onMessageUpdated`, `onMessageRemoved`, `onConversationUpdated`, `onConversationStateUpdated`, `onConversationRemoved`, `onParticipantAdded`, `onParticipantUpdated`, `onParticipantRemoved`, `onDeliveryUpdated` |
| `autoCreationStudioFlowSid` | `?string` | Form, Optional | For type `studio`, the studio flow SID where the webhook should be sent to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^FW[0-9a-fA-F]{32}$` |
| `autoCreationStudioRetryCount` | `?int` | Form, Optional | For type `studio`, number of times to retry the webhook request |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ConfigurationAddress`](../../doc/models/configuration-address.md).

## Example Usage

```php
$sid = 'Sid8';

$friendlyName = 'My Test Configuration Updated';

$autoCreationEnabled = false;

$autoCreationType = ConfigurationAddressAutoCreationType::STUDIO;

$autoCreationStudioFlowSid = 'FWaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$autoCreationStudioRetryCount = 3;

$conversationsV1AddressConfigurationApi = $client->getConversationsV1AddressConfigurationApi();
$apiResponse = $conversationsV1AddressConfigurationApi->updateConfigurationAddress(
    $sid,
    $friendlyName,
    $autoCreationEnabled,
    $autoCreationType,
    null,
    null,
    null,
    null,
    $autoCreationStudioFlowSid,
    $autoCreationStudioRetryCount
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ConfigurationAddress:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete Configuration Address

Remove an existing address configuration

```php
function deleteConfigurationAddress(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The SID of the Address Configuration resource. This value can be either the `sid` or the `address` of the configuration |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$sid = 'Sid8';

$conversationsV1AddressConfigurationApi = $client->getConversationsV1AddressConfigurationApi();
$apiResponse = $conversationsV1AddressConfigurationApi->deleteConfigurationAddress($sid);

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

