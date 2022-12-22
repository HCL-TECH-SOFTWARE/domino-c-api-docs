




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




**Initial Release 5.0**



**Symbolic Value : Character
Manipulation**



**NLS\_CS\_xxx** **-** Character
Set IDs


**----------------------------------------------------------------------------------------------------------**



**#include <nls.h>**


 **Symbolic Values :**      NLS\_CS\_xxx            -  see Description  

  




**Description :**


#define
NLS\_CS\_DEFAULT           0xFFFF


#define
NLS\_CS\_LICS              0x0000 /\* Lotus Intl Char Set (WK1) \*/


#define
NLS\_CS\_IBMCP851          0x0001


#define
NLS\_CS\_IBMCP852          0x0002


#define
NLS\_CS\_IBMCP853          0x0003


#define
NLS\_CS\_IBMCP857          0x0004


#define
NLS\_CS\_IBMCP862          0x0005


#define
NLS\_CS\_IBMCP864          0x0006


#define
NLS\_CS\_IBMCP866          0x0007


#define
NLS\_CS\_IBMCP437          0x0008


#define
NLS\_CS\_IBMCP850          0x0009


#define
NLS\_CS\_IBMCP855          0x000A


#define
NLS\_CS\_IBMCP860          0x000B


#define
NLS\_CS\_IBMCP861          0x000C


#define
NLS\_CS\_IBMCP863          0x000D


#define
NLS\_CS\_IBMCP865          0x000E


#define
NLS\_CS\_IBMCP869          0x000F


#define
NLS\_CS\_IBMCP874          0x0090


#define
NLS\_CS\_IBMCP899          0x0011


#define
NLS\_CS\_IBMCP932          0x0012


#define
NLS\_CS\_IBMCP942          0x0012 /\* 932  942 for Lotus \*/


#define
NLS\_CS\_IBMCP943          0x0012


#define
NLS\_CS\_IBMCP5039         0x0012


#define
NLS\_CS\_IBMCP891          0x0013


#define
NLS\_CS\_DECMCS            0x0014 /\* DEC Multinational Char Set \*/


 


#define
NLS\_CS\_EUC               0x0017 /\* Extended Unix Code \*/


#define
NLS\_CS\_KS                0x0018 /\* Korean - KSC 5601 \*/


#define
NLS\_CS\_IBMCP949          0x0018


#define
NLS\_CS\_TCA               0x0019


#define
NLS\_CS\_BIG5              0x001A /\* Taiwan Chinese - traditional \*/


#define
NLS\_CS\_IBMCP950          0x001A


#define
NLS\_CS\_GB                0x001B /\* PRC Chinese - simplified \*/


#define
NLS\_CS\_IBMCP936          0x001B


#define
NLS\_CS\_NECESJIS          0x001C /\* NEC Extended Shift-JIS \*/


#define
NLS\_CS\_ISO646            0x001F /\* aka 'ASCII' \*/


#define
NLS\_CS\_ASCII             0x001F


#define
NLS\_CS\_ISO88591          0x0020 /\* ISO Latin-1 \*/


#define
NLS\_CS\_IBMCP819          0x0020


#define
NLS\_CS\_ISO88592          0x0021 /\* ISO Latin-2 (E. Europe) \*/


#define
NLS\_CS\_IBMCP912          0x0021


#define
NLS\_CS\_ISO88593          0x0022


#define
NLS\_CS\_ISO88594          0x0023


#define
NLS\_CS\_ISO88595          0x0024


#define
NLS\_CS\_IBMCP915          0x0024


#define
NLS\_CS\_ISO88596          0x0025


#define
NLS\_CS\_IBMCP1008         0x0025


#define
NLS\_CS\_ISO88597          0x0026


#define
NLS\_CS\_IBMCP813          0x0026


#define
NLS\_CS\_ISO88598          0x0027


#define
NLS\_CS\_IBMCP916          0x0027


#define
NLS\_CS\_ISO88599          0x0028


#define
NLS\_CS\_IBMCP920          0x0028


 


#define
NLS\_CS\_HPROMAN           0x0030 /\* HP Roman (LaserJet) \*/


#define
NLS\_CS\_HPGREEK           0x0031 /\* HP Roman (LaserJet) \*/


#define
NLS\_CS\_HPTURKISH         0x0032 /\* HP Roman (LaserJet) \*/


#define
NLS\_CS\_HPHEBREW          0x0034


#define
NLS\_CS\_HPARABIC          0x0035


