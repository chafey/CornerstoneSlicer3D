# /segmentationJob

Provides methods to create, cancel and get the results of segmentation jobs.  Segmentation jobs work on a volume
or image and produce segmentations which can be converted into DICOM SEG SOP Instances.
## Methods

### POST
#### /segment

Creates a new segmentation job and returns a JSON response describing the job.  After a job
is created, a caller may issue a GET request to get the status of the job and any results.  A
caller may also issue a DELETE request to cancel/delete a job.  Since segmentation jobs may
be time consuming, a caller may "poll" via GET requests to monitor progress.

acceptable request representations

* application/json

```javascript
{
  "examineJob" : "URL to examine job"
  "volumeId" : "volumeId",
  "seedPoint" : "Seed Point in DICOM Patient Coordinate system x,y,z"
}


```

available response representations

* application/json

```javascript
{
    "segmentJob" : "URL to segment job resource"
}
```

### GET
#### /segment

Returns the segmentation job result.

available response representations

* application/json

```javascript
{
    "status" : "created | running | completed",
    "percentComplete" : "number 0-100",
    "request" : {
      "examineJob" : "URL to examine job"
      "volumeId" : "volumeId",
      "seedPoint" : "Seed Point in DICOM Patient Coordinate system x,y,z"
    },
    "result" : {
        "segmentation"
    }
    "TBD" : "support multiple segmentation results in one job?"
    "details" : {
        "TBD" : "Details about segmentation - dimensions, etc"
    }
}
```

### DELETE
#### /segment

Deletes the specified segmentation job.
