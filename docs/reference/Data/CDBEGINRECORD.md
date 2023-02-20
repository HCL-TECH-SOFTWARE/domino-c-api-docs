##### Data Type : Composite Data
##### CDBEGINRECORD - Defines the beginning of a CD record.
---
```
#include <editods.h>
```
**Description :**

This CD record defines the beginning of a series of CD Records.  Not all CD 
records are enclosed within a CDBEGINRECORD/CDENDRECORD combination.  For those 
CD records that are enclosed within a CDBEGINRECORD/CDENDRECORD combination, 
the Version element is defined in the following table.


CD Signature	Version Value	Symbol (if any)
SIG_CD_BAR	0	BAR_VERSION1
SIG_CD_OLEBEGIN	0	
SIG_CD_FIELD	0	
SIG_CD_EMBEDDEDCTL	0	EMBEDDEDCTL_VERSION1
SIG_CD_GRAPHIC	1	CDGRAPHIC_VERSION2
SIG_CD_V4HOTSPOTBEGIN	0	
SIG_CD_HORIZONTALRULE	1	CDHORIZONTALRULE_VERSION1
SIG_CD_KEYWORD	0	
SIG_CD_LINK2	0	LINK_VERSION1
SIG_CD_MAPELEMENT	1	CDMAPELEMENT_VERSION1
SIG_CD_AREAELEMENT	1	CDAREAELEMENT_VERSION1
SIG_CD_TEXT	0	
SIG_CD_PRETABLEBEGIN	1	
SIG_CD_BUTTON	0	BUTTON_VERSION1
SIG_CD_LAYER	2	CDLAYER_VERSION2

Header Defines the record as a CDBEGINRECORD.
Version Version of this element.  (Note see table above)
Signature Defines the CD Signature the CDBEGINRECORD is for.



**See Also :**
[BAR_VERSIONxxx](/reference/Symb/BAR_VERSIONxxx)
[BUTTON_VERSIONxxx](/reference/Symb/BUTTON_VERSIONxxx)
[CDAREAELEMENT_VERSIONxxx](/reference/Symb/CDAREAELEMENT_VERSIONxxx)
[CDBUTTON](/reference/Data/CDBUTTON)
[CDENDRECORD](/reference/Data/CDENDRECORD)
[CDGRAPHIC_VERSIONxxx](/reference/Symb/CDGRAPHIC_VERSIONxxx)
[CDHORIZONTALRULE_VERSIONxxx](/reference/Symb/CDHORIZONTALRULE_VERSIONxxx)
[CDMAPELEMENT_VERSIONxxx](/reference/Symb/CDMAPELEMENT_VERSIONxxx)
[EMBEDDEDCTL_VERSIONxxx](/reference/Symb/EMBEDDEDCTL_VERSIONxxx)
[LINK_VERSIONxxx](/reference/Symb/LINK_VERSIONxxx)
---
