---
layout: default
title: "Types"
---

# Types

A set of types exposed from react-audio-visualizers-core.

- [`Audio`](#audio)
- [`AudioVisualizerCommonProps`](#audiovisualizercommonprops)
- [`AudioVisualizerEvents`](#audiovisualizerevents)
- [`AudioVisualizerStatus`](#audiovisualizerstatus)
- [`Color`](#color)

## `Audio`

The `Audio` is a type used to describe what the library accepts as audio. It can either be a `string`, a [`File`](https://developer.mozilla.org/en-US/docs/Web/API/File) or an [`ArrayBuffer`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer).


## `AudioVisualizerCommonProps`

The `AudioVisualizerCommonProps` is an interface with a list of common props shared between visualizers. See [`<AudioVisualizer>`](./AudioVisualizer.html) for a full list and description of each prop.

## `AudioVisualizerEvents`

A list of events that the audio visualizer can emit and can be accessed through [`onEvent`](./AudioVisualizer.html#onevent).

Here's a full list of possible events:

- **playing**
- **paused**
- **loading**
- **loaded**
- **error**

## `AudioVisualizerStatus`

An enum with the possible audio visualizer status, **playing** or **paused**. 

## `Color`

The `Color` is a type used to describe what the library accepts as color. It can either be a `string`, a `number` or a ThreeJS [`Color`](https://threejs.org/docs/#api/en/math/Color).
