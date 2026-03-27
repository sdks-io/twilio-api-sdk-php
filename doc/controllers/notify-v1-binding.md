# Notify V1 Binding

```php
$notifyV1BindingApi = $client->getNotifyV1BindingApi();
```

## Class Name

`NotifyV1BindingApi`

## Methods

* [Fetch Binding](../../doc/controllers/notify-v1-binding.md#fetch-binding)
* [Delete Binding](../../doc/controllers/notify-v1-binding.md#delete-binding)
* [Create Binding](../../doc/controllers/notify-v1-binding.md#create-binding)
* [List Binding](../../doc/controllers/notify-v1-binding.md#list-binding)


# Fetch Binding

```php
function fetchBinding(string $serviceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `serviceSid` | `string` | Template, Required | The SID of the [Service](https://www.twilio.com/docs/notify/api/service-resource) to fetch the resource from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the Binding resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^BS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Binding`](../../doc/models/binding.md).

## Example Usage

```php
$serviceSid = 'ServiceSid8';

$sid = 'Sid8';

$notifyV1BindingApi = $client->getNotifyV1BindingApi();
$apiResponse = $notifyV1BindingApi->fetchBinding(
    $serviceSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Binding:';
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
  "address": "a7c658f4111ec4ff5a1a647f9d0edd819025b9f20522d2fae897049f32873e73",
  "binding_type": "apn",
  "credential_sid": null,
  "date_created": "2015-07-30T20:00:00Z",
  "date_updated": "2015-07-30T20:00:00Z",
  "endpoint": "26607274",
  "identity": "24987039",
  "notification_protocol_version": "3",
  "service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "sid": "BSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "tags": [
    "26607274"
  ],
  "links": {
    "user": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/24987039"
  },
  "url": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings/BSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Binding

```php
function deleteBinding(string $serviceSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `serviceSid` | `string` | Template, Required | The SID of the [Service](https://www.twilio.com/docs/notify/api/service-resource) to delete the resource from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the Binding resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^BS[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$serviceSid = 'ServiceSid8';

$sid = 'Sid8';

$notifyV1BindingApi = $client->getNotifyV1BindingApi();
$apiResponse = $notifyV1BindingApi->deleteBinding(
    $serviceSid,
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


# Create Binding

```php
function createBinding(
    string $serviceSid,
    string $identity,
    string $bindingType,
    string $address,
    ?array $tag = null,
    ?string $notificationProtocolVersion = null,
    ?string $credentialSid = null,
    ?string $endpoint = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `serviceSid` | `string` | Template, Required | The SID of the [Service](https://www.twilio.com/docs/notify/api/service-resource) to create the resource under.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `identity` | `string` | Form, Required | The `identity` value that uniquely identifies the new resource's [User](https://www.twilio.com/docs/chat/rest/user-resource) within the [Service](https://www.twilio.com/docs/notify/api/service-resource). Up to 20 Bindings can be created for the same Identity in a given Service. |
| `bindingType` | [`string(BindingBindingType)`](../../doc/models/binding-binding-type.md) | Form, Required | The transport technology to use for the Binding. Can be: `apn`, `fcm`, `gcm`, `sms`, or `facebook-messenger`. |
| `address` | `string` | Form, Required | The channel-specific address. For APNS, the device token. For FCM and GCM, the registration token. For SMS, a phone number in E.164 format. For Facebook Messenger, the Messenger ID of the user or a phone number in E.164 format. |
| `tag` | `?(string[])` | Form, Optional | A tag that can be used to select the Bindings to notify. Repeat this parameter to specify more than one tag, up to a total of 20 tags. |
| `notificationProtocolVersion` | `?string` | Form, Optional | The protocol version to use to send the notification. This defaults to the value of `default_xxxx_notification_protocol_version` for the protocol in the [Service](https://www.twilio.com/docs/notify/api/service-resource). The current version is `"3"` for `apn`, `fcm`, and `gcm` type Bindings. The parameter is not applicable to `sms` and `facebook-messenger` type Bindings as the data format is fixed. |
| `credentialSid` | `?string` | Form, Optional | The SID of the [Credential](https://www.twilio.com/docs/notify/api/credential-resource) resource to be used to send notifications to this Binding. If present, this overrides the Credential specified in the Service resource. Applies to only `apn`, `fcm`, and `gcm` type Bindings.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `endpoint` | `?string` | Form, Optional | Deprecated. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Binding`](../../doc/models/binding.md).

## Example Usage

```php
$serviceSid = 'ServiceSid8';

$identity = '24987039';

$bindingType = BindingBindingType::APN;

$address = 'address';

$tag = [
    'tag'
];

$notificationProtocolVersion = 'notification_protocol_version';

$credentialSid = 'CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$endpoint = 'endpoint';

$notifyV1BindingApi = $client->getNotifyV1BindingApi();
$apiResponse = $notifyV1BindingApi->createBinding(
    $serviceSid,
    $identity,
    $bindingType,
    $address,
    $tag,
    $notificationProtocolVersion,
    $credentialSid,
    $endpoint
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Binding:';
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
  "address": "a7c658f4111ec4ff5a1a647f9d0edd819025b9f20522d2fae897049f32873e73",
  "binding_type": "apn",
  "credential_sid": null,
  "date_created": "2015-07-30T20:00:00Z",
  "date_updated": "2015-07-30T20:00:00Z",
  "endpoint": "26607274",
  "identity": "24987039",
  "notification_protocol_version": "3",
  "service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "sid": "BSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "tags": [
    "26607274"
  ],
  "links": {
    "user": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Users/24987039"
  },
  "url": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings/BSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# List Binding

```php
function listBinding(
    string $serviceSid,
    ?\DateTime $startDate = null,
    ?\DateTime $endDate = null,
    ?array $identity = null,
    ?array $tag = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `serviceSid` | `string` | Template, Required | The SID of the [Service](https://www.twilio.com/docs/notify/api/service-resource) to read the resource from.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `startDate` | `?DateTime` | Query, Optional | Only include usage that has occurred on or after this date. Specify the date in GMT and format as `YYYY-MM-DD`. |
| `endDate` | `?DateTime` | Query, Optional | Only include usage that occurred on or before this date. Specify the date in GMT and format as `YYYY-MM-DD`. |
| `identity` | `?(string[])` | Query, Optional | The [User](https://www.twilio.com/docs/chat/rest/user-resource)'s `identity` value of the resources to read. |
| `tag` | `?(string[])` | Query, Optional | Only list Bindings that have all of the specified Tags. The following implicit tags are available: `all`, `apn`, `fcm`, `gcm`, `sms`, `facebook-messenger`. Up to 5 tags are allowed. |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListBindingResponse`](../../doc/models/list-binding-response.md).

## Example Usage

```php
$serviceSid = 'ServiceSid8';

$identity = [
    'identity'
];

$tag = [
    'tag'
];

$notifyV1BindingApi = $client->getNotifyV1BindingApi();
$apiResponse = $notifyV1BindingApi->listBinding(
    $serviceSid,
    null,
    null,
    $identity,
    $tag
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListBindingResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "bindings": [],
  "meta": {
    "first_page_url": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings?Tag=tag&Identity=identity&PageSize=50&Page=0",
    "key": "bindings",
    "next_page_url": null,
    "page": 0,
    "page_size": 50,
    "previous_page_url": null,
    "url": "https://notify.twilio.com/v1/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Bindings?Tag=tag&Identity=identity&PageSize=50&Page=0"
  }
}
```