#define
NLS\_CS\_HPTHAI            0x0036


#define
NLS\_CS\_HPJAPAN           0x0037


#define
NLS\_CS\_HPKANA            0x0038


#define
NLS\_CS\_HPKOREA           0x0039


#define
NLS\_CS\_HPPRC             0x003A


#define
NLS\_CS\_HPROC             0x003B  /\* Traditional Chinese \*/


 


 


#define
NLS\_CS\_IBMCP37           0x0040 /\* EBCDIC \*/


#define
NLS\_CS\_IBMCP273          0x0041


#define
NLS\_CS\_IBMCP278          0x0042


#define
NLS\_CS\_IBMCP280          0x0043


#define
NLS\_CS\_IBMCP284          0x0044


#define NLS\_CS\_IBMCP285         
0x0045


#define
NLS\_CS\_IBMCP290          0x0046


#define
NLS\_CS\_IBMCP297          0x0047


#define
NLS\_CS\_IBMCP500          0x0048


#define
NLS\_CS\_IBMCP277          0x004C


#define
NLS\_CS\_IBMCP1047         0x004D


#define
NLS\_CS\_IBMCP1250         0x0050 /\* Windows ANSI \*/


#define
NLS\_CS\_IBMCP1251         0x0051


#define
NLS\_CS\_IBMCP1252         0x0052


#define
NLS\_CS\_ANSI              0X0052


#define
NLS\_CS\_IBMCP1253         0x0053


#define
NLS\_CS\_IBMCP1254         0x0054


#define
NLS\_CS\_IBMCP1255         0x0055


#define
NLS\_CS\_IBMCP1256         0x0056


#define
NLS\_CS\_IBMCP1257         0x0057


#define
NLS\_CS\_MACSCRIPT0        0x0060 /\* Mac Roman \*/


#define
NLS\_CS\_MACSCRIPT1        NLS\_CS\_IBMCP932  /\*0x0061\*/


#define
NLS\_CS\_MACSCRIPT2        NLS\_CS\_GB        /\*0x0062\*/


#define
NLS\_CS\_MACSCRIPT3        NLS\_CS\_KS        /\*0x0063\*/


#define
NLS\_CS\_MACSCRIPT4        NLS\_CS\_ISO88596  /\*0x0064\*/


#define
NLS\_CS\_MACSCRIPT5        NLS\_CS\_ISO88598  /\*0x0065\*/


#define
NLS\_CS\_MACSCRIPT6        0x0066 /\* cckSTRCharSetISO88597 \*/


#define
NLS\_CS\_MACSCRIPT7        0x0067 /\* cckSTRCharSetISO88595 \*/


#define
NLS\_CS\_MACSCRIPT8        0x0068


#define
NLS\_CS\_MACSCRIPT9        0x0069


#define
NLS\_CS\_MACSCRIPT10       0x006A


#define
NLS\_CS\_MACSCRIPT11       0x006B


#define
NLS\_CS\_MACSCRIPT12       0x006C


#define
NLS\_CS\_MACSCRIPT13       0x006D


#define
NLS\_CS\_MACSCRIPT14       0x006E


#define
NLS\_CS\_MACSCRIPT15       0x006F


#define
NLS\_CS\_MACSCRIPT16       0x0070


#define
NLS\_CS\_MACSCRIPT17       0x0071


#define
NLS\_CS\_MACSCRIPT18       0x0072


#define
NLS\_CS\_MACSCRIPT19       0x0073


#define
NLS\_CS\_MACSCRIPT20       0x0074


#define
NLS\_CS\_MACSCRIPT21       0x0075


#define
NLS\_CS\_MACSCRIPT22       0x0076


#define
NLS\_CS\_MACSCRIPT23       0x0077


#define
NLS\_CS\_MACSCRIPT24       0x0078


#define
NLS\_CS\_MACSCRIPT25       0x0079


#define
NLS\_CS\_MACSCRIPT26       0x007A


#define
NLS\_CS\_MACSCRIPT27       0x007B


#define
NLS\_CS\_MACSCRIPT28       0x007C


#define
NLS\_CS\_MACSCRIPT29       0x007D


#define
NLS\_CS\_MACSCRIPT30       0x007E


#define
NLS\_CS\_MACSCRIPT31       0x007F


#define
NLS\_CS\_MACSCRIPT32       0x0080


#define
NLS\_CS\_MACSCRIPT0CROATIAN    0x0081


