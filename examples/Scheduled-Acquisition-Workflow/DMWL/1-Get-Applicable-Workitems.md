### Example: Get all workitems for a scheduled station (CTSCANNER), start date (20240105) and modality (CT), only the first 20 and return all attributes

#### Using DICOM tags and application/dicom+json media type:
Modality (0008,0060)  
Scheduled Procedure Step Sequence (0040,0100) SQ       

```http
GET /radiology/modalityworklist?&00400100.00080060=CT&00400100.00400002=20240105&00400100.00400001=CTSCANNER&limit=20&offset=0&includefield=all HTTP/1.1
Host: www.hospital-stmarco
Accept: application/dicom+json
```

#### The response returns two scheduled procedure steps, one for head and the other one for the spine
Attributes according to: https://dicom.nema.org/medical/dicom/current/output/chtml/part04/sect_K.6.html#table_K.6-1  
Patient's Name (0010,0010)  
Study Instance UID (0020,000D)  
Requested Procedure ID (0040,1001)  
Scheduled Procedure Step Sequence (0040,0100) SQ   
-> Scheduled Procedure Step Description (0040,0007)  
-> Scheduled Station Name (0040,0010)  
-> Scheduled Procedure Step Start Date (0040,0002)   
-> Scheduled Procedure Step ID (0040,0009)  

```http
HTTP/1.1 200 OK
Content-Length: 1191
Content-Type: application/dicom+json; charset=utf-8
…
[ {
  , …
  , "00100010": { "vr": "PN", "Value": [{ "Alphabetic": "Doe^Sally" }] }
  , "0020000D": { "vr": "UI", "Value": ["1.3.12.2.1107.5.99.3.30000008090412501082300000004"] }
  , "00401001": { "vr": "SH", "Value": ["P-ID-22"] }
  , …
  , "00400100": { "vr": "SQ", "Value":
    [ { "00400002": { "vr": "DA", "Value": ["20250101"] }
      , "00400007": { "vr": "LO", "Value": ["Specials^04a_HeadCTA"] }
      , "00400009": { "vr": "SH", "Value": ["PS-ID-23"] }
      , "00400010": { "vr": "SH", "Value": ["CTSCANNER"] }
      , …
      }
    , { "00400002": { "vr": "DA", "Value": ["20250101"] }
      , "00400007": { "vr": "LO", "Value": ["Specials^04a_SpineCTA"] }
      , "00400009": { "vr": "SH", "Value": ["PS-ID-24"] }
      , "00400010": { "vr": "SH", "Value": ["CTSCANNER"] }
      , …
      }
    , …
    ] }
  , …
  }
, …
]
 
```