### Example: Notify RIS or PACS that the procedure has started, change the state of procdeure step to in progress

#### Using DICOM tags and application/dicom+json media type:  
#### Procedure Step State (0074, 1000)
#### Transaction UID (0008,1195)

```http
PUT /radiology/workitems/1.2.392.200036.9116.2.2.2.1762893313.1029997326.945873/state HTTP/1.1
Host: www.hospital-stmarco
Content-Type: application/dicom+json
…
{
 "00741000": { "vr": "CS", "Value": ["IN PROGRESS"] },
 "00081195": { "vr": "UI", "Value": ["1.9.99.2.2203.5.88.3.1020304050"] }
}
…
```

#### The response returns 200 based on the sucess status code with no body
```http
HTTP/1.1 200 OK

```