#define
NLS\_CS\_MACSCRIPT0GREEK       0x0082


#define
NLS\_CS\_MACSCRIPT0ICELANDIC   0x0083


#define
NLS\_CS\_MACSCRIPT0ROMANIAN    0x0084


#define
NLS\_CS\_MACSCRIPT0TURKISH     0x0085


#define
NLS\_CS\_THAI              0x0090 /\* MS Thai Windows \*/


#define
NLS\_CS\_IBMCP1200         0x00A0 /\* Unicode/ISO 10646 \*/


#define
NLS\_CS\_UNICODE           0x00A0


#define
NLS\_CS\_UNICODE           0x00A0


#define
NLS\_CS\_ISO10646          0x00A0 /\* Also Unicode \*/


#define
NLS\_CS\_UTF7              0x00AA /\* Unicode Transformation Formats \*/


#define
NLS\_CS\_UTF8              0x00AB


#define
NLS\_CS\_LMBCS10           0x0100 /\* Version 1.0 is the only one \*/


#define
NLS\_CS\_LMBCS11           0x0101


#define
NLS\_CS\_LMBCS12           0x0102


#define
NLS\_CS\_LMBCS             0x0100


#define
NLS\_CS\_DECNRCUK          0x0A00 /\* DEC National Replacement Char \*/


#define
NLS\_CS\_DECNRCDUTCH       0x0A01


#define
NLS\_CS\_DECNRCFINNISH     0x0A02


#define
NLS\_CS\_DECNRCFRENCH      0x0A03


#define
NLS\_CS\_DECNRCFRENCHCANADIAN  0x0A04


#define
NLS\_CS\_DECNRCGERMAN      0x0A05


#define
NLS\_CS\_DECNRCITALIAN     0x0A06


#define
NLS\_CS\_DECNRCNORWEGIANDANISH 0x0A07


#define
NLS\_CS\_DECNRCPORTUGUESE  0x0A08


#define
NLS\_CS\_DECNRCSPANISH     0x0A09


#define
NLS\_CS\_DECNRCSWEDISH     0x0A0A


#define
NLS\_CS\_DECNRCSWISS       0x0A0B


#define
NLS\_CS\_T61               0x0B00


#define
NLS\_CS\_T50               0x0B01


#define
NLS\_CS\_ASN1              0x0B10


#define
NLS\_CS\_IBMCP856          0x0C00


#define
NLS\_CS\_IBMCP1004         0x0C01


#define
NLS\_CS\_IBMCP1002         0x0CA0


#define
NLS\_CS\_IBMCP1003         0x0CA1


#define
NLS\_CS\_IBMCP1025         0x0CA2


#define
NLS\_CS\_IBMCP1026         0x0CA3


#define
NLS\_CS\_IBMCP1028         0x0CA4


#define
NLS\_CS\_IBMCP256          0x0CA5


#define
NLS\_CS\_IBMCP259          0x0CA6


#define
NLS\_CS\_IBMCP274          0x0CA7


#define
NLS\_CS\_IBMCP275          0x0CA8


#define
NLS\_CS\_IBMCP281          0x0CA9


#define
NLS\_CS\_IBMCP282          0x0CAA


#define
NLS\_CS\_IBMCP361          0x0CAB


 


#define
NLS\_CS\_IBMCP382          0x0CAD


#define
NLS\_CS\_IBMCP383          0x0CAE


#define
NLS\_CS\_IBMCP384          0x0CAF


#define
NLS\_CS\_IBMCP385          0x0CB0


#define
NLS\_CS\_IBMCP386          0x0CB1


#define
NLS\_CS\_IBMCP387          0x0CB2


#define
NLS\_CS\_IBMCP388          0x0CB3


#define
NLS\_CS\_IBMCP389          0x0CB4


#define
NLS\_CS\_IBMCP390          0x0CB5


#define
NLS\_CS\_IBMCP391          0x0CB6


#define
NLS\_CS\_IBMCP392          0x0CB7


#define
NLS\_CS\_IBMCP393          0x0CB8


#define
NLS\_CS\_IBMCP394          0x0CB9


#define
NLS\_CS\_IBMCP395          0x0CBA


#define
NLS\_CS\_IBMCP423          0x0CBB


#define
NLS\_CS\_IBMCP424          0x0CBC


#define
NLS\_CS\_IBMCP803          0x0CBD


#define
NLS\_CS\_IBMCP870          0x0CBE


#define
NLS\_CS\_IBMCP871          0x0CBF


