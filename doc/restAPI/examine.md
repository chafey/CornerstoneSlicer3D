# /examine

Provides methods to create, cancel and get the results of examine jobs.  Examine jobs identify functionality
that slicer 3d can perform on a given DICOM data set.

## Methods

### POST
#### /examine

Creates a new examine job.

acceptable request representations

* application/json

```javascript
{
  "dicom" : {
    "studies" : [
        {
            "dicomweb" : "url to DICOMWeb WADO-RS Retrieve Metadata endpoint for a study",
            "studyInstanceUID" : "Study Instance UID",
        }
    ],
    "series" : [
        {
            "dicomweb" : "url to DICOMWeb WADO-RS Retrieve Metadata endpoint for a series",
            "seriesInstanceUID" : "Series Instance UID"
        }
    ],
    "instances" : [
        {
            "dicomweb" : "url to DICOMWeb WADO-RS Retrieve Metadata endpoint for an instance",
            "sopInstanceUID" : "SOP Instance UID"
        }
    ]
  }
}


```

available response representations

* application/json

```javascript
{
    "examineJob" : "URL to examine job resource"
}
```



### GET
#### /examine/{{examineJobId}}

Returns the examine job result.

available response representations

* application/json

```javascript
{
    "status" : "created | running | completed",
    "request" : {
        "dicom" : {
            "studies" : [
                {
                    "dicomweb" : "url to DICOMWeb WADO-RS Retrieve Metadata endpoint for a study",
                    "studyInstanceUID" : "Study Instance UID",
                }
            ],
            "series" : [
                {
                    "dicomweb" : "url to DICOMWeb WADO-RS Retrieve Metadata endpoint for a series",
                    "seriesInstanceUID" : "Series Instance UID"
            }
            ],
            "instances" : [
                {
                    "dicomweb" : "url to DICOMWeb WADO-RS Retrieve Metadata endpoint for an instance",
                    "sopInstanceUID" : "SOP Instance UID"
                }
            ]
        }
    },
    "studies" : [
        {
            "volumes" : [
                {
                    "id" : "unique id for this volume",
                    "name" : "human readable name for volume - e.g. taken from series description",
                    "extents" : {
                        // TBD: info about the volume - x,y,z, in mm and voxels, shear, etc
                    }
                }
            ],
            "segmentations" : [
                {
                    "id" : "unique id for this segmentation",
                    "volumeId" : "unique id for the volume associated with this segmentation"
                    "name" : "Human readable name for this segmentation - e.g. bone"
                }
            ]
        }
    ]

}
```

### DELETE
#### /examine/{{examineJobId}}

Deletes the specified examine job.

HTTP Status Codes
200 - Resource successfully deleted
