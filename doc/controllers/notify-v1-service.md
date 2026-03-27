# Notify V1 Service

```php
$notifyV1ServiceApi = $client->getNotifyV1ServiceApi();
```

## Class Name

`NotifyV1ServiceApi`

## Methods

* [Create Service](../../doc/controllers/notify-v1-service.md#create-service)
* [List Service](../../doc/controllers/notify-v1-service.md#list-service)
* [Delete Service](../../doc/controllers/notify-v1-service.md#delete-service)
* [Fetch Service](../../doc/controllers/notify-v1-service.md#fetch-service)
* [Update Service](../../doc/controllers/notify-v1-service.md#update-service)


# Create Service

```php
function createService(
    ?string $friendlyName = null,
    ?string $apnCredentialSid = null,
    ?string $gcmCredentialSid = null,
    ?string $messagingServiceSid = null,
    ?string $facebookMessengerPageId = null,
    ?string $defaultApnNotificationProtocolVersion = null,
    ?string $defaultGcmNotificationProtocolVersion = null,
    ?string $fcmCredentialSid = null,
    ?string $defaultFcmNotificationProtocolVersion = null,
    ?bool $logEnabled = null,
    ?string $alexaSkillId = null,
    ?string $defaultAlexaNotificationProtocolVersion = null,
    ?string $deliveryCallbackUrl = null,
    ?bool $deliveryCallbackEnabled = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `friendlyName` | `?string` | Form, Optional | A descriptive string that you create to describe the resource. It can be up to 64 characters long. |
| `apnCredentialSid` | `?string` | Form, Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for APN Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `gcmCredentialSid` | `?string` | Form, Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for GCM Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `messagingServiceSid` | `?string` | Form, Optional | The SID of the [Messaging Service](https://www.twilio.com/docs/sms/quickstart#messaging-services) to use for SMS Bindings. This parameter must be set in order to send SMS notifications.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `facebookMessengerPageId` | `?string` | Form, Optional | Deprecated. |
| `defaultApnNotificationProtocolVersion` | `?string` | Form, Optional | The protocol version to use for sending APNS notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. |
| `defaultGcmNotificationProtocolVersion` | `?string` | Form, Optional | The protocol version to use for sending GCM notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. |
| `fcmCredentialSid` | `?string` | Form, Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for FCM Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `defaultFcmNotificationProtocolVersion` | `?string` | Form, Optional | The protocol version to use for sending FCM notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. |
| `logEnabled` | `?bool` | Form, Optional | Whether to log notifications. Can be: `true` or `false` and the default is `true`. |
| `alexaSkillId` | `?string` | Form, Optional | Deprecated. |
| `defaultAlexaNotificationProtocolVersion` | `?string` | Form, Optional | Deprecated. |
| `deliveryCallbackUrl` | `?string` | Form, Optional | URL to send delivery status callback. |
| `deliveryCallbackEnabled` | `?bool` | Form, Optional | Callback configuration that enables delivery callbacks, default false |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Service1`](../../doc/models/service-1.md).

## Example Usage

```php
$friendlyName = 'friendly_name';

$apnCredentialSid = 'CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$messagingServiceSid = 'MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$facebookMessengerPageId = '4';

$defaultApnNotificationProtocolVersion = '3';

$defaultGcmNotificationProtocolVersion = '3';

$defaultFcmNotificationProtocolVersion = '3';

$logEnabled = true;

$deliveryCallbackUrl = 'Hello';

$deliveryCallbackEnabled = true;

$notifyV1ServiceApi = $client->getNotifyV1ServiceApi();
$apiResponse = $notifyV1ServiceApi->createService(
    $friendlyName,
    $apnCredentialSid,
    null,
    $messagingServiceSid,
    $facebookMessengerPageId,
    $defaultApnNotificationProtocolVersion,
    $defaultGcmNotificationProtocolVersion,
    null,
    $defaultFcmNotificationProtocolVersion,
    $logEnabled,
    null,
    null,
    $deliveryCallbackUrl,
    $deliveryCallbackEnabled
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Service1:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "733c7f0f-6541-42ec-84ce-e2ae1cac588c",
  "date_created": "2016-03-09T20:22:31Z",
  "date_updated": "2016-03-09T20:22:31Z",
  "apn_credential_sid": null,
  "gcm_credential_sid": null,
  "fcm_credential_sid": null,
  "messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "facebook_messenger_page_id": "4",
  "alexa_skill_id": null,
  "default_apn_notification_protocol_version": "3",
  "default_gcm_notification_protocol_version": "3",
  "default_fcm_notification_protocol_version": "3",
  "default_alexa_notification_protocol_version": "3",
  "log_enabled": true,
  "delivery_callback_url": "Hello",
  "delivery_callback_enabled": true,
  "url": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "bindings": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings",
    "notifications": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Notifications",
    "segments": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Segments",
    "users": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users"
  }
}
```


# List Service

```php
function listService(
    ?string $friendlyName = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `friendlyName` | `?string` | Query, Optional | The string that identifies the Service resources to read. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListServiceResponse`](../../doc/models/list-service-response.md).

## Example Usage

```php
$notifyV1ServiceApi = $client->getNotifyV1ServiceApi();
$apiResponse = $notifyV1ServiceApi->listService();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListServiceResponse:';
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
    "first_page_url": "https://notify.twilio.com/v1/Services?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://notify.twilio.com/v1/Services?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "services"
  },
  "services": [
    {
      "sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "733c7f0f-6541-42ec-84ce-e2ae1cac588c",
      "date_created": "2016-03-09T20:22:31Z",
      "date_updated": "2016-03-09T20:22:31Z",
      "apn_credential_sid": null,
      "gcm_credential_sid": null,
      "fcm_credential_sid": null,
      "messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "facebook_messenger_page_id": "4",
      "alexa_skill_id": null,
      "default_apn_notification_protocol_version": "3",
      "default_gcm_notification_protocol_version": "3",
      "default_fcm_notification_protocol_version": "3",
      "default_alexa_notification_protocol_version": "3",
      "log_enabled": true,
      "delivery_callback_url": "Hello",
      "delivery_callback_enabled": true,
      "url": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "links": {
        "bindings": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings",
        "notifications": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Notifications",
        "segments": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Segments",
        "users": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users"
      }
    }
  ]
}
```


# Delete Service

```php
function deleteService(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the Service resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$sid = 'Sid8';

$notifyV1ServiceApi = $client->getNotifyV1ServiceApi();
$apiResponse = $notifyV1ServiceApi->deleteService($sid);

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


# Fetch Service

```php
function fetchService(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the Service resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Service1`](../../doc/models/service-1.md).

## Example Usage

```php
$sid = 'Sid8';

$notifyV1ServiceApi = $client->getNotifyV1ServiceApi();
$apiResponse = $notifyV1ServiceApi->fetchService($sid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Service1:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "733c7f0f-6541-42ec-84ce-e2ae1cac588c",
  "date_created": "2016-03-09T20:22:31Z",
  "date_updated": "2016-03-09T20:22:31Z",
  "apn_credential_sid": null,
  "gcm_credential_sid": null,
  "fcm_credential_sid": null,
  "messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "facebook_messenger_page_id": "4",
  "alexa_skill_id": null,
  "default_apn_notification_protocol_version": "3",
  "default_gcm_notification_protocol_version": "3",
  "default_fcm_notification_protocol_version": "3",
  "default_alexa_notification_protocol_version": "3",
  "log_enabled": true,
  "delivery_callback_url": "Hello",
  "delivery_callback_enabled": true,
  "url": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "bindings": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings",
    "notifications": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Notifications",
    "segments": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Segments",
    "users": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users"
  }
}
```


# Update Service

```php
function updateService(
    string $sid,
    ?string $friendlyName = null,
    ?string $apnCredentialSid = null,
    ?string $gcmCredentialSid = null,
    ?string $messagingServiceSid = null,
    ?string $facebookMessengerPageId = null,
    ?string $defaultApnNotificationProtocolVersion = null,
    ?string $defaultGcmNotificationProtocolVersion = null,
    ?string $fcmCredentialSid = null,
    ?string $defaultFcmNotificationProtocolVersion = null,
    ?bool $logEnabled = null,
    ?string $alexaSkillId = null,
    ?string $defaultAlexaNotificationProtocolVersion = null,
    ?string $deliveryCallbackUrl = null,
    ?bool $deliveryCallbackEnabled = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the Service resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `friendlyName` | `?string` | Form, Optional | A descriptive string that you create to describe the resource. It can be up to 64 characters long. |
| `apnCredentialSid` | `?string` | Form, Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for APN Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `gcmCredentialSid` | `?string` | Form, Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for GCM Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `messagingServiceSid` | `?string` | Form, Optional | The SID of the [Messaging Service](https://www.twilio.com/docs/sms/quickstart#messaging-services) to use for SMS Bindings. This parameter must be set in order to send SMS notifications.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `facebookMessengerPageId` | `?string` | Form, Optional | Deprecated. |
| `defaultApnNotificationProtocolVersion` | `?string` | Form, Optional | The protocol version to use for sending APNS notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. |
| `defaultGcmNotificationProtocolVersion` | `?string` | Form, Optional | The protocol version to use for sending GCM notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. |
| `fcmCredentialSid` | `?string` | Form, Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) to use for FCM Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `defaultFcmNotificationProtocolVersion` | `?string` | Form, Optional | The protocol version to use for sending FCM notifications. Can be overridden on a Binding by Binding basis when creating a [Binding](https://www.twilio.com/docs/notify/api/binding-resource) resource. |
| `logEnabled` | `?bool` | Form, Optional | Whether to log notifications. Can be: `true` or `false` and the default is `true`. |
| `alexaSkillId` | `?string` | Form, Optional | Deprecated. |
| `defaultAlexaNotificationProtocolVersion` | `?string` | Form, Optional | Deprecated. |
| `deliveryCallbackUrl` | `?string` | Form, Optional | URL to send delivery status callback. |
| `deliveryCallbackEnabled` | `?bool` | Form, Optional | Callback configuration that enables delivery callbacks, default false |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Service1`](../../doc/models/service-1.md).

## Example Usage

```php
$sid = 'Sid8';

$friendlyName = 'friendly_name';

$apnCredentialSid = 'CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$messagingServiceSid = 'MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$facebookMessengerPageId = '4';

$defaultApnNotificationProtocolVersion = '3';

$defaultGcmNotificationProtocolVersion = '3';

$defaultFcmNotificationProtocolVersion = '3';

$logEnabled = true;

$deliveryCallbackUrl = 'Hello';

$deliveryCallbackEnabled = true;

$notifyV1ServiceApi = $client->getNotifyV1ServiceApi();
$apiResponse = $notifyV1ServiceApi->updateService(
    $sid,
    $friendlyName,
    $apnCredentialSid,
    null,
    $messagingServiceSid,
    $facebookMessengerPageId,
    $defaultApnNotificationProtocolVersion,
    $defaultGcmNotificationProtocolVersion,
    null,
    $defaultFcmNotificationProtocolVersion,
    $logEnabled,
    null,
    null,
    $deliveryCallbackUrl,
    $deliveryCallbackEnabled
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Service1:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "733c7f0f-6541-42ec-84ce-e2ae1cac588c",
  "date_created": "2016-03-09T20:22:31Z",
  "date_updated": "2016-03-09T20:22:31Z",
  "apn_credential_sid": null,
  "gcm_credential_sid": null,
  "fcm_credential_sid": null,
  "default_apn_notification_protocol_version": "3",
  "default_gcm_notification_protocol_version": "3",
  "default_fcm_notification_protocol_version": "3",
  "default_alexa_notification_protocol_version": "3",
  "messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "alexa_skill_id": null,
  "facebook_messenger_page_id": "4",
  "log_enabled": true,
  "delivery_callback_url": "Hello",
  "delivery_callback_enabled": true,
  "url": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "links": {
    "bindings": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings",
    "notifications": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Notifications",
    "segments": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Segments",
    "users": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users"
  }
}
```

