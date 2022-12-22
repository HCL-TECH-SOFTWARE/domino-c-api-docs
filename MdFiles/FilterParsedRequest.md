




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 6**



**Data Type : DSAPI**



**FilterParsedRequest** **-** Filter
parsed request


**----------------------------------------------------------------------------------------------------------**



**#include
<dsapi.h>**



**Definition :**




typedef
struct {


        unsigned
int requestMethod;


 


        int
( \*GetAllHeaders )( FilterContext \*pContext,


                                                     char
\*\*ppHeaders,


                                                     unsigned
int \*pErrID );


 


        int
( \*GetHeader )( FilterContext \*pContext,


                                             char
\*pName,


                                             char
\*pBuffer,


                                             unsigned
int bufferSize,


                                             unsigned
int \*pErrID );


 


        unsigned
int reserved;


}
FilterParsedRequest;


 


**Description :**



After
pre-parsing of the http input headers, this structure could be utilized to
process a request again ( only access the headers, not change the headers ). 


 


int (
\*GetAllHeaders )( FilterContext \*pContext,


                                                char\*\*
ppHeaders,


                                                unsigned
int \*pErrID );


 


This
callback function allows the filter to gain access to the input http headers.


 


Returns the
byte count of the buffer containing the http headers.


 


pContext is
a pointer to the structure, FilterContext, and contains all the context data
needed by the DSAPI layer implementation to identify which request this
pertains to.


 


ppHeaders is
a pointer to a location where the DSAPI layer will store the pointer to a
buffer that will contain the input http headers. The format for the http
headers is the following:
"<header1><\r\n><header2><\r\n>....<headern><\r\n><\r\n>".


 


pErrID is a
pointer to an unsigned integer that is set to 0 if successful, to an error code
otherwise. Possible error codes are: DSAPI\_INVALID\_ARGUMENT, DSAPI\_MEMORY\_ERROR
and DSAPI\_INTERNAL\_ERROR.


 


 


int (
\*GetHeader )( FilterContext \*pContext,


                                         char
\*pName,


                                         char
\*pBuffer,


                                         unsigned
int bufferSize,


                                         unsigned
int \*pErrID );


 


This
callback function retrieves a single http header value. The http header name is
supplied. If the http header does not exist, an empty string is returned in the
supplied buffer.


 


Returns 0
for a hard failure (bad argument passed), the number of bytes valid in the
buffer containing the result if successful, or the required buffer size if the
buffer is too small to contain the result.


 


pContext is
a pointer to the structure, FilterContext, and contains all the context data
needed by the DSAPI layer implementation to identify which request this
pertains to.


 


pName is a
pointer to a string containing the name of the desired http header. This cannot
be NULL or an empty string.


 


pBuffer is a
pointer to a buffer where to store the result. This argument cannot be NULL.


 


bufferSize
is the size of supplied buffer.


 


pErrID is a
pointer to an unsigned integer that is set to 0 if successful, to
DSAPI\_BUFFER\_TOO\_SMALL if the supplied buffer is too small to contain the
result.


 




----------------------------------------------------------------------------------------------------------


 





