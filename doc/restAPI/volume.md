# /volume

Provides methods to get and delete 3D volumes

## Methods

###

### GET
#### /volume/{{id}}

Returns the specified volume definition.

available response representations

* application/json

[volumeGetResponse JSON Schema](schemas/volumeGetResponse.md)

Example

```javascript

{
    "name" : "CT Chest With Contrast",
    "examineJobUrl" : "http://localhost/examineJob/e64ac045-a8a8-4ac0-8b2f-0c77e3a02627",
    "dimensions" : {
        "x" : 512,
        "y" : 512,
        "z" : 200
    },
    "spacing" : {
        "x" : 0.5,
        "y" : 0.5,
        "z" : 0.5
    }
    "origin" : {
        "x" : 0.0,
        "y" : 0.0,
        "z" : 0.0
    }
}

```


### DELETE
#### /volume/{{id}}

Deletes the specified volume.

HTTP Status Codes
200 - Resource successfully deleted
