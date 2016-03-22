# /DICOMSEG

Provides a method to obtain a DICOM P10 Segmentation SOP Instance for a given set of segmentation resources
created by slicer.

## Methods


### POST
#### /DICOMSEG

Returns the DICOM P10 Segmentation SOP Instance for the specified segmentations

acceptable request representations

* application/json

Example

```javascript
{
    "segmentationUrls" : [
        "http://localhost/segmentation/930d8999-4ba4-43f5-b667-0c90183a2c02"
    ]
}

available response representations

* application/dicom

