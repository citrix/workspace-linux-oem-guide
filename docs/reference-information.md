# Reference Information   

This section includes the following:  

* Command line utilities  
* Configuration files  
* Library files  
* Scripts  

## Command Line utilities  

### wfica
  
You can use a connection file simply by typing its name after wfica without any of the options below.  

| To | Type |
|---|---|
| Specify the custom connection to use from the Connection file. <br><br>**Note**: With the new self-service UI, you cannot set up a custom connection in this way. | `-desc description`| 
| Specify the custom connection to use from the Connection file. <br><br>**Note**: With the new self-service UI, you cannot set up a custom connection in this way. | `-description` |
| Specify a desktop file. | `-desktop filename` |
| Specify a connection file.  | `-file connection_filename` |
| Set alternative protocol file. This enables the use of an alternative module.ini. |   `-protocolfile filename` |
| Set alternative client configuration file. This enables the use of an alternative wfclient.ini. | `-clientfile filename` |
| Display a different name for Workspace app, specified by name, wherever that name appears. The default name is the device name. However, if you use a Sunray device, the default name is derived from the device's MAC address. This is overridden by the ClientName entry in .ICAClient/wfclient.ini, which is itself overridden by issuing the - clientname option. | `-clientname name`  | 
| Show this list of parameters. | `-help`  |
| Display version information.  | `-version` |  
| Show error numbers and string.  | `-errno` |  
| Set the location of Workspace app installation files. This is equivalent to setting the ICAROOT environment variable. | `-icaroot directory` |  
| Suppress connection dialogs.  | `-quiet` |  
| Enable key logging.  | `-keylog` |
| Set session geometry.  | `-geometry WxH+X+Y` |
| Set color depth. | `-depth <4 | 8 | 16 | 24 | auto>` | 
| Set monitor spanning. | `-span [h][o][a| mon1[,mon2[,mon3,mon4]]]`  |
| Use private color map.  | `-private` |
| Use shared color map.  | `-shared` |
| Specify a string to be added to a published application. | `-param string` |
| Specify the UNIX path to be accessed through client drive mapping by a published application. | `-fileparam unixpath` |
| Specify a user name. | `-username` |
| Specify a disguised password.  | `-password` |
| Specify a clear text password. | `-clearpassword "clear password"` |
| Specify a domain. |  `-domain` |
| Specify an initial program. | `-program` |  
| Specify a directory for the initial program to use.  | `-directory` |
| Turn on sound. | `-sound` |
| Turn off sound. | `-nosound` |
| Set drive mapping overrides. These are of the form `A$=path`, where path can contain an environment variable (for example `A$=$HOME/tmp`). This option must be repeated for each drive to be overridden. For the override to work, there must be an existing mapping, though it need not be enabled. | `-drivemap string` |

### storebrowse 
 
The following table documents the options that you can use with the storebrowse utility.  

| Option | Description | Notes |
|---|---|---|
| `-a`, `--addstore` | Adds a new store | To add a store, the operation accepts an incomplete URL and tries possible stores, using default names, until it finds one that exists. Whenever it adds a store it reports the complete URL. <br><br> With this release, other operations that require a store can implicitly add the store in addition to their main function, provided that they are given the complete URL for the store. |
| `-E`, `--enumerate` | Enumerates the available resources. | By default, the resource name, display name, and folder of the resource are displayed. Additional information can be displayed, by using the `--details` option. |
| `-e`, `--listerrorcodes` | Lists error codes.  | |
| `-S`, `--subscribed` | Lists the subscribed resources. | By default, the resource name, display name, and folder of the resource are displayed. Additional information can be displayed using the `--details` option. |
| `-M`, `--details` <br><br> Use in conjunction with the `-E` or `-S` option. | Selects which attributes of published applications are returned. This option takes an argument that is the sum of the numbers corresponding to the required details: <br><br> Publisher(0x1), VideoType(0x2), SoundType(0x4), AppInStartMenu(0x8), AppOnDesktop(0x10), AppIsDesktop(0x20), AppIsDisabled(0x40), WindowType(0x80), WindowScale(0x100), and DisplayName(0x200). <br><br> CreateShortcuts(0x100000) can be used in conjunction with `-S`, `-s`, and `-u` to create menu entries for subscribed applications. <br><br> RemoveShortcuts(0x20000 0) can be used with `-S` to delete all menu entries. | Some of these details are not available through storebrowse. If this is the case, the output is 0. Values can also be expressed in decimal as well as hexadecimal (for example, 512 for 0x200). |
| `-v`, `--version` | Writes the version number of storebrowse to the standard output. | |
| `-?`,  `-h`, `--help` | Lists the usage for storebrowse. | An abbreviated version of this table is displayed.  |
| `-U`,  `--username` | Passes the user name to the server. | These options work with Program Neighborhood Agent sites and StoreFront sites. When used with a StoreFront site, the site must be configured to support HTTP Basic authentication, otherwise, these options are ignored. |
| `-P`,  `--password` | Passes the password to the server. | These options work with Program Neighborhood Agent sites and StoreFront sites. When used with a StoreFront site, the site must be configured to support HTTP Basic authentication, otherwise, these options are ignored. |
| `-D`, `--domain` | Passes the domain to the server.  | These options work with Program Neighborhood Agent sites and StoreFront sites. When used with a StoreFront site, the site must be configured to support HTTP Basic authentication, otherwise, these options are ignored. |
| `-r`, `--icaroot` | Specifies the root directory of the Citrix Workspace app for Linux installation. | If not specified, the value is taken from the ICAROOT environment variable or determined at run time. |
| `-i`, `--icons` <br><br> Use in conjunction with the `-E` or `-S` option. | Fetches desktop or application icons, in PNG format, of the size and depth given by the best or size argument. <br><br> If the best argument is used, the best sized icon available on the server is fetched. You can convert this to any size required. The best argument is the most efficient for storage and bandwidth, and can simplify scripting. <br><br> If the size argument is used, an icon is fetched of the specified size and depth. <br><br> In both cases, icons are saved in a file for each of the resources that the `–E` or `-S` option returns. | The `best` argument creates an icon of the form `<resource name>`.png. <br><br> The size argument is of the form WxB, where W is the width of the icon (all icons are square, so only one value is needed to specify the size), and B is the color depth (that is, the number of bits per pixel). W is required but B is optional. If it is not specified, icons of all available image depths are fetched for that size. The files that are created are named `<resource name>_WxWxB.png`.  |
| `-u`, 	`--unsubscribe` | Unsubscribes the specified resource from the given store. | |  
| `-s`, `--subscribe` | Subscribes the specified resource from the given store. | If you use a different Workspace app, subscriptions on Program Neighborhood Agent servers are unavailable.  |

**Important**: The unique gateway

| Option | Description | Notes |
|---|---|---|
| `-d`, `--deletestore` | Deregisters a store with the Service Record daemon. | |
| `-c`, `--configselfservice` | Gets and sets the self- service UI settings that are stored in StoreCache.ctx. Takes an argument of the form `<entry[=value]>`. If only entry is present, the setting's current value is printed. If a value is present, it is used to configure the setting. | **Example**: `storebrowse --configselfservice SharedUserMode=True` <br><br> **Important**: Both entry and value are case sensitive. Commands that use this option will fail if the case is different to the documented case of the setting itself (in StoreCache.ctx). |  
| `-C`, `--addCR` | Reads the provided Citrix Workspace app (CR) file, and prompts the user to add each store.  | The output is the same as `–a`, but might contain more than one store, separated by newlines. |
| `-K`, `--killdaemon` | Terminates the storebrowse daemon process.  | All credentials and tokens are purged. The SSO credentials inserted last are also removed. |

### storebrowse return codes  


| Error number  | Description  |
|---|---|
| 0  | NO\_ERROR  |
| 5  | INVALID\_ARGUMENTS  |
| 6 | IO\_ERROR  |
| 7 | UNKNOWN\_ERROR |
| 37 | CANNOT\_LOAD\_LIBRARY |
| 150 | SERVER\_CERTIFICATE\_NOT\_TRUSTED |
| 235 | UNABLE\_TO\_ADD\_STORE |
| 236 | CANT\_UNSUBSCRIBE\_NOT\_TRUSTED |
| 237 | STORE\_NOT\_FOUND |
| 238 | PASSWORD\_EXPIRED\_OR\_MUST\_CHANGE |
| 247 | RESOURCE\_NOT\_RECOGNISED |
| 248 | INVALID\_CREDENTIALS |
| 249 | ENUMERATION\_FAILURE |
| 253 | NO\_URL\_SPECIFIED |
| 254 | MISSING\_ARGUMENTS |
| 255 | EXEC\_FAILED |

### Pnabrowse  

**Important**: The pnabrowse utility is deprecated but can still query Program Neighborhood Agent sites for lists of servers and published resources, and lets you connect to a published resource. Citrix discourages the use of pnabrowse because it prevents users from accessing StoreFront stores; use storebrowse instead. storebrowse can prompt for credentials from both sites and stores. The `-U`, `-P` and `-D` options only work with Program Neighborhood Agent sites. 

