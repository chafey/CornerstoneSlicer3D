# /segmentationJob

Provides methods to create, delete and get the results of segmentation jobs.  Segmentation jobs work on a volume
and produce [segmentation](segmentation.md) objects.

## Methods

### POST
#### /segmentationJob

Creates a new segmentation job and returns a JSON response describing the job.  After a job
is created, a caller may issue a GET request to get the status of the job and the results when completed.  A
caller may also issue a DELETE request to delete a job regardless of status.  Since segmentation jobs may
be time consuming, a caller may "poll" via GET requests to monitor progress.

acceptable request representations

* application/json

Example

```javascript
{
  "volumeUrl" : "http://localhost/volume/7599abe3-e899-4d7d-9924-33847a959368",
  "algorithmId" : "8239eaaf-9280-48f7-989e-470b93799a27", // Airways Segmentation
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
#### /segmentationJob/{{id}}

Returns the segmentation job result.

available response representations

* application/json

Example of running segmentationJob

```javascript

{
    "status" : "running",
    "percentComplete" : 50,
    "segmentationJobRequest" : {
          "volumeUrl" : "http://localhost/volume/7599abe3-e899-4d7d-9924-33847a959368",
          "algorithmId" : "8239eaaf-9280-48f7-989e-470b93799a27", // Airways Segmentation
          "seedPoint" : {
            "x" : 64.0,
            "y" : 32.0,
            "z" : -32.0
          }
    },
    "result" : {
        "segmentations" : [
        ]
    }
}

```

Example of completed segmentationJob


```javascript

{
    "status" : "completed",
    "percentComplete" : 100,
    "segmentationJobRequest" : {
          "volumeUrl" : "http://localhost/volume/7599abe3-e899-4d7d-9924-33847a959368",
          "algorithmId" : "8239eaaf-9280-48f7-989e-470b93799a27", // Airways Segmentation
          "seedPoint" : {
            "x" : 64.0,
            "y" : 32.0,
            "z" : -32.0
          }
    },
    "result" : {
        "segmentations" : [
            {
                "segmentationUrl" : "http://localhost/segmentation/930d8999-4ba4-43f5-b667-0c90183a2c02"
            }
        ]
    }
}

```

### DELETE
#### /segmentationJob/{{id}}

Deletes the specified segmentation job.
