# Accounts V1 Aws

```php
$accountsV1AwsApi = $client->getAccountsV1AwsApi();
```

## Class Name

`AccountsV1AwsApi`

## Methods

* [List Credential Aws](../../doc/controllers/accounts-v1-aws.md#list-credential-aws)
* [Create Credential Aws](../../doc/controllers/accounts-v1-aws.md#create-credential-aws)
* [Fetch Credential Aws](../../doc/controllers/accounts-v1-aws.md#fetch-credential-aws)
* [Update Credential Aws](../../doc/controllers/accounts-v1-aws.md#update-credential-aws)
* [Delete Credential Aws](../../doc/controllers/accounts-v1-aws.md#delete-credential-aws)


# List Credential Aws

Retrieves a collection of AWS Credentials belonging to the account used to make the request

```php
function listCredentialAws(?int $pageSize = null, ?int $page = null, ?string $pageToken = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListCredentialAwsResponse`](../../doc/models/list-credential-aws-response.md).

## Example Usage

```php
$accountsV1AwsApi = $client->getAccountsV1AwsApi();
$apiResponse = $accountsV1AwsApi->listCredentialAws();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListCredentialAwsResponse:';
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
    "first_page_url": "https://accounts.twilio.com/v1/Credentials/AWS?PageSize=50&Page=0",
    "key": "credentials",
    "next_page_url": null,
    "page": 0,
    "page_size": 50,
    "previous_page_url": null,
    "url": "https://accounts.twilio.com/v1/Credentials/AWS?PageSize=50&Page=0"
  }
}
```


# Create Credential Aws

Create a new AWS Credential

```php
function createCredentialAws(
    string $credentials,
    ?string $friendlyName = null,
    ?string $accountSid = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `credentials` | `string` | Form, Required | A string that contains the AWS access credentials in the format `<AWS_ACCESS_KEY_ID>:<AWS_SECRET_ACCESS_KEY>`. For example, `AKIAIOSFODNN7EXAMPLE:wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY` |
| `friendlyName` | `?string` | Form, Optional | A descriptive string that you create to describe the resource. It can be up to 64 characters long. |
| `accountSid` | `?string` | Form, Optional | The SID of the Subaccount that this Credential should be associated with. Must be a valid Subaccount of the account issuing the request.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^AC[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`CredentialAws`](../../doc/models/credential-aws.md).

## Example Usage

```php
$credentials = 'aws_credentials';

$friendlyName = 'friendly_name';

$accountSid = 'ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$accountsV1AwsApi = $client->getAccountsV1AwsApi();
$apiResponse = $accountsV1AwsApi->createCredentialAws(
    $credentials,
    $friendlyName,
    $accountSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'CredentialAws:';
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
  "url": "https://accounts.twilio.com/v1/Credentials/AWS/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Fetch Credential Aws

Fetch the AWS credentials specified by the provided Credential Sid

```php
function fetchCredentialAws(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the AWS resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`CredentialAws`](../../doc/models/credential-aws.md).

## Example Usage

```php
$sid = 'Sid8';

$accountsV1AwsApi = $client->getAccountsV1AwsApi();
$apiResponse = $accountsV1AwsApi->fetchCredentialAws($sid);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'CredentialAws:';
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
  "url": "https://accounts.twilio.com/v1/Credentials/AWS/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Update Credential Aws

Modify the properties of a given Account

```php
function updateCredentialAws(string $sid, ?string $friendlyName = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the AWS resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `friendlyName` | `?string` | Form, Optional | A descriptive string that you create to describe the resource. It can be up to 64 characters long. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`CredentialAws`](../../doc/models/credential-aws.md).

## Example Usage

```php
$sid = 'Sid8';

$friendlyName = 'friendly_name';

$accountsV1AwsApi = $client->getAccountsV1AwsApi();
$apiResponse = $accountsV1AwsApi->updateCredentialAws(
    $sid,
    $friendlyName
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'CredentialAws:';
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
  "url": "https://accounts.twilio.com/v1/Credentials/AWS/CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Delete Credential Aws

Delete a Credential from your account

```php
function deleteCredentialAws(string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `sid` | `string` | Template, Required | The Twilio-provided string that uniquely identifies the AWS resource to delete.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$sid = 'Sid8';

$accountsV1AwsApi = $client->getAccountsV1AwsApi();
$apiResponse = $accountsV1AwsApi->deleteCredentialAws($sid);

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

