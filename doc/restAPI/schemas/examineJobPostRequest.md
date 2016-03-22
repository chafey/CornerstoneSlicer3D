# ExamineJob POST Request [JSON Schema](http://json-schema.org/)

```javascript

{
    "$schema": "http://json-schema.org/draft-04/schema",
    "type" : "object",
    "properties" : {
        "dicom" : {
            "type" : "object",
            "properties" :
                "study" : {
                    "type" : "object",
                    "properties" : {
                        "studyInstanceUID" : {
                            "description": "DICOM Study Instance UID",
                            "type" : "string"
                        }
                    },
                    "required" : ["studyInstanceUID"],
                    "additionalProperties": false
                }
            },
            "required" : ["study"]
        }
    },
    "required" : ["dicom"],
    "additionalProperties": false
}

```