#define
NLS\_CS\_IBMCP875          0x0CC0


#define
NLS\_CS\_IBMCP880          0x0CC1


#define
NLS\_CS\_IBMCP905          0x0CC2


#define
NLS\_CS\_IBMCP948          0x0CC4


#define
NLS\_CS\_IBMCP938          0x0CC5


#define
NLS\_CS\_IBMCP1381         NLS\_CS\_GB  /\* 0x0CC8 \*/


#define
NLS\_CS\_IBMCP1386         NLS\_CS\_GB


#define
NLS\_CS\_EACC              0x0CCB


#define
NLS\_CS\_ISO2022JP         0x0CCC /\* do not use this. use JIS \*/


#define
NLS\_CS\_JIS               0x0CCD


#define
NLS\_CS\_CCCII             0x0CCE


#define
NLS\_CS\_XEROXCJK          0x0CCF


#define
NLS\_CS\_IBMCP944          0x0CD1


#define
NLS\_CS\_IBMCP934          0x0CD2


#define
NLS\_CS\_IBMCP737          0x0CE0


#define
NLS\_CS\_IBMCP775          0x0CE1


#define
NLS\_CS\_ISO6937           0x0CE2


#define
NLS\_CS\_BASE64            0x0CE3


#define
NLS\_CS\_JIS2              0x0CE4


#define
NLS\_CS\_EUCJ              0x0CE5


#define
NLS\_CS\_EUCT              0x0CE6


#define
NLS\_CS\_ISOKR             0x0CE7


#define
NLS\_CS\_EUCK              NLS\_CS\_ISOKR


#define
NLS\_CS\_EUCC              0x0CE8


 


#define
NLS\_CS\_IA5JIS            0x0CE9   /\* Dummy \*/


 


#define
NLS\_CS\_IBMCP921          0x0CEA /\* Replacement for Lithuanian \*/


#define
NLS\_CS\_IBMCP922          0x0CEB /\* More White Russian \*/


 


#define
NLS\_CS\_KOI8              0x0CEC /\* Cyrillic Internet support \*/ 


#define
NLS\_CS\_IBMCP720          0x0CED


 


#define
NLS\_CS\_IBMCP1258         0x0CEE /\* Windows Vietnamese \*/


#define NLS\_CS\_ISO885910        
0x0CEF /\* Sami, etc. \*/


    


#define
NLS\_CS\_JP1TEXT           0x0CF0 /\* OSI/JIS X 5003-1987 X.400 Japanese ISP \*/


#define
NLS\_CS\_VIQRI             0x0CF1 /\* Vietnamese Quoted Readable\*/


#define
NLS\_CS\_VISCII            0x0CF2 /\* Vietnamese VISCII 1.1 \*/


#define
NLS\_CS\_VISCII1           0x0CF3 /\* TCVN Viet 1 \*/


#define
NLS\_CS\_VISCII2           0x0CF4 /\* TCVN Viet 2 \*/


#define
NLS\_CS\_IBMCP838          0x0CF5


#define
NLS\_CS\_IBMCP9030         NLS\_CS\_IBMCP838


#define
NLS\_CS\_IBMCP833          0x0CF7


#define
NLS\_CS\_IBMCP836          0x0CFA


#define
NLS\_CS\_IBMCP1027         0x0CFD


#define
NLS\_CS\_IBMCP420          0x0CFE


#define
NLS\_CS\_IBMCP918          0x0CFF


#define
NLS\_CS\_IBMCP1097         0x0D00


#define
NLS\_CS\_IBMCP1112         0x0D01


#define
NLS\_CS\_IBMCP1122         0x0D02


#define
NLS\_CS\_IBMCP1123         0x0D03


#define
NLS\_CS\_IBMCP1129         0x0D04


#define
NLS\_CS\_IBMCP1130         0x0D05


#define
NLS\_CS\_IBMCP1132         0x0D06


#define
NLS\_CS\_IBMCP1133         0x0D07


 


#define
NLS\_CS\_IBMCP806          0x0D08


#define
NLS\_CS\_IBMCP1137         0x0D09


#define
NLS\_CS\_VISCII3           0x0D0A /\* Vietnamese TCVN3 \*/


#define
NLS\_CS\_TCVN3             NLS\_CS\_VISCII3


 


#define
NLS\_CS\_IBMCP858          0x0D10 /\* Euro: 850 with D5 = Euro \*/


