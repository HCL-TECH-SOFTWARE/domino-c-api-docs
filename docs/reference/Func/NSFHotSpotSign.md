##### Function : Hotspot
##### NSFHotSpotSign - Sign the source and object code associated with a hotspot on a document.
---
```
#include <nsfnote.h>
STATUS LNPUBLIC NSFHotSpotSign(

	BYTE *pSource,
	DWORD  dwSourceLength,
	BYTE *pObject,
	DWORD  dwObjectLength,
	DHANDLE *hSigData,
	DWORD *dwSigLength);
```
**Description :**

When the hotspot type is HOTSPOTREC_TYPE_ACTIVEOBJECT (for example: a Java 
code, or a Lotus Script), you can sign the source and the object code with this 
API.  The signature is included at the end of the CDHOTSPOTBEGIN record.  

Here are some points for creating and signing a Java applet:

Creating a signature data buffer, copying the ACTIVEOBJECT, the 
ACTIVEOBJECTPARAM and the ACTIVEOBJECTSTORAGELINK structures and their 
associate variable data to this buffer.
Signing the signature data buffer with the NSFHotSpotSign API.
Now, creating a CDHOTSPOTBEGIN CD buffer and starting to fill it up with 
information.
 The CDHOTSPOTBEGIN.Flags field should include HOTSPOTREC_RUNFLAG_SIGNED.
The CDHOTSPOTBEGIN.Header.Length field should include a WORD (for the value of 
the signature length) and the length of the signature.
Copying the CDHOTSPOTBEGIN structure to the CD buffer.
Copying the ACTIVEOBJECT,the ACTIVEOJBECTPARAM, and the ACTIVEOBJECTSTORAGELINK 
structures and their associate data to the CD buffer  (yes, they are the same 
as the data in the signature data buffer created above, so you can just copy 
the signature data buffer to the CD buffer.)
Coping the signature length and the signature to the CDHOTSPOTBEGIN buffer 
following the variable data of ACTIVEOBJECTSTORAGELINK.
Be sure to free hSigData when it's done.


**Parameters :**
Input :
pSource  -  Pointer of the source to be signed.

dwSourceLength  -  Total length of the source  to be signed.

pObject  -  Pointer of the generated object code of the pSource content, if existed.  Specify NULL, if the pSource does not generate object code.

dwObjectLength  -  Total length of the object code.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - The hotspot was successfully signed.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.


hSigData  -  Handle to the memory that contains the signature.

dwSigLength  -  Length of the memory that contains the signature.


**See Also :**
[CDHOTSPOTBEGIN](/domino-c-api-docs/reference/Data/CDHOTSPOTBEGIN)
[HOTSPOTREC_RUNFLAG_xxx](/domino-c-api-docs/reference/Symb/HOTSPOTREC_RUNFLAG_xxx)
[NSFNoteSignHotspots](/domino-c-api-docs/reference/Func/NSFNoteSignHotspots)
---
