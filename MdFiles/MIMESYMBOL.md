




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
-->




**Initial Release 7.0.2**



**Data Type : MIME**



**MIMESYMBOL** **-** symbolic
values representing MIME content types, subtypes, etc.  

  




**----------------------------------------------------------------------------------------------------------**



**#include
<mimedirs.h>**



**Definition :**



typedef enum
tagMimeWellKnownSymbolId {  

      MIME\_SYMBOL\_UNKNOWN                = 0,  

      MIME\_SYMBOL\_TEXT             = 1,      /\*  TEXT ... NONE - must stay in
this order for the \*/  

      MIME\_SYMBOL\_MULTIPART   = 2,      /\*  array of content-type handlers in
the 'inbound' \*/  

      MIME\_SYMBOL\_MESSAGE                 = 3,      /\* 
converter                                       \*/  

      MIME\_SYMBOL\_APPLICATION           = 4,  

      MIME\_SYMBOL\_IMAGE                       = 5,  

      MIME\_SYMBOL\_AUDIO                       = 6,  

      MIME\_SYMBOL\_VIDEO                       = 7,  

      MIME\_SYMBOL\_NONE            = 8,      /\*  last 'inbound' content-type
handler \*/  

  

      MIME\_SYMBOL\_TO,  

      MIME\_SYMBOL\_FROM,  

      MIME\_SYMBOL\_COMMENTS,  

      MIME\_SYMBOL\_DATE,  

      MIME\_SYMBOL\_ENCRYPTED,  

      MIME\_SYMBOL\_IN\_REPLY\_TO,  

      MIME\_SYMBOL\_KEYWORDS,  

      MIME\_SYMBOL\_PLAIN,  

      MIME\_SYMBOL\_BCC,  

      MIME\_SYMBOL\_CC,  

      MIME\_SYMBOL\_OCTET\_STREAM,  

      MIME\_SYMBOL\_SUBJECT,  

      MIME\_SYMBOL\_HTML,  

      MIME\_SYMBOL\_SENDER,  

      MIME\_SYMBOL\_REPLY\_TO,  

      MIME\_SYMBOL\_INLINE,  

      MIME\_SYMBOL\_ATTACHMENT,  

      MIME\_SYMBOL\_FILENAME,  

      MIME\_SYMBOL\_ALTERNATIVE,  

      MIME\_SYMBOL\_MIXED,  

      MIME\_SYMBOL\_7BIT,  

      MIME\_SYMBOL\_8BIT,  

      MIME\_SYMBOL\_QUOTED\_PRINTABLE,  

      MIME\_SYMBOL\_BASE64,  

      MIME\_SYMBOL\_BINARY,  

      MIME\_SYMBOL\_VERSION,  

      MIME\_SYMBOL\_CHARSET,  

      MIME\_SYMBOL\_BOUNDARY,  

      MIME\_SYMBOL\_NAME,  

      MIME\_SYMBOL\_MESSAGE\_ID,  

      MIME\_SYMBOL\_CONTENT\_TYPE,  

      MIME\_SYMBOL\_CONTENT\_TRANSFER\_ENCODING,  

      MIME\_SYMBOL\_CONTENT\_DISPOSITION,  

      MIME\_SYMBOL\_CONTENT\_MD5,  

      MIME\_SYMBOL\_CONTENT\_LANGUAGE,  

      MIME\_SYMBOL\_RECEIVED,  

      MIME\_SYMBOL\_NEWSGROUPS,  

      MIME\_SYMBOL\_PATH,  

      MIME\_SYMBOL\_FOLLOWUP\_TO,  

      MIME\_SYMBOL\_EXPIRES,  

      MIME\_SYMBOL\_REFERENCES,  

      MIME\_SYMBOL\_CONTROL,  

      MIME\_SYMBOL\_DISTRIBUTION,  

      MIME\_SYMBOL\_ORGANIZATION,  

      MIME\_SYMBOL\_SUMMARY,  

      MIME\_SYMBOL\_APPROVED,  

      MIME\_SYMBOL\_LINES,  

      MIME\_SYMBOL\_XREF,  

      MIME\_SYMBOL\_NNTP\_POSTING\_HOST,  

      MIME\_SYMBOL\_XNEWSREADER,  

      MIME\_SYMBOL\_XMAILER,  

      MIME\_SYMBOL\_RFC822,  

      MIME\_SYMBOL\_CONTENT\_DESCRIPTION,  

      MIME\_SYMBOL\_CONTENT\_ID,  

      MIME\_SYMBOL\_RELATED,  

      MIME\_SYMBOL\_GIF,  

      MIME\_SYMBOL\_JPEG,  

      MIME\_SYMBOL\_PARTIAL,  

      MIME\_SYMBOL\_EXTERNAL\_BODY,  

      MIME\_SYMBOL\_ENRICHED,  

      MIME\_SYMBOL\_MPEG,  

      MIME\_SYMBOL\_BASIC,  

      MIME\_SYMBOL\_START,  

      MIME\_SYMBOL\_PARALLEL,  

      MIME\_SYMBOL\_URL,  

      MIME\_SYMBOL\_ACCESS\_TYPE,  

      MIME\_SYMBOL\_EXPIRATION,  

      MIME\_SYMBOL\_SITE,  

      MIME\_SYMBOL\_SERVER,  

      MIME\_SYMBOL\_DIRECTORY,  

      MIME\_SYMBOL\_MODE,  

      MIME\_SYMBOL\_PERMISSION,  

      MIME\_SYMBOL\_SIZE,  

      MIME\_SYMBOL\_CONTENT\_BASE,  

      MIME\_SYMBOL\_CONTENT\_LOCATION,  

      MIME\_SYMBOL\_X\_X509\_USER\_CERT,  

      MIME\_SYMBOL\_X\_X509\_CA\_CERT,  

      MIME\_SYMBOL\_SIGNED,  

      MIME\_SYMBOL\_XPKCS7SIGNATURE,  

      MIME\_SYMBOL\_PKCS7SIGNATURE,  

      MIME\_SYMBOL\_XPKCS7MIME,  

      MIME\_SYMBOL\_PKCS7MIME,  

      MIME\_SYMBOL\_APPLEDOUBLE,  

      MIME\_SYMBOL\_APPLEFILE,  

      MIME\_SYMBOL\_METHOD,  

      MIME\_SYMBOL\_PROFILE,  

      MIME\_SYMBOL\_CALENDAR,  

      MIME\_SYMBOL\_VCARD21,  

      MIME\_SYMBOL\_X\_MAC\_TYPE,  

      MIME\_SYMBOL\_X\_MAC\_CREATOR,  

      MIME\_SYMBOL\_MAC\_BINHEX40,  

      MIME\_SYMBOL\_X\_NOTES\_ITEM,  

      MIME\_SYMBOL\_X\_UUENCODE,  

      MIME\_SYMBOL\_X\_UUE,  

      MIME\_SYMBOL\_UUENCODE,  

      MIME\_SYMBOL\_X\_LOTUS\_ENCAP,  

      MIME\_SYMBOL\_X\_LOTUS\_ENCAP1,  

      MIME\_SYMBOL\_X\_LOTUS\_ENCAP2,  

      MIME\_SYMBOL\_X\_MIMETRACK,  

      MIME\_SYMBOL\_DIGEST,  

      MIME\_SYMBOL\_32KADPCM,  

      MIME\_SYMBOL\_VOICE\_MESSAGE,  

      MIME\_SYMBOL\_BMP,  

      MIME\_SYMBOL\_DELIVERY\_STATUS,  

      MIME\_SYMBOL\_REPORT,  

      MIME\_SYMBOL\_RFC822\_HEADERS,  

      MIME\_SYMBOL\_PROTOCOL,  

      MIME\_SYMBOL\_CGM,  

      MIME\_SYMBOL\_CSS,  

      MIME\_SYMBOL\_POSTSCRIPT,  

      MIME\_SYMBOL\_RICHTEXT,  

      MIME\_SYMBOL\_TIFF,  

      MIME\_SYMBOL\_TNEF,


            MIME\_SYMBOL\_PNG,


  
        MIME\_SYMBOL\_EMBEDDED\_XML,


            MIME\_SYMBOL\_EMBEDDED\_JSON,


 


MIME\_SYMBOL\_LAST   
/\* for bounds checking -- no equivalent in mime\mimdrsym.cpp \*/  

  

} MimeWellKnownSymbolId;  

  

typedef MimeWellKnownSymbolId                     MIMESYMBOL;  

  




 


 


**Description :**



A MIMESYMBOL
is an enumeration type used by Notes/Domino to represent parsed MIME content
types, subtypes, parameter names, etc.


 


 




----------------------------------------------------------------------------------------------------------


 





