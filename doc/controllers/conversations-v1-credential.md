# Conversations V1 Credential

```php
$conversationsV1CredentialApi = $client->getConversationsV1CredentialApi();
```

## Class Name

`ConversationsV1CredentialApi`

## Methods

* [Create Credential](../../doc/controllers/conversations-v1-credential.md#create-credential)
* [List Credential](../../doc/controllers/conversations-v1-credential.md#list-credential)
* [Update Credential](../../doc/controllers/conversations-v1-credential.md#update-credential)
* [Delete Credential](../../doc/controllers/conversations-v1-credential.md#delete-credential)
* [Fetch Credential](../../doc/controllers/conversations-v1-credential.md#fetch-credential)


# Create Credential

Add a new push notification credential to your account

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
| `type` | [`string(CredentialPushType)`](../../doc/models/credential-push-type.md) | Form, Required | The type of push-notification service the credential is for. Can be: `fcm`, `gcm`, or `apn`. |
| `friendlyName` | `?string` | Form, Optional | A descriptive string that you create to describe the new resource. It can be up to 64 characters long. |
| `certificate` | `?string` | Form, Optional | [APN only] The URL encoded representation of the certificate. For example,<br>`-----BEGIN CERTIFICATE----- MIIFnTCCBIWgAwIBAgIIAjy9H849+E8wDQYJKoZIhvcNAQEF.....A== -----END CERTIFICATE-----`. |
| `privateKey` | `?string` | Form, Optional | [APN only] The URL encoded representation of the private key. For example,<br>`-----BEGIN RSA PRIVATE KEY----- MIIEpQIBAAKCAQEAuyf/lNrH9ck8DmNyo3fG... -----END RSA PRIVATE KEY-----`. |
| `sandbox` | `?bool` | Form, Optional | [APN only] Whether to send the credential to sandbox APNs. Can be `true` to send to sandbox APNs or `false` to send to production. |
| `apiKey` | `?string` | Form, Optional | [GCM only] The API key for the project that was obtained from the Google Developer console for your GCM Service application credential. |
| `secret` | `?string` | Form, Optional | [FCM only] The **Server key** of your project from the Firebase console, found under Settings / Cloud messaging. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Credential`](../../doc/models/credential.md).

## Example Usage

```php
$type = CredentialPushType::APN;

$conversationsV1CredentialApi = $client->getConversationsV1CredentialApi();
$apiResponse = $conversationsV1CredentialApi->createCredential($type);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Credential:';
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
  "url": "https://conversations.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# List Credential

Retrieve a list of all push notification credentials on your account

```php
function listCredential(?int $pageSize = null, ?int $page = null, ?string $pageToken = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 100.<br><br>**Constraints**: `>= 1`, `<= 100` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListCredentialResponse`](../../doc/models/list-credential-response.md).

## Example Usage

```php
$conversationsV1CredentialApi = $client->getConversationsV1CredentialApi();
$apiResponse = $conversationsV1CredentialApi->listCredential();

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
      "url": "https://conversations.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ],
  "meta": {
    "page": 0,
    "page_size": 50,
    "first_page_url": "https://conversations.twilio.com/v1/Credentials?PageSize=50&Page=0",
    "previous_page_url": null,
    "url": "https://conversations.twilio.com/v1/Credentials?PageSize=50&Page=0",
    "next_page_url": null,
    "key": "credentials"
  }
}
```


# Update Credential

Update an existing push notification credential on your account

```php
function updateCredential(
    string $sid,
    ?string $type = null,
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
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `type` | [`?string(CredentialPushType)`](../../doc/models/credential-push-type.md) | Form, Optional | The type of push-notification service the credential is for. Can be: `fcm`, `gcm`, or `apn`. |
| `friendlyName` | `?string` | Form, Optional | A descriptive string that you create to describe the new resource. It can be up to 64 characters long. |
| `certificate` | `?string` | Form, Optional | [APN only] The URL encoded representation of the certificate. For example,<br>`-----BEGIN CERTIFICATE----- MIIFnTCCBIWgAwIBAgIIAjy9H849+E8wDQYJKoZIhvcNAQEF.....A== -----END CERTIFICATE-----`. |
| `privateKey` | `?string` | Form, Optional | [APN only] The URL encoded representation of the private key. For example,<br>`-----BEGIN RSA PRIVATE KEY----- MIIEpQIBAAKCAQEAuyf/lNrH9ck8DmNyo3fG... -----END RSA PRIVATE KEY-----`. |
| `sandbox` | `?bool` | Form, Optional | [APN only] Whether to send the credential to sandbox APNs. Can be `true` to send to sandbox APNs or `false` to send to production. |
| `apiKey` | `?string` | Form, Optional | [GCM only] The API key for the project that was obtained from the Google Developer console for your GCM Service application credential. |
| `secret` | `?string` | Form, Optional | [FCM only] The **Server key** of your project from the Firebase console, found under Settings / Cloud messaging. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Credential`](../../doc/models/credential.md).

## Example Usage

```php
$sid = 'Sid8';

$friendlyName = 'Test slow create';

$conversationsV1CredentialApi = $client->getConversationsV1CredentialApi();
$apiResponse = $conversationsV1CredentialApi->updateCredential(
    $sid,
    null,
    $friendlyName
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Credential:';
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
  "url": "https://conversations.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Credential

Remove a push notification credential from your account

```php
function deleteCredential(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$sid = 'Sid8';

$conversationsV1CredentialApi = $client->getConversationsV1CredentialApi();
$apiResponse = $conversationsV1CredentialApi->deleteCredential($sid);

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


# Fetch Credential

Fetch a push notification credential from your account

```php
function fetchCredential(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this resource.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Credential`](../../doc/models/credential.md).

## Example Usage

```php
$sid = 'Sid8';

$conversationsV1CredentialApi = $client->getConversationsV1CredentialApi();
$apiResponse = $conversationsV1CredentialApi->fetchCredential($sid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Credential:';
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
  "url": "https://conversations.twilio.com/v1/Credentials/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```

