# Experimental Features
  
## GStreamer audio
  
### Switch to GStreamer audio  

You can switch between your existing implementation and an implementation based on GStreamer, as follows.  

**Note**: GStreamer 0.10.25 (or a later 0.10 version) is required, including its "plugins-good" package.
  
**Important**: Be aware that GStreamer audio has limitations that are described elsewhere in this section

If wfica encodes or decodes audio using CPU, VDCAM.DLL is normally loaded. In a GStreamer implementation, ensure that VDGSTCAM.DLL is loaded instead by editing the [ClientAudio] section of module.ini to include the appropriate driver name:  

* VDCAM.DLL - DriverName=VDCAM.DLL  
* VDGSTCAM.DLL - DriverName=VDGSTCAM.DLL  

If VDGSTCAM is used for audio output, gst\_aud\_play passes the encoded audio stream to GStreamer with the correct codec information to decode the stream. For audio input, gst\_aud\_read reads the encoded audio stream from GStreamer.  

The input and output pipelines are as follows:  

* Speex audio input - autoaudiosrc > audioconvert > speexenc > appsink  
* Vorbis audio input - autoaudiosrc > audioconvert > vorbisenc > oggmux > appsink  
* Speex audio output - appsrc > speexdec > audioconvert > autoaudiosink  
* Vorbix audio output - appsrc > oggdemux > vorbisdec > audioconvert > autoaudiosink

### Optimize GStreamer audio 
 
If you have set up Citrix Receiver to use the GStreamer framework, you can modify how audio is processed by it using the following settings in the [ClientAudio] section of the appropriate configuration file.  

Before using this procedure, you should be familiar the GStreamer SDK, including the concepts of audio sinks and audio sources.
  
Reduce GStreamer startup time by setting:  

* GSTAudioSinkName - This is the GStreamer element that you want to use as the sink for audio. By default, this is autoaudiosink, the automatically detected audio sink.  
* GSTAudioSrcName - This is the GStreamer element that you want to use as the source for audio. By default, this is autoaudiosrc, the automatically detected audio source.  
* In GSTSpeexBufferingLatency, specify the amount of additional output buffering when rendering audio in Speex format. The default is 50 ms.  
* In GSTVorbisBufferingLatency, specify the amount of additional output buffering when rendering audio in Vorbis format. The default is 150 ms. 

### Configure GStreamer in non-default locations
  
If GStreamer is installed in a non-default location (for example, /gstreamer), you must make the following changes in addition to adjusting the configuration file.  

1.	Allow `$ICAROOT/util/gst_play` to link with GStreamer: `ldconfig/gstreamer/lib`
2. In $ICAROOT, rename selfservice to selfservice.real.  
2.	Create a shell script wrapper called selfservice and set an environment variable that GStreamer uses to locate its plug-ins:

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

* Playback in a separate thread - GStreamer lets you decode and play audio in a new process on a separate CPU. You can also achieve this without using GStreamer by ensuring that VDCAM.DLL, rather than VDGSTCAM.DLL, is loaded.  
* Hardware acceleration - GStreamer lets you encode and decode audio using hardware. You can also achieve this without GStreamer by replacing the supplied libvorbis.so or libspeex.so library files with your own. Any replacements must be API-compatible. 

 
  
  
 
 
 

 
