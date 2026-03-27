# Verify V2 Service

```php
$verifyV2ServiceApi = $client->getVerifyV2ServiceApi();
```

## Class Name

`VerifyV2ServiceApi`


# Create Service

Create a new Verification Service.

```php
function createService(
    string $friendlyName,
    ?int $codeLength = null,
    ?bool $lookupEnabled = null,
    ?bool $skipSmsToLandlines = null,
    ?bool $dtmfInputRequired = null,
    ?string $ttsName = null,
    ?bool $psd2Enabled = null,
    ?bool $doNotShareWarningEnabled = null,
    ?bool $customCodeEnabled = null,
    ?bool $pushIncludeDate = null,
    ?string $pushApnCredentialSid = null,
    ?string $pushFcmCredentialSid = null,
    ?string $totpIssuer = null,
    ?int $totpTimeStep = null,
    ?int $totpCodeLength = null,
    ?int $totpSkew = null,
    ?string $defaultTemplateSid = null,
    ?string $whatsappMsgServiceSid = null,
    ?string $whatsappFrom = null,
    ?string $passkeysRelyingPartyId = null,
    ?string $passkeysRelyingPartyName = null,
    ?string $passkeysRelyingPartyOrigins = null,
    ?string $passkeysAuthenticatorAttachment = null,
    ?string $passkeysDiscoverableCredentials = null,
    ?string $passkeysUserVerification = null,
    ?bool $verifyEventSubscriptionEnabled = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `friendlyName` | `string` | Form, Required | A descriptive string that you create to describe the verification service. It can be up to 32 characters long. **This value should not contain PII.** |
| `codeLength` | `?int` | Form, Optional | The length of the verification code to generate. Must be an integer value between 4 and 10, inclusive. |
| `lookupEnabled` | `?bool` | Form, Optional | Whether to perform a lookup with each verification started and return info about the phone number. |
| `skipSmsToLandlines` | `?bool` | Form, Optional | Whether to skip sending SMS verifications to landlines. Requires `lookup_enabled`. |
| `dtmfInputRequired` | `?bool` | Form, Optional | Whether to ask the user to press a number before delivering the verify code in a phone call. |
| `ttsName` | `?string` | Form, Optional | The name of an alternative text-to-speech service to use in phone calls. Applies only to TTS languages. |
| `psd2Enabled` | `?bool` | Form, Optional | Whether to pass PSD2 transaction parameters when starting a verification. |
| `doNotShareWarningEnabled` | `?bool` | Form, Optional | Whether to add a security warning at the end of an SMS verification body. Disabled by default and applies only to SMS. Example SMS body: `Your AppName verification code is: 1234. Don’t share this code with anyone; our employees will never ask for the code` |
| `customCodeEnabled` | `?bool` | Form, Optional | Whether to allow sending verifications with a custom code instead of a randomly generated one. |
| `pushIncludeDate` | `?bool` | Form, Optional | Optional configuration for the Push factors. If true, include the date in the Challenge's response. Otherwise, the date is omitted from the response. See [Challenge](https://www.twilio.com/docs/verify/api/challenge) resource’s details parameter for more info. Default: false. **Deprecated** do not use this parameter. This timestamp value is the same one as the one found in `date_created`, please use that one instead. |
| `pushApnCredentialSid` | `?string` | Form, Optional | Optional configuration for the Push factors. Set the APN Credential for this service. This will allow to send push notifications to iOS devices. See [Credential Resource](https://www.twilio.com/docs/notify/api/credential-resource)<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `pushFcmCredentialSid` | `?string` | Form, Optional | Optional configuration for the Push factors. Set the FCM Credential for this service. This will allow to send push notifications to Android devices. See [Credential Resource](https://www.twilio.com/docs/notify/api/credential-resource)<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CR[0-9a-fA-F]{32}$` |
| `totpIssuer` | `?string` | Form, Optional | Optional configuration for the TOTP factors. Set TOTP Issuer for this service. This will allow to configure the issuer of the TOTP URI. Defaults to the service friendly name if not provided. |
| `totpTimeStep` | `?int` | Form, Optional | Optional configuration for the TOTP factors. Defines how often, in seconds, are TOTP codes generated. i.e, a new TOTP code is generated every time_step seconds. Must be between 20 and 60 seconds, inclusive. Defaults to 30 seconds |
| `totpCodeLength` | `?int` | Form, Optional | Optional configuration for the TOTP factors. Number of digits for generated TOTP codes. Must be between 3 and 8, inclusive. Defaults to 6 |
| `totpSkew` | `?int` | Form, Optional | Optional configuration for the TOTP factors. The number of time-steps, past and future, that are valid for validation of TOTP codes. Must be between 0 and 2, inclusive. Defaults to 1 |
| `defaultTemplateSid` | `?string` | Form, Optional | The default message [template](https://www.twilio.com/docs/verify/api/templates). Will be used for all SMS verifications unless explicitly overriden. SMS channel only.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^HJ[0-9a-fA-F]{32}$` |
| `whatsappMsgServiceSid` | `?string` | Form, Optional | The SID of the Messaging Service containing WhatsApp Sender(s) that Verify will use to send WhatsApp messages to your users.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |
| `whatsappFrom` | `?string` | Form, Optional | The number to use as the WhatsApp Sender that Verify will use to send WhatsApp messages to your users.This WhatsApp Sender must be associated with a Messaging Service SID. |
| `passkeysRelyingPartyId` | `?string` | Form, Optional | The Relying Party ID for Passkeys. This is the domain of your application, e.g. `example.com`. It is used to identify your application when creating Passkeys. |
| `passkeysRelyingPartyName` | `?string` | Form, Optional | The Relying Party Name for Passkeys. This is the name of your application, e.g. `Example App`. It is used to identify your application when creating Passkeys. |
| `passkeysRelyingPartyOrigins` | `?string` | Form, Optional | The Relying Party Origins for Passkeys. This is the origin of your application, e.g. `login.example.com,www.example.com`. It is used to identify your application when creating Passkeys, it can have multiple origins split by `,`. |
| `passkeysAuthenticatorAttachment` | `?string` | Form, Optional | The Authenticator Attachment for Passkeys. This is the type of authenticator that will be used to create Passkeys. It can be empty or it can have the values `platform`, `cross-platform` or `any`. |
| `passkeysDiscoverableCredentials` | `?string` | Form, Optional | Indicates whether credentials must be discoverable by the authenticator. It can be empty or it can have the values `required`, `preferred` or `discouraged`. |
| `passkeysUserVerification` | `?string` | Form, Optional | The User Verification for Passkeys. This is the type of user verification that will be used to create Passkeys. It can be empty or it can have the values `required`, `preferred` or `discouraged`. |
| `verifyEventSubscriptionEnabled` | `?bool` | Form, Optional | Whether to allow verifications from the service to reach the stream-events sinks if configured |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Service2`](../../doc/models/service-2.md).

## Example Usage

```php
$friendlyName = 'name';

$codeLength = 4;

$lookupEnabled = false;

$skipSmsToLandlines = false;

$dtmfInputRequired = false;

$ttsName = 'name';

$psd2Enabled = false;

$doNotShareWarningEnabled = false;

$customCodeEnabled = true;

$pushApnCredentialSid = 'CRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$totpIssuer = 'test-issuer';

$totpTimeStep = 30;

$totpCodeLength = 3;

$totpSkew = 2;

$defaultTemplateSid = 'HJaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$verifyEventSubscriptionEnabled = false;

$verifyV2ServiceApi = $client->getVerifyV2ServiceApi();
$apiResponse = $verifyV2ServiceApi->createService(
    $friendlyName,
    $codeLength,
    $lookupEnabled,
    $skipSmsToLandlines,
    $dtmfInputRequired,
    $ttsName,
    $psd2Enabled,
    $doNotShareWarningEnabled,
    $customCodeEnabled,
    null,
    $pushApnCredentialSid,
    null,
    $totpIssuer,
    $totpTimeStep,
    $totpCodeLength,
    $totpSkew,
    $defaultTemplateSid,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    $verifyEventSubscriptionEnabled
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Service2:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

