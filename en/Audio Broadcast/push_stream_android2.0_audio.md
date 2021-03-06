
---
title: Push Streams to the CDN
description: 
platform: Android
updatedAt: Thu Feb 21 2019 08:19:42 GMT+0000 (UTC)
---
# Push Streams to the CDN
## Introduction

The CDN live streaming feature enables a host (broadcaster) to transform the uplink stream into RTMP and distribute it through different channels such as the Web browser or streaming media player. 

> Contact sales@agora.io to enable Agora's CDN live streaming feature. 

Agora's CDN publishing solution is based on the following API methods to publish streams to the CDN, inject external audio streams, transcode, and set the output layout.

-   [`addPublishStreamUrl`](https://docs.agora.io/en/Audio%20Broadcast/API%20Reference/java/classio_1_1agora_1_1rtc_1_1_rtc_engine.html#a4445b4ca9509cc4e2966b6d308a8f08f)
-   [`removePublishStreamUrl`](https://docs.agora.io/en/Audio%20Broadcast/API%20Reference/java/classio_1_1agora_1_1rtc_1_1_rtc_engine.html#a87b3f2f17bce8f4cc42b3ee6312d30d4)
-   [`setLiveTranscoding`](https://docs.agora.io/en/Audio%20Broadcast/API%20Reference/java/classio_1_1agora_1_1rtc_1_1_rtc_engine.html#a3cb9804ae71819038022d7575834b88c)

This solution is flexible and allows:

-   Starting or stopping publishing to the CDN.
-   Adding or removing a streaming URL without interrupting the ongoing publishing.
-   Adding extra controls to the ongoing streams.
-   Using callbacks to monitor the status of the publishing.
-   Quick migration from the legacy approach to the new approach.


## Pushing Streams to the CDN

Contact [sales@agora.io](mailto:sales@agora.io) to enable this function.

> You can enable this function in Dashboard in future releases.
> -  A host can dynamically add or remove a URL after joining the channel.
> -  A host can set transcoding and the layout, for example, the canvas settings, only after joining a channel. The host still needs to set a 16 &times; 16 view when only publishing an audio stream to CDN.

The following figure shows a typical CDN-pushing scenario.

![](https://web-cdn.agora.io/docs-files/1550737160039)


### Sample Code:

```
// CDN transcoding settings.
LiveTranscoding config;
config.audioSampleRate = TYPE_44100;
config.audioChannels = 0;
// config.audioBitrate
config.width = 16;
config.height = 16;
config.videoFramerate = 15;
config.videoCodecProfile = HIGH;

// Sets the output layout for each user.
LiveTranscoding transcoding = new LiveTranscoding();
LiveTranscoding.TranscodingUser user = new LiveTranscoding.TranscodingUser();
user.uid = 123456;
transcoding.addUser(user);
user.x = 0;
user.audioChannel = 0;
user.y = 0;
user.width = 16;
user.height = 16;

rtcEngine.setLiveTranscoding(transcoding);
```

```
// Add a URL to which the host pushes a stream.
rtcEngine.addPublishStreamUrl(url, false);
```

```
// Remove a URL to which the host pushes a stream.
rtcEngine.removePublishStreamUrl(url);
```