#define
NLS\_CS\_IBMCP1140         0x0D11 /\* Euro version of CP37 \*/


#define
NLS\_CS\_IBMCP1141         0x0D12 /\* Euro version of CP273 \*/


#define
NLS\_CS\_IBMCP1142         0x0D13 /\* Euro version of CP277 \*/


#define
NLS\_CS\_IBMCP1143         0x0D14 /\* Euro version of CP278 \*/


#define
NLS\_CS\_IBMCP1144         0x0D15 /\* Euro version of CP280 \*/


#define
NLS\_CS\_IBMCP1145         0x0D16 /\* Euro version of CP284 \*/


#define
NLS\_CS\_IBMCP1146         0x0D17 /\* Euro version of CP285 \*/


#define
NLS\_CS\_IBMCP1147         0x0D18 /\* Euro version of CP297 \*/


#define
NLS\_CS\_IBMCP1148         0x0D19 /\* Euro version of CP500 \*/


#define
NLS\_CS\_IBMCP1149         0x0D1A /\* Euro version of CP871 \*/


#define
NLS\_CS\_IBMCP924          0x0D1B /\* EBCDIC Euro cp \*/


#define
NLS\_CS\_ISO88598i         0x0D1C /\* logical bidi \*/


#define
NLS\_CS\_ISO88598e         0x0D1D /\* explicit bidi \*/


#define
NLS\_CS\_ISCII             0x0D1E /\* ISCII \*/


#define
NLS\_CS\_GB18030           0x0D31 /\* GB18030 \*/       


 


/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/


/\*\*\* THIS
RANGE RESERVED FOR EBCDIC DBCS CODEPAGES \*\*\*/


#define
NLS\_CS\_EBCDICDBCS\_START       0x0E00


 


/\* Dual
codepages - really these are CCSID's \*/


#define
NLS\_CS\_IBMCP930               0x0E00      /\* Japan  \*/


#define
NLS\_CS\_IBMCP933               0x0E01      /\* Korea  \*/


#define
NLS\_CS\_IBMCP935               0x0E02      /\* PRC    \*/


#define
NLS\_CS\_IBMCP937               0x0E03      /\* Taiwan \*/


#define
NLS\_CS\_IBMCP939               0x0E04      /\* Japan  \*/


#define
NLS\_CS\_IBMCP931            0x0E05   /\* PRC    \*/


#if
defined(OS390)


#define
NLS\_CS\_IBMCP1388              0x0E06      /\* PRC    \*/


#else


#define
NLS\_CS\_IBMCP1388              NLS\_CS\_IBMCP935


#endif


#define
NLS\_CS\_IBMCP5026              NLS\_CS\_IBMCP930


#define
NLS\_CS\_IBMCP5035              NLS\_CS\_IBMCP939


 


#define
NLS\_CS\_MIXED\_END              0x0E7F


 


/\*
DBCS-only \*/


#define
NLS\_CS\_IBMCP300               0x0E80      /\* Japan  \*/


#define
NLS\_CS\_IBMCP834               0x0E81      /\* Korea  \*/


#define
NLS\_CS\_IBMCP835               0x0E82      /\* Taiwan \*/


#define
NLS\_CS\_IBMCP837               0x0E83      /\* PRC    \*/


#define
NLS\_CS\_IBMCP930X              0x0E84      /\* Japan  \*/


#define
NLS\_CS\_IBMCP933X              0x0E85      /\* Korea  \*/


#define
NLS\_CS\_IBMCP935X              0x0E86      /\* PRC    \*/


#define
NLS\_CS\_IBMCP937X              0x0E87      /\* Taiwan \*/


#define
NLS\_CS\_IBMCP939X              0x0E88      /\* Japan  \*/


#define
NLS\_CS\_IBMCP931X              0x0E89      /\* PRC    \*/


#define
NLS\_CS\_IBMCP1388X             NLS\_CS\_IBMCP935X 


#define
NLS\_CS\_IBMCP1364              0x0E8A      /\* Korea  \*/


#define
NLS\_CS\_IBMCP1399              0x0E07      /\* Japan, Mixed, Not  DBCS-Only\*/


 


#define
NLS\_CS\_EBCDICDBCS\_END         0x0EFF


/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/


 


#define
NLS\_CS\_ANYCS                  0xFFFE


#define
NLS\_CS\_NOCS                   0xFFFF


 **See Also :**


**[NLS\_load\_charset](NLS_load_charset.md)**



----------------------------------------------------------------------------------------------------------


 





