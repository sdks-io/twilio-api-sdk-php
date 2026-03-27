# Accounts V1 Public Key

```php
$accountsV1PublicKeyApi = $client->getAccountsV1PublicKeyApi();
```

## Class Name

`AccountsV1PublicKeyApi`

## Methods

* [List Credential Public Key](../../doc/controllers/accounts-v1-public-key.md#list-credential-public-key)
* [Create Credential Public Key](../../doc/controllers/accounts-v1-public-key.md#create-credential-public-key)
* [Fetch Credential Public Key](../../doc/controllers/accounts-v1-public-key.md#fetch-credential-public-key)
* [Update Credential Public Key](../../doc/controllers/accounts-v1-public-key.md#update-credential-public-key)
* [Delete Credential Public Key](../../doc/controllers/accounts-v1-public-key.md#delete-credential-public-key)


# List Credential Public Key

Retrieves a collection of Public Key Credentials belonging to the account used to make the request

```php
function listCredentialPublicKey(
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListCredentialPublicKeyResponse`](../../doc/models/list-credential-public-key-response.md).

## Example Usage

```php
$accountsV1PublicKeyApi = $client->getAccountsV1PublicKeyApi();
$apiResponse = $accountsV1PublicKeyApi->listCredentialPublicKey();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListCredentialPublicKeyResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "credentials": [],
  "meta": {
    "first_page_url": "https://accounts.twilio.com/v1/Credentials/PublicKeys?PageSize=50&Page=0",
    "key": "credentials",
    "next_page_url": null,
    "page": 0,
    "page_size": 50,
    "previous_page_url": null,
    "url": "https://accounts.twilio.com/v1/Credentials/PublicKeys?PageSize=50&Page=0"
  }
}
```


# Create Credential Public Key

Create a new Public Key Credential

```php
function createCredentialPublicKey(
    string $publicKey,
    ?string $friendlyName = null,
    ?string $accountSid = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `publicKey` | `string` | Form, Required | A URL encoded representation of the public key. For example, `-----BEGIN PUBLIC KEY-----MIIBIjANB.pa9xQIDAQAB-----END PUBLIC KEY-----` |
| `friendlyName` | `?string` | Form, Optional | A descriptive string that you create to describe the resource. It can be up to 64 characters long. |
| `accountSid` | `?string` | Form, Optional | The SID of the Subaccount that this Credential should be associated with. Must be a valid Subaccount of the account issuing the request<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`CredentialPublicKey`](../../doc/models/credential-public-key.md).

## Example Usage

```php
$publicKey = 'public_key';

$friendlyName = 'friendly_name';

$accountSid = 'ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$accountsV1PublicKeyApi = $client->getAccountsV1PublicKeyApi();
$apiResponse = $accountsV1PublicKeyApi->createCredentialPublicKey(
    $publicKey,
    $friendlyName,
    $accountSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'CredentialPublicKey:';
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
  "date_created": "2015-07-31T04:00:00Z",
  "date_updated": "2015-07-31T04:00:00Z",
  "friendly_name": "friendly_name",
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://accounts.twilio.com/v1/Credentials/PublicKeys/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Fetch Credential Public Key

Fetch the public key specified by the provided Credential Sid

```php
function fetchCredentialPublicKey(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the PublicKey resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`CredentialPublicKey`](../../doc/models/credential-public-key.md).

## Example Usage

```php
$sid = 'Sid8';

$accountsV1PublicKeyApi = $client->getAccountsV1PublicKeyApi();
$apiResponse = $accountsV1PublicKeyApi->fetchCredentialPublicKey($sid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'CredentialPublicKey:';
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
  "date_created": "2015-07-31T04:00:00Z",
  "date_updated": "2015-07-31T04:00:00Z",
  "friendly_name": "friendly_name",
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://accounts.twilio.com/v1/Credentials/PublicKeys/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Update Credential Public Key

Modify the properties of a given Account

```php
function updateCredentialPublicKey(string $sid, ?string $friendlyName = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the PublicKey resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `friendlyName` | `?string` | Form, Optional | A descriptive string that you create to describe the resource. It can be up to 64 characters long. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`CredentialPublicKey`](../../doc/models/credential-public-key.md).

## Example Usage

```php
$sid = 'Sid8';

$friendlyName = 'friendly_name';

$accountsV1PublicKeyApi = $client->getAccountsV1PublicKeyApi();
$apiResponse = $accountsV1PublicKeyApi->updateCredentialPublicKey(
    $sid,
    $friendlyName
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'CredentialPublicKey:';
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
  "date_created": "2015-07-31T04:00:00Z",
  "date_updated": "2015-07-31T04:00:00Z",
  "friendly_name": "friendly_name",
  "sid": "CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://accounts.twilio.com/v1/Credentials/PublicKeys/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Credential Public Key

Delete a Credential from your account

```php
function deleteCredentialPublicKey(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the PublicKey resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$sid = 'Sid8';

$accountsV1PublicKeyApi = $client->getAccountsV1PublicKeyApi();
$apiResponse = $accountsV1PublicKeyApi->deleteCredentialPublicKey($sid);

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

