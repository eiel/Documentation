
---
title: Live-related Issues
description: 
platform: Live-related Issues
updatedAt: Thu Nov 22 2018 08:43:11 GMT+0000 (UTC)
---
# Live-related Issues
This page provides common troubleshooting strategies for Agora's interactive broadcast products and services.

### Why can I hear the voice in the CDN broadcast but cannot see any image?
Check whether the app calls the setLiveTranscoding method.

### Why can two hosts join the same channel but cannot see each other?
Check the following:
* Ensure that the two hosts use the same App ID, especially when a customer has multiple App IDs.
* Ensure that the two hosts enter the same channel name and join the same channel.
* Ensure that the two hosts are connected to the Internet.

### I set the resolution as 640 x 360. Why is the actual resolution of the screen 640 x 352?
On some Android systems, the video widths must be multiples of 16. Hence, if you set the video width as 360 pixels, the actual width is 352 pixels.
