




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
 /\* List Definitions \*/
 ol
 {margin-bottom:0cm;}
ul
 {margin-bottom:0cm;}
-->




**Initial Release 5.0.8**



**Function : Hotspot**



**NSFHotSpotSign** **- Sign the
source and object code associated with a hotspot on a document.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFHotSpotSign(**  

      BYTE \*pSource,  

      DWORD  dwSourceLength,  

      BYTE \*pObject,  

      DWORD  dwObjectLength,  

      DHANDLE \*hSigData,  

      DWORD \*dwSigLength**);**



**Description :**



When the
hotspot type is HOTSPOTREC\_TYPE\_ACTIVEOBJECT (for example: a Java code, or a
Lotus Script), you can sign the source and the object code with this API.  The
signature is included at the end of the CDHOTSPOTBEGIN record.  


 


Here are
some points for creating and signing a Java applet:  

  




1.      Creating a
signature data buffer, copying the ACTIVEOBJECT, the ACTIVEOBJECTPARAM and the
ACTIVEOBJECTSTORAGELINK structures and their associate variable data to this
buffer.


2.      Signing the
signature data buffer with the NSFHotSpotSign API.


3.      Now,
creating a CDHOTSPOTBEGIN CD buffer and starting to fill it up with
information.


4.       The
CDHOTSPOTBEGIN.Flags field should include HOTSPOTREC\_RUNFLAG\_SIGNED.


5.      The
CDHOTSPOTBEGIN.Header.Length field should include a WORD (for the value of the
signature length) and the length of the signature.


6.      Copying the
CDHOTSPOTBEGIN structure to the CD buffer.


7.      Copying the
ACTIVEOBJECT,the ACTIVEOJBECTPARAM, and the ACTIVEOBJECTSTORAGELINK structures
and their associate data to the CD buffer  (yes, they are the same as the data
in the signature data buffer created above, so you can just copy the signature
data buffer to the CD buffer.)


8.      Coping the
signature length and the signature to the CDHOTSPOTBEGIN buffer following the
variable data of ACTIVEOBJECTSTORAGELINK.


9.      Be sure to
free hSigData when it's done.  

  




 


**Parameters :**



Input :  

pSource  -  Pointer of the source to be signed.  

  

dwSourceLength  -  Total length of the source  to be signed.  

  

pObject  -  Pointer of the generated object code of the pSource content, if
existed.  Specify NULL, if the pSource does not generate object code.  

  

dwObjectLength  -  Total length of the object code.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - The hotspot was successfully signed.  

ERR\_xxx - STATUS returned from a lower level Notes function.  This value can be
passed to OSLoadString to obtain a text string that can be presented in a
dialog box or log entry.  

  

  

hSigData  -  Handle to the memory that contains the signature.  

  

dwSigLength  -  Length of the memory that contains the signature.  

  




 **See Also :**


**[CDHOTSPOTBEGIN](CDHOTSPOTBEGIN.md)**


**[HOTSPOTREC\_RUNFLAG\_xxx](HOTSPOTREC_RUNFLAG_xxx.md)**


**[NSFNoteSignHotspots](NSFNoteSignHotspots.md)**



----------------------------------------------------------------------------------------------------------


 





