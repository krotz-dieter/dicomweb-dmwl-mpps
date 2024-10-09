### Example: Notify RIS or PACS that the procedure has started, change the state to in progress

#### Using DICOM tags and application/dicom+json media type:
#### Scheduled Step Attributes Sequence (0040,0270) SQ
#### -> Study Instance UID (0020,000D) 
#### -> Accession Number (0008,0050)
#### -> Scheduled Procedure Step Description (0040,0007)  
#### Patient's Name (0010,0010)
#### Performed Procedure Step ID (0040,0253)
#### Performed Station Name (0040,0242)
#### Performed Procedure Step Status (0040,0252)

```http
PUT /radiology/workitems/1.2.392.200036.9116.2.2.2.1762893313.1029997326.945873/state HTTP/1.1
Host: www.hospital-stmarco
Accept: application/dicom+json
…
{
…

…
},
…
```

#### The response returns 200 based on the sucess status code.  
```http
HTTP/1.1 200 OK
Content-Length: 220
Content-Type: application/dicom+json; charset=utf-8
...

…
```