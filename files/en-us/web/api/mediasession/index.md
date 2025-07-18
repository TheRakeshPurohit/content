---
title: MediaSession
slug: Web/API/MediaSession
page-type: web-api-interface
browser-compat: api.MediaSession
---

{{APIRef("Media Session API")}}

The **`MediaSession`** interface of the {{domxref("Media Session API", "", "", "nocode")}} allows a web page to provide custom behaviors for standard media playback interactions, and to report metadata that can be sent by the user agent to the device or operating system for presentation in standardized user interface elements.

For example, a smartphone might have a standard panel in its lock screen that provides controls for media playback and information display. A browser on the device can use `MediaSession` to make browser playback controllable from that standard/global user interface.

## Instance properties

- {{domxref("MediaSession.metadata", "metadata")}}
  - : Returns an instance of {{domxref("MediaMetadata")}}, which contains rich media metadata for display in a platform UI.
- {{domxref("MediaSession.playbackState", "playbackState")}}
  - : Indicates whether the current media session is playing. Valid values are `none`, `paused`, or `playing`.

## Instance methods

- {{domxref("MediaSession.setActionHandler", "setActionHandler()")}}
  - : Sets an action handler for a media session action, such as play or pause.
- {{domxref("MediaSession.setCameraActive", "setCameraActive()")}}
  - : Indicates to the user agent whether the user's camera is considered to be active.
- {{domxref("MediaSession.setMicrophoneActive", "setMicrophoneActive()")}}
  - : Indicates to the user agent whether the user's microphone is considered to be currently muted.
- {{domxref("MediaSession.setPositionState", "setPositionState()")}}
  - : Sets the current playback position and speed of the media currently being presented.
- {{domxref("MediaSession.setScreenshareActive", "setScreenshareActive()")}} {{experimental_inline}}
  - : Indicates to the user agent the screenshare capture state desired by the page.

## Examples

### Setting up action handlers for a music player

The following example creates a new media session and assigns action handlers to it:

```js
if ("mediaSession" in navigator) {
  navigator.mediaSession.metadata = new MediaMetadata({
    title: "Unforgettable",
    artist: "Nat King Cole",
    album: "The Ultimate Collection (Remastered)",
    artwork: [
      {
        src: "https://dummyimage.com/96x96",
        sizes: "96x96",
        type: "image/png",
      },
      {
        src: "https://dummyimage.com/128x128",
        sizes: "128x128",
        type: "image/png",
      },
      {
        src: "https://dummyimage.com/192x192",
        sizes: "192x192",
        type: "image/png",
      },
      {
        src: "https://dummyimage.com/256x256",
        sizes: "256x256",
        type: "image/png",
      },
      {
        src: "https://dummyimage.com/384x384",
        sizes: "384x384",
        type: "image/png",
      },
      {
        src: "https://dummyimage.com/512x512",
        sizes: "512x512",
        type: "image/png",
      },
    ],
  });

  navigator.mediaSession.setActionHandler("play", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("pause", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("stop", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("seekbackward", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("seekforward", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("seekto", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("previoustrack", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("nexttrack", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("skipad", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("togglecamera", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("togglemicrophone", () => {
    /* Code excerpted. */
  });
  navigator.mediaSession.setActionHandler("hangup", () => {
    /* Code excerpted. */
  });
}
```

The following example sets up two functions for playing and pausing, then uses them as callbacks with the relevant action handlers.

```js
const actionHandlers = [
  // play
  [
    "play",
    async () => {
      // play our audio
      await audioEl.play();
      // set playback state
      navigator.mediaSession.playbackState = "playing";
      // update our status element
      updateStatus(allMeta[index], "Action: play  |  Track is playing…");
    },
  ],
  [
    "pause",
    () => {
      // pause out audio
      audioEl.pause();
      // set playback state
      navigator.mediaSession.playbackState = "paused";
      // update our status element
      updateStatus(allMeta[index], "Action: pause  |  Track has been paused…");
    },
  ],
];

for (const [action, handler] of actionHandlers) {
  try {
    navigator.mediaSession.setActionHandler(action, handler);
  } catch (error) {
    console.log(`The media session action "${action}" is not supported yet.`);
  }
}
```

### Using action handlers to control a slide presentation

The `"previousslide"` and `"nextslide"` action handlers can be used to handle moving forward and backward through a slide presentation, for example when the user puts their presentation into a {{domxref("Picture-in-Picture API", "Picture-in-Picture", "", "nocode")}} window, and presses the browser-supplied controls for navigating through slides.

```js
try {
  navigator.mediaSession.setActionHandler("previousslide", () => {
    log('> User clicked "Previous Slide" icon.');
    if (slideNumber > 1) slideNumber--;
    updateSlide();
  });
} catch (error) {
  log('Warning! The "previousslide" media session action is not supported.');
}

try {
  navigator.mediaSession.setActionHandler("nextslide", () => {
    log('> User clicked "Next Slide" icon.');
    slideNumber++;
    updateSlide();
  });
} catch (error) {
  log('Warning! The "nextslide" media session action is not supported.');
}
```

See [Presenting Slides / Media Session Sample](https://googlechrome.github.io/samples/media-session/slides.html) for a working example.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
