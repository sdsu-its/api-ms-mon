# Recorder Statuses

Recorders can be in a variety of statuses, which are listed below. The API should always return the state string, which can be used to describe the status of the recorder. This status string may change at any time to best describe the situation of the recorder across versions, but will always be consistent within the same version.

| Status ID | Status String | Is Alarm State | Status Reason |
| :--- | :--- | :--- | :--- |
| -1 | Unknown | Yes | Unable to reach recorder |
| 0 | Unavailable | Yes |  Recorder Response |
| 1 | Idle | No | Recorder Response |
| 2 | Busy | No | Recorder Response |
| 3 | Recording | No | Recorder Response |
| 4 | Before Record | No | Recorder Response |
| 5 | After Record | No | Recorder Response |
| 6 | Paused | No | Recorder Response |
| 7 | Incompatible | Yes | Recorder Response |
| 8 | Unknown Error | Yes | Recorder Response |
| 9 | Error Additional Info | Yes | Recorder Response |
| 10 | Details Devices | Yes | Recorder Response |
| 11 | Monitor | Yes | Recorder Response |
| 12 | Could Not Delete All Format | Yes | Recorder Response |
| 13 | Could Not License | Yes | Recorder Response |
| 14 | License Initiated | Yes | Recorder Response |
| 15 | Update Login Error | Yes | Recorder Response |
| 16 | Update Error | Yes | Recorder Response |
| 17 | Update Success | Yes | Recorder Response |
| 18 | Update Remove | Yes | Recorder Response |



