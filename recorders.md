# Recorders
Since we are Monitoring the Recorders, we want to be able to get their statuses independent of the emails that are sent in the event of trouble situations.

All requests must include a Session Header, else will return a **401-Unauthorized** response.

{% method %}
## GET `/recorders`

You can either request information on all of the Recorders, via this endpoint, or a recorder with a specific id, defined below. 

{% sample lang="js" %}
Recorder request using jQuery. A Session Token, while recommended, is not required for these requests, as they are Read Only.

```js
$.ajax({
  type: "GET",
  url: API_ROOT + '/recorders',
  success: success
});
```

{% common %}
If successful (**200**), all of the Recorders in the DB are returned as a JSON array.

```json
[
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
  },
  {
    "Online": true,
    "LastSeen": "May 10, 2017 2:15:08 PM",
    "Id": "18f6c548a5eb4ba38ea9c0b7986b99764a",
    "Name": "SC-Mediasite-GMCS301",
    "Description": "",
    "SerialNumber": "003-1740526",
    "Version": "Mediasite Recorder 7.1.12 Build 3853",
    "LastVersionUpdateDate": "2017-02-10T04:33:14.787Z",
    "PhysicalAddress": "54-BE-F7-FF-FF-FF",
    "ImageVersion": "7.1.10"
  }
]
```

{% endmethod %}

{% method %}
## GET `/recorders/{id}`

If you know the specific ID of a recorder, you can retrieve the information for only that recorder, provided it is in the DB.

{% sample lang="js" %}
Recorder request using jQuery. A Session Token, while recommended, is not required for these requests, as they are Read Only. In the provided JS example, `RECORDER_ID` is the ID of the recorder you would like to retrieve. 

```js
$.ajax({
type: "GET",
url: API_ROOT + '/recorders/' + RECORDER_ID,
success: success
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


If no recorders with the specified ID exist, a status **404** is returned, along with a JSON error message.

```json
{
"status": "Error",
"message": "No recorders with that ID were found"
}
```
{% endmethod %}
