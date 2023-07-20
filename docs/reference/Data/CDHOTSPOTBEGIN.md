##### Data Type : Composite Data
##### CDHOTSPOTBEGIN - Specifies the start of a hotspot.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG  Header; /* Signature and length of this record */ 
   WORD  Type;
   DWORD Flags;
   WORD  DataLength;
/* Data follows... */
	/*  if HOTSPOTREC_RUNFLAG_SIGNED, WORD SigLen then SigData follows. */
} CDHOTSPOTBEGIN;
```

**Description :**

This structure specifies the start of a &quot;hot&quot; region in a rich text field.  Clicking on a hot region causes some other action to occur.  For instance, clicking on a popup will cause a block of text associated with that popup to be displayed.
<ul><br>
<br>
Normally, each CDHOTSPOTBEGIN record is followed by records describing the hotspot and any associated action formula and, finally, a CDHOTSPOTEND record.  There are special cases for Release 4.x, Release 5.x and 6 hotspot records which have either Lotus Script or Release 4.x (or 5.x or 6) actions associated with them.  These hotspots contain a CDHOTSPOTBEGIN record with the signature SIG_CD_V4HOTSPOTBEGIN (or SIG_CD_V5HOTSPOTBEGIN or SIG_CD_V6HOTSPOTBEGIN_CONTINUATION), and a CDHOTSPOTEND record with the signature SIG_CD_V4HOTSPOTEND (or SIG_CD_V5HOTSPOTEND).</ul>

<ul>The fields in this record are:</ul>
<br>
<tt><font size="2">&nbsp; Header: &nbsp; &nbsp; Defines this composite data item as a</font></tt>
<ul><tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; CDHOTSPOTBEGIN item.<br>
 &nbsp;Type: &nbsp; &nbsp; &nbsp; Specifies the type of hotspot.</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; See HOTSPOTREC_TYPE_xxx.<br>
 &nbsp;Flags: &nbsp; &nbsp; &nbsp;Defines some of the hotspot's attributes.</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; See HOTSPOTREC_RUNFLAG_xxx<br>
 &nbsp;DataLength: Specifies the length of the variable-length</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; data for this item.</font></tt><br>
<br>
The above fields are then followed by some variable length data, the format of which is dependent on the type of hotspot that is being defined.  The variable length data for the different hotspot types is as follows:<br>

<ul>
<ul type="disc">
<li>If the Type is HOTSPOTREC_TYPE_POPUP and the  HOTSPOTREC_RUNFLAG_FORMULA flag is not set, then the variable-length data is a packed string containing the popup's static text.
<li>If the Type is HOTSPOTREC_TYPE_POPUP and the  HOTSPOTREC_RUNFLAG_FORMULA flag is set, then the variable-length data is the compiled formula that will generate the popup's text.
<li>If theType is HOTSPOTREC_TYPE_BUTTON then the variable-length data is the button's compiled formula.
<li>If the Type is HOTSPOTREC_TYPE_FILE then the variable-length data consists of two null-terminated strings. The first string is the internal unique file name assigned to the attached file by Domino or Notes. The second string is the original name of the file.
<li>If the Type is HOTSPOTREC_TYPE_HOTLINK and the HOTSPOTREC_RUNFLAG_INOTES flag is set, then the variable-length data is a packed string containing the URL's static text.
<li>If the flag HOTSPOTREC_RUNFLAG_SIGNED is set, the variable-length data determined by the hotspot type and other flags is followed by a WORD containing the length of the digital signature, then the digital signature for the hotspot.</ul>
</ul>
<br>
Note that rich text fields are items of type TYPE_COMPOSITE. Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on CD record structures such as this when accessing rich text item data in a note.</ul>



**See Also :**
[CDHOTSPOTEND](/domino-c-api-docs/reference/Data/CDHOTSPOTEND)
[HOTSPOTREC_TYPE_xxx](/domino-c-api-docs/reference/Symb/HOTSPOTREC_TYPE_xxx)
[HOTSPOTREC_RUNFLAG_xxx](/domino-c-api-docs/reference/Symb/HOTSPOTREC_RUNFLAG_xxx)
---
