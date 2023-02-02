##### Data Type : Composite Data
##### CDEVENT - Structure which defines simple actions, fromulas or LotusScript for an image map..
---
##### #include <editods.h>
**Description :**
This CD structure defines simple actions, formulas or LotusScript within a 
given image map.

Header  Signature defining CDEVENT.
Flags  See EVENT_HAS_LIBRARIES.
EventType  See HTML_EVENT_xxx and HTML_EVENT_CLIENT_xxx for values.
ActionType  See ACTION_TYPE_xxx for values.
ActionLength
SignatureLength
Reserved[14]


If the ActionType is ACTION_TYPE_JAVASCRIPT, the ActionLength indicates the 
total length of the JavaScript code.  The CDEVENT record is followed by one or 
more CDBLOBPART records, each one of them is followed by a section of the 
JavaScript code.  Loop through all the CDBLOBPART records to read in the 
complete JavaScript code.
**See Also :**
[ACTION_TYPE_xxx](D:/md_files/ACTION_TYPE_xxx.md)
[CDBLOBPART](D:/md_files/CDBLOBPART.md)
[EVENT_HAS_LIBRARIES](D:/md_files/EVENT_HAS_LIBRARIES.md)
[HTML_EVENT_CLIENT_xxx](D:/md_files/HTML_EVENT_CLIENT_xxx.md)
[HTML_EVENT_xxx](D:/md_files/HTML_EVENT_xxx.md)
---
