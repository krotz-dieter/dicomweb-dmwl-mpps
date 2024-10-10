### Example: Update workitem with content produced in the acquisition, maps to an update of the workitem with updated information containing the series and image produced

#### Using DICOM tags and application/dicom+json media type:
Requested SOP Instance UID (0000,1001)
Unified Procedure Step Performed Procedure Sequence (0074,1216) SQ
-> Type of Instances (0040,E020)
-> Series Instance UID (0020,000E)
-> Referenced SOP Sequence (0008,1199) SQ
->-> Referenced SOP Class UID (0008,1150)
->-> Referenced SOP Instance UID (0008,1155)

```http
# update workitem state
POST /radiology/workitems/1.9.99.2.2203.5.88.3.1020304050 HTTP/1.1
Host: www.hospital-stmarco
Content-Type: application/dicom
…
{
 "00001001": { "vr": "UI", "Value": ["1.2.392.200036.9116.2.2.2.1762893313.1029997326.945873"]},
…
 "00741216": { 
    "vr": "SQ",
    "Value": [
        {
            "0040E020": { "vr": "CS", "Value": ["DICOM"] }, 
            "0020000E": { "vr": "UI", "Value": ["1.3.12.2.1107.5.99.3.99.197132.30000020040718322840300000007"] }, 
            …     
            "00081199": { 
               "vr": "SQ",
               "Value": [
                    {
                        "00081150": { "vr": "UI", "Value": ["1.2.840.10008.5.1.4.1.1.2"] },
                        "00081155": { "vr": "UI", "Value": ["1.3.12.2.1107.5.99.3.99.197132.30000020040718322840300000520"]  },
                    … 
                    },
                    {
                        "00081150": { "vr": "UI", "Value": ["1.2.840.10008.5.1.4.1.1.2"] },
                        "00081155": { "vr": "UI", "Value": ["1.3.12.2.1107.5.99.3.99.197132.30000020040718322840300000521"]  },
                    …
                    },                     
                    …
               ]
            }
            … 
        },
        …
    ]
 }
 …
}
…
```

#### The response returns 200 based on the sucess status code with no body

```http
HTTP/1.1 200 OK

```
