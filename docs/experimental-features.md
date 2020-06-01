# Experimental Features

## Audio optimization for Microsoft Teams

As an experimental feature, Citrix Workspace app provides audio optimization for Microsoft Teams running within a Citrix Virtual Desktop session.

> **Note:**
>
> Microsoft Teams audio optimization is supported only on x64 architecture.

For more information, see the [Optimization for Microsoft Teams](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/opt-ms-teams.html) and [Microsoft Teams redirection](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/policies/reference/ica-policy-settings/multimedia-policy-settings.html#microsoft-teams-redirection) sections in the Citrix Virtual Apps and Desktops documentation.

## Support for NetScaler App Experience (NSAP) virtual channel

As an experimental feature, all HDX Insight data is sourced from the NSAP virtual channel exclusively and sent uncompressed. This approach improves scalability and performance of sessions. The NSAP virtual channel is enabled by default. To disable it, toggle the VDNSAP flag `VDNSAP=Off` in the module.ini file.

For more information, see [HDX Insight](https://docs.citrix.com/en-us/linux-virtual-delivery-agent/current-release/configuration/hdx-insight.html) in Linux Virtual Delivery Agent documentation, and [HDX Insight](https://docs.citrix.com/en-us/citrix-application-delivery-management-service/analytics/hdx-insight.html) in Citrix Application Delivery Management service documentation.

## GStreamer 1.x support

In earlier releases, GStreamer 0.10 was the default version supported for multimedia redirection. Starting with this release, you can configure GStreamer 1.x as the default version.

**Limitations:**

-  When you play a video, forward and backward seek might not work as expected.
-  When you launch the Citrix Workspace app on ARMHF devices, GStreamer 1.x might not work as expected.

For more information, see [Enabling GStreamer 1.x](/en-us/citrix-workspace-app-for-linux/configure-xenapp.html#enabling-gstreamer-1x).

## Chromium Embedded Framework (CEF) for Browser Content Redirection (BCR)

The BCR feature redirects contents of a web browser to a client device, and creates a corresponding browser that embeds within the Citrix Workspace app.

In earlier releases, BCR used a WebkitGTK+ based overlay to render the content. However, on thin clients, there were performance issues. Starting with this release, BCR uses a CEF based overlay. This functionality enriches the user experience for BCR. It helps offload network usage, page processing, and graphics rendering to the endpoint.

For more information, see [Enabling CEF based BCR.](/en-us/citrix-workspace-app-for-linux/configure-xenapp.html#enabling-cef-based-bcr)

For information about BCR, see [Browser content redirection](https://docs.citrix.com/en-us/citrix-virtual-apps-desktops/multimedia/browser-content-redirection.html) in the Citrix Virtual Apps and Desktops documentation.

> **Notes:**
>
> -  The **pacexec** binary is removed from the x86 version of Citrix Workspace app.
> -  Citrix Files might not work with the “Workspace with Intelligence” feature.

## Secure SaaS with Citrix Embedded Browser

Secure access to SaaS applications provides a unified user experience that delivers published SaaS applications to the users. SaaS apps are available with single sign-on. Administrators can now protect the organization’s network and end-user devices from malware and data leaks by filtering access to specific websites and website categories.

Citrix Workspace app for Linux support the use of SaaS apps using the Access Control Service. The service enables administrators to provide a cohesive experience, integrating single sign-on, and content inspection.

**Prerequisite:**

To launch the SaaS applications, ensure libgtkglext1 package is available.

Delivering SaaS apps from the cloud has the following benefits:

-  Simple configuration – Easy to operate, update, and consume.
-  Single sign-on – Hassle-free log on with single sign-on.
-  Standard template for different apps – Template-based configuration of popular apps.

> **Note:**
>
> SaaS with Citrix Browser Engine is supported only on x64 and x86 platforms and not on ArmHardFloatPort (armhf) hardware.

For information on how to configure SaaS apps using Access Control Services, see the [Access Control](/en-us/citrix-access-control.html) documentation.

For more information about SaaS apps with Citrix Workspace app, see [Workspace configuration](/en-us/citrix-workspace-app-for-windows/configure.html#workspace-configuration) in in Citrix Workspace app for Windows documentation.

## GStreamer audio

### Switch to GStreamer audio

You can switch between your existing implementation and an implementation based on GStreamer, as follows.

**Note**: GStreamer 0.10.25 (or a later 0.10 version) is required, including its "plugins-good" package.

**Important**: Be aware that GStreamer audio has limitations that are described elsewhere in this section

If wfica encodes or decodes audio using CPU, VDCAM.DLL is normally loaded. In a GStreamer implementation, ensure that VDGSTCAM.DLL is loaded instead by editing the [ClientAudio] section of module.ini to include the appropriate driver name:

-  VDCAM.DLL - DriverName=VDCAM.DLL
-  VDGSTCAM.DLL - DriverName=VDGSTCAM.DLL

If VDGSTCAM is used for audio output, gst\_aud\_play passes the encoded audio stream to GStreamer with the correct codec information to decode the stream. For audio input, gst\_aud\_read reads the encoded audio stream from GStreamer.

The input and output pipelines are as follows:

-  Speex audio input - autoaudiosrc > audioconvert > speexenc > appsink
-  Vorbis audio input - autoaudiosrc > audioconvert > vorbisenc > oggmux > appsink
-  Speex audio output - appsrc > speexdec > audioconvert > autoaudiosink
-  Vorbix audio output - appsrc > oggdemux > vorbisdec > audioconvert > autoaudiosink

### Optimize GStreamer audio

If you have set up Citrix Workspace app to use the GStreamer framework, you can modify how audio is processed by it using the following settings in the [ClientAudio] section of the appropriate configuration file.

Before using this procedure, you should be familiar the GStreamer SDK, including the concepts of audio sinks and audio sources.

Reduce GStreamer startup time by setting:

-  GSTAudioSinkName - This is the GStreamer element that you want to use as the sink for audio. By default, this is autoaudiosink, the automatically detected audio sink.
-  GSTAudioSrcName - This is the GStreamer element that you want to use as the source for audio. By default, this is autoaudiosrc, the automatically detected audio source.
-  In GSTSpeexBufferingLatency, specify the amount of additional output buffering when rendering audio in Speex format. The default is 50 ms.
-  In GSTVorbisBufferingLatency, specify the amount of additional output buffering when rendering audio in Vorbis format. The default is 150 ms.

### Configure GStreamer in non-default locations

If GStreamer is installed in a non-default location (for example, /gstreamer), you must make the following changes in addition to adjusting the configuration file.

1.  Allow `$ICAROOT/util/gst_play` to link with GStreamer: `ldconfig/gstreamer/lib`
1.  In $ICAROOT, rename selfservice to selfservice.real.
1.  Create a shell script wrapper called selfservice and set an environment variable that GStreamer uses to locate its plug-ins:

```
#!/bin/sh export GST_PLUGIN_SYSTEM_PATH=/gstreamer/lib exec
/opt/Citrix /ICAClient/selfservice.real $@
```

**Note**: You can also create a similar wrapper for storebrowse.

### GStreamer audio limitations

Bear the following limitations in mind when implementing GStreamer audio.

#### armhf platform

No GStreamer processes run on the user device on the ARM hard float (armhf) platform. As a result, the features GStreamer audio and HDX Windows Multimedia Redirection, which rely on GStreamer, are not supported on this platform unless you are running Ubuntu 12.10 or later.

#### Recording

Audio input is not always functional on some user devices. Symptoms include an inability to record more than once or twice, an inability to record any input, and distorted input. There is no known workaround for this issue.

#### Pausing and resuming

Some audio software does not stop and restart the audio device when users pause, and then try to restart, playback. The software might also not issue any data to the device during silence. Both of these symptoms prevent new audio data from being played. Use the following setting to mitigate this problem.

In the [ClientAudio] section of module.ini, set GSTUseNoClock to True. This disables the built-in clock in GStreamer.

A disadvantage of using this setting is that any gaps in the audio that are caused by network outages result in permanently increased latency, since they are no longer detected.

### Alternatives to GStreamer audio

The advantages of using GStreamer audio can in some cases be achieved in other ways:

-  Playback in a separate thread - GStreamer lets you decode and play audio in a new process on a separate CPU. You can also achieve this without using GStreamer by ensuring that VDCAM.DLL, rather than VDGSTCAM.DLL, is loaded.
-  Hardware acceleration - GStreamer lets you encode and decode audio using hardware. You can also achieve this without GStreamer by replacing the supplied libvorbis.so or libspeex.so library files with your own. Any replacements must be API-compatible.