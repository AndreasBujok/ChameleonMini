
# ChameleonMini Rev.G #

###This is a user friendly documentation for the [ChameleonMini](https://github.com/emsec/ChameleonMini/wiki) from Kasper & Oswald GmbH.<br>
###Feel free to add or adapt the documentation 




<a id="top">


__Table of content__

- [VERSION](#version)
- [CONFIG](#config)
- [UID](#uid)
- [READONLY](#readonly)
- [UPLOAD](#upload)
- [DOWNLOAD](#download)
- [RESET](#reset)
- [UPGRADE](#upgrade)
- [MEMSIZE](#memsize)
- [UIDSIZE](#uidsize)
- [RBUTTON](#rbutton)
- [RBUTTON_LONG](#rbutton_long)
- [LBUTTON](#lbutton)
- [LBUTTON_LONG](#lbutton_long)
- [LEDGREEN](#ledgreen)
- [LEDRED](#ledred)
- [LOGMODE](#logmode)
- [LOGMEM](#logmem)
- [LOGDOWNLOAD](#logdownload)
- [LOGSTORE](#logstore)
- [LOGCLEAR](#logclear)
- [SETTING](#setting)
- [CLEAR](#clear)
- [STORE](#store)
- [RECALL](#store)
- [CHARGING](#charging)
- [HELP](#help)
- [RSSI](#rssi)
- [SYSTICK](#systick)
- [SEND_RAW](#send_raw)
- [SEND](#send)
- [GETUID](#getuid)
- [DUMP_MFU](#dump_mfu)
- [IDENTIFY](#identify)
- [TIMEOUT](#timeout)
- [THRESHOLD](#threshold)
- [AUTOCALIBRATE](#autocalibrate)
- [FIELD](#field)

##VERSION<a id="version">##
[Top](#top)

Print the current version of ChameleonMini<br>

**Syntax:** `version?`<br>
*101:OK WITH TEXT<br>
ChameleonMini RevG 171107 using LUFA 151115 compiled with AVR-GCC 4.9.2. Based on the open-source NFC tool ChameleonMini. https://github.com/emsec/ChameleonMini commit 33f3525*

##CONFIG<a id="config">##
[Top](#top)

Get/Set the configuratopn of the current slot. The "slot" includes the behavior of the Card. The ChameleonMini can emulate differend Cards, and each slot contains one Card.
The slot 8 is configured as "READER" in the default configuration.<br>
*Note: The ChameleonMini has 8 possible slots (1-8)*

**Syntax:** `config=?`<br>
*101:OK WITH TEXT
NONE,MF\_ULTRALIGHT,MF\_CLASSIC\_1K,MF\_CLASSIC\_1K\_7B,MF\_CLASSIC\_4K,MF\_CLASSIC\_4K\_7B,ISO14443A\_SNIFF,ISO14443A\_READER*

Set current slot as a MIFARE classic 4K emulation.<br>
**Syntax:** `config=MF_CLASSIC_4K`<br>
*101:OK WITH TEXT<br>*

Get the value of the current slot<br>
**Syntax:** `config?`<br>
*101:OK WITH TEXT<br>
MF\_CLASSIC\_4K<br>*


##UID<a id="uid"></a>##
[Top](#top)

Print the current uid of the emulated card(slot)<br>
**Syntax:** `uid?`<br>
*101:OK WITH TEXT<br>
9E63BC03A<br>*


##READONLY<a id="readonly"></a>##

Configures the read-only mode to the internal memory. Activates (1) or deactivates (0) the read-only mode (***Any writing to the memory is silently ignored.***)<br>

Print the possible states.<br>
**Syntax:** `readonly=?`<br>
*101:OK WITH TEXT<br>
1,0<br>*

Print the current state of the accessrights<br>
**Syntax:** `readonly?`<br>
*101:OK WITH TEXT<br>
0<br>*

Activate the read-only mode<br>
**Syntax:** `readonly=1`<br>
*100:OK<br>*


##UPLOAD<a id="upload"></a>##
[Top](#top)

**Syntax:** `upload`\<ENTER\><br>

Waits for an XModem connection in order to upload a new virtualized card into the currently selected slot, with a size up to the current memory size. 


##DOWNLOAD<a id="download"></a>##
[Top](#top)

**Syntax:** `download`\<ENTER\><br>

Waits for an XModem connection in order to download a virtualized card with the current memory size.


##RESET<a id="reset"></a>##
[Top](#top)

**Syntax:** `reset`\<ENTER\><br>

Reboots the Chameleon, i.e., power down and subsequent power-up. Note: A reset usually requires a new Terminal session. 


##UPGRADE<a id="upgrade"></a>##
[Top](#top)

Sets the Chameleon into firmware upgrade mode (DFU). This command can be used instead of holding the RBUTTON while power-on to trigger the bootloader. 

**Syntax:** `upgrade`\<ENTER\><br>


##MEMSIZE<a id="memsize"></a>##
[Top](#top)

Returns the memory size occupied by the current configuration in Byte

**Syntax:** `memsize?`<br>
*101:OK WITH TEXT<br>
4096<br>*

##UIDSIZE<a id="uidsize"></a>##
[Top](#top)

Print the size in bytes of the current uid on the emulated card<br>
**Syntax:** `uidsize?`<br>
*101:OK WITH TEXT<br>
4<br>*


##CHARGING<a id="charging"></a>
[Top](#top)

Returns if the battery is currently being charged (TRUE) or not (FALSE) 

**Syntax:** `charging?`<br>
*120:FALSE*



##HELP<a id="help"></a>
[Top](#top)

Returns a comma-separated list of all commands supported by the current firmware

**Syntax:** `help`<br>
*101:OK WITH TEXT<br>
VERSION,CONFIG,UID,READONLY,UPL....*


##RSSI<a id="rssi"></a>
[Top](#top)

Returns the voltage measured at the antenna of the Chameleon, e.g., to detect the presence of an RF field or compare the field strength of different RFID readers

**Syntax:** `help`\<ENTER\><br>
*101:OK WITH TEXT<br>
2648 mV*

##SYSTICK<a id="systick"></a>##
[Top](#top)

Print the value of the left system tick **in ms** since PowerOn.<br>
*Note: An overflow occurs every 65,536 ms.*<br>

**Syntax:** `systick?`<br>
*101:OK WITH TEXT<br>
9C30<br>*

##LEDGREEN<a id="ledgreen"></a>##
[Top](#top)

Possible values are:<br>
**Syntax:** `ledgreen=?`<br>
*101:OK WITH TEXT<br>
NONE,POWERED,TERMINAL\_CONN,TERMINAL\_RXTX,SETTING\_CHANGE,MEMORY\_STORED,MEMORY\_CHANGED,CODEC\_RX,CODEC\_TX,FIELD\_DETECTED,LOGMEM\_FULL*

Get current state:<br>
**Syntax:** `ledgreen?`<br>
*101:OK WITH TEXT<br>
POWERED<br>*

Set value for example:<br>
**Syntax:** `ledgreen=terminal_rxtx`\<ENTER\><br>
*100:OK*

##LEDRED<a id="ledred"></a>##
[Top](#top)

Possible values are:<br>
**Syntax:** `ledred=?`<br>
*101:OK WITH TEXT<br>
NONE,POWERED,TERMINAL\_CONN,TERMINAL\_RXTX,SETTING\_CHANGE,MEMORY\_STORED,MEMORY\_CHANGED,CODEC\_RX,CODEC\_TX,FIELD\_DETECTED,LOGMEM\_FULL*

Get current state:<br>
**Syntax:** `ledred?`<br>
*101:OK WITH TEXT<br>
FIELD_DETECTED<br>*

Set value for example:<br>
**Syntax:** `ledred=powered`\<ENTER\><br>
*100:OK*


##RBUTTON<a id="rbutton"></a>##
[Top](#top)

Set/Get the behavior of a right button with "short push"<br>

Possible values are:<br>
**Syntax:** `rbutton=?`<br>
*101:OK WITH TEXT<br>
NONE,UID_RANDOM,UID\_LEFT\_INCREMENT,UID\_RIGHT\_INCREMENT,UID\_LEFT\_DECREMENT,UID\_RIGHT\_DECREMENT,CYCLE\_SETTINGS,STORE\_MEM,RECALL\_MEM,TOGGLE\_FIELD,STORE\_LOG*

Get current value:<br>
**Syntax:** `rbutton?`<br>
*101:OK WITH TEXT<br>
CYCLE_SETTINGS<br>*

Set value for example:<br>
**Syntax:** `rbutton=ui_random`


##RBUTTON\_LONG<a id="rbutton_long"></a>##
[Top](#top)

Set/Get the behavior of a right button with "long push"<br>

Possible values are:<br>
**Syntax:** `rbutton_long=?`<br>
101:OK WITH TEXT<br>
NONE,UID_RANDOM,UID\_LEFT\_INCREMENT,UID\_RIGHT\_INCREMENT,UID\_LEFT\_DECREMENT,UID\_RIGHT\_DECREMENT,CYCLE\_SETTINGS,STORE\_MEM,RECALL\_MEM,TOGGLE\_FIELD,STORE\_LOG

Get current value:<br>
**Syntax:** `rbuttton_long?`<br>
*101:OK WITH TEXT<br>
CYCLE_SETTINGS<br>*

Set value for example:<br>
**Syntax:** `rbutton_long=uid_random`<br>
*100:OK*

##LBUTTON<a id="lbutton"></a>##
[Top](#top)

Set/Get the behavior of a left button with "short push"<br>

Possible values are:<br>
**Syntax:** `lbutton_long=?`<br>
*101:OK WITH TEXT<br>
NONE,UID_RANDOM,UID\_LEFT\_INCREMENT,UID\_RIGHT\_INCREMENT,UID\_LEFT\_DECREMENT,UID\_RIGHT\_DECREMENT,CYCLE\_SETTINGS,STORE\_MEM,RECALL\_MEM,TOGGLE\_FIELD,STORE\_LOG*

Get current value:<br>
**Syntax:** `lbutton?`<br>
*101:OK WITH TEXT<br>
CYCLE_SETTINGS<br>*

Set value for example:<br>
**Syntax:** `lbutton=uid_random`<br>
*100:OK*

##LBUTTON\_LONG<a id="lbutton_long"></a>##
[Top](#top)

Set/Get the behavior of a left button with "long push"<br>

Possible values are:<br>
**Syntax:** `lbutton_long=?`<br>
*101:OK WITH TEXT<br>
NONE,UID_RANDOM,UID\_LEFT\_INCREMENT,UID\_RIGHT\_INCREMENT,UID\_LEFT\_DECREMENT,UID\_RIGHT\_DECREMENT,CYCLE\_SETTINGS,STORE\_MEM,RECALL\_MEM,TOGGLE\_FIELD,STORE\_LOG*

Get current value:<br>
**Syntax:** `lbuttton_long?`<br>
*101:OK WITH TEXT<br>
CYCLE_SETTINGS<br>*

Set value for example:<br>
**Syntax:** `lbutton_long=ui_random?`<br>
*100:OK*


##LOGMODE<a id="logmode"></a>##
[Top](#top)

The 'logmode' command set the behavior of the datalogging.<br>
 
Possible values are:<br>
**Syntax:** `logmode=?`<br>
*101:OK WITH TEXT<br>
OFF,MEMORY,LIVE<br>*

- **off** -> logging disabled
- **LIVE** -> log events are written directly to the terminal
- **MEMORY** -> log events are written to SRAM (uC RAM)

Get current value:<br>
**Syntax:** `logmode?`<br>
*101:OK WITH TEXT<br>
LIVE<br>*

Set logging mode:<br>
**Syntax:** `logmode=MEMORY`<br>
*100:OK<br>*

####Log Entry Format####
The log entries use a TLV (Type Length Value)-like format:

- **Entry type** -> 1 byte, see possible types on [GitHub](*https://rawgit.com/emsec/ChameleonMini/master/Doc/Doxygen/html/_log_8h.html#a34112fbd78128ae58dc7801690dfa6e0)
- **Data length** -> 1 byte, the length of the appended data
- **Timestamp** -> 2 bytes, current systick timestamp value (ms) 
- **Data** -> Data length bytes, it's also possible that no data is appended, then the Data length field is zero


##LOGMEM<a id="logmem"></a>##
[Top](#top)

Returns the remaining free space for logging data to the SRAM (max. 2048 byte)

**Syntax:** `logmem?`<br>
*101:OK WITH TEXT<br>
18430 (from which 16382 non-volatile)*


##LOGDOWNLOAD<a id="logdownload"></a>##
[Top](#top)

Waits for an XModem connection and then downloads the binary log - including any log data in FRAM. 

**Syntax:** `logdownload`\<ENTER\><br>


##LOGSTORE<a id="logstore"></a>##
[Top](#top)

Writes the current log from SRAM to FRAM and clears the SRAM log. 

**Syntax:** `logstore?`<br>
*100:OK<br>*

***Warning***<br>
If the FRAM is full, currently no error message is shown.<br>
If calling `LOGMEM?` after executing this command returns any other value than the maximum SRAM log size, there was not sufficient space in the FRAM and nothing has been done. 


##LOGCLEAR<a id="logclear"></a>##
[Top](#top)

Clears the log memory (SRAM on ATMega and FRAM on external RAM IC5) 

**Syntax:** `logclear`<ENTER\><br>
*100:OK<br>*

##SETTING<a id="setting"></a>##
[Top](#top)

Get/Set the current slot (slot 1-8) for the card/reader emulation.

Get the current slot number<br>
**Syntax:** `setting?`<br>
*101:OK WITH TEXT<br>
1*

Switch to slot 2<br>
**Syntax:** `setting=2`<br> 
*100:OK*

##CLEAR<a id="clear"></a>##
[Top](#top)

Clears the content of the current slot

**Syntax:** `clear`\<ENTER\><br>
*100:OK<br>*

##STORE<a id="store"></a>##
[Top](#top)

Stores the content of the current slot from the external FRAM into the Flash memory

**Syntax:** `store`\<ENTER\><br>
*100:OK*


##RECALL<a id="recall"></a>##
[Top](#top)

Recalls/restores the content of the current slot from the Flash memory into the external FRAM 

**Syntax:** `recall`\<ENTER\><br>
*100:OK*


##SEND\_RAW<a id="send_raw"></a>##
[Top](#top)

Adds parity bits, sends the given byte string <BYTEVALUE>, and returns the cards answer 

Request type A<br>
**Syntax:** `send 26`\<ENTER\><br>
*101:OK WITH TEXT<br>
0400<br>
0010<br>
PARITY OK*<br>

Select card<br>
**Syntax:** `send 9320'\<enter\><br>
*101:OK WITH TEXT<br>
BA46A1B2EF<br>
0028<br>
PARITY OK<br>*

##SEND<a id="send"></a>##
[Top](#top)

Does NOT add parity bits, sends the given byte string <BYTEVALUE> and returns the cards answer

**Syntax:** `send 26`\<ENTER\><br>
*101:OK WITH TEXT<br>
0400<br>
0010<br>
PARITY OK*<br>


##GETUID<a id="getuid"></a>##
[Top](#top)

Obtains the UID of a card that is in the range of the antenna and returns it. This command is a Timeout command.<br>

**Valid only in 'ISO14443A\_READER' mode**

**Syntax:** `getuid`\<ENTER\><br>
*101:OK WITH TEXT<br>
BA46A1B2*


##DUMP\_MFU<a id="dump_mfu"></a>##
[Top](#top)

Reads the whole content of a Mifare Ultralight card that is in the range of the antenna and returns it. This command is a Timeout command

**Valid only in 'ISO14443A\_READER' mode**

**Syntax:** `dump_mfu`\<ENTER\><br>
*101:OK WITH TEXT<br>
04A8DEFAE2B54C809B48000000000000<br>
FFFFFFFF000000000000000000000000<br>
00000000000000000000000000000000<br>
00000000000000000000000000000000<br>*


##IDENTIFY<a id="identify"></a>##
[Top](#top)

dentifies the type of a card in the range of the antenna and returns it. This command is a Timeout command.

**Valid only in 'ISO14443A\_READER' mode**

**Syntax:** `identify`\<ENTER\><br>
*101:OK WITH TEXT<br>
MIFARE Classic 1k<br>
ATQA:.0400<br>
UID:.BA46A1B2<br>
SAK: 08<br>**

##TIMEOUT<a id="timeout"></a>##
[Top](#top)

Get/Set the timeout for the current slot in multiples of 128 ms. If set to zero, there is no timeout. See also Timeout commands. 

Get the possible range<br>
**Syntax:** `timeout=?`<br> 
*101:OK WITH TEXT<br>
0 = no timeout<br>
1-600 = 100 ms - 60000 ms timeout<br>*

Get the current value<br>
**Syntax:** `timeout?`<br> 
*101:OK WITH TEXT<br>
5000 ms<br>*


##THRESHOLD<a id="threshold"></a>##
[Top](#top)

Get/Set the possible number for the reader threshold.

Get the possible range<br>
**Syntax:** `threshold=?`<br>
*101:OK WITH TEXT<br>
Any integer from 0 to 4095. Reference voltage will be (VCC \* THRESHOLD / 4095) mV*


Set the reader threshold. The *\<NUMBER\>* influences the reader function and range. Setting a wrong value may result in malfunctioning of the reader. **DEFAULT: 400**

**Syntax:** `threshold=300`\<ENTER\><br>
*100:OK*

##AUTOCALIBRATE<a id="autocalibrate"></a>##
[Top](#top)

Automatically finds a good threshold for communicating with the card that currently is on top of the Chameleon. This command is a Timeout command

**Valid only in 'ISO14443A\_READER' mode**

**Syntax:** `autocalibrate`\<ENTER\><br>
*101:OK WITH TEXT<br>
 128: -<br>
 136: -<br>
 144: -<br>
 .<br>
 .<br>
 .<br>
1000: +<br>
1008: +<br>
1016: -<br>*


##FIELD<a id="field"></a>##
[Top](#top)

Get/Set the state of the reader field

Get the possible values<br>
**Syntax:** `field=?`<br>
*101:OK WITH TEXT<br>
1,0*

Switch the reader field on<br>
**Syntax:** `field=1`<br>
*100:OK*

