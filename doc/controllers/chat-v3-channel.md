# Chat V3 Channel

```php
$chatV3ChannelApi = $client->getChatV3ChannelApi();
```

## Class Name

`ChatV3ChannelApi`


# Update Channel

Update a specific Channel.

```php
function updateChannel(
    string $serviceSid,
    string $sid,
    ?string $xTwilioWebhookEnabled = null,
    ?string $type = null,
    ?string $messagingServiceSid = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `serviceSid` | `string` | Template, Required | The unique SID identifier of the Service.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^IS[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | A 34 character string that uniquely identifies this Channel. |
| `xTwilioWebhookEnabled` | [`?string(ChannelWebhookEnabledType)`](../../doc/models/channel-webhook-enabled-type.md) | Header, Optional | The X-Twilio-Webhook-Enabled HTTP request header |
| `type` | [`?string(ChannelChannelType)`](../../doc/models/channel-channel-type.md) | Form, Optional | The visibility of the channel. Can be: `public` or `private`. |
| `messagingServiceSid` | `?string` | Form, Optional | The unique ID of the [Messaging Service](https://www.twilio.com/docs/messaging/api/service-resource) this channel belongs to.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^MG[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Channel`](../../doc/models/channel.md).

## Example Usage

```php
$serviceSid = 'ServiceSid8';

$sid = 'Sid8';

$type = ChannelChannelType::PRIVATE_;

$messagingServiceSid = 'MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$chatV3ChannelApi = $client->getChatV3ChannelApi();
$apiResponse = $chatV3ChannelApi->updateChannel(
    $serviceSid,
    $sid,
    null,
    $type,
    $messagingServiceSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Channel:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
{
  "sid": "CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "service_sid": "ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "messaging_service_sid": "MGaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "friendly_name": "friendly_name",
  "unique_name": "unique_name",
  "attributes": "{ \"foo\": \"bar\" }",
  "type": "public",
  "date_created": "2015-12-16T22:18:37Z",
  "date_updated": "2015-12-16T22:18:38Z",
  "created_by": "username",
  "members_count": 0,
  "messages_count": 0,
  "url": "https://chat.twilio.com/v3/Services/ISaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Channels/CHaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```

