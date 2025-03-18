### Example 1: Get a specific performed workitem and return all attributes
      
```http
GET /radiology/modality-performed-procedure-steps/1.2.12345678.987654?includefield=all HTTP/1.1
Host: www.hospital-stmarco
Accept: application/dicom+json
```

#### The response returns the requested performed procedure step
Attributes according to: https://dicom.nema.org/dicom/2013/output/chtml/part04/sect_F.8.html 

```http
HTTP/1.1 200 OK
Content-Length: 2191
Content-Type: application/dicom+json; charset=utf-8
…
[ {
…
  , "00100010": { "vr": "PN", "Value": [{ "Alphabetic": "Doe^Sally" }] }
  , "00400253": { "vr": "SH", "Value": ["1.2.12345678.987654"] }
  , "00400242": { "vr": "SH", "Value": ["CTSCANNER"] }
  , "00400252": { "vr": "CS", "Value": ["COMPLETED"] }
  , …
  , "00400270": { "vr": "SQ", "Value":
    [ { "0020000D": { "vr": "UI", "Value": ["1.3.12.2.1107.5.99.3.30000008090412501082300000004"] }
      , "00080050": { "vr": "SH", "Value": ["1"] }
      , "00400007": { "vr": "LO", "Value": ["Specials^04a_HeadCTA"] }
      , "00401001": { "vr": "SH", "Value": ["P-ID-22"] }
      , "00400009": { "vr": "SH", "Value": ["PS-ID-23"] }
      …
      }
    , …
    ] }
  , …  
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
]
 
```

### Example 2: Get a specific performed workitem and return only specific attributes
      
```http
GET /radiology/modality-performed-procedure-steps/1.2.12345678.987654?includefield=00100010,00400242,00400252 HTTP/1.1
Host: www.hospital-stmarco
Accept: application/dicom+json
```

#### The response returns the requested performed procedure step
Attributes according to: https://dicom.nema.org/dicom/2013/output/chtml/part04/sect_F.8.html 

```http
HTTP/1.1 200 OK
Content-Length: 2191
Content-Type: application/dicom+json; charset=utf-8
…
[ {
  , "00100010": { "vr": "PN", "Value": [{ "Alphabetic": "Doe^Sally" }] }
  , "00400242": { "vr": "SH", "Value": ["CTSCANNER"] }
  , "00400252": { "vr": "CS", "Value": ["COMPLETED"] }
}
]
