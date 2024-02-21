|Status Code| Sent By | Description | Additional Information |
|---|---|---|---|
|000|HUBJECT|Success|Everything is fine 🙂|
|001|HUBJECT|Hubject system error|The status code 001 is returned for many reason including any internal problem of Hubject.|
|002|HUBJECT|Hubject database error||
|009|HUBJECT|Data transaction error||
|017|HUBJECT|Unauthorized access|The status code 017 is returned when you are using a wrong SSL certificate or a SSL certificate that it has already expired.|
|018|HUBJECT|Inconsistent EvseID|This status code 018 is returned when there is a duplicated EvseID included in the body of the request.|
|019|HUBJECT|Inconsistent EvcoID||
|021|CPO, EMP|System error|Generic error on the partner side|
|022||Data error|The status code 022 is returned for many reason but mostly for Bad Request , please check you request carefully.|
|101||QR code authentication failed – Invalid credentials||
|102|EMP|RFID authentication failed – Invalid UID||
|103||RFID authentication failed – Card not readable||
|105||PLC authentication failed - Invalid EvcoID||
|106|HUBJECT, CPO|No positive authentication response||
|110||QR code app authentication failed – Time out error||
|120||PLC (ISO/ IEC 15118) authentication failed – Invalid underlying EvcoID||
|121||PLC (ISO/ IEC 15118) authentication failed – Invalid certificate||
|122||PLC (ISO/ IEC 15118) authentication failed – Time out error||
|200||EvcoID locked||
|210||No valid contract|Most probably there isn’t an active offer or the current offer has expired with eRoamingPlatform.|
|300||Partner not found|This status code is returned mostly because the OperatorID provided in the URL or request body is not correct.|
|310|Hubject|Partner did not respond||
|320|CPO/EMP|Service not available||
|400||Session is invalid||
|404|Data not found|||
|401|Call not authorized|||
|500|Processing error|||
|501||Communication to EVSE failed||
|510|CPO|No EV connected to EVSE||
|601||EVSE already reserved||
|602|CPO|EVSE already in use/ wrong token||
|603||Unknown EVSE ID||
|604|HUBJECT|EVSE ID is not Hubject compatible|If the Attribute in the EVSEData isHubjectCompatible is set to false this error is displayed.|
|700|CPO|EVSE out of service||![image](https://github.com/FirasHubject/OICP23_Integration_Guide/assets/135227574/dd4708b5-1ba8-4f50-bf1a-221d9fd5873b)
