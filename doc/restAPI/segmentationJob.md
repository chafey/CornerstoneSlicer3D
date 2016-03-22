# /segmentationJob

Provides methods to create, cancel and get the results of segmentation jobs.  Segmentation jobs work on a volume
or image and produce segmentations which can be converted into DICOM SEG SOP Instances.
## Methods

### POST
#### /segmentationJob

Creates a new segmentation job and returns a JSON response describing the job.  After a job
is created, a caller may issue a GET request to get the status of the job and any results.  A
caller may also issue a DELETE request to cancel/delete a job.  Since segmentation jobs may
be time consuming, a caller may "poll" via GET requests to monitor progress.

acceptable request representations

* application/json

Example

```javascript
{
  "volumeUrl" : "http://localhost/volume/7599abe3-e899-4d7d-9924-33847a959368",
  "seedPoint" : {
    "x" : 64.0,
    "y" : 32.0,
    "z" : -32.0
  }
}


```

available response representations

* application/json

Example

```javascript

{
    "segmentationJobUrl" : "http://localhost/segmentationJob/62704070-b8ff-4173-a9af-a9b08a5b1193"
}

```

### GET
#### /segmentationJob

Returns the segmentation job result.

available response representations

* application/json

Example

```javascript

{
    "status" : "completed",
    "percentComplete" : 100,
    "segmentationJobRequest" : {
          "volumeUrl" : "http://localhost/volume/7599abe3-e899-4d7d-9924-33847a959368",
          "seedPoint" : {
            "x" : 64.0,
            "y" : 32.0,
            "z" : -32.0
          }
    },
    "result" : {
        "segmentations" : [
            "http://localhost/segmentationJob/930d8999-4ba4-43f5-b667-0c90183a2c02"
        ]
    }
}

```

### DELETE
#### /segmentationJob

Deletes the specified segmentation job.
