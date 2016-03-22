# /examineJob

Provides methods to create, delete and get examine jobs.  Examine jobs identify functionality
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


Example of fetching examine job

```javascript

{
    "status" : "fetching",
    "createdTimeStamp" : "2016-03-21T12:42:31+00:32",
    "fetchStartTimeStamp" : "2016-03-21T12:42:32+00:32",
    "progress" : 33,
    "examineJobRequest" : {
        "dicom" : {
            "study" : {
                "studyInstanceUID" : "1.3.6.1.4.1.14519.5.2.1.2744.7002.150059977302243314164020079415"
            }
        }
    },
    "result" : {
        "volumes" : [
        ]
    }
}

```

Example of examining examine job

```javascript

{
    "status" : "examining",
    "createdTimeStamp" : "2016-03-21T12:42:31+00:32",
    "fetchStartTimeStamp" : "2016-03-21T12:42:32+00:32",
    "fetchEndTimeStamp" : "2016-03-21T12:42:40+00:32",
    "examineStartTimeStamp" : "2016-03-21T12:42:41+00:32",
    "progress" : 50,
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
                "name" : "CT Chest With Contrast",
                "volumeUrl" : "http://localhost/volume/7599abe3-e899-4d7d-9924-33847a959368",
                "algorithms" : [
                    {
                        "id" : "8239eaaf-9280-48f7-989e-470b93799a27",
                        "name" : "Airways Segmentation"
                    }
                ]
            }
        ]
    }
}

```

Example of completed examine job

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
                "name" : "CT Chest With Contrast",
                "volumeUrl" : "http://localhost/volume/7599abe3-e899-4d7d-9924-33847a959368",
                "algorithms" : [
                    {
                        "id" : "8239eaaf-9280-48f7-989e-470b93799a27",
                        "name" : "Airways Segmentation"
                    }
                ]
            },
            {
                "name" : "CT Chest Without Contrast",
                "volumeUrl" : "http://localhost/volume/93782dfc-a4b5-4f93-a49a-6892b24c8fdc",
                "algorithms" : [
                ]

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
