### Example: Complete the workitem by setting the state to COMPLETE (similar to N-SET with setting procedure step state to COMPLETED)

#### Using DICOM tags and application/dicom+json media type:  
Performed Procedure Step End Date (0040,0250)  
Performed Procedure Step End Time (0040,0251)  
Performed Procedure Step Status (0040,0252)  

```http
PATCH /radiology/modalityperformedprocedure/1.2.12345678.987654 HTTP/1.1
Host: www.hospital-stmarco
Content-Type: application/dicom+json
…
{
…
 "00400250": { "vr": "DA", "Value": ["20200101"] },
 "00400251": { "vr": "TM", "Value": ["1300"] },
 "00400252": { "vr": "CS", "Value": ["COMPLETED"] },
…
}
…
```

#### The response returns 200 based on the sucess status code.  
```http
HTTP/1.1 200 OK

```