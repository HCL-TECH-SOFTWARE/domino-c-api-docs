




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



**FilterRawRequest** **-** Filter raw
request (headers not processed yet)


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


                                                     char\*\*
ppHeaders,


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


 


        int
( \*SetHeader )( FilterContext \*pContext,


                                             char
\*pName,


                                             char
\*pValue,


                                             unsigned
int \*pErrID );


 


        int
( \*AddHeader )( FilterContext \*pContext,


                                             char
\*pHheader,


                                             unsigned
int \*pErrID );


 


        unsigned
int reserved;


}
FilterRawRequest;


 


**Description :**




requestMethod*-*is the request method. It can be one of the following:


*     kRequestNone:
            No HTTP request method is provided.


*     kRequestHEAD:           Method
is often used for testing hypertext links for validity, accessibility, and
recent modification.


*     kRequestGET:
             GET method - used to retrieve whatever information (in the form of
an entity) is identified by the Request-URL.


*     kRequestPOST:
          POST method - requests that the origin server accept the entity
enclosed in the request as a new subordinate of the resource identified by the
Request-URL in the Request-Line.


*     kRequestPUT:
             PUT method - requests that the enclosed entity be stored under the
supplied Request-URL.


*     kRequestDELETE:        DELETE
method - requests that the origin server delete the resource identified by the
Request-URL.


*     kRequestTRACE:         TRACE
method.


*     kRequestCONNECT:    CONNECT
method.


*     kRequestOPTIONS:     OPTIONS
method.


*     kRequestUNKNOWN:
  Unknown request method.


*     kRequestBAD:
             Bad request method. Error.


 


**int (
\*GetAllHeaders )( FilterContext \*pContext,**


**char\*\* ppHeaders,**


**unsigned int
\*pErrID );**


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
headers is the following: "<header1><\r\n><header2><\r\n>....<headern><\r\n><\r\n>".


 


pErrID is a
pointer to an unsigned integer that is set to 0 if successful, to an error code
otherwise. Possible error codes are: DSAPI\_INVALID\_ARGUMENT, DSAPI\_MEMORY\_ERROR
and DSAPI\_INTERNAL\_ERROR.


 


**int (
\*GetHeader )( FilterContext \*pContext,**


**char \*pName,**


**char \*pBuffer,**


**unsigned int bufferSize,**


**unsigned int \*pErrID );**


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
pointer to an unsigned integer that is set to 0 if successful, to DSAPI\_BUFFER\_TOO\_SMALL
if the supplied buffer is too small to contain the result.


 


**int (
\*SetHeader )( FilterContext \*pContext,**


**char \*pName,**


**char \*pValue,**


**unsigned int \*pErrID );**


This
callback function allows a filter to change the value of an existing input http
header. Note that if the http header does not exist, it is added to the list of
input headers.


 


Returns TRUE
if successful, FALSE otherwise.


 


pContext is
a pointer to the structure, FilterContext, and contains all the context data
needed by the DSAPI layer implementation to identify which request this
pertains to.


 


pName is a
pointer to a string containing the name of the http header to change. This
argument cannot be NULL or an empty string.


 


pValue is a
pointer to a string containing the value for the http header.


 


pErrID is a
pointer to an unsigned integer where to store a status code. The status code is
set to 0 if the operation is successful, to a non-zero value otherwise.


 


**int (
\*AddHeader )( FilterContext \*pContext,**


**char \*pHheader,**


**unsigned int \*pErrID );**


This
callback function allows a filter to add an http header to the list of the
input http headers. Note that if the http header already exists, its value is
changed to reflect the new value.


 


Return TRUE
if successful, FALSE otherwise.


 


pContext is
a pointer to the structure, FilterContext, and contains all the context data
needed by the DSAPI layer implementation to identify which request this
pertains to.


 


pHeader is a
pointer to a valid http header. The expected format is the same as the format
of input http headers, i.e., *<headerName:value>.*



pErrIDis
a pointer to an unsigned integer where to store a status code. The status code
is set to 0 if the operation is successful, to a non-zero value otherwise. The
only valid non-zero status in this case is DSAPI\_INVALID\_ARGUMENT which
indicates that an error in the format of the supplied header has been detected.


 


 reserved- is reserved for future use.


 




----------------------------------------------------------------------------------------------------------


 





