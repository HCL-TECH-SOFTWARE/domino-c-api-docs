




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




**Initial Release 5.0.3**



**Data Type : DSAPI**



**EventFlags** **-** DSAPI
Defined events for a filter.


**----------------------------------------------------------------------------------------------------------**



**#include
<dsapi.h>**



**Definition :**



typedef enum {  

    kFilterRawRequest             = 0x01,  

    kFilterParsedRequest   = 0x02,  

    kFilterAuthUser               = 0x04,  

    kFilterUserNameList    = 0x08,  

    kFilterMapURL          = 0x10,


        kFilterResponse               =
0x20,


        kFilterRawWrite               =
0x40,  

        kFilterEndRequest             = 0x80,  

        kFilterStartRequest    = 0x100,  

        kFilterPostTranslate   = 0x200,  

        kFilterAuthorized             = 0x400,  

        kFilterProcessRequest  = 0x800,  

        kFilterAuthenticate    = 0x2000,  

        kFilterRewriteURL             = 0x4000,


 


        kFilterAny                    =
0x6FFF & ~kFilterAuthUser           /\*  \*/  

} EventFlags;


#define
kFilterTranslateRequest       0x10    /\* Same as kFilterMapURL event. \*/


 


**Description :**



EventFlags
indicate for which event(s) the filter will act upon.  The events can be OR'ed
to specifiy more than one event.


 


kFilterRawRequest             -
Notification that the input headers for a request are ready for processing.


kFilterParsedRequest         -
Notification the input http headers have been parsed and are available.


kFilterAuthUser                   -
Backward compatibility of authentication and authorizing a web user. For new
filters, use the kFilterAuthenticate and kFilterAuthorized events instead.


kFilterUserNameList           -
Notification that the user's group list is about to be computed. Filters can
override the default implementation of user's group list generation.


kFilterMapURL                    -
Notification that a request is about to be translated to a resource.  (Note
that kFilterTranslateRequest is equivalent to kFilterMapURL)


      kFilterResponse       
         - Notification that the headers for a response are about to be sent to
the client. A filter that supports this event can                                                        change
the response given to the user for a given request.


      kFilterRawWrite                  -
 Notification
that a response data buffer is about to be sent to the client. A filter
supporting this event can change the                                                  data
before it is sent.


kFilterEndRequest              -
Notification that the servicing of an http request is finished. It is now time
to clean up and release any global resources the filter is holding.


kFilterStartRequest             -
Notification that we are about to start servicing a new http request.


kFilterPostTranslate            -
Notification that a request has been translated. A filter could change which
resource we are about to access.


kFilterAuthorized                 -
Notification that the authorization phase is about to take place. A filter can
override the default authorization implementation by supporting this event.


kFilterProcessRequest        -
Notification that we are about to process the request after all previous steps
have taken place. A filter can override the default implementation of servicing
some request by supporting this event.


kFilterAuthenticate              -
Notification that the authentication phase is about to start. Filters can
override the default implementation of authentication by supporting this event.


kFilterRewriteURL               -
Notification to change the original URL. A filter might choose to change the
original URL.


kFilterAny                           -
All event types


 


kFilterTranslateRequest         
- This is equivalent to the kFilterMapURL event flag


 


See
the chapter, Domino Web Server Application Interface (DSAPI), in the *Lotus C
API User Guide* for details.


 **See Also :**


**[FilterAuthenticate](FilterAuthenticate.md)**


**[FilterInitData](FilterInitData.md)**


**[FilterUserNameList](FilterUserNameList.md)**



----------------------------------------------------------------------------------------------------------


 





