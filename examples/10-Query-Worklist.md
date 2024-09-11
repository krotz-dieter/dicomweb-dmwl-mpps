### Example: Get all workitems for a scheduled station (CTSCANNER), start date (20240105) and modality (CT), only the first 10 and return all attributes

#### Using DICOM tags and application/dicom+json media type:
```http
GET /radiology/workitems?00080060=CT&00400100.00400002=20240105&00400100.00400010=CTSCANNER&=&limit=20&offset=0&includefield=all HTTP/1.1
Host: www.hospital-stmarco
Accept: application/dicom+json
```

#### Using DICOM keywords and application/dicom+json media type:

```http
GET /radiology/workitems?Modality=CT&Scheduled​Procedure​Step​Sequence.Scheduled​Procedure​Step​Start​Date=20240105&Scheduled​Procedure​Step​Sequence.Scheduled​Station​Name=CTSCANNER&=&limit=20&offset=0&includefield=all HTTP/1.1
Host: www.hospital-stmarco
Accept: application/dicom+json
```

#### One of the returned workitems is an Coronary CT examination
```http
HTTP/1.1 200 OK
Content-Length: 1191
Content-Type: application/dicom+json; charset=utf-8
...

[
 {
 "00080018": {
 "vr": "UI",
 "Value": ["1.2.392.200036.9116.2.2.2.1762893313.1029997326.945873"]
 },
…
 "0020000D": {
 "vr": "UI",
 "Value": ["1.3.12.2.1107.5.99.3.30000008090412501082300000004"]
 },
…
 "00741204": {
 "vr": "LO",
 "Value": ["Specials^04a_CaScCoronaryCTA"]
 },
…
 },
…
] 
```