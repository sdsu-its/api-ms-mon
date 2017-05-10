# Recorders
Since we are Monitoring the Recorders, we want to be able to get their statuses independent of the emails that are sent in the event of trouble situations.

All requests must include a Session Header, else will return a **401-Unauthorized** response.

{% method %}
## GET `/recorders`

You can either request information on all of the Recorders, via this endpoint, or a recorder with a specific id, defined below. 

{% sample lang="js" %}
Recorder request using jQuery. You will need to supply the `SESSION_TOKEN` which can be obtained during [user authentication](/authentication.md). 

```js
var payload = {};


$.ajax({
  type: "GET",
  url: API_ROOT + '/recorders',
  data: payload,
  success: success,
  headers: {"session": SESSION_TOKEN}
});
```

{% common %}
If successful (**200**), all of the Recorders in the DB are returned as a JSON array.

```json

```


If either the username or password or incorrect a status **404** is returned, along with a JSON error message. All expected errors will return a status message, along with a possible explanation of why the error occurred.

```json
{
  "status": "Error",
  "message": "That user does not exist or the password is incorrect."
}
```
{% endmethod %}

{% method %}
## GET `/recorders/{id}`

If you know the specific ID of a recorder, you can retrieve the information for only that recorder, provided it is in the DB.

{% sample lang="js" %}
Recorder request using jQuery. You will need to supply the `SESSION_TOKEN` which can be obtained during [user authentication](/authentication.md). In the provided JS example, `RECORDER_ID` is the ID of the recorder you would like to retrieve. 

```js
var payload = {};


$.ajax({
type: "GET",
url: API_ROOT + '/recorders/' + RECORDER_ID,
data: payload,
success: success,
headers: {"session": SESSION_TOKEN}
});
```

{% common %}
If successful (**200**), all of the Recorders in the DB are returned as a JSON array.

```json
{
  "Online": true,
  "LastSeen": "May 10, 2017 2:15:08 PM",
  "Id": "16058358100749308de350eaf446fb88a4",
  "Name": "SC-MEDIASITE-SHW011",
  "Description": "",
  "SerialNumber": "001-9400223",
  "Version": "Mediasite Recorder 7.1.12 Build 3840",
  "LastVersionUpdateDate": "2016-12-16T22:25:26.673Z",
  "PhysicalAddress": "00-30-48-FF-FF-FF",
  "ImageVersion": "7.1.10"
}
```


If either the username or password or incorrect a status **404** is returned, along with a JSON error message. All expected errors will return a status message, along with a possible explanation of why the error occurred.

```json
{
"status": "Error",
"message": "That user does not exist or the password is incorrect."
}
```
{% endmethod %}
