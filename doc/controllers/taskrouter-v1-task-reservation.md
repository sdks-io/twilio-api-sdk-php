# Taskrouter V1 Task Reservation

```php
$taskrouterV1TaskReservationApi = $client->getTaskrouterV1TaskReservationApi();
```

## Class Name

`TaskrouterV1TaskReservationApi`

## Methods

* [List Task Reservation](../../doc/controllers/taskrouter-v1-task-reservation.md#list-task-reservation)
* [Fetch Task Reservation](../../doc/controllers/taskrouter-v1-task-reservation.md#fetch-task-reservation)
* [Update Task Reservation](../../doc/controllers/taskrouter-v1-task-reservation.md#update-task-reservation)


# List Task Reservation

Tasks reserved for workers

```php
function listTaskReservation(
    string $workspaceSid,
    string $taskSid,
    ?string $reservationStatus = null,
    ?string $workerSid = null,
    ?int $pageSize = null,
    ?int $page = null,
    ?string $pageToken = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the TaskReservation resources to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `taskSid` | `string` | Template, Required | The SID of the reserved Task resource with the TaskReservation resources to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |
| `reservationStatus` | [`?string(TaskReservationStatus)`](../../doc/models/task-reservation-status.md) | Query, Optional | Returns the list of reservations for a task with a specified ReservationStatus.  Can be: `pending`, `accepted`, `rejected`, or `timeout`. |
| `workerSid` | `?string` | Query, Optional | The SID of the reserved Worker resource to read.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WK[0-9a-fA-F]{32}$` |
| `pageSize` | `?int` | Query, Optional | How many resources to return in each list page. The default is 50, and the maximum is 1000.<br><br>**Constraints**: `>= 1`, `<= 1000` |
| `page` | `?int` | Query, Optional | The page index. This value is simply for client state.<br><br>**Constraints**: `>= 0` |
| `pageToken` | `?string` | Query, Optional | The page token. This is provided by the API. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ListTaskReservationResponse`](../../doc/models/list-task-reservation-response.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$taskSid = 'TaskSid8';

$taskrouterV1TaskReservationApi = $client->getTaskrouterV1TaskReservationApi();
$apiResponse = $taskrouterV1TaskReservationApi->listTaskReservation(
    $workspaceSid,
    $taskSid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ListTaskReservationResponse:';
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
    "first_page_url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations?PageSize=50&Page=0",
    "key": "reservations",
    "next_page_url": null,
    "page": 0,
    "page_size": 50,
    "previous_page_url": null,
    "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations?PageSize=50&Page=0"
  },
  "reservations": [
    {
      "account_sid": "ACaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "date_created": "2014-05-14T10:50:02Z",
      "date_updated": "2014-05-15T16:03:42Z",
      "links": {
        "task": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "worker": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
      },
      "reservation_status": "accepted",
      "sid": "WRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "task_sid": "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations/WRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "worker_name": "Doug",
      "worker_sid": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
    }
  ]
}
```


# Fetch Task Reservation

Tasks reserved for workers

```php
function fetchTaskReservation(string $workspaceSid, string $taskSid, string $sid): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the TaskReservation resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `taskSid` | `string` | Template, Required | The SID of the reserved Task resource with the TaskReservation resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the TaskReservation resource to fetch.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WR[0-9a-fA-F]{32}$` |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`TaskReservation`](../../doc/models/task-reservation.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$taskSid = 'TaskSid8';

$sid = 'Sid8';

$taskrouterV1TaskReservationApi = $client->getTaskrouterV1TaskReservationApi();
$apiResponse = $taskrouterV1TaskReservationApi->fetchTaskReservation(
    $workspaceSid,
    $taskSid,
    $sid
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'TaskReservation:';
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
  "date_created": "2014-05-14T10:50:02Z",
  "date_updated": "2014-05-15T16:03:42Z",
  "links": {
    "task": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "worker": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
  },
  "reservation_status": "accepted",
  "sid": "WRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_sid": "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations/WRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "worker_name": "Doug",
  "worker_sid": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```


# Update Task Reservation

Tasks reserved for workers

```php
function updateTaskReservation(
    string $workspaceSid,
    string $taskSid,
    string $sid,
    ?string $ifMatch = null,
    ?string $reservationStatus = null,
    ?string $workerActivitySid = null,
    ?string $instruction = null,
    ?string $dequeuePostWorkActivitySid = null,
    ?string $dequeueFrom = null,
    ?string $dequeueRecord = null,
    ?int $dequeueTimeout = null,
    ?string $dequeueTo = null,
    ?string $dequeueStatusCallbackUrl = null,
    ?string $callFrom = null,
    ?string $callRecord = null,
    ?int $callTimeout = null,
    ?string $callTo = null,
    ?string $callUrl = null,
    ?string $callStatusCallbackUrl = null,
    ?bool $callAccept = null,
    ?string $redirectCallSid = null,
    ?bool $redirectAccept = null,
    ?string $redirectUrl = null,
    ?string $to = null,
    ?string $from = null,
    ?string $statusCallback = null,
    ?string $statusCallbackMethod = null,
    ?array $statusCallbackEvent = null,
    ?int $timeout = null,
    ?bool $record = null,
    ?bool $muted = null,
    ?string $beep = null,
    ?bool $startConferenceOnEnter = null,
    ?bool $endConferenceOnExit = null,
    ?string $waitUrl = null,
    ?string $waitMethod = null,
    ?bool $earlyMedia = null,
    ?int $maxParticipants = null,
    ?string $conferenceStatusCallback = null,
    ?string $conferenceStatusCallbackMethod = null,
    ?array $conferenceStatusCallbackEvent = null,
    ?string $conferenceRecord = null,
    ?string $conferenceTrim = null,
    ?string $recordingChannels = null,
    ?string $recordingStatusCallback = null,
    ?string $recordingStatusCallbackMethod = null,
    ?string $conferenceRecordingStatusCallback = null,
    ?string $conferenceRecordingStatusCallbackMethod = null,
    ?string $region = null,
    ?string $sipAuthUsername = null,
    ?string $sipAuthPassword = null,
    ?array $dequeueStatusCallbackEvent = null,
    ?string $postWorkActivitySid = null,
    ?string $supervisorMode = null,
    ?string $supervisor = null,
    ?bool $endConferenceOnCustomerExit = null,
    ?bool $beepOnCustomerEntrance = null,
    ?string $jitterBufferSize = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `workspaceSid` | `string` | Template, Required | The SID of the Workspace with the TaskReservation resources to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WS[0-9a-fA-F]{32}$` |
| `taskSid` | `string` | Template, Required | The SID of the reserved Task resource with the TaskReservation resources to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WT[0-9a-fA-F]{32}$` |
| `sid` | `string` | Template, Required | The SID of the TaskReservation resource to update.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WR[0-9a-fA-F]{32}$` |
| `ifMatch` | `?string` | Header, Optional | The If-Match HTTP request header |
| `reservationStatus` | [`?string(TaskReservationStatus)`](../../doc/models/task-reservation-status.md) | Form, Optional | The current status of the reservation. Can be: `pending`, `accepted`, `rejected`, or `timeout`. |
| `workerActivitySid` | `?string` | Form, Optional | The new worker activity SID if rejecting a reservation.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |
| `instruction` | `?string` | Form, Optional | The assignment instruction for reservation. |
| `dequeuePostWorkActivitySid` | `?string` | Form, Optional | The SID of the Activity resource to start after executing a Dequeue instruction.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |
| `dequeueFrom` | `?string` | Form, Optional | The Caller ID of the call to the worker when executing a Dequeue instruction. |
| `dequeueRecord` | `?string` | Form, Optional | Whether to record both legs of a call when executing a Dequeue instruction or which leg to record. |
| `dequeueTimeout` | `?int` | Form, Optional | Timeout for call when executing a Dequeue instruction. |
| `dequeueTo` | `?string` | Form, Optional | The Contact URI of the worker when executing a Dequeue instruction. Can be the URI of the Twilio Client, the SIP URI for Programmable SIP, or the [E.164](https://www.twilio.com/docs/glossary/what-e164) formatted phone number, depending on the destination. |
| `dequeueStatusCallbackUrl` | `?string` | Form, Optional | The Callback URL for completed call event when executing a Dequeue instruction. |
| `callFrom` | `?string` | Form, Optional | The Caller ID of the outbound call when executing a Call instruction. |
| `callRecord` | `?string` | Form, Optional | Whether to record both legs of a call when executing a Call instruction or which leg to record. |
| `callTimeout` | `?int` | Form, Optional | Timeout for call when executing a Call instruction. |
| `callTo` | `?string` | Form, Optional | The Contact URI of the worker when executing a Call instruction.  Can be the URI of the Twilio Client, the SIP URI for Programmable SIP, or the [E.164](https://www.twilio.com/docs/glossary/what-e164) formatted phone number, depending on the destination. |
| `callUrl` | `?string` | Form, Optional | TwiML URI executed on answering the worker's leg as a result of the Call instruction. |
| `callStatusCallbackUrl` | `?string` | Form, Optional | The URL to call  for the completed call event when executing a Call instruction. |
| `callAccept` | `?bool` | Form, Optional | Whether to accept a reservation when executing a Call instruction. |
| `redirectCallSid` | `?string` | Form, Optional | The Call SID of the call parked in the queue when executing a Redirect instruction.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^CA[0-9a-fA-F]{32}$` |
| `redirectAccept` | `?bool` | Form, Optional | Whether the reservation should be accepted when executing a Redirect instruction. |
| `redirectUrl` | `?string` | Form, Optional | TwiML URI to redirect the call to when executing the Redirect instruction. |
| `to` | `?string` | Form, Optional | The Contact URI of the worker when executing a Conference instruction. Can be the URI of the Twilio Client, the SIP URI for Programmable SIP, or the [E.164](https://www.twilio.com/docs/glossary/what-e164) formatted phone number, depending on the destination. |
| `from` | `?string` | Form, Optional | The Caller ID of the call to the worker when executing a Conference instruction. |
| `statusCallback` | `?string` | Form, Optional | The URL we should call using the `status_callback_method` to send status information to your application. |
| `statusCallbackMethod` | [`?string(ConfigurationWebhookMethod)`](../../doc/models/configuration-webhook-method.md) | Form, Optional | The HTTP method we should use to call `status_callback`. Can be: `POST` or `GET` and the default is `POST`. |
| `statusCallbackEvent` | [`?(string(TaskReservationCallStatus)[])`](../../doc/models/task-reservation-call-status.md) | Form, Optional | The call progress events that we will send to `status_callback`. Can be: `initiated`, `ringing`, `answered`, or `completed`. |
| `timeout` | `?int` | Form, Optional | Timeout for call when executing a Conference instruction. |
| `record` | `?bool` | Form, Optional | Whether to record the participant and their conferences, including the time between conferences. The default is `false`. |
| `muted` | `?bool` | Form, Optional | Whether the agent is muted in the conference. The default is `false`. |
| `beep` | `?string` | Form, Optional | Whether to play a notification beep when the participant joins or when to play a beep. Can be: `true`, `false`, `onEnter`, or `onExit`. The default value is `true`. |
| `startConferenceOnEnter` | `?bool` | Form, Optional | Whether to start the conference when the participant joins, if it has not already started. The default is `true`. If `false` and the conference has not started, the participant is muted and hears background music until another participant starts the conference. |
| `endConferenceOnExit` | `?bool` | Form, Optional | Whether to end the conference when the agent leaves. |
| `waitUrl` | `?string` | Form, Optional | The URL we should call using the `wait_method` for the music to play while participants are waiting for the conference to start. The default value is the URL of our standard hold music. [Learn more about hold music](https://www.twilio.com/labs/twimlets/holdmusic). |
| `waitMethod` | [`?string(ConfigurationWebhookMethod)`](../../doc/models/configuration-webhook-method.md) | Form, Optional | The HTTP method we should use to call `wait_url`. Can be `GET` or `POST` and the default is `POST`. When using a static audio file, this should be `GET` so that we can cache the file. |
| `earlyMedia` | `?bool` | Form, Optional | Whether to allow an agent to hear the state of the outbound call, including ringing or disconnect messages. The default is `true`. |
| `maxParticipants` | `?int` | Form, Optional | The maximum number of participants in the conference. Can be a positive integer from `2` to `250`. The default value is `250`. |
| `conferenceStatusCallback` | `?string` | Form, Optional | The URL we should call using the `conference_status_callback_method` when the conference events in `conference_status_callback_event` occur. Only the value set by the first participant to join the conference is used. Subsequent `conference_status_callback` values are ignored. |
| `conferenceStatusCallbackMethod` | [`?string(ConfigurationWebhookMethod)`](../../doc/models/configuration-webhook-method.md) | Form, Optional | The HTTP method we should use to call `conference_status_callback`. Can be: `GET` or `POST` and defaults to `POST`. |
| `conferenceStatusCallbackEvent` | [`?(string(TaskReservationConferenceEvent)[])`](../../doc/models/task-reservation-conference-event.md) | Form, Optional | The conference status events that we will send to `conference_status_callback`. Can be: `start`, `end`, `join`, `leave`, `mute`, `hold`, `speaker`. |
| `conferenceRecord` | `?string` | Form, Optional | Whether to record the conference the participant is joining or when to record the conference. Can be: `true`, `false`, `record-from-start`, and `do-not-record`. The default value is `false`. |
| `conferenceTrim` | `?string` | Form, Optional | How to trim the leading and trailing silence from your recorded conference audio files. Can be: `trim-silence` or `do-not-trim` and defaults to `trim-silence`. |
| `recordingChannels` | `?string` | Form, Optional | The recording channels for the final recording. Can be: `mono` or `dual` and the default is `mono`. |
| `recordingStatusCallback` | `?string` | Form, Optional | The URL that we should call using the `recording_status_callback_method` when the recording status changes. |
| `recordingStatusCallbackMethod` | [`?string(ConfigurationWebhookMethod)`](../../doc/models/configuration-webhook-method.md) | Form, Optional | The HTTP method we should use when we call `recording_status_callback`. Can be: `GET` or `POST` and defaults to `POST`. |
| `conferenceRecordingStatusCallback` | `?string` | Form, Optional | The URL we should call using the `conference_recording_status_callback_method` when the conference recording is available. |
| `conferenceRecordingStatusCallbackMethod` | [`?string(ConfigurationWebhookMethod)`](../../doc/models/configuration-webhook-method.md) | Form, Optional | The HTTP method we should use to call `conference_recording_status_callback`. Can be: `GET` or `POST` and defaults to `POST`. |
| `region` | `?string` | Form, Optional | The [region](https://support.twilio.com/hc/en-us/articles/223132167-How-global-low-latency-routing-and-region-selection-work-for-conferences-and-Client-calls) where we should mix the recorded audio. Can be:`us1`, `us2`, `ie1`, `de1`, `sg1`, `br1`, `au1`, or `jp1`. |
| `sipAuthUsername` | `?string` | Form, Optional | The SIP username used for authentication. |
| `sipAuthPassword` | `?string` | Form, Optional | The SIP password for authentication. |
| `dequeueStatusCallbackEvent` | `?(string[])` | Form, Optional | The Call progress events sent via webhooks as a result of a Dequeue instruction. |
| `postWorkActivitySid` | `?string` | Form, Optional | The new worker activity SID after executing a Conference instruction.<br><br>**Constraints**: *Minimum Length*: `34`, *Maximum Length*: `34`, *Pattern*: `^WA[0-9a-fA-F]{32}$` |
| `supervisorMode` | [`?string(TaskReservationSupervisorMode)`](../../doc/models/task-reservation-supervisor-mode.md) | Form, Optional | - |
| `supervisor` | `?string` | Form, Optional | The Supervisor SID/URI when executing the Supervise instruction. |
| `endConferenceOnCustomerExit` | `?bool` | Form, Optional | Whether to end the conference when the customer leaves. |
| `beepOnCustomerEntrance` | `?bool` | Form, Optional | Whether to play a notification beep when the customer joins. |
| `jitterBufferSize` | `?string` | Form, Optional | The jitter buffer size for conference. Can be: `small`, `medium`, `large`, `off`. |

## Response Type

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`TaskReservation`](../../doc/models/task-reservation.md).

## Example Usage

```php
$workspaceSid = 'WorkspaceSid0';

$taskSid = 'TaskSid8';

$sid = 'Sid8';

$reservationStatus = TaskReservationStatus::ACCEPTED;

$instruction = 'supervise';

$supervisorMode = TaskReservationSupervisorMode::MONITOR;

$supervisor = 'WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa';

$taskrouterV1TaskReservationApi = $client->getTaskrouterV1TaskReservationApi();
$apiResponse = $taskrouterV1TaskReservationApi->updateTaskReservation(
    $workspaceSid,
    $taskSid,
    $sid,
    null,
    $reservationStatus,
    null,
    $instruction,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    null,
    $supervisorMode,
    $supervisor
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'TaskReservation:';
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
  "date_created": "2014-05-14T10:50:02Z",
  "date_updated": "2014-05-15T16:03:42Z",
  "links": {
    "task": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "worker": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Workers/WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "workspace": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
  },
  "reservation_status": "accepted",
  "sid": "WRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "task_sid": "WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "url": "https://taskrouter.twilio.com/v1/Workspaces/WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Tasks/WTaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa/Reservations/WRaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "worker_name": "Doug",
  "worker_sid": "WKaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
  "workspace_sid": "WSaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"
}
```

