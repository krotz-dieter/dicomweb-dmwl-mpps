### Example: Notify RIS or PACS that the procedure has started, create the Modality Performed Procedure Step (similar to N-CREATE of MPPS)

#### Using DICOM tags and application/dicom+json media type:
Patient's Name (0010,0010)  
Performed Procedure Step ID (0040,0253)   
Performed Station Name (0040,0242)  
Performed Procedure Step Status (0040,0252)
Scheduled Step Attributes Sequence (0040,0270) SQ  
-> Study Instance UID (0020,000D)  
-> Accession Number (0008,0050)  
-> Scheduled Procedure Step Description (0040,0007)  
-> Requested Procedure ID (0040,1001)  
-> Scheduled Procedure Step ID (0040,0009)      

```http
POST /radiology/modalityperformedprocedure/1.2.12345678.987654 HTTP/1.1
Host: www.hospital-stmarco
Content-Type: application/dicom+json
…
{
…
 "00100010": { "vr": "PN", "Value": [{ "Alphabetic": "Doe^Sally" }] },
 "00400253": { "vr": "SH", "Value": ["1.2.12345678.987654"] },
 "00400242": { "vr": "SH", "Value": ["CTSCANNER"] },
 "00400252": { "vr": "CS", "Value": ["IN PROGRESS"] },
…
 "00400270": { 
    "vr": "SQ",
    "Value": [
        {
            "0020000D": { "vr": "UI", "Value": ["1.3.12.2.1107.5.99.3.30000008090412501082300000004"] },
            "00080050": { "vr": "SH", "Value": ["1"] },
            "00400007": { "vr": "LO", "Value": ["Specials^04a_HeadCTA"] },  
            "00401001": { "vr": "SH", "Value": ["P-ID-22"] },
            "00400009": { "vr": "SH", "Value": ["PS-ID-23"] },
            …          
        },
        …
    ]
    }
…
}
…
```

#### The response returns 200 based on the sucess status code.  
```http
HTTP/1.1 200 OK

```