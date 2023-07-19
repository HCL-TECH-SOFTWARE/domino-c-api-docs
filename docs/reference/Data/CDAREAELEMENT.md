##### Data Type : Composite Data
##### CDAREAELEMENT - Structure defining an HTML AREA element.
---
```
#include <editods.h>
```

**Definition :**

typedef struct {
   WSIG  Header;
   DWORD Flags;        /* reserved for future use */
   WORD  Shape;        /* one of AREA_SHAPE_xxx */
   WORD  TabIndex;
   WORD  AccessKey;
   BYTE  Reserved[16];

/* variable length items follow:
 * If Shape == rect
 *   CDRECT
 * else if Shape == circle
 *   NOTE: points for the rect the circle is drawn in CDRECT
 * else if Shape == polygon
 *   WORD  numPts
 *   CDPOINT 1
 *   CDPOINT 2
 *   ...
 *   CDPOINT n
 * else if Shape == default
 *   No points
 */
} CDAREAELEMENT;

**Description :**

An AREA element defines the shape and coordinates of a region within a client side image MAP. 
<ul><br>
<br>
Header		Identifies the record as a CDAREAELEMENT<br>
Flags		Reserved for future use<br>
Shape		Shape of area (see AREA_SHAPE_xxx)<br>
TabIndex		Tab selection order<br>
AccessKey		The accelerator key for the object<br>
Reserved[16]	Reserved<br>
<br>
This structure is followed by the description of the shape.  If AREA_SHAPE_xxx equals AREA_SHAPE_RECT then we are dealing with a rectangle whose area is defined in CDRECT.  If AREA_SHAPE_xxx equals AREA_SHAPE_CIRCLE then we are dealing with a circle whose area is defined in CDRECT.  If AREA_SHAPE_xxx equals AREA_SHAPE_POLYGON then we are dealing with a polygon whose area is defined with CDBPOINT.</ul>



**See Also :**
[AREA_SHAPE_xxx](/domino-c-api-docs/reference/Symb/AREA_SHAPE_xxx)
[CDAREAELEMENT_VERSIONxxx](/domino-c-api-docs/reference/Symb/CDAREAELEMENT_VERSIONxxx)
[CDMAPELEMENT](/domino-c-api-docs/reference/Data/CDMAPELEMENT)
[CDPOINT](/domino-c-api-docs/reference/Data/CDPOINT)
[CDRECT](/domino-c-api-docs/reference/Data/CDRECT)
---
