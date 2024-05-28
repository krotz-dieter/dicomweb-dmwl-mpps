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

