##### Data Type : Composite Data
##### CDENDRECORD - Defines the end of a series of CD Records.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   BSIG Header;    /* Signature and length of this record */
   WORD Version;  
   WORD Signature; /* Signature of record end is for */ 
} CDENDRECORD;
```

**Description :**

This CD record defines the end of a series of CD records.  Not all CD records are enclosed within a CDBEGINRECORD/CDENDRECORD combination.  For those CD records that are enclosed within a CDBEGINRECORD/CDENDRECORD combination, the Version element is defined in the following table.<br>
<div align="center"><br>

<table border="1">
<tr valign="top"><td width="240"><div align="center"><b>CD Signature</b></div></td><td width="72"><div align="center"><b>Version Value</b></div></td><td width="240"><div align="center"><b>Symbol (if any)</b></div></td></tr>

<tr valign="top"><td width="240">SIG_CD_BAR</td><td width="72"><div align="center">0</div></td><td width="240">BAR_VERSION1</td></tr>

<tr valign="top"><td width="240">SIG_CD_OLEBEGIN</td><td width="72"><div align="center">0</div></td><td width="240"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="240">SIG_CD_FIELD</td><td width="72"><div align="center">0</div></td><td width="240"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="240">SIG_CD_EMBEDDEDCTL</td><td width="72"><div align="center">0</div></td><td width="240">EMBEDDEDCTL_VERSION1</td></tr>

<tr valign="top"><td width="240">SIG_CD_GRAPHIC</td><td width="72"><div align="center">1</div></td><td width="240">CDGRAPHIC_VERSION2</td></tr>

<tr valign="top"><td width="240">SIG_CD_V4HOTSPOTBEGIN</td><td width="72"><div align="center">0</div></td><td width="240"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="240">SIG_CD_HORIZONTALRULE</td><td width="72"><div align="center">1</div></td><td width="240">CDHORIZONTALRULE_VERSION1</td></tr>

<tr valign="top"><td width="240">SIG_CD_KEYWORD</td><td width="72"><div align="center">0</div></td><td width="240"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="240">SIG_CD_LINK2</td><td width="72"><div align="center">0</div></td><td width="240">LINK_VERSION1</td></tr>

<tr valign="top"><td width="240">SIG_CD_MAPELEMENT</td><td width="72"><div align="center">1</div></td><td width="240">CDMAPELEMENT_VERSION1</td></tr>

<tr valign="top"><td width="240">SIG_CD_AREAELEMENT</td><td width="72"><div align="center">1</div></td><td width="240">CDAREAELEMENT_VERSION1</td></tr>

<tr valign="top"><td width="240">SIG_CD_TEXT</td><td width="72"><div align="center">0</div></td><td width="240"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>

<tr valign="top"><td width="240">SIG_CD_PRETABLEBEGIN</td><td width="72"><div align="center">1</div></td><td width="240"><img width="1" height="1" src="/icons/ecblank.gif" border="0" alt=""></td></tr>
</table>
</div>
<ul>Header	Defines this record as a CDENDRECORD<br>
Version	Defines the version of this element.  (Note see table above)<br>
Signature	Defines the CD Signature the CDENDRECORD is for.<br>
</ul>



**See Also :**
[BAR_VERSIONxxx](/domino-c-api-docs/reference/Symb/BAR_VERSIONxxx)
[CDAREAELEMENT_VERSIONxxx](/domino-c-api-docs/reference/Symb/CDAREAELEMENT_VERSIONxxx)
[CDBEGINRECORD](/domino-c-api-docs/reference/Data/CDBEGINRECORD)
[CDGRAPHIC_VERSIONxxx](/domino-c-api-docs/reference/Symb/CDGRAPHIC_VERSIONxxx)
[CDHORIZONTALRULE_VERSIONxxx](/domino-c-api-docs/reference/Symb/CDHORIZONTALRULE_VERSIONxxx)
[CDMAPELEMENT_VERSIONxxx](/domino-c-api-docs/reference/Symb/CDMAPELEMENT_VERSIONxxx)
[EMBEDDEDCTL_VERSIONxxx](/domino-c-api-docs/reference/Symb/EMBEDDEDCTL_VERSIONxxx)
[LINK_VERSIONxxx](/domino-c-api-docs/reference/Symb/LINK_VERSIONxxx)
---
