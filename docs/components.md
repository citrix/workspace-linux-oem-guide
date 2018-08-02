# Citrix Workspace app for Linux components 
 
This section describes the components that make up Citrix Workspace app for Linux and describes how developers can configure the client. Typically, such configuration may be required when the user interface of Workspace app for Linux is being replaced with a custom version  

## About Citrix Workspace app for Linux 

Citrix Workspace app for Linux is a Linux application that provides access to a session running on a server. When the connection to the server is established, the user can access desktops and applications, and work with files in a way similar to working on a local computer.  

Citrix Workspace app for Linux displays the session on the Linux workstation screen, and is fully integrated with other Linux X applications. The workstation’s mouse and keyboard can be used with applications in the usual way, and the user can set up key mappings to enter PC keys that are interpreted locally on the workstation.  

Generally, the features in Citrix Workspace app are performed by software, but it is possible to configure certain Citrix HDX features to take advantage of hardware or your own optimized implementation.  

## Components used by Citrix Workspace app for Linux
  
Citrix Workspace app for Linux contains the following files:

* selfservice - This program replaces the configuration manager, wfcmgr, and allows access to Citrix StoreFront or Program Neighborhood Agent services through the new self-service user interface (UI).  
* storebrowse - This program is equivalent to the deprecated pnabrowse utility. It queries StoreFront or Program Neighborhood Agent services for virtual desktops and published applications and allows access to them. 
* wfica - This program is the client engine that creates connections to the server and performs all of the functions of the connections.  
* Configuration files - These files are designed like Windows .ini files and provide configuration information. The default files are located in the `$ICAROOT/config/` directory. A user’s .ini files are located in `$HOME/.ICAClient`.  
* Keyboard mapping files - These files store the key mappings that allow Workspace app for Linux to interpret keystrokes made on keyboards of various types and layouts.  
* Library files - These shared library files control specific Workspace app for Linux features such as security and smart card support.  
* Background processes (daemons) - These provide functionality for several features such as StoreFront authentication, StoreFront connection, and USB redirection.  
* Helper processes - These run when features such as HDX MediaStream Windows Media Redirection are active.  
* Utilities - These are occasionally useful for checking system compatibility (hdxcheck.sh) or collecting information for Citrix Technical Support (lurdump), or installing new certificates (ctx\_rehash).  

## Command line utilities 
 
storebrowse replaces pnabrowse. The latter is still available and is documented as part of this release, but it is deprecated and does not support the new features in this release. Citrix does not recommend using pnabrowse, unless necessary, to create or customize connections.  

icabrowse is no longer available and is not documented as part of this release. 
 
## Authentication Manager 
 
Authentication Manager (AM) is a background process for Citrix Workspace app that manages credentials with StoreFront.  

A StoreFront server can at any time request credentials, which can take many forms. Authentication Manager is a long-lived daemon process that runs on the user device and is responsible for communicating with StoreFront. Authentication Manager can launch helper processes, when needed, to gather credentials from user input using the UI Dialog Library. The Service Record daemon manages the relationship between stores and Authentication Manager by supplying the latter with configuration information.
  
Storebrowse and selfservice communicate with Authentication Manager using a proprietary protocol.
  
## Related components
  
Citrix Workspace app deployments involve other Citrix components. These typically include XenDesktop, XenApp, StoreFront (which replaces Web Interface as the mechanism for publishing applications), and Secure Gateway or NetScaler® Gateway. Configuring and customizing these related components is not covered in this document. For information on each, see the [Product Documentation](http://docs.citrix.com/) site.  

 

