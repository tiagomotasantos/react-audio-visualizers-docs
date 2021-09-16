---
layout: default
title: "Hooks"
---

# Hooks

A set of hooks exposed from react-audio-visualizers-core.

- [`useAudioVisualizerContext`](#useaudiovisualizercontext)

## `useAudioVisualizerContext`

The `useAudioVisualizerContext` hook gives access to the context of the core `<AudioVisualizer>` by returning an object with `audioContext` of type [`AudioContext`](https://developer.mozilla.org/en-US/docs/Web/API/AudioContext), `analyser` of type [`AnalyserNode`](https://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode) and `status` of type `AudioVisualizerStatus`.

See an usage example bellow:

```jsx
import { AudioVisualizerStatus, useAudioVisualizerContext } from 'react-audio-visualizers-core';

export const YourVisualizer = () => {
  const { audioContext, analyser, status } = useAudioVisualizerContext();
  const dataArray = new Uint8Array(analyser ? analyser.frequencyBinCount : 0);

    if (analyser && audioContext && status === AudioVisualizerStatus.playing) {
      analyser.getByteTimeDomainData(dataArray);

      // do stuff with dataArray
    }

    // render <AudioVisualizer> ...
};
```