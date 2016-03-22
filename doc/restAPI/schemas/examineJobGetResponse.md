# ExamineJob GET Response [JSON Schema](http://json-schema.org/)

```javascript

{
    "$schema": "http://json-schema.org/draft-04/schema",
    "type" : "object",
    "properties" : {
        "status" : {
            "enum" : ["created", "fetching", "examining", "completed"]
        },
        "createdTimeStamp" : {
            "description" : "the date time the job was created",
            "type" : "string",
            "format" : "date-time"
        },
        "fetchStartTimeStamp" : {
            "description" : "the date time the job started fetching data",
            "type" : "string",
            "format" : "date-time"
        },
        "fetchEndTimeStamp" : {
            "description" : "the date time the job ended fetching data",
            "type" : "string",
            "format" : "date-time"
        },
        "examineStartTimeStamp" : {
            "description" : "the date time the job started examining the data set",
            "type" : "string",
            "format" : "date-time"
        },
        "examineEndTimeStamp" : {
            "description" : "the date time the job ended examining the data set",
            "type" : "string",
            "format" : "date-time"
        },
        "progress" : {
            "description" : "the progress for the current status (0 = none, 100 = done)",
            "type" : "integer",
            "minimum": 0,
            "maximum": 100
        },
        "examineJobRequest" : {
            "description" : "the request that created this job",
            "type" : "object",
        },
        "result" : {
            "description" : "the result of the examine job completing",
            "type" : "object",
            "properties" : {
                "volumes" : {
                    "type" : "array",
                    "items" : {
                        "description" : "URL to volume",
                        "type" : "string"
                    }
                },
                "segmentations" : {
                    "type" : "array",
                    "items" : {
                        "description" : "URL to segmentation object",
                        "type" : "string"
                    }
                }
            }

        }
    }
}

```