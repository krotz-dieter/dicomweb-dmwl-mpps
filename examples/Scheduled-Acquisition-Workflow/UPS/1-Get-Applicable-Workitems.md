### Example: Get all workitems for a scheduled station (CTSCANNER), start date (20240105) and modality (CT), only the first 20 and return all attributes

#### Using DICOM tags and application/dicom+json media type:
Scheduled Station Class Code Sequence (0040,4026) SQ (using Code Value & Coding Scheme Designator)  
Scheduled Procedure Step Start Date and Time (0040,4005) DT   
Scheduled Station Name Code Sequence (0040,4025) SQ  (using Code Value, Coding Scheme Designator ?)  

```http
GET /radiology/workitems?00404026.00080100=CT&00404026.00080102=DCM&00404005=20240105000000&00404025.00080100=CTSCANNER&&limit=20&offset=0&includefield=all HTTP/1.1
Host: www.hospital-stmarco
Accept: application/dicom+json
```

#### The response returns two unified procedure steps, one for head and the other one for the spine
Attributes according to: https://dicom.nema.org/medical/dicom/current/output/html/part04.html#table_CC.2.5-3  
SOP Instance UID (0008,0018)  
Patient's Name  (0010,0010)  
Study Instance UID (0020,000D)  
Procedure Step Label (0074,1204)  
Scheduled Station Name Code Sequence (0040,4025)  

```http
HTTP/1.1 200 OK
Content-Length: 1191
Content-Type: application/dicom+json; charset=utf-8
...

[
{
 "00080018": { "vr": "UI", "Value": ["1.2.392.200036.9116.2.2.2.1762893313.1029997326.945873"]},
…
 "00100010": { "vr": "PN", "Value": [{ "Alphabetic": "Doe^Sally" }] },
…
 "0020000D": { "vr": "UI", "Value": ["1.3.12.2.1107.5.99.3.30000008090412501082300000004"] },
…
 "00741204": { "vr": "LO", "Value": ["Specials^04a_HeadCTA"] },
…
 "00404025": { 
    "vr": "SQ",
    "Value": [
        "00080100": { "vr": "SH", "Value": ["CTSCANNER"] },
        … 
    ]
 }
…
 },
 {
 "00080018": { "vr": "UI", "Value": ["1.2.392.200036.9116.2.2.2.1762893313.1029997326.945874"]},
…
 "00100010": { "vr": "PN", "Value": [{ "Alphabetic": "Doe^Sally" }] },
…
 "0020000D": { "vr": "UI", "Value": ["1.3.12.2.1107.5.99.3.30000008090412501082300000004"] },
…
 "00741204": { "vr": "LO", "Value": ["Specials^04a_SpineCTA"] },
…
 "00404025": { 
    "vr": "SQ",
    "Value": [
        "00080100": { "vr": "SH", "Value": ["CTSCANNER"] },
        … 
    ]
 }
 },
…
] 
```