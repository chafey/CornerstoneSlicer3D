# /examineJob

Provides methods to create, cancel and get the results of examine jobs.  Examine jobs identify functionality
that slicer 3d can perform on a given DICOM data set.  This includes which volumes exist in a given DICOM dataset
and which algorithms can be run on those volumes.  For example, a CT Chest study with two series (one with contrast
and one without contrast) could result in two volumes (one for each series) and an airways segmentation algorithm
being available for the volume that has contrast.

## Methods

### POST
#### /examineJob

Creates a new examine job.  It is assumed that Slicer 3D can locate the images in its local database or via
DICOM Query Retrieve.

acceptable request representations

* application/json

[examineJobPostRequest JSON Schema](schemas/examineJobPostRequest.md)

Example

```javascript

{
    "dicom" : {
        "study" : {
            "studyInstanceUID" : "1.3.6.1.4.1.14519.5.2.1.2744.7002.150059977302243314164020079415"
        }
    }
}

```

available response representations

* application/json

[examineJobPostResponse JSON Schema](schemas/examineJobPostResponse.md)


Example

```javascript

{
    "examineJobUrl" : "http://localhost/examineJob/e64ac045-a8a8-4ac0-8b2f-0c77e3a02627"
}

```



### GET
#### /examineJob/{{id}}

Returns the specified examine job.

available response representations

* application/json

[examineJobGetResponse JSON Schema](schemas/examineJobGetResponse.md)


Example

```javascript

{
    "status" : "completed",
    "createdTimeStamp" : "2016-03-21T12:42:31+00:32",
    "fetchStartTimeStamp" : "2016-03-21T12:42:32+00:32",
    "fetchEndTimeStamp" : "2016-03-21T12:42:40+00:32",
    "examineStartTimeStamp" : "2016-03-21T12:42:41+00:32",
    "examineEndTimeStamp" : "2016-03-21T12:42:43+00:32",
    "progress" : 100,
    "examineJobRequest" : {
        "dicom" : {
            "study" : {
                "studyInstanceUID" : "1.3.6.1.4.1.14519.5.2.1.2744.7002.150059977302243314164020079415"
            }
        }
    },
    "result" : {
        "volumes" : [
            {
                "volumeUrl" : "http://localhost/volume/7599abe3-e899-4d7d-9924-33847a959368"
            }
        ],
        "segmentations" : [
            {
                "segmentationUrl" : "http://localhost/volume/62704070-b8ff-4173-a9af-a9b08a5b1193"
            }
        ]
    }
}

```


### DELETE
#### /examineJob/{{id}}

Deletes the specified examine job.

HTTP Status Codes
200 - Resource successfully deleted
