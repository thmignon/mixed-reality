---
title: Using WebVR in Edge with Windows Mixed Reality
description: 
author: 
ms.author: leweaver
ms.date: 2/28/2018
ms.topic: article
keywords: 
---



# Using WebVR in Edge with Windows Mixed Reality

## Creating WebVR content for Windows Mixed reality immersive headsets

WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Creators Update as a developer unlock feature. Developers can now use this API to create immersive VR experiences on the web.

The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD. Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/en-us/microsoft-edge/platform/status/webvr/). The WebVR API surface area is present at all times within Microsoft Edge. However, a call to getVRDisplays() will only return a headset if the operating system has been placed in Developer Mode, and either a headset is plugged in or the simulator has been turned on.

## Viewing WebVR content in Windows Mixed Reality immersive headsets

Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/webvr).

## See Also
* [WebVR information](http://webvr.info)
* [WebVR specification](https://w3c.github.io/webvr/)
* [WebVR API](https://msdn.microsoft.com/en-us/library/mt806281(v=vs.85).aspx)
* [WebGL API](https://msdn.microsoft.com/en-us/library/bg182648(v=vs.85).aspx)
* [Gamepad API](https://msdn.microsoft.com/en-us/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)
* [Handling Lost Context in WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](http://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)