An optional argument of pnabrowse specifies the server to connect to. This may be either:  

* The name of the XenApp server, for options -S and -A.  
* The URL of the server running a Program Neighborhood Agent site, for options -E and -L.  

The pnabrowse utility returns an exit value indicating success or failure, and can use the following options with XenApp.  
 
| Option | Description | 
|---|---|
| `-S` | List servers, one per line. | 
| `-A` | List published applications, one per line.  |
| `-m` | Used in conjunction with `-A`, this expands the information returned about published applications to include Publisher, Video Type, Sound Type, AppInStartMenu, AppOnDesktop, AppIsDesktop, AppIsDisabled, Window Type, WindowScale, and Display Name. |
| `-M` | Used in conjunction with -A, this selects individual columns of information returned about published applications. It takes an argument (1-1023) which is the sum of the numbers corresponding to the required details: Publisher(1), Video Type(2), Sound Type(4), AppInStartMenu(8), AppOnDesktop(16), AppIsDesktop(32), AppIsDisabled(64), Window Type(128), Window Scale(256), and DisplayName(512). |
| `-c` | When appended to option `-A`, create files specifying the minimum information the client engine needs to connect to published applications; for example, application name, browse server, window resolution, color depth, audio, and encryption settings. File names are formatted as follows: /tmp/xxx\_1.ica, /tmp/xxx\_2.ica where xxx is replaced by the decimal process identifier for the pnabrowse process. | 
| `-d` | Used in conjunction with -L to specify the XDG desktop file. |  
| `-e` | Shows error numbers. |
| `-i` | Include paths to files containing icon images for published applications in the output from option -A. Either .xpm or .png files are returned depending on the use of the size (WxB) option: <br><br> -i returns 16x16 icons in XPM format at 4 bits per pixel <br><br> -iWxB returns WxW icons in PNG format at B bits per pixel | 
| `-f` | Include Citrix XenApp folder names for published applications in the output from option -A. | 
| `-u` | Specify a user name for authenticating the user to a proxy server.  |
| `-p` | Specify a password for authenticating the user to a proxy server.  |

The following options provide Citrix XenApp (Program Neighborhood Agent) Service functionality and can be used with both XenApp and XenDesktop.  

| Option | Description | 
|---|---|
| `-E` | Invoke Citrix XenApp and enumerate all published resources. <br><br> If you specify both -E and -L, the last option on the command line takes effect. The utility then terminates, possibly leaving a connection open. <br><br> For each resource the following details are written to standard output, enclosed in single quotation marks and separated by tab characters: <br><br> **Name**: The display name from the Access Management Console Application Properties dialog box. <br><br>**Folder**: The Program Neighborhood folder from the Access Management Console Application Properties dialog box.<br><br> **Type**: Either Application or Content.<br><br> **Icon**: The full path name of an .xpm format icon file.  |
| `-L` | Specify the name of the published resource to which you want to connect. This invokes Citrix XenApp and launches a connection to a published resource. If you specify both -E and -L, the last option on the command line takes effect. The utility then terminates, possibly leaving a connection open. |
| `-N` | Specify a new password. This option must be used with existing credentials and is valid only when the existing password has expired, as indicated by the exit code 238: PASSWORD\_EXPIRED\_OR\_MUST\_CHANGE. |
| `-P` | Specify a password for authenticating the user to the server running the Web Interface or the server running the Citrix XenApp (Program Neighborhood Agent) Service. | 
| `-U` | Specify a user name for authenticating the user to the server running the Web Interface or the server running the Citrix XenApp (Program Neighborhood Agent) Service. | 
| `-D` | Specify a domain for authenticating the user to the server running the Web Interface or the server running the Citrix XenApp (Program Neighborhood Agent) Service. | 
| `-WD` | Disconnects all active sessions for the user.  | 
| `-WT` | Terminates all sessions for the user.  |
| `-Wr` | Reconnects to all disconnected sessions for the user.  |
| `-WR` | Reconnects to all sessions (active or disconnected) for the user. | 
| `-k` | Use an existing Kerberos ticket to authenticate, rather than user name, password, and domain. This requires configuration of the client and server. It is applicable only for pnabrowse. |

The following common options are used:  

| Option | Description | 
|---|---|
| -q | Quiet mode; do not print error messages.  |
| -r  | Include raw icon data for published applications in the output from options - E or -A. |  
| -V | Displays version details.  |
| -h | Print a usage message listing the options.  |
| -? | Print a usage message listing the options.  |

### Exit Status values 
 
The command-line utilities storebrowse and pnabrowse report exit status values to indicate success or failure. If problems arise, these values give guidance on possible error causes and their meanings, and are listed in the following table. Note that some error conditions may result in different exit values depending on which part of the code detects them. 

| Value  | Description  |
|---|---|
| 0 | Success |
| 1-242  | These error codes are associated with common error messages. Run pnabrowse -errno for a list of these messages. | 
| 246 | Citrix XenApp has reported an error. See the text written to standard output for more information on this error. | 
| 247 | A published resource has not been recognized. |  
| 248 | Invalid credentials.  |
| 249 | Failed to enumerate servers. |
| 250 | Failed to make a directory.  |
| 251 | Failed to load a .ini file.  |
| 252 | No Web Interface server was specified.  |
| 253 | No Program Neighborhood Agent server was specified. |
| 254 | A parameter is missing  |
| 255 | Execution failed  |

When pnabrowse fails to change a password, the exit code can be useful in diagnosing the problem. For example:  

```
0 SUCCESS  
4 E_MISSING_ARG  
63 E_NOT_ALLOWED WI configuration prohibits change  
65 E_NOT_SUPPORTED Could be seen if :-  
-	WI config requires “direct connection” (=Kerberos), but couldn’t load Kerberos library  
-	Support is not compiled into client - might see it with pre 11.114 version  
-	Trying to change a Novell password    
74 E_NEW_PASSWORD_INVALID  
248 EX_INVALID_CREDENTIALS  
255 EX_EXEC_FAILED Some problem with the server changing the password, such as it hasn’t expired. 
```

##  Configuration files
  
For any given connection, the configuration files are checked in a specific order. For details, see Configuration files earlier in this document.  

### wfclient.ini  

This .ini file contains a section for parameters specific to the Workspace app user interface (UI), such as version number and desired resolution.  

In Version 10.x and later of Workspace app for Linux, for each entry in wfclient.ini, there must be a corresponding entry in All\_Regions.ini for the setting to take effect. In addition, for each entry in the [Thinwire3.0], [ClientDrive], and [TCP/IP] sections of wfclient.ini, there must be a corresponding entry in canonicalization.ini for the setting to take effect. See the All\_Regions.ini and canonicalization.ini files in the $ICAROOT/config/ directory for more information.

### Parameter syntax  

Boolean parameters use Yes, True, 1, or On to indicate TRUE. Any other values, including No, False, 0, or Off, are interpreted as FALSE.
  
For all parameters, spaces are significant and values are case-sensitive. 
 
Parameters marked as ignored are not currently used by the client, but can be reserved for future use, redundant, or used by other clients; for example, Win32 or Macintosh. In the last case, the parameter is read by the client but the result is discarded.  

Default values are embedded into the client program itself. Fixed values are set by the unmodified .ini configuration files. 
 
In the following table, the parameters are listed alphabetically within each section of the file. 

