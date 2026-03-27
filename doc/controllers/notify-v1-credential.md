# Notify V1 Credential

```php
$notifyV1CredentialApi = $client->getNotifyV1CredentialApi();
```

## Class Name

`NotifyV1CredentialApi`

## Methods

* [List Credential](../../doc/controllers/notify-v1-credential.md#list-credential)
* [Create Credential](../../doc/controllers/notify-v1-credential.md#create-credential)
* [Fetch Credential](../../doc/controllers/notify-v1-credential.md#fetch-credential)
* [Update Credential](../../doc/controllers/notify-v1-credential.md#update-credential)
* [Delete Credential](../../doc/controllers/notify-v1-credential.md#delete-credential)


# List Credential

```php
function listCredential(?int $pageSize = null, ?int $page = null, ?string $pageToken = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListCredentialResponse`](../../doc/models/list-credential-response.md).

## Example Usage

```php
$notifyV1CredentialApi = $client->getNotifyV1CredentialApi();
$apiResponse = $notifyV1CredentialApi->listCredential();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListCredentialResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "credentials": [
    {
      "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "friendly_name": "Test slow create",
      "type": "apn",
      "sandbox": "False",
      "date_created": "2015-10-07T17:50:01Z",
      "date_updated": "2015-10-07T17:50:01Z",
      "url": "https://notify.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ],
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://notify.twilio.com/v1/Credentials?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://notify.twilio.com/v1/Credentials?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "credentials"
  }
}
```


# Create Credential

```php
function createCredential(
    string $type,
    ?string $friendlyName = null,
    ?string $certificate = null,
    ?string $privateKey = null,
    ?bool $sandbox = null,
    ?string $apiKey = null,
    ?string $secret = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `type` | [`string(CredentialPushType)`](../../doc/models/credential-push-type.md) | Form, Required | The Credential type. Can be: `gcm`, `fcm`, or `apn`. |
| `friendlyName` | `?string` | Form, Optional | A descriptive string that you create to describe the resource. It can be up to 64 characters long. |
| `certificate` | `?string` | Form, Optional | [APN only] The URL-encoded representation of the certificate. Strip everything outside of the headers, e.g. `-----BEGIN CERTIFICATE-----MIIFnTCCBIWgAwIBAgIIAjy9H849+E8wDQYJKoZIhvcNAQEFBQAwgZYxCzAJBgNV.....A==-----END CERTIFICATE-----` |
| `privateKey` | `?string` | Form, Optional | [APN only] The URL-encoded representation of the private key. Strip everything outside of the headers, e.g. `-----BEGIN RSA PRIVATE KEY-----MIIEpQIBAAKCAQEAuyf/lNrH9ck8DmNyo3fGgvCI1l9s+cmBY3WIz+cUDqmxiieR\n.-----END RSA PRIVATE KEY-----` |
| `sandbox` | `?bool` | Form, Optional | [APN only] Whether to send the credential to sandbox APNs. Can be `true` to send to sandbox APNs or `false` to send to production. |
| `apiKey` | `?string` | Form, Optional | [GCM only] The `Server key` of your project from Firebase console under Settings / Cloud messaging. |
| `secret` | `?string` | Form, Optional | [FCM only] The `Server key` of your project from Firebase console under Settings / Cloud messaging. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Credential1`](../../doc/models/credential-1.md).

## Example Usage

```php
$type = CredentialPushType::APN;

$notifyV1CredentialApi = $client->getNotifyV1CredentialApi();
$apiResponse = $notifyV1CredentialApi->createCredential($type);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Credential1:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Test slow create",
  "type": "apn",
  "sandbox": "False",
  "date_created": "2015-10-07T17:50:01Z",
  "date_updated": "2015-10-07T17:50:01Z",
  "url": "https://notify.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Fetch Credential

```php
function fetchCredential(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the Credential resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Credential1`](../../doc/models/credential-1.md).

## Example Usage

```php
$sid = 'Sid8';

$notifyV1CredentialApi = $client->getNotifyV1CredentialApi();
$apiResponse = $notifyV1CredentialApi->fetchCredential($sid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Credential1:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Test slow create",
  "type": "apn",
  "sandbox": "False",
  "date_created": "2015-10-07T17:50:01Z",
  "date_updated": "2015-10-07T17:50:01Z",
  "url": "https://notify.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Update Credential

```php
function updateCredential(
    string $sid,
    ?string $friendlyName = null,
    ?string $certificate = null,
    ?string $privateKey = null,
    ?bool $sandbox = null,
    ?string $apiKey = null,
    ?string $secret = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the Credential resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `friendlyName` | `?string` | Form, Optional | A descriptive string that you create to describe the resource. It can be up to 64 characters long. |
| `certificate` | `?string` | Form, Optional | [APN only] The URL-encoded representation of the certificate. Strip everything outside of the headers, e.g. `-----BEGIN CERTIFICATE-----MIIFnTCCBIWgAwIBAgIIAjy9H849+E8wDQYJKoZIhvcNAQEFBQAwgZYxCzAJBgNV.....A==-----END CERTIFICATE-----` |
| `privateKey` | `?string` | Form, Optional | [APN only] The URL-encoded representation of the private key. Strip everything outside of the headers, e.g. `-----BEGIN RSA PRIVATE KEY-----MIIEpQIBAAKCAQEAuyf/lNrH9ck8DmNyo3fGgvCI1l9s+cmBY3WIz+cUDqmxiieR\n.-----END RSA PRIVATE KEY-----` |
| `sandbox` | `?bool` | Form, Optional | [APN only] Whether to send the credential to sandbox APNs. Can be `true` to send to sandbox APNs or `false` to send to production. |
| `apiKey` | `?string` | Form, Optional | [GCM only] The `Server key` of your project from Firebase console under Settings / Cloud messaging. |
| `secret` | `?string` | Form, Optional | [FCM only] The `Server key` of your project from Firebase console under Settings / Cloud messaging. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Credential1`](../../doc/models/credential-1.md).

## Example Usage

```php
$sid = 'Sid8';

$friendlyName = 'Test slow create';

$notifyV1CredentialApi = $client->getNotifyV1CredentialApi();
$apiResponse = $notifyV1CredentialApi->updateCredential(
    $sid,
    $friendlyName
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Credential1:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "Test slow create",
  "type": "apn",
  "sandbox": "False",
  "date_created": "2015-10-07T17:50:01Z",
  "date_updated": "2015-10-07T17:50:01Z",
  "url": "https://notify.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Credential

```php
function deleteCredential(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the Credential resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$sid = 'Sid8';

$notifyV1CredentialApi = $client->getNotifyV1CredentialApi();
$apiResponse = $notifyV1CredentialApi->deleteCredential($sid);

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

