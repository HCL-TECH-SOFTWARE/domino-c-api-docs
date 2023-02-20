##### Data Type : Composite Data
##### CDAREAELEMENT - Structure defining an HTML AREA element.
---
```
#include <editods.h>
```
**Description :**

An AREA element defines the shape and coordinates of a region within a client 
side image MAP. 

Header  Identifies the record as a CDAREAELEMENT
Flags  Reserved for future use
Shape  Shape of area (see AREA_SHAPE_xxx)
TabIndex  Tab selection order
AccessKey  The accelerator key for the object
Reserved[16] Reserved

This structure is followed by the description of the shape.  If AREA_SHAPE_xxx 
equals AREA_SHAPE_RECT then we are dealing with a rectangle whose area is 
defined in CDRECT.  If AREA_SHAPE_xxx equals AREA_SHAPE_CIRCLE then we are 
dealing with a circle whose area is defined in CDRECT.  If AREA_SHAPE_xxx 
equals AREA_SHAPE_POLYGON then we are dealing with a polygon whose area is 
defined with CDBPOINT.


**See Also :**
[AREA_SHAPE_xxx](/reference/Symb/AREA_SHAPE_xxx)
[CDAREAELEMENT_VERSIONxxx](/reference/Symb/CDAREAELEMENT_VERSIONxxx)
[CDMAPELEMENT](/reference/Data/CDMAPELEMENT)
[CDPOINT](/reference/Data/CDPOINT)
[CDRECT](/reference/Data/CDRECT)
---