| Item | Description |
|---|---|
| `[WFClient]` | The engine uses this section. It contains default session oriented parameters. |
| `AllowAudioInput=boolean`  |	To enable the webcam and audio input for connections, you must ensure this parameter is set to True; otherwise, it overrides the setting for the EnableAudioInput parameter in appsrv.ini. Default=False | 
| `ApplySucConnTimeoutToDesk tops=boolean` | Works with the SucConnTimeout setting. Ensures that the setting SucConnTimeout is honored by virtual desktops as well as virtual applications. When `ApplySucConnTimeoutToDesktops` is applied to desktops, repeated clicks open multiple sessions, but you can set `SucConnTimeout` to a suitable timeout and run a custom script in between the desktop launches. Default=False |
| `AutoResponse=integer`  |	Specifies a bitmapped value that enables automatic response to user prompts (such as dialog boxes). The values are as follows: 1: log message to standard error output; 2: exit program whenever that choice is offered. Default=0 (wait for user response). |
| `BalanceShiftKeys=boolean` | Corrects the server when it attempts to change the state of the client keyboard's locking shift key. Default = True | 
| `BalancedShiftMask=integer` |	Uses a bit mask to control the response to attempted changes of individual locking shifts: Scroll=1; Num=2; Caps=4. Setting BalanceShiftKeys=true is equivalent to BalancedShiftMask = 7. Overrides BalanceShiftKeys when set. No default value. | 
| `BufferLength=integer` | Input buffer length. Default=2048  |
| `BypassSetLED=boolean`  |	Prevents virtual applications running macros multiple times. When a virtual application runs a macro on one of the LED key presses (that is, on the Caps Lock, Number Lock, or Scroll Lock key), the application expects the key state to be sent once. However, the macro runs multiple times and sends the state each time. Default=False |
| `CGPAllowed=[On|Off]` | 	Enables or disables Common Gateway Protocol (CGP), the underlying mechanism that provides HDX Broadcast session reliability. Disabling CGP can be useful when debugging this feature. Do not use this setting to configure the feature permanently for users. Use server policies instead. Default=On |
| `CGPAddress=string`  |	Address and port for CGP connection. The address is usually `*` to indicate that the same address should be used as if CGP is not used. For example,`*:1111` will set the port to 1111. Default="*:2598" |
| `CGPSecurityTicket=boolean` | Specifies whether CGP security ticket is to be used, when traversing a Secure Gateway. Default=Off | 
| `ClientComm=[On|Off]`  |	Determines if Client COM Port Mapping is on. Default=On |
| `ClientName=string` | Allows client name to be overridden; normally this is obtained from the system. Default=none (no override) |
| `ClientPrinterList=string`  | Allows specified named printers to be used; for example, `lp1:laser1:lp2`. No default (look in /etc/printcap if `UsePrintcap` is true; or run `lpstat -a`)  |
| `ClientUnicodeEnabled=boolean` |  	Client can use UNICODE. Default=True  |
| `ComPort1...99=string` | COM port device name. No default |
| `ConnectionBar=integer` | Enables the pulldown Connection Bar ("Desktop Viewer") in nonseamless sessions. Default=0 (Disabled) |
| `ConnectionBarDisplayChar=string` | Specifies an alternative keyboard shortcut char for displaying the Desktop Viewer accessibility menu. This can be any of the values F1-F12, Minus, Plus, Tab, or Pause as listed in the ‘[Hotkey Keys]’ section of `$ICAROOT/config/module.ini`. Remember to add this entry to both All\_Regions.ini. Default=Pause  |
| `ConnectionBarDisplayShift=string` | 	Specifies an alternative keyboard shortcut shift for displaying the Desktop Viewer accessibility menu. This can be any of the values Alt, Ctrl, Shift, Alt+Ctrl, Alt+Shift, Ctrl+Shift, and Alt+Ctrl+Shift as listed in the ‘[Hotkey Shift States]’section of `$ICAROOT/config/module.ini`. Remember to add this entry to both All\_Regions.ini. Default=Alt+Ctrl |
| `CRBrowserCommand=string` | Indicates the command used to request the display in an existing browser or start a new browser from those listed. This command is executed after appending the URL. Default= nslaunch firefox, mozilla, iceweasel  |
| `CRBrowserPath=string` | Server to client content redirection browser path. No default. Use `$PATH Obsolete`. |  
| `CREnabled=boolean` | 	Server to client content redirection enabled. Default=True   |
| `CRPlayerCommand=string`  |	Server to client content redirection media player command. `Default=realplay %s Obsolete`. |
| `CRPlayerPath=string`  | 	Server to client content redirection media player path.   No default. Use `$PATH` Obsolete. |
| `CursorStipple=hex_integer,he x_integer` | Defines a stipple pattern in cursor masks to replace inversion regions in Windows cursors. Default=aaaa,5555 |
| `DefaultPrinter=string` |  	Print queue to be used as the default printer in the Citrix XenApp session. For more information, see Workspace app for Linux on the [Product Documentation site](http://docs.citrix.com/). |
| `DefaultPrinterDriver=string` | Printer driver to be used for the default printer in XenApp sessions on Windows. For more information, see Workspace app for Linux on the [Product Documentation site](http://docs.citrix.com/). |
| `DeferredUpdateMode=boolean` |  	Enables batched updates from the Local Video Buffer (LVB) to the screen. The LVB is used when seamless windows or SpeedScreen Latency Reduction are in use, and for 256-color connections when specified by the UseSDLVB parameter. Default=False  |
| `DisableClientAutoQuit=boolean` | Quit client on disconnect. Ignored. |
| `DisableCtrlAltDel=boolean` | Disable requirement for Ctrl+Alt+Delete event to start logon to a Windows server. Default=On. Must be Off for smart card logons. | 
| `DisableSound=boolean` | Disables Windows alert sounds. Default=False  
| `DriveEnabledA…Z=boolean` | True if drive is mapped. Default=False  
| `DrivePathA…Z=string` | UNIX file path for client drive mapping. No default.  
| `DriveReadAccessA...Z=[0|1|2]` | 0=full access, 1=no access, 2=ask user. Default=0  
| `DriveWriteAccessA…Z=[0|1|2]` | 0=full access, 1=no access, 2=ask user. Default=0  
| `DynamicCDM=[On|Off`] | Enabled Dynamic Client Drive Mapping. Default=On  |
| `DynamicCDMDirs=string` | Comma-separated list of directories to monitor for newly mounted file systems. No default  |
| `EchoShiftKeys=boolean`| To improve the behavior of a Windows application that attempts to manipulate the keyboard shift key state. Default=False |
| `EnableAudioLRVolume=boolean` | Specifies that the client audio accepts the left and right volume control set by server. Default=True |  
| `EnableAudioPlaybackRate=boolean` | Specifies that the client audio accepts the playback rate control set by server. Default=True | 
| `EnableAudioVolume=boolean` | Specifies that the client audio accepts the volume control set by the server. Default=True |
| `EnableICC=boolean` | Enables inter-client communication features used by seamless session sharing and Connection Center. Default=True |
| `EnableOSS=boolean` | Allows off-screen drawing surfaces to be used when constructing the image to be displayed. This reduces flicker. Default=True  
| `EnableSessionSharingClient=boolean` | Sends session sharing requests to other ICA sessions on the same X display. Default=False | 
| `EnableSessionSharingHost=boolean` | Accepts session sharing requests from other ICA sessions on the same X display. Default=False | 
| `EnableSSOnThruICAFile=boolean` | Allow ICA file to turn on single sign-on. Default=False  |
| `ForceLVBMode=boolean` | Ensures that the Local Video Buffer (LVB) is used. Default=False  |
| `ForceRedrawOnReset=boolean` | Force server to redraw after a Thinwire reset. This may be needed to clean-up the screen on entry or exit from Shadowing. Default=True  |
| `HBCCapMB` | Sets the cap of the hot bitmap cache. This value is also used when `BatchDecoding` is enabled and replaces `BatchDecodeCacheSize`. Default=48 |
| `HDXoverUDP= string` | Transport protocol; On – Use UDP and do not fall back to TCP on failure; Off – Use TCP; Preferred – Try UDP first and fall back to TCP on failure  Default=Off. |
| `edtMSS= integer` | EDT maximum segment size in bytes. Default = 1500. |
| `edtRCVBUF=integer` | Receive flow window * (edtMSS-28) in bytes. Default = 0. |
| `edtSNDBUF=integer` | Send flow window * (edtMSS-28) in bytes. Default = 0. |
| `edtUDPRCVBUF=integer` | SO\_RCVBUF value passed to underlying UDP socket. Default = 0.| 
| `edtUDPSNDBUF=integer` | SO\_SNDBUF value passed to underlying UDP socket. Default = 0.| 
| `edtIFlightFlagSize=integer` | Buffer count related to in-flight data. Default = 0.| 
| `edtNSGHAFTimeout=integer`| NetScaler Gateway high-availability failover timeout.|  Default = 0.| 
| `HDXWebCamDebug=boolean`| Enables the gst_read debug option. Default=False |  
| `HDXWebCamDelayTime=integer`| The period of time, in milliseconds, to wait before opening a webcam during a session. Default=2000ms | 
| `HDXWebCamDelayType=integer`| Determines whether or not to delay the opening of a webcam during a session. 0=do not delay opening, 1=if last close was less than delay time, delay by time remaining, 2=always delay. Default=1 |  
| `HDXRTMEWebCamLaunchDelayTime=integer` | Determines the delay, in milliseconds, to wait at startup before the webcam can be activated, to allow the RTME plugin a chance to grab the camera (if installed). Default = 45000ms |
| `HDXWebCamDevice=string` | Location of the webcam device. Default=/dev/video0  
| `HDXWebCamEnabled=boolean` | Enables webcam support if AllowAudioInput is also true. Default=True |  
| `HDXWebCamFramesPerSec=integer` | Frame rate requested from a webcam. Default=15  
| `HDXWebCamGStDebug=string` | Comma-separated list of GStreamer debug options. No default |   
| `HDXWebCamHeight=integer` | Height of image requested from a webcam. Default=288  |  
| `HDXWebCamFramesPerSecDenominator=integer`  | Denominator of a fraction specifying the frame rate requested from webcam. The numerator is HDXWebCamFramesPerSec. Default=1 |  
| `HDXWebCamQuality=integer` | Theora quality requested from a webcam, within a range of 1-63. Default=16  |  
| `HDXWebCamWidth=integer` | Width of image requested from a webcam. Default=352 |   
| `HoldComPortsOpen=boolean` | Determines whether the client holds system serial ports open for session duration. Default=False  |  
| `Hotkey1...12Char=[F1...F12]` | Function key to use for mapping keyboard shortcut sequence ALT+Fn.  |  
| `HotKey1...12Shift=string` | Shift state to get keyboard shortcut mapping for Alt+Fn; for example, ALT+CTRL. |
| `HowManySkipRedrawPerChange=integer` | The maximum number of successive palette changes that can follow one another closely without a redraw. Default=9  |
| `HttpBrowserAddress=string` | Server name or IP address used for HTTP browsing. Default=ica |
| `HttpBrowserAddress2...14=string` | Server names or IP addresses for business failover. No default |
| `ICAKeepAliveEnabled=boolean` | Monitors reception of data from the ICA host and assumes the connection has failed if a request packet fails to produce a response. Default=TransportReconnectEnabled setting | 
| `ICAKeepAliveInterval=integer` | The interval, in milliseconds, for checking on data received when ICAKeepAliveEnabled is set. Disconnection occurs if the connection is idle for the specified period and if no response is received during this time after a request. Default=10000 | 
| `IgnoreErrors=integer list` | A comma-separated list of the error numbers to be ignored by the client. No default | 
| `IgnoreFileChangeSize=boolean` | Stops time-out copying large files to floppies.  Default=False | 
| `IgnoreShutdownErrors=boolean` | Error messages are not shown during session shutdown when this is enabled. Default=True | 
| `KeyboardDescription=string` | Description of keyboard mapping. Default=Automatic (User Profile) | 
| `KeyboardLayout=string` | Keyboard layout from module.ini. Default=none  
| `KeyboardMappingFile=string` | Name of file in `$ICAROOT/keyboard`. Default=automatic.kbd | 
| `KeyboardTimer=integer` | Keyboard event flush interval. Default=0ms  
| `KeyboardType=string` | Selects a keyboard type code to be sent to the server. The value should be one of the strings in the [KeyboardType] section of module.ini.  
| `LastComPortNum=integer` | Last COM port device number used. Default=0  
| `MapMouseButton2= boolean` | Treats the middle mouse button the same as the right button. Default=False  |
| `MouseDoubleClickHeight=integer` | Mouse double-click height in pixels. Default=4 |  
| `MouseDoubleClickTimer=integer` | Mouse double-click time. Default=500ms | 
| `MouseDoubleClickWidth=integer` | Mouse double-click width in pixels. Default=4 | 
| `MouseMap=string` | 	Mouse button remapping: a string of up to ten of the letters X, B, W, C. M, with an optional unsigned integer parameter, each specifying an action for a mouse button: <br> X - ignore; <br> B - send a (possibly different) button to the server; <br> W - send a vertical scroll wheel up/down event <br> H - send a horizontal scroll wheel left/right event <br> C - send an ASCII character with left- control down <br> M - as for C, but only to Windows servers, otherwise send the button. <br>  Buttons have the "natural" numbering, so the middle of three main buttons is 2, not 3 as MS have it. The default, "BBBW1WH1HB4B5", is good for Linux/Unix clients with X11, where wheels are presented as buttons 4-7. An alternative string for those who hate to have to touch the keyboard for cut and paste: "BM118BW1WH1HM99M120". For Windows servers, Ctrl-V, C and X are available on buttons 2, 8 and 9. (Button 2 is normally "Paste PRIMARY" in X11. |
| `MouseScrollAmount=integer` | Sets the amount moved for each scroll wheel click. Default=120 | 
| `MouseTimer=integer` | Mouse event flush interval in milliseconds or zero. Default=0 | 
| `MouseWheelMapping=integer,integer` | Mouse buttons whose down events are treated as a mouse wheel motion in the ICA protocol. Default=4,5 | 
| `MouseXButtonMapping=integer,integer` | Specifies mouse buttons that should be mapped as additional buttons X1 and X2. Default=8,9  |
| `MSLocaleNumber=hexnumber` | The Microsoft locale identifier to send to the server. These numbers are identical to the low 16-bits of the corresponding keyboard layout numbers. Always be tried before the configuration file is checked. Default=""|
| `PointerClickTime=integer` | Specifies the length of time after a mouse click that the client allows attempts by the server to move the pointer, overriding the effect of PointerGrabTime. Default=1000 (milliseconds) | 
| `PointerGrabTime=integer` | Specifies the length of time after mouse movement that the client ignores attempts by the server to move the pointer. This is for echo suppression. Default=750 (milliseconds)  |
| `ReaderStatusPollPeriod=integer` | Smart card status polling period. Default=5000ms   |
| `Realm_abc=ANY.COM` | Causes Windows domain abc to be mapped to Kerberos realm ANY.COM when changing an expired password. The default action is to map to uppercase (ABC). |  
| `SessionReliabilityTTL=integer` | Client-Side CGP timeout - the period of time in seconds during which the client will attempt a CGP reconnection. Default=180 | 
| `SetTWIFocus=boolean` | Propagates local focus changes for seamless windows to the server. Default=False Note that the default setting for versions earlier than 8.2 is True. |
| `ServerDoesMultiMod=boolean` | Should be set when the client's X11 server accurately reflects physical motion of notionally locking shift keys (Caps Lock, Scroll Lock, and Num Lock). Some (non-Linux) X servers treat these keys as though they really locked, halving the number of events reported. Default=True |
| `ShadowPointer=boolean` | Passes mouse pointer-positioning commands to the X server. Default=True  |
| `SkipRedrawPerPaletteChange=boolean` | Enables batching of redraw requests following palette changes. This reduces flickering when an application changes the palette rapidly. It is only relevant in 256 color mode when shared colors or a TrueColor visual are used. It is ignored if Session-Depth Local Video Buffer (SDLVB), the default, is used. Default=Off | 
| `SmallFramesEnabled=boolean` | Controls the use of small, non-H. 264, rectangle updates in H.264 mode. Ignored unless TextTrackingEnabled is true. Default=True |
| `SoftwareMouse=boolean` | Hides the OS mouse pointer when it is in the session window, and causes wfica to draw the mouse image itself. Not effective in Seamless sessions. Default=False | 
| `SpeedScreenMMAAudioEnabled=boolean` | Enables HDX MultiStream Windows Media Redirection support for compressed audio data. Default=True | 
| `SpeedScreenMMAFlowControlV3=boolean` | Enables Version 3 flow control for HDX MultiStream Windows Media Redirection support when used with suitable servers. Default=True | 
| `SpeedscreenMMAForceAspectRatio=boolean` | Sets the force\_aspect\_ratio property for the GStreamer image sink element. Default=False  |
| `SpeedscreenMMAGSTCheck=boolean` | When enabled, checks for GStreamer support. Default=False | 
| `SpeedScreenMMASecondsToBuffer=integer` | Number of seconds of multimedia data that the server expects to be buffered in the client. Default=10 |
| `SpeedScreenMMAStopOverlayHandlingEvents=boolean` | Stops GStreamer overlay from handling X events. This avoids a problem with mouse movements not ending Windows Media Player's full screen mode properly. Note, however, that this may cause problems with the size of the video window. Default=True |
| `SpeedScreenMMAVerbose=boolean` | Enables logging of format information for audio and video streams in the Citrix HDX MultiStream Windows Media Redirection channel. Default=False |
| `SpeedScreenMMAVideoEnabled=boolean` | Enables HDX MultiStream Windows Media Redirection support for compressed video data. Default=True  |
| `SSLEnable=boolean` | Controls the use of SSL for TCP connections that do not specify their own value. Default=False | 
| `SSLInTitle=boolean` | Controls whether or not the SSL strength indicator is shown in a session window's title bar. Default=On  |
| `SSOnUserSetting=boolean` | Allows UseLocalUserAndPassword to be trusted in appsrv.ini. Default=False |
| `StopOnUnmap=boolean` | Commands the server to stop sending screen updates when the session window is iconified. Default=True |
| `SucConnTimeout=integer` | Works with the `ApplySucConnTimeoutToDesktops` setting.  Specifies the number of seconds to wait for a recently started session to become available for session sharing. When `ApplySucConnTimeoutToDesktops` is applied to desktops, repeated clicks Delaunch multiple sessions, but you can set SucConnTimeout to a suitable timeout and run a custom script in between the desktop launches. Default=20. **Note**: To revert to the behavior in versions before Workspace app for Linux 13.0, and allow a separate session launch for each click, set SucConnTimeout to 0. |
| `SunRayClientName=string`| Specifies the prefix part of a SunRay client name with URL escape characters. This allows trailing spaces, represented by %20. The remaining part of the client name is based on the Ethernet address of the SunRay terminal. Default=SunRay- | 
| `TcpBrowserAddress=string` | Server name or IP address to use for browsing. No default. Use broadcast. | 
| `TcpBrowserAddress2...15=string` | Controls the protocol used to locate the ICA host for the connection. This is a default value for connections that do not specify it individually. | 
| `TCPRecvBufferSize=integer` | Similar to TCPSendBufferSize except that it sets the receive buffer size. No default. | 
| `TCPRecvBufferSizeNoFlow=integer` | Similar to `TCPRecvBufferSize` except that it is used only when `TCPRecvBufferSize` is not set and the server does not support flow control. When flow control is supported and `TCPRecvBufferSize` is not set, the kernel is allowed to control the buffer size. Default: 60 |
| `TextTrackingEnabled=boolean` | Controls the use of optimized lossless text overlays in H.264 mode. Default=True | 
| `TransportReconnectDelay=integer` | Time in seconds to wait for the network to recover before automatic reconnection starts. Default=30 |
| `TransportReconnectEnabled= boolean` | Enables automatic reconnection of sessions when the network connection to the ICA host is lost.  Default=True  
| `TransportReconnectOptions=integer` | Specifies options for automatic reconnection. Add 1 to show a dialog box during reconnection, and 2 to remove session windows when reconnection starts. Default=3 | 
| `TransportReconnectRetries=integer` | Specifies how often to retry automatic reconnection. Default=3  |
| `TWICleanupTimer=integer` | Period in milliseconds of a watchdog timer that prevents corruption of Seamless window after a window moves or resizes. Default = 50 |
| `TWICoordinateWinPosition=boolean` | Seamless windows: try to force repositioning of a server window after a server-controlled move has positioned it outside the work area. Recommended only when using outline move on the server, and the behavior may be sensitive to the local window manager. Default = Off |
| `TWIFlashMethod=integer` | Sets the method to handle a "flash window icon" command for a Seamless window. The value is formed by adding selection of the following numbers: <br> 1- use the \_NET\_WM\_STATE\_DEMANDS\_ATTENTION request to the Window Manager; <br> 2- set the Urgency bit in the WM_HINTS window property; <br> 4- rudely attempt to force the window to the top of the stack; <br> 8- standard-violating last ditch method: use the overrideredirect attribute to force the window to the top of the stack. <br> Default = 3 |
| `UnixPrintCommand=string` | Command format used to print files. Default="lpr -P\\"%s\\""  |
| `UpdateTime=integer` | Time in milliseconds between batched Local Video Buffer (LVB) updates. Default=100. Note that this value is used only if your server does not control updates.  |
| `UseAlternateAddress=boolean` | 	Uses alternate address for firewall connections. Default=False  |
| `UseIconWindow=boolean` | Uses a window rather than a pixmap for the icons of session windows. This is required for strict CM compliance, but note that many window managers do not show icons correctly if this is set to True. Default=False |
| `UseLocalIM=boolean` | 	Uses the local X input method to interpret keyboard input. This is supported only for European languages. Default=True | 
| `UseLocalUserAndPassword=boolean` | 	Enables Kerberos authentication for the current connection (see also SSOnUserSetting and EnableSSOThruICAFile). Default = False |
| `UsePrintcap=boolean` | Allows Workspace app for Linux to look for printers in /etc/printcap. Default=False  |
| `UserVisualClass=string` | Allow user-specified X visual class. Value is PseudoColor, TrueColor, or Grayscale. No default. |  
| `UserVisualID=hexadecimalinteger` | 	Uses this X visual, if possible, for session windows. No default.  |
| `Version=integer` | Fixed value=2, overrides value in appsrv.ini, ignored.  
| `WindowManagerHeightAllowance=integer` | Estimated height in pixels of window manager top and bottom frames. Default= 60  |
| `WindowManagerWidthAllowance=integer` | Number of pixels to allow for Window Manager decoration. Default=20  |
| `WpadHost=string` | Specifies the URL to query for the automatic proxy detection configuration file. Default= http://wpad/wpad.dat |  
| `XmlAddressResolutionType=[DNS-Port | IPv4-Port]` | Controls the form used for the ICA host location. Using DNSPort (the default) may help a connection to pass through an addresstranslating firewall.  |
| `XmsReserve=integer` | Default=0. Ignored |
| `[Thinwire3.0]` | Thinwire Virtual Driver configuration. | 
| `ApproximateColors=boolean` | Default color approximation setting. Default=False |
| `BypassWindowManager=boolean` | Creates all seamless windows with the override-redirect attribute, so that they are ignored by the local window manager. Default=False  |
| `DesiredColor=integer` | `[1|2|4|8|15]` (1 = 4 bit (16 colors), 2 = 8 bit (256 colors), 4 = 15 bit, 8 = 24 bit, 15 chooses the greatest depth that the hardware supports. If the option is not present in the ICA file, a value from [Thinwire3.0] is used, with a final built-in default value of 15. |
| `DesiredHRES=integer` | Default horizontal window dimension. Default=640  |
| `DesiredVRES=integer` | Default vertical window dimension. Default=480  |
| `DisableXRender=boolean`| Disables the use of the X11 Render extension required for color cursors. Default=False | 
| `ForceEmbeddedColormapSwitch=boolean` | Forces sessions that are embedded in a web page to use a private colormap. Default=False | 
| `IgnoreXErrors=string` | Comma separated list of entries such as m.n/ p meaning ignore error code p on X protocol request with major type m and minor type n. No default. |
| `InstallColormap=boolean` | Installs the colormap when an override- redirect seamless window gains focus. Default=True |  
| `LargeCacheSizeInK=integer` | Large cache size in KB. Default=2048 |
| `LocalWMDecorations=boolean` | Allows the X window manager to decorate seamless windows. Default=False  |
| `PersistentCacheMinBitmap=integer` | Minimum size of bitmap for caching. Default=8192 bytes |  
| `PersistentCachePath=string` | Location of persistent cache. Default=”Cache”  |
| `PersistentCacheSize=integer` | Persistent cache size in KB. Default=0  |
| `RedrawTimer=integer` | Time delay (milliseconds) before a new screen update is requested after copying multiple obscured screen regions. Default=1000  |
| `ScreenPercent=integer` | Percentage of screen to use. Default=-1. Only values 1-100 are used. |  
| `Tw2CachePower=integer` | Sets the size of the Thinwire 2 bitmap cache. Attempting to set this lower than 19 (512 KB cache) or higher than 25 is ineffective. The default value is calculated dynamically to be 1.25 times the screen image size at the preferred color depth. | 
| `TWIMoveResizeHideWindowType=integer` | Controls the method used for hiding server-side windows when moving or resizing client side seamless windows that are controlled by a window manager. 1 hides server-side windows by minimizing them. 2 hides server-side windows by moving them to the bottom right corner, outside the screen. Default=1. Other values are invalid. |
| `TWISetFocusBeforeRestore=boolean` | Sets the focus on server-side windows before restoring them. This is a workaround for an issue with virtual Java applications. Default=False  |
| `TWIWSHideWindowType=integer`| Controls the method used for hiding server-side windows when switching between client-side workspaces. 1 hides server-side windows by minimizing them. 2 hides server-side windows by moving them to the bottom right corner, outside the screen.  Default=1. Other values are invalid. | 
| `TwTotalOssSizePowerOf2=integer`| Sets the maximum size of off-screen drawing surfaces used by the X server. (See EnableOSS). Default=24, meaning 16 MB. | 
| `XFree86ShapeFixLevel= hexadecimal integer`| Highest version number of XFree86 X servers that require a workaround when using the SHAPE extension. Default=40200001 (Version 4.2.1) |  
| `RelativeMouse=int`| Sends relative (incremental) mouse position reports, if the server offers this feature. <br>  Valid values: <br> 0 - Off; <br> 1	- Under keyboard control; disabled when focus is lost, initially off; <br>2	– Automatically enabled when session has keyboard focus; <br>3	- Under keyboard control, initially on; <br>4	– Enabled when the mouse pointer is hidden, under keyboard control. <br> Default is Off.  
| `RelativeMouseMap=int` |	Bitmap-encoded policy for the relative mouse. The value is formed by adding the following values: <br> 1 - keyboard control is enabled; <br> 2 - enable when a session starts; <br> 4 - enable when a session gains keyboard focus; <br> 8 - disable when a session loses keyboard focus; <br> 16 - enable when the server hides the mouse cursor; <br> 32 - disable when the server shows the mouse cursor. <br> Default is set by the RelativeMouse value. |
| `RelativeMousePointerFeedback=boolean` | Accepts all mouse-positioning commands from a server when using Relative Mouse. That keeps the pointer positions synchronized between client and server with XenDesktop 7.11 and later when the round-trip time is short. It may cause problems otherwise. Default is True | 
| `RelativemouseOnChar=string` | Keystroke to enable Relative Mouse. Default is "F12"   |
| `RelativeMouseOnShift=string` | Modifier keys used with `RelativemouseOnChar`. Default is "Ctrl" |
| `RelativemouseOffChar=string` | Keystroke to enable Relative Mouse. Default is "F12" | 
| `RelativeMouseOffShift=string` | Modifier keys used with `RelativemouseOffChar`. Default is "Ctrl+Shift" | 
| `SpeedScreenMMAEnablePlaybin2=boolean` | Enables GStreamer playbin2 support, falling back to playbin if disabled.  Default = True |  
| `SSONDetected=boolean` | A boolean setting enabled when Single Sign-on is being used. Default=False |
| `UseLocalUserAndPassword=boolean` | Enables Kerberos authentication for all connections. Default = False |
| `EnableSSOThruICAFile=boolean` | Allows UseLocalUserAndPassword to be trusted in ICA files, default=False. Note that this is always trusted in ICA files obtained by PNAgent.  |
| `SSLCertificateRevocationCheckPolicy=string` | Accepted values: `NoCheck`, `CheckWithNoNetworkAccess`, `FullAccessCheck`, `FullAccessCheckAndCRLRequired`. Default=`CheckWithNoNetworkAccess` | 
| `SSLCRLParentDir=string` | An existing directory in which a "crls" sub-directory might be created to hold Certificate Revocation Lists. Default=`CheckWithNoNetworkAccess`. This option is only read from `$HOME/.ICAClient/wfclient.ini`. Environment variables can be expanded. | 
| `MinimumTLS=string` | The lowest version of the TLS protocol that can be used: 1.0, 1.1 or 1.2. The '.' may be omitted.  Default=1.0 |
| `MaximumTLS=string` | The highest version of the TLS protocol that can be used: 1.0, 1.1 or 1.2. The '.' may be omitted. Default=1.2 | 
| `ProxyPort=integer` | Port number for proxy. If present, it overrides any port value in ProxyHost. Default=0  |
| `ProxyHost=string` | Name of proxy server (The optional ":port" is only used if ProxyHost is not set) Default=""  |
  
### module.ini  

This file contains a comprehensive listing of parameters used to select and configure the communications stack modules. The section headings identify the target module by name. The stack element types are:  

* Transport Drivers (TD) - manage the communications connection. 
* Protocol Drivers (PD) - manage intermediate data stream filters.  
* WinStation Drivers (WD) - manage the presentation data stream. 
* Virtual Drivers (VD) - manage ICA protocol extensions.  

These elements are all loaded depending on the user configuration and the required stack relationships. The transport driver is loaded first, then protocol drivers, the WinStation driver, and virtual drivers. Each of the supported types has a section that describes the module name and default parameters. Most parameters in this file are defaults. They can be overridden by equivalent entries in appsrv.ini, an ICA file or All\_Regions.ini. 

### Parameter syntax  

Boolean parameters use Yes, True, 1, or On to indicate TRUE. Any other values, including No, False, 0, or Off, are interpreted as FALSE.  

For all parameters, spaces are significant and values are case-sensitive.  

Those marked as ignored are not currently used by the client, but can be reserved for future use, are redundant, or are used by other clients; for example, Win32 or Macintosh. In the last case, the parameter is read by the client but the result discarded. 
 
Default values are embedded into the client program itself. Fixed values are set by the unmodified .ini configuration files. 
 
Note: The values in module.ini are not affected by those in All\_Regions.ini in the same way that values from other configuration files are. This is because the same permissions are required to change both files.  

In the following table, the parameters are listed alphabetically within each section of the file.  

| Item | Description |
|---|---|
| `[WFClient]` | This section is used by the engine. It contains default session oriented parameters. |  
| `AllowWriteOpenToROF=boolean` | Emulates Microsoft Windows behavior by allowing files on a readonly disk to be opened for writing. Default=True | 
| `AttemptCrossPlatformSessionReuse=boolean` | Allows a seamless published application launched from one system to run in an ICA session originally started from a different system. The two systems must use the same X display. Default=False  |
| `AllowMultiStream=boolean` | Uses multi-stream ICA. Default=FALSE |
| `ContentRedirectionScheme=scheme1, scheme2` | Defines a list of schemes for server to client content redirection. Server-client content redirection allows administrators to specify that URLs in a published application are opened using a local application. Each scheme is defined by its own section. |  
| `DeferredUpdateMode=boolean` | Enables an efficient algorithm for updating seamless windows. Default=False |
| `DesktopApplianceMode=boolean` | Enables unconditional attaching of USB devices.  When Off devices are only candidates for remote control when the session has the keyboard focus. Default=Off |
| `EnableSessionSharingClient=boolean` | When launching a seamless published application, search for an existing ICA session that can run it. Default=False |
| `EnableSessionSharingHost=boolean` | Allow independently launched seamless published applications to run in the same ICA session. Default=False  
| `HostLookupTimeout=integer` | Time-out (in seconds) for calls to gethostbyname(). Used only on Solaris. Default=5 |
| `KeyPassthroughEscapeChar=string` | Key for the keyboard command to disable the transparent keyboard mode.  Default=F2 | 
| `KeyPassthroughEscapeShift=string` | Keyboard shift for the keyboard command to disable the transparent keyboard mode. Default=Ctrl |
| `PrinterQueryRefreshTime=integer` | Maximum time in seconds to cache list of available printer queues. Default=60 |
| `ReplaceOverlineWithTilde=boolean` | Treat overline key as tilde. Used only when Japanese keyboard layout is selected. Default=False |
| `ServerToClientPowerOf2=integer` | Controls the buffer size for the compression method used in MetaFrame 1.0. Default=15 |
| `TransparentKeyPassthrough=string` | Enables keyboard shortcut sequences defined by the local Windows manager in the session. Keywords are: Local, Remote, FullScreenOnly. Default=FullScreenOnly | 
| `UseSystemCharacterConversion=boolean` | Uses CHARICONV.DLL in preference to CHARCONV.DLL for character encoding conversions. Default=True |
| `Version=2` | Fixed value; overrides value in appsrv.ini. Ignored. | 
| `[ICA 3.0]` | Client module configuration | 
| `AllowShared16Colors=boolean` | Enables colormap entry sharing for 16-color. | 
| `BufferLength2=integer` | High performance buffer length. Default=5000  |
| `ClientAudio=boolean` | Enables client audio mapping. Default=On |
| `ClientComm=boolean` |	Enables serial port mapping. Default=On  |
| `ClientDrive=boolean` | Enables client drive mapping. Default=On |
| `ClientPrinterQueue=boolean` | Enables printer queue mapping. Default=On |
| `Clipboard=boolean` | Enables the clipboard. Default=On |
| `ICACTL=boolean` | Enables the ICA control channel. Default=On |
| `MaxRequestSize2=integer` | High performance buffer request size. Default=4116 |
| `MaxWindowSize2=integer` | High performance buffer window. Default=62500 |
| `MultiMedia=boolean` | Enables HDX MediaStream Multimedia Acceleration. Default sets to On during installation if GStreamer is installed. |
| `SmartCard=boolean` | Enables smart card support. Default=On |
| `ThinWire3.0=boolean` | Enables Thinwire. Default=On |
| `TWI=boolean` | Enables seamless VD. Default=On |
| `UserExperience=boolean` | Enables performance information. Default=On |
| `VirtualDriver=stringlist` | Comma-separated list of VDs to load. |
| `WindowSize2=integer` | High performance window size. Default=4102 bytes |
| `ZL_FONT=boolean` | Enables latency reduction font VD. Default=On |
| `ZLC=boolean` | Enables latency reduction VD. Default=On |
| `[TransportDriver]` | This section lists all of the sections in module.ini that define transport settings. |  
| `TCP/IP=` | Fixed null value. |  
| `[TCP/IP]` | Transport driver configuration. | 
| `BrowserRetry=integer` | Number of attempts to locate data collector, which acts as master browser. Default=3 |
| `BrowserTimeout=integer` | Number of milliseconds to wait before retry. Default=1000 |
| `Encrypt=boolean` | Turns on basic encryption. Default=Off. Fixed value=On |
| `ICAPortNumber=integer` | Server port to use for ICA connection. Default=1494 from the Internet Assigned Numbers Authority (IANA) |
| `ProtocolSupport=stringlist` | Protocol drivers to load, fixed value=Rframe, Encrypt. |
| `OutBufCountClient=integer` | Number of client output buffers to allocate. Default=6  |
| `OutBufCountClient2=integer` | High performance client buffer count. Default=42 |  
| `OutBufCountHost=integer` | Number of server output buffers to allocate. Default=8 |
| `OutBufCountHost2=integer` | High performance server buffer count. Default=42 |  
| `OutBufLength=integer` | Size of output buffer. Default=512. Fixed value=530 bytes. |  
| `OutBufLength2=integer` | High performance buffer length. Default=530 bytes |
| `RFrame=boolean` | Turn on reliable framing. Default=Off. Fixed value=On. |
| `[XenDesktop]` | Parameters specifically for connection to XenDesktop, particularly for full-screen sessions. | 
| `[RFrame]` | Reliable framing protocol driver configuration, no parameters. |
| `[EncryptionLevelSession]` | This section specifies the encryption protocol for each level of encryption. EncryptionLevelSession in appsrv.ini defines the level used by each connection. Each encryption protocol is defined by corresponding drivers specified in module.ini. | 
| `Basic=Encrypt` | Fixed value. | 
| `RC5 (128 bit-LoginOnly)=EncRC5-0`| Fixed value. |
| `RC5 (40 bit)=EncRC5-40` | Fixed value. | 
| `RC5 (56 bit)=EncRC5-56` | Fixed value. | 
| `RC5 (128 bit)=EncRC5-128` | Fixed value. |  
| `[Encrypt]` | Encryption protocol driver configuration. |  
| `DriverName=PDCRYPT1.DLL` | Fixed value. |
| `[EncRC5-0]` | Encryption protocol configuration. |  
| `DriverName=PDCRYPT2.DLL` | Fixed value. |  
| `[EncRC5-40]` | Encryption protocol configuration. | 
| `DriverName=PDCRYPT2.DLL` | Fixed value. | 
| `[EncRC5-56]` | Encryption protocol configuration. |  
| `DriverName=PDCRYPT2.DLL` | Fixed value.  |
| `[EncRC5-128]` | Encryption protocol configuration. | 
| `DriverName=PDCRYPT2.DLL` | Fixed value. | 
| `[Reliable]` | Reliable transport protocol driver. Ignored. | 
| `[Compress]` | Compression protocol driver configuration. Ignored. | 
| `[Framing]` | Framing protocol driver configuration. Ignored. | 
| `[Modem]` | Async protocol driver configuration. Ignored. | 
| `[Thinwire3.0]` | Thinwire virtual driver configuration, overridden by parameters in wfclient.ini.  
| `[Clipboard]` | Clipboard virtual driver configuration. | 
| `ClipboardAllowed=boolean` | Enables the clipboard channel. Default=True |  
| `[ClientDrive]` | Client drive mapping virtual driver configuration. | 
| `AllowSymlinkTraversalOutsideMap=boolean` | Allows the following of symlinks outside the mapped root of the client drive mapping host. Default=False | 
| `CacheDisable=boolean` | Disable cache. Default=False | 
| `CacheTimeout=integer` | Cache time-out (seconds). Default=600 |  
| `CacheTimeoutHigh=integer` | Cache time-out for times greater than 18 hours. Default=0 |
| `CacheTransferSize=integer` | Amount of data to transfer per operation. Default=0 (ICA buffer size) |  
| `CacheWriteAllocateDisable=boolean` | Disable cache for write operations. Default=False | 
| `CDMReadOnly=boolean` | Allow only read-only access to client filesystems. Default=False |  
| `DesktopFolder=path` | Sets the desktop directory for the Special Folder Redirection feature. No default. |  
| `DocumentsFolder=path` | Sets the documents directory for the Special Folder Redirection feature. No default. |
| `MaxRequestSize=integer` | For flow management. Fixed value=1046 bytes. |
| `MaxWindowSize=integer` | Window size for flow management. Fixed value=6276 bytes.  |
| `SFRAllowed=boolean` | Enables the Special Folder Redirection option. Default=False | 
| `TranslateCDMFileNames=boolean` | The file names passed through the CDM channel are translated into the character encoding of the receiving system, in both directions. Default=True | 
| `[ClientPrinterQueue]` | Client printer mapping virtual driver configuration. | 
| `MaxWindowSize=integer` | Maximum window size for flow management. | Fixed value=1024 bytes. | 
| `MFPrintCommand=string` | Command to use for Universal Printer Driver (UPD) printing. Default=lpr -P |
| `UnicodeEnabled=boolean` | Enable UNICODE printer names. Default=True |
| `UnixPrintCommand=string` | Command to use for non-UPD printing. Default=lpr -l -P |
| `WindowSize=integer` | Write window size for flow management. Fixed value=512 bytes. | 
| `[ClientAudio]` | Client audio mapping virtual driver configuration.  
| `AckDelayThresh=integer` | Max time (in milliseconds) between sending "resource free" message if any resources free. Default=350 |
| `AudioBufferSizeMilliseconds=integer` | Audio buffer size, in ms. Default=200 ms |
| `AudioDevice=string` | Audio device name. Linux default=default, SPARC default=/dev/audio. No default for other platforms. | 
| `AudioLatencyControlEnabled=boolean` | Enables latency control. Default=False |
| `AudioMaxLatency=integer` | Sets the maximum latency (in ms) before trying to discard audio data. Default=300 ms |
| `AudioLatencyCorrectionInterval=integer` | Defines how often to correct the latency (in ms). Default=300 ms |
| `AudioTempLatencyBoost=integer` | Sets the higher latency band (in ms) above the lower PlaybackDelayThresh band. Default=300 ms |
| `CommandAckThresh=integer` | Number of free client command buffers causing a "resource free" message to be sent to the server. Default=10 | 
| `DataAckThresh=integer` | Number of free client data buffers causing a "resource free" message to be sent to the server. Default=10 |
| `DriverName=VDCAM.DLL` | Fixed value. |
| `MaxDataBufferSize = integer` | Maximum size of each data buffer. Default=2048 bytes |
| `NumCommandBuffers=integer` | Number of client buffers to use for audio commands. Default=64 |
| `PlaybackDelayThresh=integer` | Delay (in ms) between being asked to start audio playback and actually starting audio playback in order to build up a backlog of sound. Default=150 |
| `[AudioConverter]` | Audio format converter configuration. | 
| `DriverName=ClientAudCvt` | Fixed value. |
| `[AudioConverterList]` | Audio format converter configuration. |  
| `Converter0=ADPCMConverter` | Fixed value. | 
| `NumConverters=1` | Fixed value. | 
| `[ADPCMConverter]` | Audio format converter configuration. |  
| `DriverName=ADPCM_Module` | Fixed value. |  
| `NumDataBuffers=integer` | Number of client audio data buffers. Default=32 | 
| `[ClientComm]` | Client COM port mapping virtual driver configuration.  
| `CommPollSize=string` | Use asynchronous polling. Default=Off |
| `CommPollWaitInc=integer` | See CommPollWaitIncTime. Default=1 |
| `CommPollWaitIncTime=integer` | Time (in ms) polling will poll before slowing by the number of milliseconds defined in CommPollWaitInc. Default=20 |
| `CommPollWaitMax=integer` | Slowest COM port polling rate. Default=500 ms |
| `CommPollWaitMin=integer` | Time (in milliseconds) to delay after receiving data. Default=1 | 
| `CommWakeOnInput=boolean` | Uses the client's event loop to wake up immediately when serial port data is available to be read. Used only when CommPollSize=True. Default=True |
| `WindowSize=integer` | Window for flow management. Default=1024 bytes |
| `[TWI]` | Seamless parameters. | 
| `DriverName=VDTWIN.DLL` | Fixed value. | 
| `[ZLC]` | Zero latency parameters. |
| `DriverName=VDZLC.DLL` | Fixed value. | 
| `[ZL_FONT]` | Zero latency font parameter. | 
| `DriverName=VDFON30W.DLL` | Fixed value. | 
| `[ICACTL]` | ICA control channel parameters. |  
| `[KeyboardLayout]` | List of possible keyboards supported. |
| `keyboardname=locale` | Keyboard name; for example, British, German, US, and NT locale identifier. Fixed value. | 
| `[KeyboardType]` | List of supported keyboard types.  
| `keyboardtype=identifier` | One keyboard type entry for each supported keyboard type. |
| `[SmartCard]` | Smart card virtual driver configuration. | 
| `DriverName=VSCARD.DLL` | Fixed value. |
| `PCSCCodePage=integer` | Code page that must be used for communication with smart cards and readers. Default=0. A value of zero means use the default code page for the language used by the client. | 
| `PCSCLibraryName=string` | File name of PC/SC shared library for smart card access.   Default=libpscsclite.so |
| `SmartCardAllowed=boolean` | Allows access to smart card devices on the client machine. Default=True | 
| `[Hotkey Shift States]` | Fixed values for keyboard shortcut masking. | 
| `(none)=0` | Fixed value. |  
| `Alt=2560` | Fixed value. |
| `Ctrl=1280` | Fixed value. | 
| `Shift=3` | Fixed value. | 
| `Alt+Ctrl=3840` | Fixed value. |  
| `Alt+Shift=2563` | Fixed value. |  
| `Ctrl+Shift=1283` | Fixed value. |
| `Alt+Ctrl+Shift=3843` | Fixed value. | 
| `[Hotkey Keys]` | Fixed scan code values for keyboard shortcut keys.  
| `(none)=0` | Fixed value.  
| `F1...F12=112...123` | Fixed values. |
| `Minus=12` | Fixed value. |
| `Plus=13` | Fixed value. |
| `Tab=16` | Fixed value. |
| `[File Type Associations]` | This section lists the names of applications together with the file name extensions of their data files. It is used to construct the File Associations properties menu on clients with CDE support, and when the client is configured to use static file type associations. |
| `[Scheme]` | Defines the type of scheme for this section, for example [Browser] or [Player]. For more information, see the ContentRedirectionScheme parameter in module.ini. |
| `AcceptURLType=type1, type2` | The types of URL accepted by a given scheme, for example http, https. |
| `Command=string` | The command that runs the executable used for server to client redirection. No default. |
| `Path=string` | Search path for the executable used for server to client redirection. No default. |
| `PercentS=integer` | Number of "%s" occurrences in the command used for server to client redirection. |
| `RejectURLType=type1, type2` | The types of URL rejected by a given scheme. |
| `[HeimdalKerberos]` | This section contains information about the Heimdal implementation of Kerberos. | 
| `LIBKCP=string` | The library to use for changing expired passwords using Heimdal 
Kerberos. Default=libkcph.so  |
| `[MITKerberos]` | This section contains information about the MIT implementation of Kerberos. | 
| `LIBKCP=string` | The library to use for changing an expired password using MITKerberos. Default=libkcpm.so | 
| `PrinterFlowControl=boolean` | Enables flow control in the printing channel, usually only used with `UnixPrintCommand` when the command is blocked. Default = Off  |
| `[CEIP]` | This section contains information about the Citrix Customer Experience Improvement Program (CEIP). |
| `EnableCeip=Enable` | By default, you are automatically enrolled in CEIP when you install Citrix Workspace app for Linux. |
| `[WebPageRedirection]` | This section contains information about driver which is used for browser content redirection. |
| `DriverName = VDBROWSER.DLL` |  |
| `[PortForward]` | This section contains information about driver which is used for  port forwarding. |
| `DriverName = VDPORTFORWARD.DLL	` | |

### reg.ini  

reg.ini contains Citrix XenApp configuration settings. It is written by pnabrowse so it does not exist immediately after a typical installation. reg.ini provides initial values to pnabrowse that you can override through command-line arguments.  

**Important**: reg.ini works with pnabrowse only. It has no effect on the deployments involving storebrowse or selfservice.  

You may prefer to have a password in reg.ini, because this file has restricted read permission, rather than have it appearing on the command line. To do this, change  
`lastSavePassword=REG_DWORD:0` to `lastSavePassword=REG_DWORD:1`, and append the 
password using basic encryption to `lastPassword=REG_SZ:`.  

This allows pnabrowse to run without the -P option. To do this, you must also omit the `-U` and `D` options. pnabrowse continues to be governed by config.xml and therefore may reset these entries if the Web Interface does not have the authentication method properties set to allow the user to save the password.  

### Other configuration files

The `$ICAROOT/config/` directory also contains several other .ini files, including All\_Regions.ini, canonicalization.ini, regions.ini, Trusted\_Region.ini, Unknown\_Region.ini, and Untrusted\_Region.ini. These files offer administrators an alternative way to configure the client settings described in previous sections. The files also allow administrators to configure client selective trust, a security feature that restricts the characteristics of an ICA session depending on the server to which the client connects.   

For more information, see the configuration files in the `$ICAROOT/config/` directory. 

## Library files  

You can disable specific functionality from Citrix Workspace app for Linux by removing the appropriate shared library file (.dll or .so file) from a client installation. The following table describes these libraries.  

| File | Location | Description |
|---|---|---|
| ADPCM.DLL | /opt/Citrix/ICAClient | Provides support for low quality audio if Speex is not available. |
| AUDALSA.DLL | /opt/Citrix/ICAClient | Provides ALSA backend for the Client Audio Mapping Virtual Channel. |
| AUDOSS.DLL | /opt/Citrix/ICAClient | Provides OSS backend for the Client Audio Mapping Virtual Channel. | 
| CHARICONV.DLL | /opt/Citrix/ICAClient | Provides character conversion functionality using the facilities of the standard system libraries. An alternative version, CHARCONV.DLL, is available for embedded system environments that lack the necessary library support. Note that Citrix recommends you do not remove this library without replacing it with the alternative. |
| ctxusb | /opt/Citrix/ICAClient | Helper utility for Generic USB redirection. |
| ctxh264.so | /opt/Citrix/ICAClient | Decoder for H.264 images. |
| ctxh264\_fb.so | /opt/Citrix/ICAClient | Fallback decoder for H.264 images. |
| ctxjpeg.so | /opt/Citrix/ICAClient | Decoder for JPEG images. |
| ctxjpeg\_fb.so | /opt/Citrix/ICAClient | Fallback decoder for JPEG images when Version 6 of libjpeg is present. This decoder also supports libjpegturbo. |
| ctxjpeg\_fb\_8.so | /opt/Citrix/ICAClient | Fallback decoder for JPEG images when Version 8 of libjpeg is present. | 
| ctxusbd | /opt/Citrix/ICAClient | Daemon process for Generic USB redirection. | 
| ctx\_usb\_isactive | /opt/Citrix/ICAClient | Helper utility for Generic USB redirection. | 
| FlashContainer.bin | /opt/Citrix/ICAClient | Provides support for Flash redirection. | 
| gst\_play | /opt/Citrix/ICAClient/util | A GStreamer utility required for HDX Windows Multimedia Redirection. |
| gst\_read | /opt/Citrix/ICAClient/util | HDX RealTime Webcam Video Compression requires GStreamer 0.10.25 (or a later 0.10.x version), 
including the distribution's "plugins-good" package; or GStreamer 1.0 (or a later 1.x version), including the distribution’s “plugins-base,” “plugins-good,” “plugins-bad,” “plugins-ugly,” and “gstreamer-libav” packages. If GStreamer is not included in your Linux distribution, you can download it from [http://gstreamer.freedesktop.org](http://gstreamer.freedesktop.org). |
| libAMSDK.so | /opt/Citrix/ICAClient/lib | SDK used for communications between Workspace app and Authentication Manager. This is required for connections using storebrowse or selfservice, but not pnabrowse. |
| libcrypto.so | This is a system library. | Cryptographic functions used to authenticate to NTLM proxies. Can be downloaded from [http://www.openssl.org/](http://www.openssl.org/). |
| libproxy.so | /opt/Citrix/ICAClient | Contains functionality for using proxies and functionality for Citrix SSL Relay, which provides endto-end Secure Sockets Layer/ Transport Layer Security (SSL/TLS) encryption between specific servers and clients. |
| libcoreavc\_sdk.so | /opt/Citrix/ICAClient/lib | The library required by ctxh264\_fb.so. |  
| libgstflatstm.so | /opt/Citrix/ICAClient/util | The GStreamer plug-in required for HDX MultiStream Windows Media Redirection. |
| libkcph.so | /opt/Citrix/ICAClient/lib | Provides password change support for pnabrowse using Heimdal Kerberos. | 
| libkcpm.so | /opt/Citrix/ICAClient/lib | Provides password change support for pnabrowse using MIT Kerberos. | 
| new\_store | /opt/Citrix/ICAClient/util | A helper script used by npica.so to handle CR files. |
| npica.so | /opt/Citrix/ICAClient | Plug-in for web browsers that are compatible with Netscape software. |
| PDCRYPT1.DLL | /opt/Citrix/ICAClient | Contains basic Citrix encryption functionality. Citrix recommends that you do not remove this library. |
| PDCRYPT2.DLL | /opt/Citrix/ICAClient | Contains functionality for Citrix Secure ICA, which encrypts information sent between servers and clients. |  
| SPEEX.DLL | /opt/Citrix/ICAClient | Provides preferred support for low and medium quality audio.|  
| UIDialogLib.so | /opt/Citrix/ICAClient/lib | Allows creation of customized dialogs including for non-X Windows systems. See UI Dialog library earlier in this document. |  
| VDFLASH2.DLL | /opt/Citrix/ICAClient | Provides support for Flash redirection. | 
| VDCAM.DLL | /opt/Citrix/ICAClient | Provides support for bi-directional audio using Client Audio Mapping. |
| VDGUSB.DLL | /opt/Citrix/ICAClient | Provides support for Generic USB redirection.  
| VDGSTCAM.DLL | /opt/Citrix/ICAClient | Provides an experimental GStreamer based implementation of Client Audio Mapping. | 
| VDMM.DLL | /opt/Citrix/ICAClient | Contains functionality for HDX MultiStream Windows Media Redirection. |
| VDSCARD.DLL | /opt/Citrix/ICAClient | Contains functionality for smart card support. The support is based around the PC/SC standard, to which any deployment of Workspace app for Linux involving smart cards must adhere. | 
| VORBIS.DLL | /opt/Citrix/ICAClient | Provides preferred support for high quality audio. | 
  
 





  














 


  





  
 

 





  

 


 
 


 







  





 





   

  

  




    
  

 
 





  
  



