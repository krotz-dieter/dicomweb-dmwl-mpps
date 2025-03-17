### Example: Report progress on workitem with content produced from the acquisition, maps to an N-SET with updated information containing the series and image produced

#### Using DICOM tags and application/dicom+json media type:  
Performed Series Sequence (0040,0340) SQ  
-> Performing Physician's Name (0008,1050)  
-> Protocol Name (0018,1030)  
-> Series Instance UID (0020,000E)   
-> Series Description (0008,103E)  
-> Referenced Image Sequence (0008,1140)  
->-> Referenced SOP Class UID (0008,1150)  
->-> Referenced SOP Instance UID (0008,1155)  

```http
PATCH /radiology/modality-performed-procedure-steps/1.2.12345678.987654 HTTP/1.1
Host: www.hospital-stmarco
Content-Type: application/dicom+json
…
{ …
, "00400340": { "vr": "SQ", "Value":
  [ { "00081050": { "vr": "PN", "Value": [{ "Alphabetic": "House^Gregory" }] }
    , "00181030": { "vr": "LO", "Value": ["Special^99a_HeadCTA"] }
    , "0020000E": { "vr": "UI", "Value": ["1.3.12.2.1107.5.99.3.99.197132.30000020040718322840300000007"] }
    , "0008103E": { "vr": "LO", "Value": ["Head 1.50 Hr64 ax"] }
    , …     
    , "00081140": { "vr": "SQ", "Value":
      [ { "00081150": { "vr": "UI", "Value": ["1.2.840.10008.5.1.4.1.1.2"] }
        , "00081155": { "vr": "UI", "Value": ["1.3.12.2.1107.5.99.3.99.197132.3000002004071832284030000520"] }
        , …
        }
      , { "00081150": { "vr": "UI", "Value": ["1.2.840.10008.5.1.4.1.1.2"] }
        , "00081155": { "vr": "UI", "Value": ["1.3.12.2.1107.5.99.3.99.197132.3000002004071832284030000521"] }
        , …
        }
      , …
      ] }
    , … 
    }
  , …
  ] }
, …
}
…

```

#### The response returns 200 based on the sucess status code.  
```http
HTTP/1.1 200 OK

```

