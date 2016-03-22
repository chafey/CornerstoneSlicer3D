# /DICOMSEG

Provides a method to obtain a DICOM P10 Segmentation SOP Instance for a given set of segmentation resources
created by slicer.

## Methods

### GET
#### /DICOMSEG

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

Returns the DICOM P10 Segmentation SOP Instance.

acceptable request representations

* application/json

```javascript
{
  "segmentJob" : "URL to segment job"
  "volumeId" : "volumeId",
  "seedPoint" : "Seed Point in DICOM Patient Coordinate system x,y,z"
}



available response representations

* application/dicom

