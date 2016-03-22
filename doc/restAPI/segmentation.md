# /volume

Provides methods to get and delete Slicer 3D segmentation objects

## Methods

###

### GET
#### /segmentation/{{id}}

Returns the specified volume definition.

available response representations

* application/json

[segmentationGetResponse JSON Schema](schemas/volumeGetResponse.md)

Example

```javascript

{
    "name" : "Airways",
    "algorithmName" : "Airways Segmentation",
    "segmentationJobUrl" : "http://localhost/segmentationJob/62704070-b8ff-4173-a9af-a9b08a5b1193",
    "volumeUrl" : "http://localhost/volume/7599abe3-e899-4d7d-9924-33847a959368",
    "dimensions" : {
        "x" : 64,
        "y" : 32,
        "z" : 20
    },
    "spacing" : {
        "x" : 0.5,
        "y" : 0.5,
        "z" : 0.5
    }
    "origin" : {
        "x" : 64.0,
        "y" : 32.0,
        "z" : -32.0
    }
}

```


### DELETE
#### /segmentation/{{id}}

Deletes the specified segmentation.

HTTP Status Codes
200 - Resource successfully deleted

